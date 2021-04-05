---
title: Добавление инструментирования распределенной трассировки — .NET
description: Учебник по инструментированию распределенных трассировок в приложениях .NET
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: eeb065d1ac39dd34d9b27e2ad63195818d0d6493
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111517"
---
# <a name="adding-distributed-tracing-instrumentation"></a><span data-ttu-id="1f524-103">Добавление инструментирования распределенной трассировки</span><span class="sxs-lookup"><span data-stu-id="1f524-103">Adding distributed tracing instrumentation</span></span>

<span data-ttu-id="1f524-104">**Эта статья применяется к: ✔️** .NET Core 2.1 и более поздних версий **и**.NET Framework 4.5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="1f524-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="1f524-105">Приложения .NET можно инструментировать с использованием API <xref:System.Diagnostics.Activity?displayProperty=nameWithType> для создания данных телеметрии распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="1f524-105">.NET applications can be instrumented using the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> API to produce distributed tracing telemetry.</span></span> <span data-ttu-id="1f524-106">Некоторые инструментирования встроены в стандартные библиотеки .NET, но вам может потребоваться добавить дополнительные для упрощения диагностики кода.</span><span class="sxs-lookup"><span data-stu-id="1f524-106">Some instrumentation is built-in to standard .NET libraries but you may want to add more to make your code more easily diagnosable.</span></span> <span data-ttu-id="1f524-107">В этом учебнике вы добавите новое настраиваемое инструментирование распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="1f524-107">In this tutorial you will add new custom distributed tracing instrumentation.</span></span> <span data-ttu-id="1f524-108">Дополнительные сведения о записи данных телеметрии, создаваемых этим инструментированием, см. [в руководстве по сбору данных](distributed-tracing-instrumentation-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="1f524-108">See [the collection tutorial](distributed-tracing-instrumentation-walkthroughs.md) to learn more about recording the telemetry produced by this instrumentation.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f524-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="1f524-109">Prerequisites</span></span>

