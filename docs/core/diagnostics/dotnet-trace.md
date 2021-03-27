---
title: Средство диагностики dotnet-trace — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-trace для получения трассировки .NET для запущенного процесса без собственного профилировщика с помощью .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: e4e5bf91a7e6a9bf98e8cb006864b4cbc5ca17a2
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624192"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>Программа анализа производительности dotnet-trace

**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий

## <a name="install"></a>Установка

Есть два способа загрузки и установки `dotnet-trace`:

- **Средство dotnet global:**

  Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-trace) `dotnet-trace`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- **Прямое скачивание:**

  скачайте исполняемый файл средства, соответствующий вашей платформе:

  | OS  | Платформа |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-trace/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64) |

> [!NOTE]
> Для использования `dotnet-trace` в приложении x86 необходима соответствующая версия средства для архитектуры x86.

## <a name="synopsis"></a>Краткий обзор

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Описание

Программа `dotnet-trace` —

* это кроссплатформенное средство .NET Core.
* Выполняет сбор трассировок .NET Core для запущенного процесса без встроенного профилировщика.
* Построен на [`EventPipe`](./eventpipe.md) среды выполнения .NET Core.
* Предоставляет одинаковые возможности в Windows, Linux и macOS.

## <a name="options"></a>Параметры

- **`-h|--help`**

  Отображение справки в командной строке.

- **`--version`**

  Отображение версии служебной программы dotnet-trace.

## <a name="commands"></a>Команды

