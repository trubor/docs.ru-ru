---
title: Ведение журнала с высокой производительностью в .NET
author: IEvangelist
description: Сведения о том, как использовать LoggerMessage для создания кэшируемых делегатов, которым нужно меньше выделений объектов в сценариях высокопроизводительного ведения журналов.
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "102402135"
---
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="6bf52-103">Ведение журнала с высокой производительностью в .NET</span><span class="sxs-lookup"><span data-stu-id="6bf52-103">High-performance logging in .NET</span></span>

<span data-ttu-id="6bf52-104">Класс <xref:Microsoft.Extensions.Logging.LoggerMessage> предоставляет функциональные возможности для создания кэшируемых делегатов, которым нужно меньше выделений объектов и вычислительных ресурсов, чем [методам расширения для средства ведения журнала](xref:Microsoft.Extensions.Logging.LoggerExtensions), таким как <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> и <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="6bf52-105">Для сценариев высокопроизводительного ведения журналов используйте шаблон <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="6bf52-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> предоставляет следующие преимущества производительности по сравнению с методами расширения для средства ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="6bf52-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="6bf52-107">Методы расширения для средства ведения журнала требуют "упаковку-преобразование" типов значений, таких как `int`, в `object`.</span><span class="sxs-lookup"><span data-stu-id="6bf52-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="6bf52-108">Шаблон <xref:Microsoft.Extensions.Logging.LoggerMessage> позволяет избежать упаковки-преобразования за счет статических полей <xref:System.Action> и методов расширения со строго типизированными параметрами.</span><span class="sxs-lookup"><span data-stu-id="6bf52-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="6bf52-109">Методы расширения для средства ведения журнала должны анализировать шаблон сообщения (именованную строку формата) при каждой записи сообщения журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="6bf52-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> требует анализировать шаблон всего один раз — при определении сообщения.</span><span class="sxs-lookup"><span data-stu-id="6bf52-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="6bf52-111">В этом примере приложения демонстрируются возможности <xref:Microsoft.Extensions.Logging.LoggerMessage> с рабочей службой для обработки приоритетной очереди.</span><span class="sxs-lookup"><span data-stu-id="6bf52-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="6bf52-112">Это приложение обрабатывает рабочие элементы в порядке приоритета.</span><span class="sxs-lookup"><span data-stu-id="6bf52-112">The app processes work items in priority order.</span></span> <span data-ttu-id="6bf52-113">По мере выполнения этих операций создаются сообщения журнала с помощью шаблона <xref:Microsoft.Extensions.Logging.LoggerMessage>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="6bf52-114">Определение сообщения средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="6bf52-114">Define a logger message</span></span>

<span data-ttu-id="6bf52-115">Примените [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A), чтобы создать делегат <xref:System.Action> для сохранения сообщения в журнал.</span><span class="sxs-lookup"><span data-stu-id="6bf52-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="6bf52-116">Перегрузки <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> позволяют передать до шести параметров типа в именованную строку формата (шаблон).</span><span class="sxs-lookup"><span data-stu-id="6bf52-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="6bf52-117">Строка, предоставляемая методу <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, является шаблоном, а не интерполированной строкой.</span><span class="sxs-lookup"><span data-stu-id="6bf52-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="6bf52-118">Заполнители заполняются в том порядке, в котором указаны типы.</span><span class="sxs-lookup"><span data-stu-id="6bf52-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="6bf52-119">Имена заполнителей в шаблоне должны быть описательными и согласованными между разными шаблонами.</span><span class="sxs-lookup"><span data-stu-id="6bf52-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="6bf52-120">Они выступают в качестве имен свойств в структурированных данных журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="6bf52-121">Мы рекомендуем использовать [стиль Pascal ](../../standard/design-guidelines/capitalization-conventions.md) для имен заполнителей.</span><span class="sxs-lookup"><span data-stu-id="6bf52-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="6bf52-122">Например, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="6bf52-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="6bf52-123">Каждое сообщение журнала является <xref:System.Action>, хранящимся в статическом поле, созданном [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span><span class="sxs-lookup"><span data-stu-id="6bf52-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="6bf52-124">Следующий пример приложения создает поле для описания сообщения журнала при обработке рабочих элементов.</span><span class="sxs-lookup"><span data-stu-id="6bf52-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

