---
title: Ведение журнала с помощью пакета Azure SDK для .NET
description: Узнайте, как включить ведение журнала с помощью пакета клиентских библиотек Azure SDK для .NET
ms.date: 03/20/2020
ms.custom: devx-track-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b0f7bdf7eaf7db242545d43856fae8d1548bc004
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494341"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="bfab2-103">Ведение журнала с помощью пакета Azure SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="bfab2-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="bfab2-104">Клиентские библиотеки [пакета Azure SDK](https://azure.microsoft.com/downloads/) для .NET включают возможность ведения журнала операций клиентской библиотеки.</span><span class="sxs-lookup"><span data-stu-id="bfab2-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="bfab2-105">Это позволяет отслеживать запросы ввода-вывода, которые клиентские библиотеки отправляют службам Azure, и ответы на эти запросы.</span><span class="sxs-lookup"><span data-stu-id="bfab2-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="bfab2-106">Как правило, журналы используются для отладки или диагностики проблем связи.</span><span class="sxs-lookup"><span data-stu-id="bfab2-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="bfab2-107">В этой статье описываются три подхода к включению ведения журнала с помощью пакета Azure SDK для .NET:</span><span class="sxs-lookup"><span data-stu-id="bfab2-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="bfab2-108">Ведение журнала в окне консоли</span><span class="sxs-lookup"><span data-stu-id="bfab2-108">Log to the console window</span></span>
- <span data-ttu-id="bfab2-109">Ведение журнала с помощью трассировки диагностики .NET</span><span class="sxs-lookup"><span data-stu-id="bfab2-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="bfab2-110">Настраиваемое ведение журнала</span><span class="sxs-lookup"><span data-stu-id="bfab2-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bfab2-111">Эта статья применяется к клиентским библиотекам, использующим последние версии пакета Azure SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="bfab2-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="bfab2-112">Чтобы узнать, поддерживается ли библиотека, обратитесь к списку [последних выпусков Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="bfab2-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="bfab2-113">Если приложение использует более раннюю версию клиентских библиотек пакета Azure SDK, ознакомьтесь с конкретными инструкциями в соответствующей документации службы.</span><span class="sxs-lookup"><span data-stu-id="bfab2-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="bfab2-114">Сведения о журнале</span><span class="sxs-lookup"><span data-stu-id="bfab2-114">Log information</span></span>

<span data-ttu-id="bfab2-115">Пакет SDK записывает в журнал следующие сведения, выполняя очистку значений параметров запроса и заголовка для удаления персональных данных.</span><span class="sxs-lookup"><span data-stu-id="bfab2-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="bfab2-116">Запись HTTP-запроса в журнале:</span><span class="sxs-lookup"><span data-stu-id="bfab2-116">HTTP request log entry:</span></span>

- <span data-ttu-id="bfab2-117">Уникальный идентификатор</span><span class="sxs-lookup"><span data-stu-id="bfab2-117">Unique ID</span></span>
- <span data-ttu-id="bfab2-118">Метод HTTP</span><span class="sxs-lookup"><span data-stu-id="bfab2-118">HTTP method</span></span>
- <span data-ttu-id="bfab2-119">URI</span><span class="sxs-lookup"><span data-stu-id="bfab2-119">URI</span></span>
- <span data-ttu-id="bfab2-120">Заголовки исходящего запроса</span><span class="sxs-lookup"><span data-stu-id="bfab2-120">Outgoing request headers</span></span>

<span data-ttu-id="bfab2-121">Запись HTTP-ответа в журнале:</span><span class="sxs-lookup"><span data-stu-id="bfab2-121">HTTP response log entry:</span></span>

- <span data-ttu-id="bfab2-122">Длительность операции ввода-вывода (прошедшее время)</span><span class="sxs-lookup"><span data-stu-id="bfab2-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="bfab2-123">Request ID (ИД запроса)</span><span class="sxs-lookup"><span data-stu-id="bfab2-123">Request ID</span></span>
- <span data-ttu-id="bfab2-124">HTTP status code (Код состояния HTTP)</span><span class="sxs-lookup"><span data-stu-id="bfab2-124">HTTP status code</span></span>
- <span data-ttu-id="bfab2-125">Описание причины HTTP</span><span class="sxs-lookup"><span data-stu-id="bfab2-125">HTTP reason phrase</span></span>
- <span data-ttu-id="bfab2-126">Заголовки ответов</span><span class="sxs-lookup"><span data-stu-id="bfab2-126">Response headers</span></span>
- <span data-ttu-id="bfab2-127">Сведения об ошибке, если применимо</span><span class="sxs-lookup"><span data-stu-id="bfab2-127">Error information, when applicable</span></span>

<span data-ttu-id="bfab2-128">Для содержимого запроса и ответа:</span><span class="sxs-lookup"><span data-stu-id="bfab2-128">For request and response content:</span></span>

- <span data-ttu-id="bfab2-129">Поток содержимого в виде текста или байтов в зависимости от заголовка Content-Type.</span><span class="sxs-lookup"><span data-stu-id="bfab2-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > [!NOTE]
     > <span data-ttu-id="bfab2-130">Ведение журнала для содержимого по умолчанию отключено.</span><span class="sxs-lookup"><span data-stu-id="bfab2-130">Content logging is disabled by default.</span></span> <span data-ttu-id="bfab2-131">Чтобы включить его, задайте для `Diagnostics.IsLoggingContentEnabled` значение `true` в `ClientOptions`.</span><span class="sxs-lookup"><span data-stu-id="bfab2-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="bfab2-132">Обычно используется один из трех следующих уровней ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="bfab2-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="bfab2-133">"Информационный" — для событий запроса и ответа</span><span class="sxs-lookup"><span data-stu-id="bfab2-133">Informational for request and response events</span></span>
- <span data-ttu-id="bfab2-134">"Предупреждение" — для ошибок</span><span class="sxs-lookup"><span data-stu-id="bfab2-134">Warning for errors</span></span>
- <span data-ttu-id="bfab2-135">"Подробный" — для записи подробных сообщений и содержимого</span><span class="sxs-lookup"><span data-stu-id="bfab2-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="bfab2-136">Включение ведения журнала с помощью встроенных методов</span><span class="sxs-lookup"><span data-stu-id="bfab2-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="bfab2-137">Клиентские библиотеки пакета Azure SDK для .NET регистрируют события в трассировке событий Windows (ETW) с помощью [класса `EventSource`](/dotnet/api/system.diagnostics.tracing.eventsource), что является типичным для .NET.</span><span class="sxs-lookup"><span data-stu-id="bfab2-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="bfab2-138">Источники событий позволяют использовать структурированное ведение журнала в коде приложения с минимальным влиянием на производительность.</span><span class="sxs-lookup"><span data-stu-id="bfab2-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="bfab2-139">Чтобы получить доступ к этим журналам событий, необходимо зарегистрировать прослушиватели событий.</span><span class="sxs-lookup"><span data-stu-id="bfab2-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="bfab2-140">Пакет SDK включает класс `Azure.Core.Diagnostics.AzureEventSourceListener` (определенный в пакете NuGet Azure.Core), который содержит два статических метода, упрощающих подробное ведение журнала для приложения .NET: `CreateConsoleLogger` и `CreateTraceLogger`.</span><span class="sxs-lookup"><span data-stu-id="bfab2-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="bfab2-141">Эти методы принимают необязательный параметр, задающий уровень ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="bfab2-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="bfab2-142">Ведение журнала в окне консоли</span><span class="sxs-lookup"><span data-stu-id="bfab2-142">Log to the console window</span></span>

<span data-ttu-id="bfab2-143">Основным принципом клиентских библиотек пакета Azure SDK для .NET является упрощение просмотра подробных журналов в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="bfab2-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="bfab2-144">Метод `CreateConsoleLogger` позволяет отправлять журналы в окно консоли с помощью одной строки кода:</span><span class="sxs-lookup"><span data-stu-id="bfab2-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="bfab2-145">Ведение журнала с помощью трассировки диагностики</span><span class="sxs-lookup"><span data-stu-id="bfab2-145">Log to diagnostic traces</span></span>

<span data-ttu-id="bfab2-146">При реализации прослушивателей трассировки можно использовать метод `CreateTraceLogger` для входа в стандартный механизм трассировки событий .NET ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span><span class="sxs-lookup"><span data-stu-id="bfab2-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="bfab2-147">Дополнительные сведения о трассировке событий в .NET см. в разделе [Прослушиватели трассировки](../framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="bfab2-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="bfab2-148">В этом примере задается уровень детализации журнала:</span><span class="sxs-lookup"><span data-stu-id="bfab2-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="bfab2-149">Настраиваемое ведение журнала</span><span class="sxs-lookup"><span data-stu-id="bfab2-149">Configure custom logging</span></span>

<span data-ttu-id="bfab2-150">Как упоминалось выше, для получения сообщений журнала из пакета SDK Azure для .NET необходимо зарегистрировать прослушиватели событий.</span><span class="sxs-lookup"><span data-stu-id="bfab2-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="bfab2-151">Если вам не требуется реализовывать подробное ведение журнала с помощью одного из упрощенных методов, описанных выше, можно создать экземпляр класса `AzureEventSourceListener` и передать ему функцию обратного вызова, написанную вами.</span><span class="sxs-lookup"><span data-stu-id="bfab2-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="bfab2-152">Эта функция будет получать сообщения журнала, и вы можете обрабатывать их так, как это необходимо.</span><span class="sxs-lookup"><span data-stu-id="bfab2-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="bfab2-153">Кроме того, при создании экземпляра можно указать включаемые уровни сообщения журнала.</span><span class="sxs-lookup"><span data-stu-id="bfab2-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="bfab2-154">В следующем примере создается прослушиватель событий, который отправляет события журнала в консоль с использованием настраиваемого ведения журнала и фильтрует основные события Azure на уровне "Подробный".</span><span class="sxs-lookup"><span data-stu-id="bfab2-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="bfab2-155">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="bfab2-155">Next steps</span></span>

- [<span data-ttu-id="bfab2-156">Включение функции ведения журналов диагностики для приложений в Службе приложений Azure</span><span class="sxs-lookup"><span data-stu-id="bfab2-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="bfab2-157">Просмотрите параметры [ведения журнала безопасности и аудита в Azure](/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="bfab2-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="bfab2-158">Узнайте о том, как работать с [журналами платформы Azure](/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="bfab2-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="bfab2-159">Ознакомьтесь с дополнительными сведениями о [Ведении журнала и трассировке в .NET Core](../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="bfab2-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
