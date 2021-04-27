---
title: Средство диагностики dotnet-counters — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-counter для нерегламентированного мониторинга работоспособности и анализа производительности первого уровня.
ms.date: 11/17/2020
ms.topic: reference
ms.openlocfilehash: 436db72677186b5fcc8b560451b69e616870f66e
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740804"
---
# <a name="investigate-performance-counters-dotnet-counters"></a>Исследование счетчиков производительности (dotnet-counter)

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий

## <a name="install"></a>Установка

Есть два способа загрузки и установки `dotnet-counters`:

- **Средство dotnet global:**

  Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-counters) `dotnet-counters`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- **Прямое скачивание:**

  скачайте исполняемый файл средства, соответствующий вашей платформе:

  | OS  | Платформа |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-counters/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64) |

> [!NOTE]
> Для использования `dotnet-counters` в приложении x86 необходима соответствующая версия средства для архитектуры x86.

## <a name="synopsis"></a>Краткий обзор

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Описание

`dotnet-counters` — это средство мониторинга производительности и первого уровня анализа производительности. Оно умеет отслеживать значения счетчиков производительности, опубликованные через API <xref:System.Diagnostics.Tracing.EventCounter>. Например, вы можете быстро отслеживать такие параметры, как загрузка ЦП или частота возникновения исключений в приложении .NET Core, чтобы обнаружить подозрительное поведение перед началом более серьезных расследований с помощью `PerfView` или `dotnet-trace`.

## <a name="options"></a>Параметры

- **`--version`**

  Отображение версии служебной программы dotnet-counters.

- **`-h|--help`**

  Отображение справки в командной строке.

## <a name="commands"></a>Команды