<span data-ttu-id="6bf52-125">Для <xref:System.Action> укажите:</span><span class="sxs-lookup"><span data-stu-id="6bf52-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="6bf52-126">уровень ведения журнала;</span><span class="sxs-lookup"><span data-stu-id="6bf52-126">The log level.</span></span>
- <span data-ttu-id="6bf52-127">уникальный идентификатор события (<xref:Microsoft.Extensions.Logging.EventId>) с именем статического метода расширения;</span><span class="sxs-lookup"><span data-stu-id="6bf52-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="6bf52-128">шаблон сообщения (именованная строка формата).</span><span class="sxs-lookup"><span data-stu-id="6bf52-128">The message template (named format string).</span></span>

<span data-ttu-id="6bf52-129">При выведении рабочих элементов из очереди для обработки приложение рабочей службы устанавливает следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="6bf52-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="6bf52-130">уровень ведения журнала — <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="6bf52-130">Log level to <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="6bf52-131">идентификатор события — `13` с именем метода `FailedToProcessWorkItem`;</span><span class="sxs-lookup"><span data-stu-id="6bf52-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="6bf52-132">шаблон сообщения (именованная строка формата) — строка.</span><span class="sxs-lookup"><span data-stu-id="6bf52-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

<span data-ttu-id="6bf52-133">Структурированные хранилища для ведения журнала могут использовать имя события, когда оно предоставляется вместе с идентификатором события, для улучшения ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="6bf52-134">Например, [Serilog](https://github.com/serilog/serilog-extensions-logging) использует имя события.</span><span class="sxs-lookup"><span data-stu-id="6bf52-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="6bf52-135"><xref:System.Action> вызывается с помощью строго типизированного метода расширения.</span><span class="sxs-lookup"><span data-stu-id="6bf52-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="6bf52-136">Метод `PriorityItemProcessed` записывает сообщение каждый раз, когда обрабатывается рабочий элемент.</span><span class="sxs-lookup"><span data-stu-id="6bf52-136">The `PriorityItemProcessed` method logs a message every time a work item is being processed.</span></span> <span data-ttu-id="6bf52-137">Метод `FailedToProcessWorkItem`, в свою очередь, вызывается только при возникновении исключения.</span><span class="sxs-lookup"><span data-stu-id="6bf52-137">Whereas, `FailedToProcessWorkItem` is called when (and if) an exception occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="6bf52-138">Изучите выходные данные консоли приложения:</span><span class="sxs-lookup"><span data-stu-id="6bf52-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="6bf52-139">Чтобы передать параметры в сообщение журнала, определите до шести типов при создании статического поля.</span><span class="sxs-lookup"><span data-stu-id="6bf52-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="6bf52-140">Пример приложения регистрирует сведения о рабочем элементе при обработке элементов, определяя тип `WorkItem` для поля <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="6bf52-141">Шаблон сообщения журнала делегата получает его значения заполнителей из предоставленных типов.</span><span class="sxs-lookup"><span data-stu-id="6bf52-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="6bf52-142">Этот пример приложения определяет делегат для добавления рабочего элемента, где используется параметр элемента `WorkItem`.</span><span class="sxs-lookup"><span data-stu-id="6bf52-142">The sample app defines a delegate for adding a work item where the item parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="6bf52-143">Статический метод расширения `PriorityItemProcessed`, который используется для сохранения в журнал сообщения об обработке рабочего элемента, получает рабочий элемент в качестве значения аргумента и передает его делегату <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="6bf52-144">В методе `ExecuteAsync` рабочей службы вызывается `PriorityItemProcessed` для записи сообщения в журнал.</span><span class="sxs-lookup"><span data-stu-id="6bf52-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="6bf52-145">Изучите выходные данные консоли приложения:</span><span class="sxs-lookup"><span data-stu-id="6bf52-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="6bf52-146">Определение области сообщения средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="6bf52-146">Define logger message scope</span></span>

<span data-ttu-id="6bf52-147">Метод [DefineScope(String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) создает делегат <xref:System.Func%601> для определения [области журнала](logging.md#log-scopes).</span><span class="sxs-lookup"><span data-stu-id="6bf52-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="6bf52-148">Перегрузки <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> позволяют передать до трех параметров типа в именованную строку формата (шаблон).</span><span class="sxs-lookup"><span data-stu-id="6bf52-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="6bf52-149">Как и в случае с методом <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, строка, предоставляемая методу <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>, является шаблоном, а не интерполированной строкой.</span><span class="sxs-lookup"><span data-stu-id="6bf52-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="6bf52-150">Заполнители заполняются в том порядке, в котором указаны типы.</span><span class="sxs-lookup"><span data-stu-id="6bf52-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="6bf52-151">Имена заполнителей в шаблоне должны быть описательными и согласованными между разными шаблонами.</span><span class="sxs-lookup"><span data-stu-id="6bf52-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="6bf52-152">Они выступают в качестве имен свойств в структурированных данных журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="6bf52-153">Мы рекомендуем использовать [стиль Pascal ](../../standard/design-guidelines/capitalization-conventions.md) для имен заполнителей.</span><span class="sxs-lookup"><span data-stu-id="6bf52-153">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="6bf52-154">Например, `{Item}`, `{DateTime}`.</span><span class="sxs-lookup"><span data-stu-id="6bf52-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="6bf52-155">Определите [область журнала](logging.md#log-scopes), чтобы применить последовательность сообщений журнала с помощью метода <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bf52-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span> <span data-ttu-id="6bf52-156">Включите `IncludeScopes` в раздел средства ведения журнала консоли в файле *appsettings.json*:</span><span class="sxs-lookup"><span data-stu-id="6bf52-156">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="6bf52-157">Для создания области журнала добавьте поле, содержащее делегат <xref:System.Func%601> для области.</span><span class="sxs-lookup"><span data-stu-id="6bf52-157">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="6bf52-158">Пример приложения создает поле `_processingWorkScope` (*Internal/LoggerExtensions.cs*):</span><span class="sxs-lookup"><span data-stu-id="6bf52-158">The sample app creates a field called `_processingWorkScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="6bf52-159">Используйте <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> для создания делегата.</span><span class="sxs-lookup"><span data-stu-id="6bf52-159">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="6bf52-160">Можно указать до трех типов для использования в качестве аргументов шаблона при вызове делегата.</span><span class="sxs-lookup"><span data-stu-id="6bf52-160">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="6bf52-161">Этот пример приложения использует шаблон сообщения, который содержит дату и время начала обработки.</span><span class="sxs-lookup"><span data-stu-id="6bf52-161">The sample app uses a message template that includes the date time in which processing started:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="6bf52-162">Предоставьте статический метод расширения для сообщения журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-162">Provide a static extension method for the log message.</span></span> <span data-ttu-id="6bf52-163">Включите любые параметры типа для именованных свойств, отображаемых в шаблоне сообщений.</span><span class="sxs-lookup"><span data-stu-id="6bf52-163">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="6bf52-164">Этот пример приложения принимает `DateTime` в качестве настраиваемой метки времени для сохранения в журнал и возвращает `_processingWorkScope`.</span><span class="sxs-lookup"><span data-stu-id="6bf52-164">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="6bf52-165">Область создает оболочку для вызовов расширения ведения журнала в блоке [using](../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6bf52-165">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="6bf52-166">Изучите сообщения журнала в выходных данных консоли приложения:</span><span class="sxs-lookup"><span data-stu-id="6bf52-166">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="6bf52-167">Следующий результат демонстрирует упорядочение сообщений журнала по приоритету, с указанием сообщения об области журнала.</span><span class="sxs-lookup"><span data-stu-id="6bf52-167">The following result shows priority ordering of log messages with the log scope message included:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a><span data-ttu-id="6bf52-168">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6bf52-168">See also</span></span>

- [<span data-ttu-id="6bf52-169">Ведение журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="6bf52-169">Logging in .NET</span></span>](logging.md)
