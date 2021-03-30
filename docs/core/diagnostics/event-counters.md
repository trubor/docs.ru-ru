---
title: Счетчики событий в .NET Core
description: В этой статье вы узнаете, что такое счетчики событий и как их реализовать и использовать.
ms.date: 08/07/2020
ms.openlocfilehash: 8efa3134e83ba6fdc7563e97ef6422cb5f2099b6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872786"
---
# <a name="eventcounters-in-net-core"></a>Счетчики событий в .NET Core

**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.0 и более поздних версий

Счетчики событий — это API .NET Core, которые используются для упрощенного кроссплатформенного сбора метрик производительности практически в реальном времени. Счетчики событий были добавлены как альтернатива счетчикам производительности, которые применялись в .NET Framework на базе Windows. В этой статье вы узнаете, что такое счетчики событий и как их реализовать и использовать.

Начиная с NET Core 3.0 среда выполнения .NET Core и некоторые библиотеки .NET публикуют основные данные диагностики, используя счетчики событий. Помимо счетчиков событий, предоставляемых средой выполнения .NET, вы можете реализовывать и собственные счетчики событий. Счетчики событий можно использовать для отслеживания различных метрик. Узнайте подробнее о них в статье, посвященной [известным счетчикам событий в .NET](available-counters.md)

Они являются частью <xref:System.Diagnostics.Tracing.EventSource> и передаются в средства прослушивания автоматически и на регулярной основе. Как и все остальные события в <xref:System.Diagnostics.Tracing.EventSource>, их можно использовать как внутри, так и вне процессов через <xref:System.Diagnostics.Tracing.EventListener> и [EventPipe](./eventpipe.md). В этой статье рассматриваются межплатформенные возможности счетчиков событий и намеренно исключены PerfView и ETW (трассировка событий для Windows), хотя обе эти функции можно использовать со счетчиками событий.

![Схема счетчиков событий внутри и вне процессов](media/event-counters.svg)

## <a name="eventcounter-api-overview"></a>Общие сведения об API счетчиков событий

Счетчики делятся на две основные категории. Некоторые счетчики предназначены для "оценки" значений, таких как общее число исключений, общее число глобальных каталогов и общее число запросов. Другие счетчики представляют "моментальные снимки" таких значений, как использование кучи, загрузка ЦП и размер рабочего набора. В каждой из этих категорий есть два типа счетчиков, которые различаются по тому, как они получают значение. Счетчики с опросом получают значение в результате обратного вызова, а значения счетчиков без опроса задаются непосредственно в экземпляре соответствующего счетчика.

Счетчики работают следующим образом:

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

Прослушиватель событий определяет величину интервала измерений. В конце каждого интервала в прослушиватель передается значение для каждого счетчика. Реализации счетчика определяют, какие API и вычисления использовались в каждом интервале для получения значения.

1. Метод <xref:System.Diagnostics.Tracing.EventCounter> регистрирует набор значений. Метод <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> добавляет новое значение в набор. В каждом интервале вычисляется статистическая сводка по набору, например минимальное, максимальное и среднее значение. Средство [dotnet-counters](dotnet-counters.md) всегда отображает среднее значение. Метод <xref:System.Diagnostics.Tracing.EventCounter> пригодится для описания дискретного набора операций. Общее использование может включать мониторинг среднего размера последних операций ввода-вывода в байтах или среднее денежное значение набора финансовых транзакций.

1. Метод <xref:System.Diagnostics.Tracing.IncrementingEventCounter> записывает промежуточные итоги для каждого интервала. Метод <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> добавляется к итогу. Например, если `Increment()` за один и тот же интервал вызывается трижды со значениями `1`, `2` и `5`, то в качестве значения счетчика для этого интервала будет выводиться промежуточный итог `8`. Средство [dotnet-counters](dotnet-counters.md) отображает скорость из расчета общая сумма/время. Метод <xref:System.Diagnostics.Tracing.IncrementingEventCounter> позволяет измерять частоту выполнения того или иного действия, например число запросов, обрабатываемых в секунду.

1. Метод <xref:System.Diagnostics.Tracing.PollingCounter> определяет выводимое значение, используя обратный вызов. В каждом интервале вызывается предоставляемая пользователем функция обратного вызова, а возвращаемое значение становится значением счетчика. Метод <xref:System.Diagnostics.Tracing.PollingCounter> можно использовать для запроса метрики из внешнего источника, например для получения текущего количества свободных байтов на диске. Его также можно использовать для получения пользовательской статистики, вычисляемой приложением по запросу. В качестве примеров можно привести отчеты по 95-му процентилю задержек последних запросов и по текущему проценту попадания в кэш.

