---
title: Добавление инструментирования распределенной трассировки — .NET
description: Учебник по инструментированию распределенных трассировок в приложениях .NET
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: 4eb791499855a1479393ef2e00d86316a81409a1
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231157"
---
# <a name="adding-distributed-tracing-instrumentation"></a>Добавление инструментирования распределенной трассировки

**Эта статья применяется к: ✔️** .NET Core 2.1 и более поздних версий **и**.NET Framework 4.5 и более поздних версий

Приложения .NET можно инструментировать с использованием API <xref:System.Diagnostics.Activity?displayProperty=nameWithType> для создания данных телеметрии распределенной трассировки. Некоторые инструментирования встроены в стандартные библиотеки .NET, но вам может потребоваться добавить дополнительные для упрощения диагностики кода. В этом учебнике вы добавите новое настраиваемое инструментирование распределенной трассировки. Дополнительные сведения о записи данных телеметрии, создаваемых этим инструментированием, см. [в руководстве по сбору данных](distributed-tracing-instrumentation-walkthroughs.md).

## <a name="prerequisites"></a>Предварительные требования

- [Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии

## <a name="an-initial-app"></a>Начальное приложение

Сначала вы создадите пример приложения, собирающий данные телеметрии с помощью OpenTelemetry, но еще не имеющий инструментирования.

```dotnetcli
dotnet new console
```

В приложения, предназначенные для .NET 5 и более поздних версий, уже включены необходимые API распределенной трассировки. Для приложений, предназначенных для более старых версий .NET, добавьте [пакет NuGet System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) версии 5 или более поздней.

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

Добавьте пакеты NuGet [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) и [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/), которые будут использоваться для сбора данных телеметрии.

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

Замените содержимое созданного файла Program.cs исходным кодом примера.

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

В приложении еще нет инструментирования, поэтому сведения трассировки для отображения отсутствуют.

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a>Рекомендации

Только разработчикам приложений необходимо ссылаться на стороннюю библиотеку для сбора данных телеметрии распределенной трассировки, например OpenTelemetry в этом примере. Авторы библиотек .NET могут ограничиться только API-интерфейсами в System.Diagnostics.DiagnosticSource, который является частью среды выполнения .NET. Это гарантирует, что библиотеки будут работать в широком спектре приложений .NET, независимо от предпочтений разработчика приложения в отношении того, какую библиотеку или какого поставщика использовать для сбора данных телеметрии.

## <a name="adding-basic-instrumentation"></a>Добавление базового инструментирования

Приложения и библиотеки добавляют инструментирование распределенной трассировки с помощью классов <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> и <xref:System.Diagnostics.Activity?displayProperty=nameWithType>.

### <a name="activitysource"></a>ActivitySource

Сначала создайте экземпляр ActivitySource. ActivitySource предоставляет API-интерфейсы для создания и запуска объектов действий Activity. Добавьте статическую переменную ActivitySource над Main() и `using System.Diagnostics;` в инструкциях using.

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

#### <a name="best-practices"></a>Рекомендации

- Создайте класс ActivitySource и сохраните его в статической переменной, а затем используйте этот экземпляр при необходимости.
Каждая библиотека и каждый из вложенных компонентов библиотеки могут (и часто должны) создавать собственный источник. Рекомендуется создать источник вместо повторного использования существующего, если предполагается, что разработчикам приложений понадобится возможность включения и отключения телеметрии действий в источниках независимым образом.

- Имя источника, передаваемое конструктору, должно быть уникальным, чтобы избежать конфликтов с другими источниками.
Рекомендуется использовать иерархическое имя, содержащее имя сборки, и (при необходимости) имя компонента, если в одной сборке есть несколько источников. Например, `Microsoft.AspNetCore.Hosting`. Если сборка добавляет инструментирование для кода во второй независимой сборке, имя должно основываться на сборке, определяющей ActivitySource, а не на сборке, код которой инструментируется.

- Параметр version является необязательным. Рекомендуется указывать версию, если вы выпускаете несколько версий библиотеки и вносите изменения в инструментированные данные телеметрии.

> [!NOTE]
> OpenTelemetry использует альтернативные термины "трассировщик" и "рабочий интервал". В .NET ActivitySource — это реализация трассировщика, а действие — это реализация рабочего интервала. Тип Activity в .NET начал использоваться значительно раньше спецификации OpenTelemetry, и исходное именование .NET было сохранено для обеспечения согласованности в рамках экосистемы .NET и совместимости приложений .NET.

### <a name="activity-creation"></a>Создание объектов Activity

Используйте объект ActivitySource для запуска и остановки объектов Activity в рамках значимых единиц работы. Измените DoSomeWork(), используя приведенный здесь код.

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

Теперь при запуске приложения отображается новое регистрируемое действие Activity.

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

#### <a name="notes"></a>Примечания

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> создает и запускает действие в одно время. В приведенном шаблоне кода используется блок `using`, который автоматически удаляет созданный объект Activity после выполнения блока. Освобождение объекта Activity приведет к его остановке, поэтому коду не нужно явно вызывать <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType>.
Это упрощает шаблон кода.

- <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> внутренним образом определяет наличие прослушивателей, записывающих действие. Если зарегистрированных прослушивателей нет или есть незаинтересованные прослушиватели, StartActivity() возвратит `null`, не создавая объект Activity. Это оптимизация производительности, чтобы шаблон кода по-прежнему можно было использовать в функциях, вызываемых очень часто.

## <a name="optional-populate-tags"></a>Дополнительно: заполнение тегов

Действия поддерживают данные типа "ключ — значение", называемые тегами. Они обычно используются для хранения любых параметров работы, которые могут быть полезны для диагностики. Измените DoSomeWork(), чтобы включить их.

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

#### <a name="best-practices"></a>Рекомендации

- Как упоминалось выше, значение `activity`, возвращаемое <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>, может быть равно NULL. Оператор объединения с NULL ?. в C# удобно использовать, чтобы вызвать только <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> в случае, если действие не равно NULL. Это поведение аналогично следующему.

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- OpenTelemetry предоставляет набор рекомендуемых [соглашений](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) по настройке тегов для действий, представляющих общие типы работы приложения.

- Если вы осуществляете инструментирование функций с высокими требованиями к производительности, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> используется как указание того, будет ли любой код, прослушивающий действия, считывать вспомогательные данные, такие как теги. Если ни один из прослушивателей не считывает эти данные, инструментированному коду не нужно тратить циклы работы ЦП на их заполнение. Для простоты этот пример не применяет подобную оптимизацию.

## <a name="optional-adding-events"></a>Дополнительно: добавление событий

События — это сообщения с метками времени, которые могут подключать к действиям произвольный поток дополнительных диагностических данных. Добавьте в действие некоторые события.

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

#### <a name="best-practices"></a>Рекомендации

- События хранятся в списке в памяти до тех пор, пока они не смогут быть переданы, что делает этот механизм применимым только для записи небольшого количества событий. При большом или неограниченном числе событий лучше подойдет использование API ведения журнала, ориентированного на данную задачу, такого как [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/). ILogger также гарантирует, что данные о ведении журнала будут доступны независимо от того, планирует ли разработчик приложения использовать распределенную трассировку.
ILogger поддерживает автоматическую запись идентификаторов активных действий, поэтому сообщения, регистрируемые через этот API, по-прежнему могут быть сопоставлены с распределенной трассировкой.

## <a name="optional-adding-status"></a>Дополнительно: добавление состояния

OpenTelemetry позволяет каждому действию сообщать [состояние](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status), представляющее успешный или неудачный результат работы. Сейчас в .NET нет строго типизированного API для этой цели, однако есть установленное соглашение об использовании тегов:

- `otel.status_code` — это имя тега, используемое для хранения `StatusCode`. Значения для тега StatusCode должны быть одной из строк UNSET, OK или ERROR, которые соответствуют перечислениям `Unset`, `Ok` и `Error` из StatusCode.
- `otel.status_description` — это имя тега, используемое для хранения необязательного `Description`.

Измените DoSomeWork(), чтобы задать состояние.

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

## <a name="optional-add-additional-activities"></a>Дополнительно: добавление дополнительных действий

Действия могут быть вложенными для описания частей более крупной единицы работы. Это может быть особенно удобно для частей кода, которые могут выполняться медленно, или для лучшего выявления сбоев, вызванных отдельными внешними зависимостями. Хотя в этом примере действие используется в каждом методе, это сделано исключительно по причине сведения лишнего кода к минимуму. В более крупных и реалистичных проектах использование действия в каждом методе приведет к созданию очень подробных трассировок и поэтому не рекомендуется.

Измените StepOne и StepTwo, чтобы добавить дополнительную трассировку для следующих отдельных шагов.

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

Обратите внимание, что StepOne и StepTwo включают в себя ParentId, который ссылается на SomeWork. Консоль не обеспечивает качественную визуализацию вложенных деревьев работы, но многие средства просмотра на базе графического пользовательского интерфейса, такие как [Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md), могут отображать его в виде диаграммы Ганта.

[![Диаграмма Ганта в средстве Zipkin](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)

### <a name="optional-activitykind"></a>Дополнительно: ActivityKind

Действия имеют свойство <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType>, описывающее связь между действием и его родительским и дочерними объектами. По умолчанию для всех новых действий задано значение <xref:System.Diagnostics.ActivityKind.Internal>, подходящее для действий, которые являются внутренней операцией в приложении без удаленных родительских или дочерних объектов. Другие типы можно задать с помощью параметра kind в <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>. Другие варианты см. в разделе <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType>.

### <a name="optional-links"></a>Дополнительно: связи

При работе в системах пакетной обработки одно действие может представлять работу от имени множества различных запросов одновременно, каждый из которых имеет собственный идентификатор трассировки. Хотя действие может иметь только один родительский объект, его можно связать с дополнительными идентификаторами трассировки с помощью <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType>. Каждый ActivityLink заполняется с использованием <xref:System.Diagnostics.ActivityContext>, где хранятся сведения об идентификаторах для действий, с которыми выполняется связь. ActivityContext можно получить из внутрипроцессных объектов Activity с помощью <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> или выделить путем анализа из сериализованных данных об идентификаторах с помощью <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType>.

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

В отличие от событий и тегов, которые можно добавлять по мере необходимости, связи необходимо добавлять во время StartActivity(), после чего они становятся неизменяемыми.
