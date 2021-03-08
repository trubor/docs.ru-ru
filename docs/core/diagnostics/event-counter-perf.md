---
title: Измерение производительности с помощью EventCounters в .NET Core
description: В этом руководстве вы узнаете, как измерять производительность с помощью EventCounters.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: bde54ce1996b2f4e2a703c23384eadece06e66cb
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105314"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="5cb65-103">Учебник. Измерение производительности с помощью EventCounters в .NET Core</span><span class="sxs-lookup"><span data-stu-id="5cb65-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="5cb65-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="5cb65-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="5cb65-105">В этом руководстве вы узнаете, как можно использовать <xref:System.Diagnostics.Tracing.EventCounter> для измерения производительности с высокой частотой событий.</span><span class="sxs-lookup"><span data-stu-id="5cb65-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="5cb65-106">Вы можете использовать [доступные счетчики](available-counters.md), опубликованные в разных официальных пакетах .NET Core или сторонними поставщиками, либо создать собственные метрики для мониторинга.</span><span class="sxs-lookup"><span data-stu-id="5cb65-106">You can use the [available counters](available-counters.md) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="5cb65-107">Изучив данный учебник, вы научитесь:</span><span class="sxs-lookup"><span data-stu-id="5cb65-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5cb65-108">Реализовывать <xref:System.Diagnostics.Tracing.EventSource>.</span><span class="sxs-lookup"><span data-stu-id="5cb65-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="5cb65-109">Организовывать мониторинг счетчиков с помощью [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5cb65-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5cb65-110">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="5cb65-110">Prerequisites</span></span>

<span data-ttu-id="5cb65-111">В этом учебнике используется:</span><span class="sxs-lookup"><span data-stu-id="5cb65-111">The tutorial uses:</span></span>

- <span data-ttu-id="5cb65-112">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="5cb65-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="5cb65-113">[dotnet-counters](dotnet-counters.md) для мониторинга счетчиков событий.</span><span class="sxs-lookup"><span data-stu-id="5cb65-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="5cb65-114">[Пример целевого приложения отладки](/samples/dotnet/samples/diagnostic-scenarios) для диагностики.</span><span class="sxs-lookup"><span data-stu-id="5cb65-114">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="5cb65-115">Получение исходного кода</span><span class="sxs-lookup"><span data-stu-id="5cb65-115">Get the source</span></span>

<span data-ttu-id="5cb65-116">Пример приложения будет использоваться в качестве основания для мониторинга.</span><span class="sxs-lookup"><span data-stu-id="5cb65-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="5cb65-117">[Пример репозитория ASP.NET](/samples/dotnet/samples/diagnostic-scenarios) доступен в обозревателе примеров.</span><span class="sxs-lookup"><span data-stu-id="5cb65-117">The [sample ASP.NET Core repository](/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="5cb65-118">Скачайте ZIP-файл, извлеките его содержимое и откройте его в избранной интегрированной среде разработки.</span><span class="sxs-lookup"><span data-stu-id="5cb65-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="5cb65-119">Выполните сборку приложения и запустите его, чтобы убедиться, что оно работает правильно, а затем закройте приложение.</span><span class="sxs-lookup"><span data-stu-id="5cb65-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="5cb65-120">Реализация счетчика событий</span><span class="sxs-lookup"><span data-stu-id="5cb65-120">Implement an EventSource</span></span>

<span data-ttu-id="5cb65-121">Для событий, происходящих каждые несколько миллисекунд, необходимо, чтобы затраты на событие были низкими (меньше миллисекунд).</span><span class="sxs-lookup"><span data-stu-id="5cb65-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="5cb65-122">В противном случае влияние на производительность будет значительным.</span><span class="sxs-lookup"><span data-stu-id="5cb65-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="5cb65-123">Регистрация события означает, что вы собираетесь записать что-то на диск.</span><span class="sxs-lookup"><span data-stu-id="5cb65-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="5cb65-124">Если диск недостаточно быстродействующий, события будут потеряны.</span><span class="sxs-lookup"><span data-stu-id="5cb65-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="5cb65-125">Потребуется решение, отличное от регистрации самого события.</span><span class="sxs-lookup"><span data-stu-id="5cb65-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="5cb65-126">При работе с большим количеством событий знание меры для каждого события не имеет смысла.</span><span class="sxs-lookup"><span data-stu-id="5cb65-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="5cb65-127">В большинстве случаев достаточно лишь некоторой статистики.</span><span class="sxs-lookup"><span data-stu-id="5cb65-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="5cb65-128">Так что вы можете получить статистику внутри самого процесса, а затем написать событие один раз в течение определенного времени для передачи статистики. Именно это и делает <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="5cb65-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="5cb65-129">Ниже приведен пример реализации <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5cb65-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="5cb65-130">Создайте новый файл с именем *MinimalEventCounterSource.cs* и используйте фрагмент кода в качестве источника:</span><span class="sxs-lookup"><span data-stu-id="5cb65-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="5cb65-131">Строка <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> — это <xref:System.Diagnostics.Tracing.EventSource> часть, которая не является частью <xref:System.Diagnostics.Tracing.EventCounter>. Она была написана для того, чтобы показать, что можно зарегистрировать сообщение вместе со счетчиком событий.</span><span class="sxs-lookup"><span data-stu-id="5cb65-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="5cb65-132">Добавление фильтра действий</span><span class="sxs-lookup"><span data-stu-id="5cb65-132">Add an action filter</span></span>

<span data-ttu-id="5cb65-133">Пример исходного кода является проектом ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5cb65-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="5cb65-134">Вы можете глобально добавить [фильтр действий](/aspnet/core/mvc/controllers/filters#action-filters), который будет регистрировать общее время запроса.</span><span class="sxs-lookup"><span data-stu-id="5cb65-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="5cb65-135">Создайте новый файл с именем *LogRequestTimeFilterAttribute.cs* и используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="5cb65-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="5cb65-136">Фильтр действий запускает <xref:System.Diagnostics.Stopwatch> по мере начала запроса и останавливается после завершения, записывая затраченное время.</span><span class="sxs-lookup"><span data-stu-id="5cb65-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="5cb65-137">Общее число миллисекунд регистрируется в отдельном экземпляре `MinimalEventCounterSource`.</span><span class="sxs-lookup"><span data-stu-id="5cb65-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="5cb65-138">Чтобы применить этот фильтр, необходимо добавить его в коллекцию фильтров.</span><span class="sxs-lookup"><span data-stu-id="5cb65-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="5cb65-139">В файле *Startup.cs* обновите метод `ConfigureServices`, чтобы включить этот фильтр.</span><span class="sxs-lookup"><span data-stu-id="5cb65-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="5cb65-140">Мониторинг счетчика событий</span><span class="sxs-lookup"><span data-stu-id="5cb65-140">Monitor event counter</span></span>

<span data-ttu-id="5cb65-141">Реализовав <xref:System.Diagnostics.Tracing.EventSource> и настраиваемый фильтр действий, создайте и запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="5cb65-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="5cb65-142">Вы зарегистрировали метрику в <xref:System.Diagnostics.Tracing.EventCounter>, но пока вы не получите доступ к статистике из нее, пользы от нее никакой.</span><span class="sxs-lookup"><span data-stu-id="5cb65-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="5cb65-143">Чтобы получить статистику, необходимо включить <xref:System.Diagnostics.Tracing.EventCounter>, создав таймер, который срабатывает с периодичностью, которая требуется для событий и нужна прослушивателю для записи событий.</span><span class="sxs-lookup"><span data-stu-id="5cb65-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="5cb65-144">Для этого можно использовать [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="5cb65-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="5cb65-145">Используйте команду [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps), чтобы отобразить список процессов .NET, которые можно отслеживать.</span><span class="sxs-lookup"><span data-stu-id="5cb65-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="5cb65-146">Используя идентификатор процесса из выходных данных команды `dotnet-counters ps`, можно начать мониторинг счетчика событий с помощью следующей команды `dotnet-counters monitor`:</span><span class="sxs-lookup"><span data-stu-id="5cb65-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="5cb65-147">Во время выполнения команды `dotnet-counters monitor` удерживайте нажатой клавишу <kbd>F5</kbd> в браузере, чтобы начать выдачу непрерывных запросов к конечной точке `https://localhost:5001/api/values`.</span><span class="sxs-lookup"><span data-stu-id="5cb65-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="5cb65-148">Через несколько секунд нажмите клавишу <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5cb65-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="5cb65-149">Команда `dotnet-counters monitor` отлично подходит для активного мониторинга.</span><span class="sxs-lookup"><span data-stu-id="5cb65-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="5cb65-150">Однако может потребоваться собрать эти метрики диагностики для обработки и анализа.</span><span class="sxs-lookup"><span data-stu-id="5cb65-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="5cb65-151">Для этого используйте команду `dotnet-counters collect`.</span><span class="sxs-lookup"><span data-stu-id="5cb65-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="5cb65-152">Команда `collect` аналогична команде `monitor`, но принимает несколько дополнительных параметров.</span><span class="sxs-lookup"><span data-stu-id="5cb65-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="5cb65-153">Можно указать требуемое имя выходного файла и формат.</span><span class="sxs-lookup"><span data-stu-id="5cb65-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="5cb65-154">Для файла JSON с именем *diagnostics.json* используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="5cb65-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json --counters Sample.EventCounter.Minimal,Microsoft.AspNetCore.Hosting[total-requests,requests-per-second],System.Runtime[cpu-usage]
```

<span data-ttu-id="5cb65-155">Во время выполнения команды удерживайте нажатой клавишу <kbd>F5</kbd> в браузере, чтобы начать выдачу непрерывных запросов к конечной точке `https://localhost:5001/api/values`.</span><span class="sxs-lookup"><span data-stu-id="5cb65-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="5cb65-156">Через несколько секунд нажмите клавишу <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5cb65-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="5cb65-157">Файл *diagnostics.json* будет записан.</span><span class="sxs-lookup"><span data-stu-id="5cb65-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="5cb65-158">Однако файл JSON не имеет отступа; для удобства чтения здесь он отображается с отступом.</span><span class="sxs-lookup"><span data-stu-id="5cb65-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="5cb65-159">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="5cb65-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cb65-160">Счетчики событий</span><span class="sxs-lookup"><span data-stu-id="5cb65-160">EventCounters</span></span>](event-counters.md)