1. Метод <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> определяет выводимое значение приращения, используя обратный вызов. В каждом интервале выполняется обратный вызов, а разница между текущим и предыдущим вызовами становится отчетным значением. Средство [dotnet-counters](dotnet-counters.md) всегда отображает разницу как скорость из расчета отчетное значение/время. Этот счетчик полезен, если при каждом вхождении вызывать API нецелесообразно, но можно запрашивать общее количество вхождений. Например, можно указывать, сколько байтов записывается в файл в секунду, даже без уведомления о записи каждого байта.

## <a name="implement-an-eventsource"></a>Реализация счетчика событий

В приведенном ниже коде реализуется пример <xref:System.Diagnostics.Tracing.EventSource>, предоставляемый как именованный поставщик `"Sample.EventCounter.Minimal"`. Этот источник содержит <xref:System.Diagnostics.Tracing.EventCounter>, который представляет время обработки запроса. Счетчик имеет имя (т. е. уникальный идентификатор в источнике) и отображаемое имя, и оба этих имени используют средства прослушивателя, такие как [dotnet-counter](dotnet-counters.md).

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

Метод `dotnet-counters ps` отображает список процессов .NET, которые можно отслеживать:

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

Передайте имя <xref:System.Diagnostics.Tracing.EventSource> в параметр `--counters`, чтобы начать мониторинг счетчика:

```console
dotnet-counters monitor --process-id 1400180 --counters Sample.EventCounter.Minimal
```

В следующем примере показаны выходные данные мониторинга:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

Нажмите <kbd>q</kbd>, чтобы остановить мониторинг.

#### <a name="conditional-counters"></a>Условные счетчики

При реализации <xref:System.Diagnostics.Tracing.EventSource> для соответствующих счетчиков могут быть созданы условные экземпляры при вызове метода <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> со значением <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> параметра `EventCommand.Enable`. Чтобы экземпляр счетчика создавался только в том случае, если он имеет значение `null`, используйте [оператор присваивания объединения со значением NULL](../../csharp/language-reference/operators/null-coalescing-operator.md). Кроме того, пользовательские методы могут оценивать метод <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A>, чтобы определить, включен ли текущий источник событий.

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> Условными называются счетчики, для которых создается условный экземпляр, т. е. производится микрооптимизация. Среда выполнения адаптирует этот шаблон для сценариев, в которых счетчики обычно не используются, чтобы сэкономить долю миллисекунды.

### <a name="net-core-runtime-example-counters"></a>Примеры счетчиков в среде выполнения .NET Core

В среде выполнения .NET Core можно привести множество хороших примеров реализации. Ниже показана реализация среды выполнения для счетчика, который отслеживает размер рабочего набора приложения.

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

Метод <xref:System.Diagnostics.Tracing.PollingCounter> сообщает о текущем объеме физической памяти, сопоставленном с процессом (рабочим набором) приложения, так как он фиксирует метрику в определенный момент времени. Обратный вызов для опроса значения — это заданное лямбда-выражение, которое, по сути, представляет собой вызов API <xref:System.Environment.WorkingSet?displayProperty=fullName>. <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> и <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> — необязательные свойства, которые можно задать, чтобы помочь клиентской стороне счетчика отображать значение точнее. Например, [dotnet-counters](dotnet-counters.md) использует эти свойства для более удобного отображения имен счетчиков на экране.

> [!IMPORTANT]
> Свойства `DisplayName` не локализуются.

Для <xref:System.Diagnostics.Tracing.PollingCounter> и <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>не нужно выполнять никаких других действий. Оба они сами опрашивают значения через указанный клиентом интервал.

Ниже приведен пример счетчика среды выполнения, реализованного с помощью <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>.

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

<xref:System.Diagnostics.Tracing.IncrementingPollingCounter> использует API <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> для сообщения о приращении общего количества конфликтов блокировок. Свойство <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> необязательное, но может подсказать, какой интервал лучше выбрать для счетчика. Например, число конфликтов блокировки лучше отображать как _количество в секунду_, поэтому для параметра <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> этого счетчика устанавливается значение одна секунда. Частоту отображения данных можно настраивать для различных типов счетчиков скорости.

> [!NOTE]
> Параметр <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> _не_ используется средством [dotnet-counters](dotnet-counters.md), а прослушиватели событий не обязаны его использовать.

Существуют и другие реализации счетчиков, к которым можно обращаться для справки. См. репозиторий [среды выполнения .NET](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs).

## <a name="concurrency"></a>Параллелизм

> [!TIP]
> API счетчиков событий не гарантирует безопасность потоков. Когда делегаты, передаваемые в экземпляры <xref:System.Diagnostics.Tracing.PollingCounter> или <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>, вызываются несколькими потоками, за безопасность потоков таких делегатов отвечаете вы.

Например, рассмотрим следующий <xref:System.Diagnostics.Tracing.EventSource> для отслеживания запросов.

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

