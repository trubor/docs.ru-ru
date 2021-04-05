---
title: Сбор распределенной трассировки — .NET
description: Учебники по сбору распределенных трассировок в приложениях .NET с использованием OpenTelemetry, Application Insights или ActivityListener
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: f5e2ea6dc09edbc7c51586f4da8d4a6088804cbd
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111533"
---
# <a name="collect-a-distributed-trace"></a><span data-ttu-id="6d955-103">Сбор распределенной трассировки</span><span class="sxs-lookup"><span data-stu-id="6d955-103">Collect a distributed trace</span></span>

<span data-ttu-id="6d955-104">**Эта статья применяется к: ✔️** .NET Core 2.1 и более поздних версий **и**.NET Framework 4.5 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="6d955-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="6d955-105">Инструментированный код может создавать объекты <xref:System.Diagnostics.Activity> в рамках распределенной трассировки, но сведения в этих объектах необходимо собирать в централизованное хранилище, чтобы позже можно было изучить всю трассировку.</span><span class="sxs-lookup"><span data-stu-id="6d955-105">Instrumented code can create <xref:System.Diagnostics.Activity> objects as part of a distributed trace, but the information in these objects needs to be collected into centralized storage so that the entire trace can be reviewed later.</span></span> <span data-ttu-id="6d955-106">В этом учебнике данные телеметрии распределенной трассировки будут собраны различными способами, чтобы они были доступными для диагностики проблем приложения в случае необходимости.</span><span class="sxs-lookup"><span data-stu-id="6d955-106">In this tutorial you will collect the distributed trace telemetry in different ways so that it is available to diagnose application issues when needed.</span></span> <span data-ttu-id="6d955-107">Если необходимо добавить новое инструментирование, см. [учебник по инструментированию](distributed-tracing-instrumentation-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="6d955-107">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) if you need to add new instrumentation.</span></span>

## <a name="collect-traces-using-opentelemetry"></a><span data-ttu-id="6d955-108">Сбор трассировок с помощью OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="6d955-108">Collect traces using OpenTelemetry</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6d955-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6d955-109">Prerequisites</span></span>