- <span data-ttu-id="1f524-110">[Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="1f524-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

## <a name="an-initial-app"></a><span data-ttu-id="1f524-111">Начальное приложение</span><span class="sxs-lookup"><span data-stu-id="1f524-111">An initial app</span></span>

<span data-ttu-id="1f524-112">Сначала вы создадите пример приложения, собирающий данные телеметрии с помощью OpenTelemetry, но еще не имеющий инструментирования.</span><span class="sxs-lookup"><span data-stu-id="1f524-112">First you will create a sample app that collects telemetry using OpenTelemetry, but doesn't yet have any instrumentation.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="1f524-113">В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="1f524-113">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="1f524-114">Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="1f524-114">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="1f524-115">Добавьте пакеты NuGet [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) и [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/), которые будут использоваться для сбора данных телеметрии.</span><span class="sxs-lookup"><span data-stu-id="1f524-115">Add the [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) and [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet packages which will be used to collect the telemetry.</span></span>

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="1f524-116">Замените содержимое созданного файла Program.cs исходным кодом примера.</span><span class="sxs-lookup"><span data-stu-id="1f524-116">Replace the contents of the generated Program.cs with this example source:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static async Task Main(string[] args)
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork("banana", 8);
            Console.WriteLine("Example work done");
        }

        // All the functions below simulate doing some arbitrary work
        static async Task DoSomeWork(string foo, int bar)
        {
            await StepOne();
            await StepTwo();
        }

        static async Task StepOne()
        {
            await Task.Delay(500);
        }

        static async Task StepTwo()
        {
            await Task.Delay(1000);
        }
    }
}
```

<span data-ttu-id="1f524-117">В приложении еще нет инструментирования, поэтому сведения трассировки для отображения отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="1f524-117">The app has no instrumentation yet so there is no trace information to display:</span></span>

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="1f524-118">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="1f524-118">Best Practices</span></span>

<span data-ttu-id="1f524-119">Только разработчикам приложений необходимо ссылаться на стороннюю библиотеку для сбора данных телеметрии распределенной трассировки, например OpenTelemetry в этом примере.</span><span class="sxs-lookup"><span data-stu-id="1f524-119">Only app developers need to reference an optional 3rd party library for collecting the distributed trace telemetry, such as OpenTelemetry in this example.</span></span> <span data-ttu-id="1f524-120">Авторы библиотек .NET могут ограничиться только API-интерфейсами в System.Diagnostics.DiagnosticSource, который является частью среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="1f524-120">.NET library authors can exclusively rely on APIs in System.Diagnostics.DiagnosticSource which is part of .NET runtime.</span></span> <span data-ttu-id="1f524-121">Это гарантирует, что библиотеки будут работать в широком спектре приложений .NET, независимо от предпочтений разработчика приложения в отношении того, какую библиотеку или какого поставщика использовать для сбора данных телеметрии.</span><span class="sxs-lookup"><span data-stu-id="1f524-121">This ensures that libraries will run in a wide range of .NET apps, regardless of the app developer's preferences about which library or vendor to use for collecting telemetry.</span></span>

## <a name="adding-basic-instrumentation"></a><span data-ttu-id="1f524-122">Добавление базового инструментирования</span><span class="sxs-lookup"><span data-stu-id="1f524-122">Adding Basic Instrumentation</span></span>

<span data-ttu-id="1f524-123">Приложения и библиотеки добавляют инструментирование распределенной трассировки с помощью классов <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> и <xref:System.Diagnostics.Activity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-123">Applications and libraries add distributed tracing instrumentation using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="1f524-124">ActivitySource</span><span class="sxs-lookup"><span data-stu-id="1f524-124">ActivitySource</span></span>

<span data-ttu-id="1f524-125">Сначала создайте экземпляр ActivitySource.</span><span class="sxs-lookup"><span data-stu-id="1f524-125">First create an instance of ActivitySource.</span></span> <span data-ttu-id="1f524-126">ActivitySource предоставляет API-интерфейсы для создания и запуска объектов действий Activity.</span><span class="sxs-lookup"><span data-stu-id="1f524-126">ActivitySource provides APIs to create and start Activity objects.</span></span> <span data-ttu-id="1f524-127">Добавьте статическую переменную ActivitySource над Main() и `using System.Diagnostics;` в инструкциях using.</span><span class="sxs-lookup"><span data-stu-id="1f524-127">Add the static ActivitySource variable above Main() and `using System.Diagnostics;` to the using statements.</span></span>

```csharp
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        private static ActivitySource source = new ActivitySource("Sample.DistributedTracing", "1.0.0");

        static async Task Main(string[] args)
        {
            ...    
```

#### <a name="best-practices"></a><span data-ttu-id="1f524-128">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="1f524-128">Best Practices</span></span>

- <span data-ttu-id="1f524-129">Создайте класс ActivitySource и сохраните его в статической переменной, а затем используйте этот экземпляр при необходимости.</span><span class="sxs-lookup"><span data-stu-id="1f524-129">Create the ActivitySource once, store it in a static variable and use that instance as long as needed.</span></span>
<span data-ttu-id="1f524-130">Каждая библиотека и каждый из вложенных компонентов библиотеки могут (и часто должны) создавать собственный источник.</span><span class="sxs-lookup"><span data-stu-id="1f524-130">Each library or library sub-component can (and often should) create its own source.</span></span> <span data-ttu-id="1f524-131">Рекомендуется создать источник вместо повторного использования существующего, если предполагается, что разработчикам приложений понадобится возможность включения и отключения телеметрии действий в источниках независимым образом.</span><span class="sxs-lookup"><span data-stu-id="1f524-131">Consider creating a new source rather than re-using an existing one if you anticipate app developers would appreciate being able to enable and disable the Activity telemetry in the sources independently.</span></span>

- <span data-ttu-id="1f524-132">Имя источника, передаваемое конструктору, должно быть уникальным, чтобы избежать конфликтов с другими источниками.</span><span class="sxs-lookup"><span data-stu-id="1f524-132">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span>
<span data-ttu-id="1f524-133">Рекомендуется использовать иерархическое имя, содержащее имя сборки, и (при необходимости) имя компонента, если в одной сборке есть несколько источников.</span><span class="sxs-lookup"><span data-stu-id="1f524-133">It is recommended to use a hierarchical name that contains the assembly name and optionally a component name if there are multiple sources within the same assembly.</span></span> <span data-ttu-id="1f524-134">Например, `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="1f524-134">For example, `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="1f524-135">Если сборка добавляет инструментирование для кода во второй независимой сборке, имя должно основываться на сборке, определяющей ActivitySource, а не на сборке, код которой инструментируется.</span><span class="sxs-lookup"><span data-stu-id="1f524-135">If an assembly is adding instrumentation for code in a 2nd independent assembly, the name should be based on the assembly that defines the ActivitySource, not the assembly whose code is being instrumented.</span></span>

- <span data-ttu-id="1f524-136">Параметр version является необязательным.</span><span class="sxs-lookup"><span data-stu-id="1f524-136">The version parameter is optional.</span></span> <span data-ttu-id="1f524-137">Рекомендуется указывать версию, если вы выпускаете несколько версий библиотеки и вносите изменения в инструментированные данные телеметрии.</span><span class="sxs-lookup"><span data-stu-id="1f524-137">It is recommended to provide the version in case you release multiple versions of the library and make changes to the instrumented telemetry.</span></span>

> [!NOTE]
> <span data-ttu-id="1f524-138">OpenTelemetry использует альтернативные термины "трассировщик" и "рабочий интервал".</span><span class="sxs-lookup"><span data-stu-id="1f524-138">OpenTelemetry uses alternate terms 'Tracer' and 'Span'.</span></span> <span data-ttu-id="1f524-139">В .NET ActivitySource — это реализация трассировщика, а действие — это реализация рабочего интервала.</span><span class="sxs-lookup"><span data-stu-id="1f524-139">In .NET 'ActivitySource' is the implementation of Tracer and Activity is the implementation of 'Span'.</span></span> <span data-ttu-id="1f524-140">Тип Activity в .NET начал использоваться значительно раньше спецификации OpenTelemetry, и исходное именование .NET было сохранено для обеспечения согласованности в рамках экосистемы .NET и совместимости приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="1f524-140">.NET's Activity type long pre-dates the OpenTelemetry specification and the original .NET naming has been preserved for consistency within the .NET ecosystem and .NET application compatibility.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="1f524-141">Создание объектов Activity</span><span class="sxs-lookup"><span data-stu-id="1f524-141">Activity Creation</span></span>

<span data-ttu-id="1f524-142">Используйте объект ActivitySource для запуска и остановки объектов Activity в рамках значимых единиц работы.</span><span class="sxs-lookup"><span data-stu-id="1f524-142">Use the ActivitySource object to Start and Stop Activity objects around meaningful units of work.</span></span> <span data-ttu-id="1f524-143">Измените DoSomeWork(), используя приведенный здесь код.</span><span class="sxs-lookup"><span data-stu-id="1f524-143">Update DoSomeWork() with the code shown here:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }
```

<span data-ttu-id="1f524-144">Теперь при запуске приложения отображается новое регистрируемое действие Activity.</span><span class="sxs-lookup"><span data-stu-id="1f524-144">Running the app now shows the new Activity being logged:</span></span>

```dotnetcli
> dotnet run
Activity.Id:          00-f443e487a4998c41a6fd6fe88bae644e-5b7253de08ed474f-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:36:51.4720202Z
Activity.Duration:    00:00:01.5025842
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 067f4bb5-a5a8-4898-a288-dec569d6dbef
```

#### <a name="notes"></a><span data-ttu-id="1f524-145">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f524-145">Notes</span></span>

- <span data-ttu-id="1f524-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> создает и запускает действие в одно время.</span><span class="sxs-lookup"><span data-stu-id="1f524-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> creates and starts the activity at the same time.</span></span> <span data-ttu-id="1f524-147">В приведенном шаблоне кода используется блок `using`, который автоматически удаляет созданный объект Activity после выполнения блока.</span><span class="sxs-lookup"><span data-stu-id="1f524-147">The listed code pattern is using the `using` block which automatically disposes the created Activity object after executing the block.</span></span> <span data-ttu-id="1f524-148">Освобождение объекта Activity приведет к его остановке, поэтому коду не нужно явно вызывать <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-148">Disposing the Activity object will stop it so the code doesn't need to explicitly call <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="1f524-149">Это упрощает шаблон кода.</span><span class="sxs-lookup"><span data-stu-id="1f524-149">That simplifies the coding pattern.</span></span>

- <span data-ttu-id="1f524-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> внутренним образом определяет наличие прослушивателей, записывающих действие.</span><span class="sxs-lookup"><span data-stu-id="1f524-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> internally determines if there are any listeners recording the Activity.</span></span> <span data-ttu-id="1f524-151">Если зарегистрированных прослушивателей нет или есть незаинтересованные прослушиватели, StartActivity() возвратит `null`, не создавая объект Activity.</span><span class="sxs-lookup"><span data-stu-id="1f524-151">If there are no registered listeners or there are listeners which are not interested, StartActivity() will return `null` and avoid creating the Activity object.</span></span> <span data-ttu-id="1f524-152">Это оптимизация производительности, чтобы шаблон кода по-прежнему можно было использовать в функциях, вызываемых очень часто.</span><span class="sxs-lookup"><span data-stu-id="1f524-152">This is a performance optimization so that the code pattern can still be used in functions that are called very frequently.</span></span>

## <a name="optional-populate-tags"></a><span data-ttu-id="1f524-153">Дополнительно: заполнение тегов</span><span class="sxs-lookup"><span data-stu-id="1f524-153">Optional: Populate tags</span></span>

<span data-ttu-id="1f524-154">Действия поддерживают данные типа "ключ — значение", называемые тегами. Они обычно используются для хранения любых параметров работы, которые могут быть полезны для диагностики.</span><span class="sxs-lookup"><span data-stu-id="1f524-154">Activities support key-value data called Tags, commonly used to store any parameters of the work that may be useful for diagnostics.</span></span> <span data-ttu-id="1f524-155">Измените DoSomeWork(), чтобы включить их.</span><span class="sxs-lookup"><span data-stu-id="1f524-155">Update DoSomeWork() to include them:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                await StepTwo();
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-2b56072db8cb5a4496a4bfb69f46aa06-7bc4acda3b9cce4d-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:37:31.4949570Z
Activity.Duration:    00:00:01.5417719
Activity.TagObjects:
    foo: banana
    bar: 8
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 25bbc1c3-2de5-48d9-9333-062377fea49c

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="1f524-156">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="1f524-156">Best Practices</span></span>

- <span data-ttu-id="1f524-157">Как упоминалось выше, значение `activity`, возвращаемое <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>, может быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="1f524-157">As mentioned above, `activity` returned by <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> may be null.</span></span> <span data-ttu-id="1f524-158">Оператор объединения с NULL ?.</span><span class="sxs-lookup"><span data-stu-id="1f524-158">The null-coallescing operator ?.</span></span> <span data-ttu-id="1f524-159">в C# удобно использовать, чтобы вызвать только <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> в случае, если действие не равно NULL.</span><span class="sxs-lookup"><span data-stu-id="1f524-159">in C# is a convenient short-hand to only invoke <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> if activity is not null.</span></span> <span data-ttu-id="1f524-160">Это поведение аналогично следующему.</span><span class="sxs-lookup"><span data-stu-id="1f524-160">The behavior is identical to writing:</span></span>

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- <span data-ttu-id="1f524-161">OpenTelemetry предоставляет набор рекомендуемых [соглашений](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) по настройке тегов для действий, представляющих общие типы работы приложения.</span><span class="sxs-lookup"><span data-stu-id="1f524-161">OpenTelemetry provides a set of recommended [conventions](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) for setting Tags on Activities that represent common types of application work.</span></span>

- <span data-ttu-id="1f524-162">Если вы осуществляете инструментирование функций с высокими требованиями к производительности, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> используется как указание того, будет ли любой код, прослушивающий действия, считывать вспомогательные данные, такие как теги.</span><span class="sxs-lookup"><span data-stu-id="1f524-162">If you are instrumenting functions with high performance requirements, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> is a hint that indicates whether any of the code listening to Activities intends to read auxilliary information such as Tags.</span></span> <span data-ttu-id="1f524-163">Если ни один из прослушивателей не считывает эти данные, инструментированному коду не нужно тратить циклы работы ЦП на их заполнение.</span><span class="sxs-lookup"><span data-stu-id="1f524-163">If no listener will read it then there is no need for the instrumented code to spend CPU cycles populating it.</span></span> <span data-ttu-id="1f524-164">Для простоты этот пример не применяет подобную оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="1f524-164">For simplicity this sample doesn't apply that optimization.</span></span>

## <a name="optional-adding-events"></a><span data-ttu-id="1f524-165">Дополнительно: добавление событий</span><span class="sxs-lookup"><span data-stu-id="1f524-165">Optional: Adding Events</span></span>

<span data-ttu-id="1f524-166">События — это сообщения с метками времени, которые могут подключать к действиям произвольный поток дополнительных диагностических данных.</span><span class="sxs-lookup"><span data-stu-id="1f524-166">Events are timestamped messages that can attach an arbitrary stream of additional diagnostic data to Activities.</span></span> <span data-ttu-id="1f524-167">Добавьте в действие некоторые события.</span><span class="sxs-lookup"><span data-stu-id="1f524-167">Add some events to the Activity:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-82cf6ea92661b84d9fd881731741d04e-33fff2835a03c041-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:39:10.6902609Z
Activity.Duration:    00:00:01.5147582
Activity.TagObjects:
    foo: banana
    bar: 8
Activity.Events:
    Part way there [3/18/2021 10:39:11 AM +00:00]
    Done now [3/18/2021 10:39:12 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: ea7f0fcb-3673-48e0-b6ce-e4af5a86ce4f

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="1f524-168">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="1f524-168">Best Practices</span></span>

- <span data-ttu-id="1f524-169">События хранятся в списке в памяти до тех пор, пока они не смогут быть переданы, что делает этот механизм применимым только для записи небольшого количества событий.</span><span class="sxs-lookup"><span data-stu-id="1f524-169">Events are stored in an in-memory list until they can be transmitted which makes this mechanism only suitable for recording a modest number of events.</span></span> <span data-ttu-id="1f524-170">При большом или неограниченном числе событий лучше подойдет использование API ведения журнала, ориентированного на данную задачу, такого как [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/).</span><span class="sxs-lookup"><span data-stu-id="1f524-170">For a large or unbounded volume of events using a logging API focused on this task such as [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) is a better choice.</span></span> <span data-ttu-id="1f524-171">ILogger также гарантирует, что данные о ведении журнала будут доступны независимо от того, планирует ли разработчик приложения использовать распределенную трассировку.</span><span class="sxs-lookup"><span data-stu-id="1f524-171">ILogger also ensures that the logging information will be available regardless whether the app developer opts to use distributed tracing.</span></span>
<span data-ttu-id="1f524-172">ILogger поддерживает автоматическую запись идентификаторов активных действий, поэтому сообщения, регистрируемые через этот API, по-прежнему могут быть сопоставлены с распределенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="1f524-172">ILogger supports automatically capturing the active Activity IDs so messages logged via that API can still be correlated with the distributed trace.</span></span>

## <a name="optional-adding-status"></a><span data-ttu-id="1f524-173">Дополнительно: добавление состояния</span><span class="sxs-lookup"><span data-stu-id="1f524-173">Optional: Adding Status</span></span>

<span data-ttu-id="1f524-174">OpenTelemetry позволяет каждому действию сообщать [состояние](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status), представляющее успешный или неудачный результат работы.</span><span class="sxs-lookup"><span data-stu-id="1f524-174">OpenTelemetry allows each Activity to report a [Status](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status) that represents the pass/fail result of the work.</span></span> <span data-ttu-id="1f524-175">Сейчас в .NET нет строго типизированного API для этой цели, однако есть установленное соглашение об использовании тегов:</span><span class="sxs-lookup"><span data-stu-id="1f524-175">.NET does not currently have a strongly typed API for this purpose but there is an established convention using Tags:</span></span>

- <span data-ttu-id="1f524-176">`otel.status_code` — это имя тега, используемое для хранения `StatusCode`.</span><span class="sxs-lookup"><span data-stu-id="1f524-176">`otel.status_code` is the Tag name used to store `StatusCode`.</span></span> <span data-ttu-id="1f524-177">Значения для тега StatusCode должны быть одной из строк UNSET, OK или ERROR, которые соответствуют перечислениям `Unset`, `Ok` и `Error` из StatusCode.</span><span class="sxs-lookup"><span data-stu-id="1f524-177">Values for the StatusCode tag must be one of the strings "UNSET", "OK", or "ERROR", which correspond respectively to the enums `Unset`, `Ok`, and `Error` from StatusCode.</span></span>
- <span data-ttu-id="1f524-178">`otel.status_description` — это имя тега, используемое для хранения необязательного `Description`.</span><span class="sxs-lookup"><span data-stu-id="1f524-178">`otel.status_description` is the Tag name used to store the optional `Description`</span></span>

<span data-ttu-id="1f524-179">Измените DoSomeWork(), чтобы задать состояние.</span><span class="sxs-lookup"><span data-stu-id="1f524-179">Update DoSomeWork() to set status:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
                
                // Pretend something went wrong
                activity?.SetTag("otel.status_code", "ERROR");
                activity?.SetTag("otel.status_description", "Use this text give more information about the error");
            }
        }