Метод `AddRequest()` может вызываться из обработчика запросов, а `RequestRateCounter` опрашивает значение с интервалом, указанным клиентом счетчика. Однако метод `AddRequest()` могут вызываться одновременно несколько потоков, создавая для `_requestCount` состояние гонки. Альтернативный, поточно-ориентированный способ приращения `_requestCount` — использовать <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

Чтобы предотвратить разорванные операции чтения (в 32-разрядных архитектурах) поля `_requestCount` типа `long`, используйте <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType>.

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a>Использование счетчиков событий

Счетчики событий можно использовать двумя основными способами — внутри и вне процессов. Использование счетчиков событий можно разделить на три уровня различных технологий потребления.

- Транспортировка событий в поток необработанных данных через ETW или EventPipe:
  - ETW API входят с ОС Windows, а EventPipe доступен как [.NET API](https://github.com/dotnet/diagnostics/blob/main/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console) или как диагностический [протокол IPC](https://github.com/dotnet/diagnostics/blob/main/documentation/design-docs/ipc-protocol.md).
- Декодирование потока двоичных событий в события:
  - [Библиотека TraceEvent](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) обрабатывает оба формата потоковой передачи, ETW и EventPipe.
- Средства командной строки и графического интерфейса:
  - Такие средства, как PerfView (ETW или EventPipe), dotnet-counters (только EventPipe) и dotnet-monitor (только EventPipe).

### <a name="consume-out-of-proc"></a>Использование вне процессов

Очень часто счетчики событий используются вне процессов. Для получения данных в кроссплатформенном режиме через EventPipe можно использовать [dotnet-counters](dotnet-counters.md). Средство `dotnet-counters` — это кроссплатформенный глобальный инструмент dotnet CLI, который можно использовать для отслеживания значений счетчиков. Чтобы узнать, как использовать `dotnet-counters` для мониторинга счетчиков, ознакомьтесь с информацией о [dotnet-counters](dotnet-counters.md) или изучите руководство [Измерение производительности с помощью счетчиков событий](event-counter-perf.md).

#### <a name="dotnet-trace"></a>dotnet-trace

Средство `dotnet-trace` можно использовать для получения данных счетчика через EventPipe. Ниже приведен пример использования `dotnet-trace` для получения данных счетчика.

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

Дополнительные сведения о том, как получать значения счетчиков в перспективе, см. в документации по [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time).

#### <a name="azure-application-insights"></a>Azure Application Insights

Счетчики событий можно использовать с помощью Azure Monitor, а именно — Application Insights Azure. Счетчики можно добавлять и удалять, а также выбирать пользовательские или популярные счетчики. Дополнительные сведения см. в статье [Настройка счетчиков для получения данных](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).

#### <a name="dotnet-monitor"></a>dotnet-monitor

`dotnet-monitor` — экспериментальное средство, упрощающее доступ к диагностическим сведениям в процессе .NET. Оно представляет собой расширенную версию всех средств диагностики. Наряду с трассировкой оно может отслеживать метрики и собирать дампы памяти и дампы сборки мусора. Оно распространяется как в виде средства командной строки, так и в виде образа Docker. Оно предоставляет REST API, а сбор артефактов диагностики осуществляется с помощью вызовов REST.

Дополнительные сведения см. в статье [Знакомство с экспериментальным средством dotnet-monitor](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).

### <a name="consume-in-proc"></a>Использование внутри процесса

Значения счетчика можно использовать через API <xref:System.Diagnostics.Tracing.EventListener>. <xref:System.Diagnostics.Tracing.EventListener> — это внутрипроцессный способ использования любых событий, записанных всеми экземплярами <xref:System.Diagnostics.Tracing.EventSource> в приложении. Дополнительные сведения об использовании API `EventListener` см. в статье <xref:System.Diagnostics.Tracing.EventListener>.

Сначала необходимо включить <xref:System.Diagnostics.Tracing.EventSource>, который создает значение счетчика. Переопределите метод <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> так, чтобы получать уведомление при создании <xref:System.Diagnostics.Tracing.EventSource>, и, если это правильный метод <xref:System.Diagnostics.Tracing.EventSource> со счетчиками событий, вы сможете вызывать для него <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType>. Пример переопределения:

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="11-22":::

#### <a name="sample-code"></a>Образец кода

Ниже приведен пример класса <xref:System.Diagnostics.Tracing.EventListener>, который выводит все имена и значения счетчиков из среды выполнения .NET <xref:System.Diagnostics.Tracing.EventSource> для публикации внутренних счетчиков (`System.Runtime`) каждую секунду.

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

Как показано выше, _необходимо_ убедиться, что аргумент `"EventCounterIntervalSec"` задан в аргументе `filterPayload` при вызове <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>. В противном случае счетчики не смогут сбрасывать значения, так как не будут знать, с каким интервалом нужно выполнять сброс.

## <a name="see-also"></a>См. также

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
