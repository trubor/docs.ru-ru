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
# <a name="collect-a-distributed-trace"></a>Сбор распределенной трассировки

**Эта статья применяется к: ✔️** .NET Core 2.1 и более поздних версий **и**.NET Framework 4.5 и более поздних версий

Инструментированный код может создавать объекты <xref:System.Diagnostics.Activity> в рамках распределенной трассировки, но сведения в этих объектах необходимо собирать в централизованное хранилище, чтобы позже можно было изучить всю трассировку. В этом учебнике данные телеметрии распределенной трассировки будут собраны различными способами, чтобы они были доступными для диагностики проблем приложения в случае необходимости. Если необходимо добавить новое инструментирование, см. [учебник по инструментированию](distributed-tracing-instrumentation-walkthroughs.md).

## <a name="collect-traces-using-opentelemetry"></a>Сбор трассировок с помощью OpenTelemetry

### <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии

### <a name="create-an-example-application"></a>Создание примера приложения

Прежде чем можно будет собрать данные телеметрии распределенной трассировки, необходимо создать их. Часто это инструментирование может находиться в библиотеках, но для простоты вы создадите небольшое приложение с примером инструментирования с использованием <xref:System.Diagnostics.ActivitySource.StartActivity%2A>. На этом этапе сбор еще не происходит, StartActivity() не имеет побочных эффектов и возвращает значение NULL. Дополнительные сведения см. в [учебнике по инструментированию](distributed-tracing-instrumentation-walkthroughs.md).

```dotnetcli
dotnet new console
```

В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки. Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Замените содержимое созданного файла Program.cs исходным кодом примера.

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

При запуске приложения данные трассировки еще не собираются:

```dotnetcli
> dotnet run
Example work done
```

### <a name="collect-using-opentelemetry"></a>Сбор с помощью OpenTelemetry