```

## <a name="optional-add-additional-activities"></a><span data-ttu-id="1f524-180">Дополнительно: добавление дополнительных действий</span><span class="sxs-lookup"><span data-stu-id="1f524-180">Optional: Add Additional Activities</span></span>

<span data-ttu-id="1f524-181">Действия могут быть вложенными для описания частей более крупной единицы работы.</span><span class="sxs-lookup"><span data-stu-id="1f524-181">Activities can be nested to describe portions of a larger unit of work.</span></span> <span data-ttu-id="1f524-182">Это может быть особенно удобно для частей кода, которые могут выполняться медленно, или для лучшего выявления сбоев, вызванных отдельными внешними зависимостями.</span><span class="sxs-lookup"><span data-stu-id="1f524-182">This can be particularly valuable around portions of code that might not execute quickly or to better localize failures that come from specific external dependencies.</span></span> <span data-ttu-id="1f524-183">Хотя в этом примере действие используется в каждом методе, это сделано исключительно по причине сведения лишнего кода к минимуму.</span><span class="sxs-lookup"><span data-stu-id="1f524-183">Although this sample uses an Activity in every method, that is solely because extra code has been minimized.</span></span> <span data-ttu-id="1f524-184">В более крупных и реалистичных проектах использование действия в каждом методе приведет к созданию очень подробных трассировок и поэтому не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="1f524-184">In a larger and more realistic project using an Activity in every method would produce extremely verbose traces so it is not recommended.</span></span>

<span data-ttu-id="1f524-185">Измените StepOne и StepTwo, чтобы добавить дополнительную трассировку для следующих отдельных шагов.</span><span class="sxs-lookup"><span data-stu-id="1f524-185">Update StepOne and StepTwo to add more tracing around these separate steps:</span></span>

```csharp
        static async Task StepOne()
        {
            using (Activity activity = source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity activity = source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-39cac574e8fda44b-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4278822Z
Activity.Duration:    00:00:00.5051364
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-4ccccb6efdc59546-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.9441095Z
Activity.Duration:    00:00:01.0052729
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4256627Z
Activity.Duration:    00:00:01.5286408
Activity.TagObjects:
    foo: banana
    bar: 8
    otel.status_code: ERROR
    otel.status_description: Use this text give more information about the error
Activity.Events:
    Part way there [3/18/2021 10:40:51 AM +00:00]
    Done now [3/18/2021 10:40:52 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Example work done
```

<span data-ttu-id="1f524-186">Обратите внимание, что StepOne и StepTwo включают в себя ParentId, который ссылается на SomeWork.</span><span class="sxs-lookup"><span data-stu-id="1f524-186">Notice that both StepOne and StepTwo include a ParentId that refers to SomeWork.</span></span> <span data-ttu-id="1f524-187">Консоль не обеспечивает качественную визуализацию вложенных деревьев работы, но многие средства просмотра на базе графического пользовательского интерфейса, такие как [Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md), могут отображать его в виде диаграммы Ганта.</span><span class="sxs-lookup"><span data-stu-id="1f524-187">The console is not a great visualization of nested trees of work, but many GUI viewers such as [Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) can show this as a Gantt chart:</span></span>

<span data-ttu-id="1f524-188">[![Диаграмма Ганта в средстве Zipkin](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span><span class="sxs-lookup"><span data-stu-id="1f524-188">[![Zipkin Gantt chart](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span></span>

### <a name="optional-activitykind"></a><span data-ttu-id="1f524-189">Дополнительно: ActivityKind</span><span class="sxs-lookup"><span data-stu-id="1f524-189">Optional: ActivityKind</span></span>

<span data-ttu-id="1f524-190">Действия имеют свойство <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType>, описывающее связь между действием и его родительским и дочерними объектами.</span><span class="sxs-lookup"><span data-stu-id="1f524-190">Activities have an <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> property which describes the relationship between the Activity, its parent and its children.</span></span> <span data-ttu-id="1f524-191">По умолчанию для всех новых действий задано значение <xref:System.Diagnostics.ActivityKind.Internal>, подходящее для действий, которые являются внутренней операцией в приложении без удаленных родительских или дочерних объектов.</span><span class="sxs-lookup"><span data-stu-id="1f524-191">By default all new Activities are set to <xref:System.Diagnostics.ActivityKind.Internal> which is appropriate for Activities that are an internal operation within an application with no remote parent or children.</span></span> <span data-ttu-id="1f524-192">Другие типы можно задать с помощью параметра kind в <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-192">Other kinds can be set using the kind parameter on <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f524-193">Другие варианты см. в разделе <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-193">See <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> for other options.</span></span>

### <a name="optional-links"></a><span data-ttu-id="1f524-194">Дополнительно: связи</span><span class="sxs-lookup"><span data-stu-id="1f524-194">Optional: Links</span></span>

<span data-ttu-id="1f524-195">При работе в системах пакетной обработки одно действие может представлять работу от имени множества различных запросов одновременно, каждый из которых имеет собственный идентификатор трассировки. Хотя действие может иметь только один родительский объект, его можно связать с дополнительными идентификаторами трассировки с помощью <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-195">When work occurs in batch processing systems a single Activity might represent work on behalf of many different requests simultaneously, each of which has its own trace-id. Although Activity is restricted to have a single parent, it can link to additional trace-ids using <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1f524-196">Каждый ActivityLink заполняется с использованием <xref:System.Diagnostics.ActivityContext>, где хранятся сведения об идентификаторах для действий, с которыми выполняется связь.</span><span class="sxs-lookup"><span data-stu-id="1f524-196">Each ActivityLink is populated with an <xref:System.Diagnostics.ActivityContext> that stores ID information about the Activity being linked to.</span></span> <span data-ttu-id="1f524-197">ActivityContext можно получить из внутрипроцессных объектов Activity с помощью <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> или выделить путем анализа из сериализованных данных об идентификаторах с помощью <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f524-197">ActivityContext can be retrieved from in-process Activity objects using <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> or it can be parsed from serialized id information using <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType>.</span></span>

```csharp
void DoBatchWork(ActivityContext[] requestContexts)
{
    // Assume each context in requestContexts encodes the trace-id that was sent with a request
    using(Activity activity = s_source.StartActivity(name: "BigBatchOfWork",
                                                     kind: ActivityKind.Internal,
                                                     parentContext: null,
                                                     links: requestContexts.Select(ctx => new ActivityLink(ctx))
    {
        // do the batch of work here
    }
}
```

<span data-ttu-id="1f524-198">В отличие от событий и тегов, которые можно добавлять по мере необходимости, связи необходимо добавлять во время StartActivity(), после чего они становятся неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="1f524-198">Unlike events and Tags that can be added on-demand, links must be added during StartActivity() and are immutable afterwards.</span></span>