- <span data-ttu-id="6d955-110">[Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="6d955-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="6d955-111">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="6d955-111">Create an example application</span></span>

<span data-ttu-id="6d955-112">Прежде чем можно будет собрать данные телеметрии распределенной трассировки, необходимо создать их.</span><span class="sxs-lookup"><span data-stu-id="6d955-112">Before any distributed trace telemetry can be collected we need to produce it.</span></span> <span data-ttu-id="6d955-113">Часто это инструментирование может находиться в библиотеках, но для простоты вы создадите небольшое приложение с примером инструментирования с использованием <xref:System.Diagnostics.ActivitySource.StartActivity%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d955-113">Often this instrumentation might be in libraries but for simplicity you will create a small app that has some example instrumentation using <xref:System.Diagnostics.ActivitySource.StartActivity%2A>.</span></span> <span data-ttu-id="6d955-114">На этом этапе сбор еще не происходит, StartActivity() не имеет побочных эффектов и возвращает значение NULL.</span><span class="sxs-lookup"><span data-stu-id="6d955-114">At this point no collection is happening yet, StartActivity() has no side-effect and returns null.</span></span> <span data-ttu-id="6d955-115">Дополнительные сведения см. в [учебнике по инструментированию](distributed-tracing-instrumentation-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="6d955-115">See [the instrumentation tutorial](distributed-tracing-instrumentation-walkthroughs.md) for more details.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="6d955-116">В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="6d955-116">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="6d955-117">Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6d955-117">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="6d955-118">Замените содержимое созданного файла Program.cs исходным кодом примера.</span><span class="sxs-lookup"><span data-stu-id="6d955-118">Replace the contents of the generated Program.cs with this example source:</span></span>

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="6d955-119">При запуске приложения данные трассировки еще не собираются:</span><span class="sxs-lookup"><span data-stu-id="6d955-119">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a><span data-ttu-id="6d955-120">Сбор с помощью OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="6d955-120">Collect using OpenTelemetry</span></span>

<span data-ttu-id="6d955-121">[OpenTelemetry](https://opentelemetry.io/) — это независимый от поставщика проект с открытым исходным кодом, поддерживаемый фондом [Cloud Native Computing Foundation](https://www.cncf.io/), который стремится стандартизировать создание и сбор данных телеметрии для ориентированного на облако программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="6d955-121">[OpenTelemetry](https://opentelemetry.io/) is a vendor neutral open source project supported by the [Cloud Native Computing Foundation](https://www.cncf.io/) that aims to standardize generating and collecting telemetry for cloud-native software.</span></span> <span data-ttu-id="6d955-122">В этом примере будут собраны и отображены сведения о распределенной трассировке в консоли, хотя OpenTelemetry можно перенастроить для отправки данных в другое место.</span><span class="sxs-lookup"><span data-stu-id="6d955-122">In this example you will collect and display distributed trace information on the console though OpenTelemetry can be reconfigured to send it elsewhere.</span></span> <span data-ttu-id="6d955-123">Дополнительные сведения см. в [руководстве по началу работы с OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md).</span><span class="sxs-lookup"><span data-stu-id="6d955-123">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) for more information.</span></span>

<span data-ttu-id="6d955-124">Добавьте пакет NuGet [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/).</span><span class="sxs-lookup"><span data-stu-id="6d955-124">Add the [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet package.</span></span>

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="6d955-125">Измените файл Program.cs с использованием дополнительных инструкций using OpenTelemetry.</span><span class="sxs-lookup"><span data-stu-id="6d955-125">Update Program.cs with additional OpenTelemetry using statments:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

<span data-ttu-id="6d955-126">Измените Main(), чтобы создать TracerProvider OpenTelemetry.:</span><span class="sxs-lookup"><span data-stu-id="6d955-126">Update Main() to create the OpenTelemetry TracerProvider:</span></span>

```C#
        public static async Task Main()
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

<span data-ttu-id="6d955-127">Теперь приложение собирает сведения распределенной трассировки и отображает их в консоли.</span><span class="sxs-lookup"><span data-stu-id="6d955-127">Now the app collects distributed trace information and displays it to the console:</span></span>

```dotnetcli
> dotnet run
Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-6081a9b8041cd840-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8649754Z
Activity.Duration:    00:00:00.5069226
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-d2b283db91cf774c-01
Activity.ParentId:    00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:47.3838737Z
Activity.Duration:    00:00:01.0142278
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Activity.Id:          00-7759221f2c5599489d455b84fa0f90f4-9a52f72c08a9d447-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:46:46.8634510Z
Activity.Duration:    00:00:01.5402045
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 909a4624-3b2e-40e4-a86b-4a2c8003219e

Example work done
```

#### <a name="sources"></a><span data-ttu-id="6d955-128">Источники</span><span class="sxs-lookup"><span data-stu-id="6d955-128">Sources</span></span>

<span data-ttu-id="6d955-129">В примере кода вы вызвали `AddSource("Sample.DistributedTracing")`, поэтому OpenTelemetry будет захватывать действия, созданные ActivitySource, который уже присутствовал в коде.</span><span class="sxs-lookup"><span data-stu-id="6d955-129">In the example code you invoked `AddSource("Sample.DistributedTracing")` so that OpenTelemetry would capture the Activities produced by the ActivitySource that was already present in the code:</span></span>

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

<span data-ttu-id="6d955-130">Данные телеметрии из любого ActivitySource могут быть захвачены путем вызова AddSource() с именем источника.</span><span class="sxs-lookup"><span data-stu-id="6d955-130">Telemetry from any ActivitySource can captured by calling AddSource() with the source's name.</span></span>

#### <a name="exporters"></a><span data-ttu-id="6d955-131">Средства экспорта</span><span class="sxs-lookup"><span data-stu-id="6d955-131">Exporters</span></span>

<span data-ttu-id="6d955-132">Средство экспорта консоли удобно для простых примеров или локальной разработки, но в рабочей среде вы, вероятно, захотите отправить трассировки в централизованное хранилище.</span><span class="sxs-lookup"><span data-stu-id="6d955-132">The console exporter is helpful for quick examples or local development but in a production deployment you will probably want to send traces to a centralized store.</span></span> <span data-ttu-id="6d955-133">OpenTelemetry поддерживает различные назначения, используя разные [средства экспорта](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library).</span><span class="sxs-lookup"><span data-stu-id="6d955-133">OpenTelemetry supports a variety of destinations using different [exporters](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library).</span></span>
<span data-ttu-id="6d955-134">Дополнительные сведения о настройке OpenTelemetry см. в [руководстве по началу работы с OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started).</span><span class="sxs-lookup"><span data-stu-id="6d955-134">See the [OpenTelemetry getting started guide](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started) for more information on configuring OpenTelemetry.</span></span>

## <a name="collect-traces-using-application-insights"></a><span data-ttu-id="6d955-135">Сбор трассировок с помощью Application Insights</span><span class="sxs-lookup"><span data-stu-id="6d955-135">Collect traces using Application Insights</span></span>

<span data-ttu-id="6d955-136">Данные телеметрии распределенной трассировки автоматически захватываются после настройки пакета SDK для Application Insights ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) или при включении [инструментирования без кода](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview).</span><span class="sxs-lookup"><span data-stu-id="6d955-136">Distributed tracing telemetry is automatically captured after configuring the Application Insights SDK ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) or by enabling [code-less instrumentation](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview).</span></span>

<span data-ttu-id="6d955-137">Дополнительные сведения см. в [документации по распределенной трассировке Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing).</span><span class="sxs-lookup"><span data-stu-id="6d955-137">See the [Application Insights distributed tracing documentation](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="6d955-138">Сейчас Application Insights поддерживает только сбор инструментирования определенных и известных действий и игнорирует новые действия, добавленные пользователем.</span><span class="sxs-lookup"><span data-stu-id="6d955-138">Currently Application Insights only supports collecting specific well-known Activity instrumentation and will ignore new user added Activities.</span></span> <span data-ttu-id="6d955-139">Application Insights предоставляет [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) в качестве API поставщика для добавления настраиваемых данных распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="6d955-139">Application Insights offers [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) as a vendor specific API for adding custom distributed tracing information.</span></span>

## <a name="collect-traces-using-custom-logic"></a><span data-ttu-id="6d955-140">Сбор трассировок с помощью пользовательской логики</span><span class="sxs-lookup"><span data-stu-id="6d955-140">Collect traces using custom logic</span></span>

<span data-ttu-id="6d955-141">Разработчики могут создавать собственную пользовательскую логику сбора для данных трассировки действий.</span><span class="sxs-lookup"><span data-stu-id="6d955-141">Developers are free to create their own customized collection logic for Activity trace data.</span></span> <span data-ttu-id="6d955-142">Этот пример собирает данные телеметрии с помощью API <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType>, предоставляемого .NET, и выводит их в консоль.</span><span class="sxs-lookup"><span data-stu-id="6d955-142">This example collects the telemetry using the <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> API provided by .NET and prints it to the console.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6d955-143">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6d955-143">Prerequisites</span></span>

- <span data-ttu-id="6d955-144">[Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="6d955-144">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

### <a name="create-an-example-application"></a><span data-ttu-id="6d955-145">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="6d955-145">Create an example application</span></span>

<span data-ttu-id="6d955-146">Сначала вы создадите пример приложения, в котором есть инструментирование распределенной трассировки, но данные трассировки собираться не будут.</span><span class="sxs-lookup"><span data-stu-id="6d955-146">First you will create an example application that has some distributed trace instrumentation but no trace data is being collected.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="6d955-147">В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="6d955-147">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="6d955-148">Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6d955-148">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="6d955-149">Замените содержимое созданного файла Program.cs исходным кодом примера.</span><span class="sxs-lookup"><span data-stu-id="6d955-149">Replace the contents of the generated Program.cs with this example source:</span></span>

```C#
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");

        static async Task Main(string[] args)
        {
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }

        static async Task DoSomeWork()
        {
            using (Activity a = s_source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }

        static async Task StepOne()
        {
            using (Activity a = s_source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity a = s_source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="6d955-150">При запуске приложения данные трассировки еще не собираются:</span><span class="sxs-lookup"><span data-stu-id="6d955-150">Running the app does not collect any trace data yet:</span></span>

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a><span data-ttu-id="6d955-151">Добавление кода для сбора трассировок</span><span class="sxs-lookup"><span data-stu-id="6d955-151">Add code to collect the traces</span></span>

<span data-ttu-id="6d955-152">Измените Main() с использованием следующего кода.</span><span class="sxs-lookup"><span data-stu-id="6d955-152">Update Main() with this code:</span></span>

```C#
        static async Task Main(string[] args)
        {
            Activity.DefaultIdFormat = ActivityIdFormat.W3C;
            Activity.ForceDefaultIdFormat = true;

            Console.WriteLine("         {0,-15} {1,-60} {2,-15}", "OperationName", "Id", "Duration");
            ActivitySource.AddActivityListener(new ActivityListener()
            {
                ShouldListenTo = (source) => true,
                Sample = (ref ActivityCreationOptions<ActivityContext> options) => ActivitySamplingResult.AllDataAndRecorded,
                ActivityStarted = activity => Console.WriteLine("Started: {0,-15} {1,-60}", activity.OperationName, activity.Id),
                ActivityStopped = activity => Console.WriteLine("Stopped: {0,-15} {1,-60} {2,-15}", activity.OperationName, activity.Id, activity.Duration)
            });
            
            await DoSomeWork();
            Console.WriteLine("Example work done");
        }
```

<span data-ttu-id="6d955-153">Теперь выходные данные включают в себя ведение журнала.</span><span class="sxs-lookup"><span data-stu-id="6d955-153">The output now includes logging:</span></span>

```dotnetcli
> dotnet run
         OperationName   Id                                                           Duration
Started: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01
Started: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01
Stopped: StepOne         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-a7c77a4e9a02dc4a-01      00:00:00.5093849
Started: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01
Stopped: StepTwo         00-bdb5faffc2fc1548b6ba49a31c4a0ae0-9210ad536cae9e4e-01      00:00:01.0111847
Stopped: SomeWork        00-bdb5faffc2fc1548b6ba49a31c4a0ae0-c447fb302059784f-01      00:00:01.5236391
Example work done
```

<span data-ttu-id="6d955-154">Параметры <xref:System.Diagnostics.Activity.DefaultIdFormat> и <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> являются необязательными, но помогают убедиться, что пример создает аналогичные выходные данные в разных версиях среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="6d955-154">Setting <xref:System.Diagnostics.Activity.DefaultIdFormat> and <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> is optional but helps ensure the sample produces similar output on different .NET runtime versions.</span></span> <span data-ttu-id="6d955-155">.NET 5 по умолчанию использует формат идентификатора W3C TraceContext, но более ранние версии .NET по умолчанию используют формат идентификатора <xref:System.Diagnostics.ActivityIdFormat.Hierarchical>.</span><span class="sxs-lookup"><span data-stu-id="6d955-155">.NET 5 uses the W3C TraceContext ID format by default but earlier .NET versions default to using <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> ID format.</span></span> <span data-ttu-id="6d955-156">Дополнительные сведения см. в разделе [Идентификаторы действий](distributed-tracing-concepts.md#activity-ids).</span><span class="sxs-lookup"><span data-stu-id="6d955-156">See [Activity IDs](distributed-tracing-concepts.md#activity-ids) for more details.</span></span>

<span data-ttu-id="6d955-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> используется для получения обратных вызовов в течение времени существования действия.</span><span class="sxs-lookup"><span data-stu-id="6d955-157"><xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> is used to receive callbacks during the lifetime of an Activity.</span></span>

- <span data-ttu-id="6d955-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> — каждое действие связано с ActivitySource, который выступает в качестве его пространства имен и производителя.</span><span class="sxs-lookup"><span data-stu-id="6d955-158"><xref:System.Diagnostics.ActivityListener.ShouldListenTo> - Each Activity is associated with an ActivitySource which acts as its namespace and producer.</span></span>
<span data-ttu-id="6d955-159">Этот обратный вызов выполняется один раз для каждого ActivitySource в процессе.</span><span class="sxs-lookup"><span data-stu-id="6d955-159">This callback is invoked once for each ActivitySource in the process.</span></span> <span data-ttu-id="6d955-160">Вы можете возвратить значение true, если заинтересованы в выполнении выборки или получении уведомлений о событиях запуска и остановки для действий, создаваемых этим источником.</span><span class="sxs-lookup"><span data-stu-id="6d955-160">Return true if you are interested in performing sampling or being notified about start/stop events for Activities produced by this source.</span></span>
- <span data-ttu-id="6d955-161"><xref:System.Diagnostics.ActivityListener.Sample> — по умолчанию <xref:System.Diagnostics.ActivitySource.StartActivity%2A> не создает объект действия, если только какой-либо ActivityListener не указывает на необходимость выборки.</span><span class="sxs-lookup"><span data-stu-id="6d955-161"><xref:System.Diagnostics.ActivityListener.Sample> - By default <xref:System.Diagnostics.ActivitySource.StartActivity%2A> does not create an Activity object unless some ActivityListener indicates it should be sampled.</span></span> <span data-ttu-id="6d955-162">Возврат <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded></span><span class="sxs-lookup"><span data-stu-id="6d955-162">Returning <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded></span></span>
<span data-ttu-id="6d955-163">указывает, что действие должно быть создано, для <xref:System.Diagnostics.Activity.IsAllDataRequested> должно быть задано значение true, а для <xref:System.Diagnostics.Activity.ActivityTraceFlags> будет установлен флаг <xref:System.Diagnostics.ActivityTraceFlags.Recorded>.</span><span class="sxs-lookup"><span data-stu-id="6d955-163">indicates that the Activity should be created, <xref:System.Diagnostics.Activity.IsAllDataRequested> should be set to true, and <xref:System.Diagnostics.Activity.ActivityTraceFlags> will have the <xref:System.Diagnostics.ActivityTraceFlags.Recorded> flag set.</span></span> <span data-ttu-id="6d955-164">IsAllDataRequested может рассматриваться инструментированным кодом как указание, что прослушиватель должен гарантировать заполнение дополнительных сведений о действии, таких как теги и события.</span><span class="sxs-lookup"><span data-stu-id="6d955-164">IsAllDataRequested can be observed by the instrumented code as a hint that a listener wants to ensure that auxilliary Activity information such as Tags and Events are populated.</span></span>
<span data-ttu-id="6d955-165">Записанный флаг кодируется в идентификаторе W3C TraceContext и является указанием для других процессов, участвующих в распределенной трассировке, о необходимости выборки этой трассировки.</span><span class="sxs-lookup"><span data-stu-id="6d955-165">The Recorded flag is encoded in the W3C TraceContext ID and is a hint to other processes involved in the distributed trace that this trace should be sampled.</span></span>
- <span data-ttu-id="6d955-166"><xref:System.Diagnostics.ActivityListener.ActivityStarted> и <xref:System.Diagnostics.ActivityListener.ActivityStopped> вызываются при запуске и остановке действия соответственно.</span><span class="sxs-lookup"><span data-stu-id="6d955-166"><xref:System.Diagnostics.ActivityListener.ActivityStarted> and <xref:System.Diagnostics.ActivityListener.ActivityStopped> are called when an Activity is started and stopped respectively.</span></span> <span data-ttu-id="6d955-167">Эти обратные вызовы позволяют записать релевантные сведения о действии или, возможно, изменить их.</span><span class="sxs-lookup"><span data-stu-id="6d955-167">These callbacks provide an oportunity to record relevant information about the Activity or potentially to modify it.</span></span>
<span data-ttu-id="6d955-168">Если действие было запущено только что, большая часть данных может оставаться неполной и будет заполнена до остановки действия.</span><span class="sxs-lookup"><span data-stu-id="6d955-168">When an Activity has just started much of the data may still be incomplete and it will be populated before the Activity stops.</span></span>

<span data-ttu-id="6d955-169">После создания ActivityListener и заполнения обратных вызовов вызов <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6d955-169">Once an ActivityListener has been created and the callbacks are populated, calling <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType></span></span>
<span data-ttu-id="6d955-170">инициирует выполнение обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="6d955-170">initiates invoking the callbacks.</span></span> <span data-ttu-id="6d955-171">Вызовите <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType>, чтобы прерывать последовательность обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="6d955-171">Call <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType> to stop the flow of callbacks.</span></span> <span data-ttu-id="6d955-172">Учтите, что в ходе обратного вызова многопоточного кода уведомления о выполнении могут быть получены при выполнении Dispose() или даже вскоре после возврата им данных.</span><span class="sxs-lookup"><span data-stu-id="6d955-172">Beware that in multi-threaded code callback notifications in progress could be received while Dispose() is running or even very shortly after it has returned.</span></span>