[OpenTelemetry](https://opentelemetry.io/) — это независимый от поставщика проект с открытым исходным кодом, поддерживаемый фондом [Cloud Native Computing Foundation](https://www.cncf.io/), который стремится стандартизировать создание и сбор данных телеметрии для ориентированного на облако программного обеспечения. В этом примере будут собраны и отображены сведения о распределенной трассировке в консоли, хотя OpenTelemetry можно перенастроить для отправки данных в другое место. Дополнительные сведения см. в [руководстве по началу работы с OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md).

Добавьте пакет NuGet [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/).

```dotnetcli
dotnet add package OpenTelemetry.Exporter.Console
```

Измените файл Program.cs с использованием дополнительных инструкций using OpenTelemetry.

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;
```

Измените Main(), чтобы создать TracerProvider OpenTelemetry.:

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

Теперь приложение собирает сведения распределенной трассировки и отображает их в консоли.

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

#### <a name="sources"></a>Источники

В примере кода вы вызвали `AddSource("Sample.DistributedTracing")`, поэтому OpenTelemetry будет захватывать действия, созданные ActivitySource, который уже присутствовал в коде.

```csharp
        static ActivitySource s_source = new ActivitySource("Sample.DistributedTracing");
```

Данные телеметрии из любого ActivitySource могут быть захвачены путем вызова AddSource() с именем источника.

#### <a name="exporters"></a>Средства экспорта

Средство экспорта консоли удобно для простых примеров или локальной разработки, но в рабочей среде вы, вероятно, захотите отправить трассировки в централизованное хранилище. OpenTelemetry поддерживает различные назначения, используя разные [средства экспорта](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/glossary.md#exporter-library).
Дополнительные сведения о настройке OpenTelemetry см. в [руководстве по началу работы с OpenTelemetry](https://github.com/open-telemetry/opentelemetry-dotnet#getting-started).

## <a name="collect-traces-using-application-insights"></a>Сбор трассировок с помощью Application Insights

Данные телеметрии распределенной трассировки автоматически захватываются после настройки пакета SDK для Application Insights ([ASP.NET](https://docs.microsoft.com/azure/azure-monitor/app/asp-net), [ASP.NET Core](https://docs.microsoft.com/azure/azure-monitor/app/asp-net-core)) или при включении [инструментирования без кода](https://docs.microsoft.com/azure/azure-monitor/app/codeless-overview).

Дополнительные сведения см. в [документации по распределенной трассировке Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing).

> [!NOTE]
> Сейчас Application Insights поддерживает только сбор инструментирования определенных и известных действий и игнорирует новые действия, добавленные пользователем. Application Insights предоставляет [TrackDependency](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics#trackdependency) в качестве API поставщика для добавления настраиваемых данных распределенной трассировки.

## <a name="collect-traces-using-custom-logic"></a>Сбор трассировок с помощью пользовательской логики

Разработчики могут создавать собственную пользовательскую логику сбора для данных трассировки действий. Этот пример собирает данные телеметрии с помощью API <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType>, предоставляемого .NET, и выводит их в консоль.

### <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии

### <a name="create-an-example-application"></a>Создание примера приложения

Сначала вы создадите пример приложения, в котором есть инструментирование распределенной трассировки, но данные трассировки собираться не будут.

```dotnetcli
dotnet new console
```

В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки. Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Замените содержимое созданного файла Program.cs исходным кодом примера.

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

При запуске приложения данные трассировки еще не собираются:

```dotnetcli
> dotnet run
Example work done
```

### <a name="add-code-to-collect-the-traces"></a>Добавление кода для сбора трассировок

Измените Main() с использованием следующего кода.

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

Теперь выходные данные включают в себя ведение журнала.

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

Параметры <xref:System.Diagnostics.Activity.DefaultIdFormat> и <xref:System.Diagnostics.Activity.ForceDefaultIdFormat> являются необязательными, но помогают убедиться, что пример создает аналогичные выходные данные в разных версиях среды выполнения .NET. .NET 5 по умолчанию использует формат идентификатора W3C TraceContext, но более ранние версии .NET по умолчанию используют формат идентификатора <xref:System.Diagnostics.ActivityIdFormat.Hierarchical>. Дополнительные сведения см. в разделе [Идентификаторы действий](distributed-tracing-concepts.md#activity-ids).

<xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> используется для получения обратных вызовов в течение времени существования действия.

- <xref:System.Diagnostics.ActivityListener.ShouldListenTo> — каждое действие связано с ActivitySource, который выступает в качестве его пространства имен и производителя.
Этот обратный вызов выполняется один раз для каждого ActivitySource в процессе. Вы можете возвратить значение true, если заинтересованы в выполнении выборки или получении уведомлений о событиях запуска и остановки для действий, создаваемых этим источником.
- <xref:System.Diagnostics.ActivityListener.Sample> — по умолчанию <xref:System.Diagnostics.ActivitySource.StartActivity%2A> не создает объект действия, если только какой-либо ActivityListener не указывает на необходимость выборки. Возврат <xref:System.Diagnostics.ActivitySamplingResult.AllDataAndRecorded>
указывает, что действие должно быть создано, для <xref:System.Diagnostics.Activity.IsAllDataRequested> должно быть задано значение true, а для <xref:System.Diagnostics.Activity.ActivityTraceFlags> будет установлен флаг <xref:System.Diagnostics.ActivityTraceFlags.Recorded>. IsAllDataRequested может рассматриваться инструментированным кодом как указание, что прослушиватель должен гарантировать заполнение дополнительных сведений о действии, таких как теги и события.
Записанный флаг кодируется в идентификаторе W3C TraceContext и является указанием для других процессов, участвующих в распределенной трассировке, о необходимости выборки этой трассировки.
- <xref:System.Diagnostics.ActivityListener.ActivityStarted> и <xref:System.Diagnostics.ActivityListener.ActivityStopped> вызываются при запуске и остановке действия соответственно. Эти обратные вызовы позволяют записать релевантные сведения о действии или, возможно, изменить их.
Если действие было запущено только что, большая часть данных может оставаться неполной и будет заполнена до остановки действия.

После создания ActivityListener и заполнения обратных вызовов вызов <xref:System.Diagnostics.ActivitySource.AddActivityListener(System.Diagnostics.ActivityListener)?displayProperty=nameWithType>
инициирует выполнение обратных вызовов. Вызовите <xref:System.Diagnostics.ActivityListener.Dispose?displayProperty=nameWithType>, чтобы прерывать последовательность обратных вызовов. Учтите, что в ходе обратного вызова многопоточного кода уведомления о выполнении могут быть получены при выполнении Dispose() или даже вскоре после возврата им данных.