| Команда                                             |
|-----------------------------------------------------|
| [dotnet-counters collect](#dotnet-counters-collect) |
| [dotnet-counters list](#dotnet-counters-list)       |
| [dotnet-counters monitor](#dotnet-counters-monitor) |
| [dotnet-counters ps](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet-counters collect

Периодический сбор выбранных значений счетчиков и их экспорт в указанном формате файла для последующей обработки.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>Параметры

- **`-p|--process-id <PID>`**

  Идентификатор процесса, из которого нужно получить данные счетчика.

- **`-n|--name <name>`**

  Имя процесса, из которого нужно получить данные счетчика.

- **`--diagnostic-port`**

  Имя создаваемого порта диагностики. Сведения об использовании этого параметра для запуска счетчиков мониторинга во время запуска приложения см. в разделе [Использование порта диагностики](#using-diagnostic-port).

- **`--refresh-interval <SECONDS>`**

  Время (в секундах) между обновлением значений отображаемых счетчиков

- **`--counters <COUNTERS>`**

  Список счетчиков, разделенный запятыми. Вы можете объявить счетчики как `provider_name[:counter_name]`. Если `provider_name` используется без соответствующего списка счетчиков, отображаются все счетчики от поставщика. Для обнаружения имен поставщиков и счетчиков используйте команду [dotnet-counters list](#dotnet-counters-list).

- **`--format <csv|json>`**

  Экспортируемый формат. В настоящее время доступно: csv, json.

- **`-o|--output <output>`**

  Имя выходного файла.

- **`-- <command>` (только для целевых приложений, использующих .NET 5.0 или более поздней версии)**

  После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0. `dotnet-counters` запустит процесс с указанной командой и соберет запрошенные метрики. Это часто бывает полезно для сбора метрик для пути запуска приложения и может использоваться для диагностики и отслеживания проблем, происходящих незадолго до основной точки входа или вскоре после нее.

  > [!NOTE]
  > При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении. Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.

  > [!NOTE]
  > При запуске исполняемого файла .NET с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать с его stdin/stdout. Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса. Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра. Если необходимо использовать stdin/stdout, можно применить параметр `--diagnostic-port`. Дополнительные сведения см. в разделе [Использование порта диагностики](#using-diagnostic-port).

> [!NOTE]
> В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-counters` будут совместно использовать одну и ту же переменную среды `TMPDIR`. В противном случае время ожидания команды истечет.

> [!NOTE]
> Чтобы получить метрики с помощью `dotnet-counters`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя. В противном случае средство не сможет установить соединение с целевым процессом.

### <a name="examples"></a>Примеры

- Сбор всех счетчиков с интервалом обновления в 3 секунды и создание CSV-файла в качестве выходных данных:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- Запустите `dotnet mvc.dll` как дочерний процесс и начните сбор счетчиков времени выполнения и счетчиков размещения ASP.NET Core из запуска и сохраните их в виде выходных данных JSON:

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a>dotnet-counters list

Отображение списка имен и описаний счетчиков, сгруппированных по поставщикам.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Пример

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> Счетчики `Microsoft.AspNetCore.Hosting` отображаются при обнаружении процессов, поддерживающих эти счетчики, например при запуске приложения ASP.NET Core на хост-компьютере.

## <a name="dotnet-counters-monitor"></a>dotnet-counters monitor

Отображение периодически обновляемых значений для выбранных счетчиков.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a>Параметры

- **`-p|--process-id <PID>`**

  Идентификатор отслеживаемого процесса.

- **`-n|--name <name>`**

  Имя отслеживаемого процесса.

- **`--diagnostic-port`**

  Имя создаваемого порта диагностики. Сведения об использовании этого параметра для запуска счетчиков мониторинга во время запуска приложения см. в разделе [Использование порта диагностики](#using-diagnostic-port).

- **`--refresh-interval <SECONDS>`**

  Время (в секундах) между обновлением значений отображаемых счетчиков

- **`--counters <COUNTERS>`**

  Список счетчиков, разделенный запятыми. Вы можете объявить счетчики как `provider_name[:counter_name]`. Если `provider_name` используется без соответствующего списка счетчиков, отображаются все счетчики от поставщика. Для обнаружения имен поставщиков и счетчиков используйте команду [dotnet-counters list](#dotnet-counters-list).

 **`-- <command>` (только для целевых приложений, использующих .NET 5.0 или более поздней версии)**

  После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0. `dotnet-counters` запустит процесс с указанной командой и будет отслеживать запрошенные метрики. Это часто бывает полезно для сбора метрик для пути запуска приложения и может использоваться для диагностики и отслеживания проблем, происходящих незадолго до основной точки входа или вскоре после нее.

  > [!NOTE]
  > При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении. Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.

  > [!NOTE]
  > При запуске исполняемого файла .NET с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать с его stdin/stdout. Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса. Если дочерний процесс завершает работу до средства, средство также завершит работу. Если необходимо использовать stdin/stdout, можно применить параметр `--diagnostic-port`. Дополнительные сведения см. в разделе [Использование порта диагностики](#using-diagnostic-port).

> [!NOTE]
> В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-counters` будут совместно использовать одну и ту же переменную среды `TMPDIR`.

> [!NOTE]
> Для мониторинга метрик с помощью `dotnet-counters` переменную необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя.

> [!NOTE]
> Если появится сообщение об ошибке, подобное сообщению `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, вы пытаетесь использовать средство `dotnet-counters`, разрядность которого не соответствует требуемой целевым процессом. Скачайте средство с соответствующей разрядностью по ссылке, приведенной в разделе [Установка](#install).

### <a name="examples"></a>Примеры

- Мониторинг всех счетчиков из `System.Runtime` с интервалом обновления 3 секунды:

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- Мониторинг только счетчиков использования ЦП и размера кучи GC из `System.Runtime`:

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Мониторинг значений `EventCounter` из определяемых пользователем `EventSource`: Дополнительные сведения см. в статье [Руководство. Измерение производительности с помощью EventCounters в .NET Core](event-counter-perf.md).

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- Просмотр всех известных счетчиков, доступных в `dotnet-counters`:

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- Просмотр всех известных счетчиков, доступных в `dotnet-counters` для приложений .NET 5:

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- Запустите `my-aspnet-server.exe` и отслеживайте число сборок, загруженных при запуске (только для .NET 5.0 или более поздних версий):

  > [!IMPORTANT]
  > Это работает только для приложений, использующих .NET 5.0 или более поздней версии.

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- Запустите `my-aspnet-server.exe` с `arg1` и `arg2` в качестве аргументов командной строки и отслеживайте рабочий набор и размер кучи сборки мусора при запуске (только для .NET 5.0 или более поздней версии):

  > [!IMPORTANT]
  > Это работает только для приложений, использующих .NET 5.0 или более поздней версии.

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a>dotnet-counters ps

Отображение списка процессов dotnet, которые можно отслеживать.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Пример

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a>Использование порта диагностики

  > [!IMPORTANT]
  > Это работает только для приложений, использующих .NET 5.0 или более поздней версии.

Порт диагностики — это новый компонент среды выполнения, который появился в .NET 5. Он позволяет запускать мониторинг или сбор данных счетчиков во время запуска приложения. Чтобы сделать это с помощью `dotnet-counters`, можно использовать либо `dotnet-counters <collect|monitor> -- <command>`, как показано в приведенных выше примерах, либо параметр `--diagnostic-port`.

Использование `dotnet-counters <collect|monitor> -- <command>` для запуска приложения в качестве дочернего процесса — самый простой способ быстрого отслеживания приложения с момента запуска.

Однако если требуется более точное управление временем отслеживания приложения (например, отслеживать приложение только в течение первых 10 минут, а затем продолжать выполнение), или если необходимо взаимодействовать с приложением их интерфейса командной строки, используйте параметр `--diagnostic-port`, который позволяет управлять как отслеживаемым целевым приложением, так и `dotnet-counters`.

1. Следующая команда заставляет dotnet-counters создать сокет диагностики с именем `myport.sock` и ожидать соединения.

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    Выходные данные:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. В отдельной консоли запустите целевое приложение с переменной среды `DOTNET_DiagnosticPorts`, для которой задано значение в выходных данных `dotnet-counters`.

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    Это должно позволить `dotnet-counters` запустить сбор данных счетчиков в `my-dotnet-app`:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > Запуск приложения с помощью `dotnet run` может привести к проблемам: интерфейс командной строки dotnet может порождать множество дочерних процессов, которые не являются вашим приложением, и они могут подключаться к `dotnet-counters` до приложения, в результате чего ваше приложение будет приостановлено во время выполнения. Рекомендуется использовать автономную версию приложения или запускать его с помощью `dotnet exec`.