| Команда                                                   |
|-----------------------------------------------------------|
| [dotnet-trace collect](#dotnet-trace-collect)             |
| [dotnet-trace convert](#dotnet-trace-convert)             |
| [dotnet-trace ps](#dotnet-trace-ps)                       |
| [dotnet-trace list-profiles](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-trace collect

Собирает диагностическую трассировку для выполняющегося процесса.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a>Параметры

- **`--buffersize <size>`**

  Задает размер кольцевого буфера в памяти (в мегабайтах). По умолчанию используется значение 256 МБ.

  > [!NOTE]
  > Если для целевого процесса события записываются слишком часто, это может привести к переполнению буфера и удалению некоторых событий. Если удаляется слишком много событий, увеличьте размер буфера и посмотрите, уменьшается ли число удаленных событий. Если не уменьшается, причиной может быть медленная работа средства чтения, из-за чего целевой буфер процесса не освобождается.

- **`--clreventlevel <clreventlevel>`**

  Уровень детализации создаваемых событий среды выполнения.

- **`--clrevents <clrevents>`**

  Список ключевых слов поставщика среды выполнения CLR, которые должны быть разделены знаками `+`. Это простое сопоставление, позволяющее указывать ключевые слова событий посредством псевдонимов строк, а не их шестнадцатеричных значений. Например, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` запрашивает тот же набор событий, что и `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`. В таблице ниже приведен список доступных ключевых слов.

  | Псевдоним строки ключевого слова | Шестнадцатеричное значение ключевого слова |
  | ------------ | ------------------- |
  | `gc` | `0x1` |
  | `gchandle` | `0x2` |
  | `fusion` | `0x4` |
  | `loader` | `0x8` |
  | `jit` | `0x10` |
  | `ngen` | `0x20` |
  | `startenumeration` | `0x40` |
  | `endenumeration` | `0x80` |
  | `security` | `0x400` |
  | `appdomainresourcemanagement` | `0x800` |
  | `jittracing` | `0x1000` |
  | `interop` | `0x2000` |
  | `contention` | `0x4000` |
  | `exception` | `0x8000` |
  | `threading` | `0x10000` |
  | `jittedmethodiltonativemap` | `0x20000` |
  | `overrideandsuppressngenevents` | `0x40000` |
  | `type` | `0x80000` |
  | `gcheapdump` | `0x100000` |
  | `gcsampledobjectallocationhigh` | `0x200000` |
  | `gcheapsurvivalandmovement` | `0x400000` |
  | `gcheapcollect` | `0x800000` |
  | `gcheapandtypenames` | `0x1000000` |
  | `gcsampledobjectallocationlow` | `0x2000000` |
  | `perftrack` | `0x20000000` |
  | `stack` | `0x40000000` |
  | `threadtransfer` | `0x80000000` |
  | `debugger` | `0x100000000` |
  | `monitoring` | `0x200000000` |
  | `codesymbols` | `0x400000000` |
  | `eventsource` | `0x800000000` |
  | `compilation` | `0x1000000000` |
  | `compilationdiagnostic` | `0x2000000000` |
  | `methoddiagnostic` | `0x4000000000` |
  | `typediagnostic` | `0x8000000000` |

  Дополнительные сведения о поставщике CLR см. в [справочной документации по поставщику среды выполнения .NET](../../fundamentals/diagnostics/runtime-events.md).

- **`--format {Chromium|NetTrace|Speedscope}`**

  Задает формат выходных данных для преобразования файла трассировки. Значение по умолчанию — `NetTrace`.

- **`-n, --name <name>`**

  Имя процесса, из которого нужно получить трассировку.

- **`--diagnostic-port <path-to-port>`**

  Имя создаваемого порта диагностики. О том, как использовать этот параметр для сбора данных трассировки из запуска приложения, см. в разделе [Использование порта диагностики для сбора данных трассировки из запуска приложения](#use-diagnostic-port-to-collect-a-trace-from-app-startup).

- **`-o|--output <trace-file-path>`**

  Выходной путь для собранных данных трассировки. Если это значение не указано, по умолчанию используется `trace.nettrace`.

- **`-p|--process-id <PID>`**

  Идентификатор процесса, из которого нужно получить трассировку.

- **`--profile <profile-name>`**

  Заранее определенный именованный набор конфигураций поставщиков, который позволяет кратко указывать типичные сценарии трассировки. Доступны следующие профили.

 | Профиль | Описание |
 |---------|-------------|
 |`cpu-sampling`|Подходит для отслеживания загрузки ЦП и общих сведений среды выполнения .NET. Этот вариант используется по умолчанию, если другой профиль или поставщики не указаны.|
 |`gc-verbose`|Отслеживает коллекции GC и распределения объектов samples.|
 |`gc-collect`|Отслеживает коллекции GC только при очень низких издержках.|

- **`--providers <list-of-comma-separated-providers>`**

  Список применяемых поставщиков `EventPipe`, разделенный запятыми. Поставщики из этого списка применяются в дополнение к тем, которые подразумеваются в `--profile <profile-name>`. При наличии несогласованности по конкретному поставщику указанная здесь конфигурация имеет приоритет над неявной конфигурацией из профиля.

  Список поставщиков предоставляется в следующем формате:

  - `Provider[,Provider]`
  - `Provider` имеет формат `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`;
  - `KeyValueArgs` имеет формат `[key1=value1][;key2=value2]`.

  Дополнительные сведения о некоторых известных поставщиках в .NET см. в статье [Стандартные поставщики событий в .NET](./well-known-event-providers.md).

- **`-- <command>` (только для целевых приложений, использующих .NET 5.0)**

  После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0. Это может быть полезно при диагностике проблем, происходящих на ранних этапах процесса, таких как проблема с производительностью при запуске или ошибки загрузчика и модуля привязки.

  > [!NOTE]
  > При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении. Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.

> [!NOTE]
> Для больших приложений остановка трассировки может занять много времени (до нескольких минут). Среде выполнения необходимо передать кэш типов для всего управляемого кода, захваченного при трассировке.

> [!NOTE]
> В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-trace` будут совместно использовать одну и ту же переменную среды `TMPDIR`. В противном случае время ожидания команды истечет.

> [!NOTE]
> Чтобы получить трассировку с помощью `dotnet-trace`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя. В противном случае средство не сможет установить соединение с целевым процессом.

> [!NOTE]
> Если появится сообщение об ошибке, подобное сообщению `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, вы пытаетесь использовать средство `dotnet-trace`, разрядность которого не соответствует требуемой целевым процессом. Скачайте средство с соответствующей разрядностью по ссылке, приведенной в разделе [Установка](#install).

## <a name="dotnet-trace-convert"></a>dotnet-trace convert

Преобразует трассировки `nettrace` в альтернативные форматы для использования с другими средствами анализа трассировок.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>Аргументы

- **`<input-filename>`**

  Исходный файл трассировки для преобразования. По умолчанию используется значение *trace.nettrace*.

### <a name="options"></a>Параметры

- **`--format <Chromium|NetTrace|Speedscope>`**

  Задает формат выходных данных для преобразования файла трассировки.

- **`-o|--output <output-filename>`**

  Имя файла выходных данных. К нему добавляется расширение целевого формата.

> [!NOTE]
> Преобразование файлов `nettrace` в файлы `chromium` или `speedscope` является необратимым. Файлы `speedscope` и `chromium` не содержат всей информации, необходимой для воссоздания `nettrace` файлов. Однако команда `convert` сохраняет исходный файл `nettrace`, поэтому не удаляйте этот файл, если вы планируете открывать его в будущем.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

 Список процессов dotnet, из которых можно получить трассировку.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-trace list-profiles

Список предварительно созданных профилей трассировки с перечислением поставщиков и фильтров в каждом профиле.

### <a name="synopsis"></a>Краткий обзор

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Сбор трассировки с помощью dotnet-trace

Для сбора трассировок с помощью `dotnet-trace` выполните указанные ниже действия.

- Получите идентификатор процесса (PID) для трассируемого приложения .NET Core.

  - В Windows его можно получить, например, через диспетчер задач или с помощью команды `tasklist`.
  - В Linux можно использовать, например, команду `ps`.
  - [dotnet-trace ps](#dotnet-trace-ps)

- Выполните следующую команду:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Приведенная выше команда создает выходные данные наподобие следующих:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Чтобы остановить сбор, нажмите клавишу `<Enter>`. `dotnet-trace` завершит запись событий в файл *trace.nettrace*.

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a>Запуск дочернего приложения и получение трассировки от запуска с помощью dotnet-trace

> [!IMPORTANT]
> Это работает только для приложений, использующих .NET 5.0 или более поздней версии.

Иногда бывает полезно получить трассировку процесса от запуска. Для приложений, использующих .NET 5.0 или более поздней версии, это можно сделать с помощью dotnet-trace.

Это приведет к запуску `hello.exe` с `arg1` и `arg2` в качестве аргументов командной строки и сбору трассировки при запуске среды выполнения:

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

Приведенная выше команда создает выходные данные наподобие следующих:

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

Вы можете отключить сбор данных трассировки, нажав клавишу `<Enter>` или `<Ctrl + C>`. Это также приведет к выходу из `hello.exe`.

> [!NOTE]
> При запуске `hello.exe` с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать со стандартным stdin/stdout.
> Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.
> Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a>Использование порта диагностики для сбора данных трассировки из запуска приложения

  > [!IMPORTANT]
  > Это работает только для приложений, использующих .NET 5.0 или более поздней версии.

Порт диагностики — это новый компонент среды выполнения, который появился в .NET 5. Он позволяет запускать трассировку из запуска приложения. Чтобы сделать это с помощью `dotnet-trace`, можно использовать либо `dotnet-trace collect -- <command>`, как показано в приведенных выше примерах, либо параметр `--diagnostic-port`.

Использование `dotnet-trace <collect|monitor> -- <command>` для запуска приложения в качестве дочернего процесса — самый простой способ быстрой трассировки приложения с момента запуска.

Однако если требуется более точное управление временем трассировки приложения (например, отслеживать приложение только в течение первых 10 минут, а затем продолжать выполнение), или если необходимо взаимодействовать с приложением их интерфейса командной строки, используйте параметр `--diagnostic-port`, который позволяет управлять как отслеживаемым целевым приложением, так и `dotnet-trace`.

1. Следующая команда заставляет `dotnet-trace` создать сокет диагностики с именем `myport.sock` и ожидать соединения.

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    Выходные данные:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. В отдельной консоли запустите целевое приложение с переменной среды `DOTNET_DiagnosticPorts`, для которой задано значение в выходных данных `dotnet-trace`.

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    Это должно позволить `dotnet-trace` начать трассировку `my-dotnet-app`:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > Запуск приложения с помощью `dotnet run` может привести к проблемам: интерфейс командной строки dotnet может порождать множество дочерних процессов, которые не являются вашим приложением, и они могут подключаться к `dotnet-trace` до приложения, в результате чего ваше приложение будет приостановлено во время выполнения. Рекомендуется использовать автономную версию приложения или запускать его с помощью `dotnet exec`.

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Просмотр трассировки, собранной с помощью dotnet-trace

В Windows файлы *NETTRACE* можно просматривать и анализировать в [PerfView](https://github.com/microsoft/perfview). Если трассировка была собрана на другой платформе, ее файл можно переместить на компьютер с Windows для просмотра в PerfView.

В Linux трассировку можно просмотреть, изменив формат выходных данных с `dotnet-trace` на `speedscope`. Чтобы изменить формат выходного файла, укажите параметр `-f|--format`. При значении `-f speedscope` программа `dotnet-trace` создаст файл `speedscope`. Вы можете выбрать варианты `nettrace` (по умолчанию) или `speedscope`. Файлы `Speedscope` можно открывать с помощью <https://www.speedscope.app>.

> [!NOTE]
> Среда выполнения .NET Core создает трассировки в формате `nettrace`. В формат speedscope (если требуется) они преобразуются уже после завершения трассировки. Так как некоторые преобразования приводят к потере данных, исходный файл `nettrace` сохраняется рядом с преобразованным файлом.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Использование dotnet-trace для получения значений счетчиков за период времени

Программа `dotnet-trace` позволяет выполнять следующие задачи:

* использовать `EventCounter` для простого мониторинга работоспособности в средах с высокой чувствительностью к производительности, например рабочих;
* собирать трассировки, чтобы их не нужно было просматривать в режиме реального времени.

Например, если вам нужны значения счетчика производительности из среды выполнения, используйте следующую команду:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Эта команда означает, что счетчики среды выполнения будут отслеживаться каждую секунду, то есть реализует не требовательную к ресурсам схему мониторинга работоспособности. Заменив `EventCounterIntervalSec=1` большим значением (например, 60), вы получите трассировку данных счетчиков меньшего объема и с меньшим уровнем детализации.

Следующая команда сокращает накладные расходы и размер трассировки сильнее, чем предыдущая:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Эта команда отключает события среды выполнения и профилировщик управляемого стека.

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a>Использование файла RSP, чтобы не вводить длинные команды

Можно запустить команду `dotnet-trace` с файлом `.rsp`, содержащим аргументы для передачи. Это может быть полезно при включении поставщиков, для которых требуются длинные аргументы, или при использовании среды оболочки, которая обрезает символы.

Ниже приведен пример поставщика, команда трассировки которого слишком громоздка, чтобы каждый раз набирать ее вручную.

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

Кроме того, в предыдущем примере аргумент содержит символ `"`. Так как кавычки в каждой оболочке обрабатываются по-разному, могут возникать различные проблемы. Например, команда в `zsh` будет отличаться от команды в `cmd`.

Вместо того чтобы вводить ее каждый раз, можно сохранить следующий текст в файл с именем `myprofile.rsp`.

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

После сохранения файла `myprofile.rsp` можно запустить `dotnet-trace` с этой конфигурацией, выполнив следующую команду:

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a>См. также раздел

- [Стандартные поставщики событий из .NET](well-known-event-providers.md)
