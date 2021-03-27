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
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="f605d-103">Программа анализа производительности dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f605d-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="f605d-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f605d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="f605d-105">Установка</span><span class="sxs-lookup"><span data-stu-id="f605d-105">Install</span></span>

<span data-ttu-id="f605d-106">Есть два способа загрузки и установки `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="f605d-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="f605d-107">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="f605d-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="f605d-108">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-trace) `dotnet-trace`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="f605d-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="f605d-109">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="f605d-109">**Direct download:**</span></span>

  <span data-ttu-id="f605d-110">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="f605d-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="f605d-111">OS</span><span class="sxs-lookup"><span data-stu-id="f605d-111">OS</span></span>  | <span data-ttu-id="f605d-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="f605d-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="f605d-113">Windows</span><span class="sxs-lookup"><span data-stu-id="f605d-113">Windows</span></span> | <span data-ttu-id="f605d-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="f605d-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="f605d-115">macOS</span><span class="sxs-lookup"><span data-stu-id="f605d-115">macOS</span></span>   | [<span data-ttu-id="f605d-116">x64</span><span class="sxs-lookup"><span data-stu-id="f605d-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="f605d-117">Linux</span><span class="sxs-lookup"><span data-stu-id="f605d-117">Linux</span></span>   | <span data-ttu-id="f605d-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="f605d-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="f605d-119">Для использования `dotnet-trace` в приложении x86 необходима соответствующая версия средства для архитектуры x86.</span><span class="sxs-lookup"><span data-stu-id="f605d-119">To use `dotnet-trace` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f605d-120">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f605d-120">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="f605d-121">Описание</span><span class="sxs-lookup"><span data-stu-id="f605d-121">Description</span></span>

<span data-ttu-id="f605d-122">Программа `dotnet-trace` —</span><span class="sxs-lookup"><span data-stu-id="f605d-122">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="f605d-123">это кроссплатформенное средство .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f605d-123">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="f605d-124">Выполняет сбор трассировок .NET Core для запущенного процесса без встроенного профилировщика.</span><span class="sxs-lookup"><span data-stu-id="f605d-124">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="f605d-125">Построен на [`EventPipe`](./eventpipe.md) среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f605d-125">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="f605d-126">Предоставляет одинаковые возможности в Windows, Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="f605d-126">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="f605d-127">Параметры</span><span class="sxs-lookup"><span data-stu-id="f605d-127">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f605d-128">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f605d-128">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="f605d-129">Отображение версии служебной программы dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="f605d-129">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="f605d-130">Команды</span><span class="sxs-lookup"><span data-stu-id="f605d-130">Commands</span></span>

| <span data-ttu-id="f605d-131">Команда</span><span class="sxs-lookup"><span data-stu-id="f605d-131">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="f605d-132">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="f605d-132">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="f605d-133">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="f605d-133">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="f605d-134">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f605d-134">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="f605d-135">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="f605d-135">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="f605d-136">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="f605d-136">dotnet-trace collect</span></span>

<span data-ttu-id="f605d-137">Собирает диагностическую трассировку для выполняющегося процесса.</span><span class="sxs-lookup"><span data-stu-id="f605d-137">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f605d-138">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f605d-138">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="f605d-139">Параметры</span><span class="sxs-lookup"><span data-stu-id="f605d-139">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="f605d-140">Задает размер кольцевого буфера в памяти (в мегабайтах).</span><span class="sxs-lookup"><span data-stu-id="f605d-140">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="f605d-141">По умолчанию используется значение 256 МБ.</span><span class="sxs-lookup"><span data-stu-id="f605d-141">Default 256 MB.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f605d-142">Если для целевого процесса события записываются слишком часто, это может привести к переполнению буфера и удалению некоторых событий.</span><span class="sxs-lookup"><span data-stu-id="f605d-142">If the target process writes events too frequently, it can overflow this buffer and some events might be dropped.</span></span> <span data-ttu-id="f605d-143">Если удаляется слишком много событий, увеличьте размер буфера и посмотрите, уменьшается ли число удаленных событий.</span><span class="sxs-lookup"><span data-stu-id="f605d-143">If too many events are getting dropped, increase the buffer size to see if the number of dropped events reduces.</span></span> <span data-ttu-id="f605d-144">Если не уменьшается, причиной может быть медленная работа средства чтения, из-за чего целевой буфер процесса не освобождается.</span><span class="sxs-lookup"><span data-stu-id="f605d-144">If the number of dropped events does not decrease with a larger buffer size, it may be due to a slow reader preventing the target process' buffers from being flushed.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="f605d-145">Уровень детализации создаваемых событий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f605d-145">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="f605d-146">Список ключевых слов поставщика среды выполнения CLR, которые должны быть разделены знаками `+`.</span><span class="sxs-lookup"><span data-stu-id="f605d-146">A list of CLR runtime provider keywords to enable separated by `+` signs.</span></span> <span data-ttu-id="f605d-147">Это простое сопоставление, позволяющее указывать ключевые слова событий посредством псевдонимов строк, а не их шестнадцатеричных значений.</span><span class="sxs-lookup"><span data-stu-id="f605d-147">This is a simple mapping that lets you specify event keywords via string aliases rather than their hex values.</span></span> <span data-ttu-id="f605d-148">Например, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` запрашивает тот же набор событий, что и `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span><span class="sxs-lookup"><span data-stu-id="f605d-148">For example, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` requests the same set of events as `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span></span> <span data-ttu-id="f605d-149">В таблице ниже приведен список доступных ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="f605d-149">The table below shows the list of available keywords:</span></span>

  | <span data-ttu-id="f605d-150">Псевдоним строки ключевого слова</span><span class="sxs-lookup"><span data-stu-id="f605d-150">Keyword String Alias</span></span> | <span data-ttu-id="f605d-151">Шестнадцатеричное значение ключевого слова</span><span class="sxs-lookup"><span data-stu-id="f605d-151">Keyword Hex Value</span></span> |
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

  <span data-ttu-id="f605d-152">Дополнительные сведения о поставщике CLR см. в [справочной документации по поставщику среды выполнения .NET](../../fundamentals/diagnostics/runtime-events.md).</span><span class="sxs-lookup"><span data-stu-id="f605d-152">You can read about the CLR provider more in detail on the [.NET runtime provider reference documentation](../../fundamentals/diagnostics/runtime-events.md).</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="f605d-153">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="f605d-153">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="f605d-154">Значение по умолчанию — `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="f605d-154">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="f605d-155">Имя процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f605d-155">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="f605d-156">Имя создаваемого порта диагностики.</span><span class="sxs-lookup"><span data-stu-id="f605d-156">The name of the diagnostic port to create.</span></span> <span data-ttu-id="f605d-157">О том, как использовать этот параметр для сбора данных трассировки из запуска приложения, см. в разделе [Использование порта диагностики для сбора данных трассировки из запуска приложения](#use-diagnostic-port-to-collect-a-trace-from-app-startup).</span><span class="sxs-lookup"><span data-stu-id="f605d-157">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="f605d-158">Выходной путь для собранных данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="f605d-158">The output path for the collected trace data.</span></span> <span data-ttu-id="f605d-159">Если это значение не указано, по умолчанию используется `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="f605d-159">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="f605d-160">Идентификатор процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f605d-160">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="f605d-161">Заранее определенный именованный набор конфигураций поставщиков, который позволяет кратко указывать типичные сценарии трассировки.</span><span class="sxs-lookup"><span data-stu-id="f605d-161">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="f605d-162">Доступны следующие профили.</span><span class="sxs-lookup"><span data-stu-id="f605d-162">The following profiles are available:</span></span>

 | <span data-ttu-id="f605d-163">Профиль</span><span class="sxs-lookup"><span data-stu-id="f605d-163">Profile</span></span> | <span data-ttu-id="f605d-164">Описание</span><span class="sxs-lookup"><span data-stu-id="f605d-164">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="f605d-165">Подходит для отслеживания загрузки ЦП и общих сведений среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="f605d-165">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="f605d-166">Этот вариант используется по умолчанию, если другой профиль или поставщики не указаны.</span><span class="sxs-lookup"><span data-stu-id="f605d-166">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="f605d-167">Отслеживает коллекции GC и распределения объектов samples.</span><span class="sxs-lookup"><span data-stu-id="f605d-167">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="f605d-168">Отслеживает коллекции GC только при очень низких издержках.</span><span class="sxs-lookup"><span data-stu-id="f605d-168">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="f605d-169">Список применяемых поставщиков `EventPipe`, разделенный запятыми.</span><span class="sxs-lookup"><span data-stu-id="f605d-169">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="f605d-170">Поставщики из этого списка применяются в дополнение к тем, которые подразумеваются в `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="f605d-170">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="f605d-171">При наличии несогласованности по конкретному поставщику указанная здесь конфигурация имеет приоритет над неявной конфигурацией из профиля.</span><span class="sxs-lookup"><span data-stu-id="f605d-171">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="f605d-172">Список поставщиков предоставляется в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="f605d-172">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="f605d-173">`Provider` имеет формат `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`;</span><span class="sxs-lookup"><span data-stu-id="f605d-173">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="f605d-174">`KeyValueArgs` имеет формат `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="f605d-174">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

  <span data-ttu-id="f605d-175">Дополнительные сведения о некоторых известных поставщиках в .NET см. в статье [Стандартные поставщики событий в .NET](./well-known-event-providers.md).</span><span class="sxs-lookup"><span data-stu-id="f605d-175">To learn more about some of the well-known providers in .NET, refer to [Well-known Event Providers](./well-known-event-providers.md).</span></span>

- <span data-ttu-id="f605d-176">**`-- <command>` (только для целевых приложений, использующих .NET 5.0)**</span><span class="sxs-lookup"><span data-stu-id="f605d-176">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="f605d-177">После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0.</span><span class="sxs-lookup"><span data-stu-id="f605d-177">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="f605d-178">Это может быть полезно при диагностике проблем, происходящих на ранних этапах процесса, таких как проблема с производительностью при запуске или ошибки загрузчика и модуля привязки.</span><span class="sxs-lookup"><span data-stu-id="f605d-178">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f605d-179">При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении.</span><span class="sxs-lookup"><span data-stu-id="f605d-179">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="f605d-180">Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="f605d-180">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-181">Для больших приложений остановка трассировки может занять много времени (до нескольких минут).</span><span class="sxs-lookup"><span data-stu-id="f605d-181">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="f605d-182">Среде выполнения необходимо передать кэш типов для всего управляемого кода, захваченного при трассировке.</span><span class="sxs-lookup"><span data-stu-id="f605d-182">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-183">В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-trace` будут совместно использовать одну и ту же переменную среды `TMPDIR`.</span><span class="sxs-lookup"><span data-stu-id="f605d-183">On Linux and macOS, this command expects the target application and `dotnet-trace` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="f605d-184">В противном случае время ожидания команды истечет.</span><span class="sxs-lookup"><span data-stu-id="f605d-184">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-185">Чтобы получить трассировку с помощью `dotnet-trace`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя.</span><span class="sxs-lookup"><span data-stu-id="f605d-185">To collect a trace using `dotnet-trace`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="f605d-186">В противном случае средство не сможет установить соединение с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="f605d-186">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-187">Если появится сообщение об ошибке, подобное сообщению `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, вы пытаетесь использовать средство `dotnet-trace`, разрядность которого не соответствует требуемой целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="f605d-187">If you see an error message similar to the following one: `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, you are trying to use `dotnet-trace` that has mismatched bitness against the target process.</span></span> <span data-ttu-id="f605d-188">Скачайте средство с соответствующей разрядностью по ссылке, приведенной в разделе [Установка](#install).</span><span class="sxs-lookup"><span data-stu-id="f605d-188">Make sure to download the correct bitness of the tool in the [install](#install) link.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="f605d-189">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="f605d-189">dotnet-trace convert</span></span>

<span data-ttu-id="f605d-190">Преобразует трассировки `nettrace` в альтернативные форматы для использования с другими средствами анализа трассировок.</span><span class="sxs-lookup"><span data-stu-id="f605d-190">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f605d-191">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f605d-191">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="f605d-192">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f605d-192">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="f605d-193">Исходный файл трассировки для преобразования.</span><span class="sxs-lookup"><span data-stu-id="f605d-193">Input trace file to be converted.</span></span> <span data-ttu-id="f605d-194">По умолчанию используется значение *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="f605d-194">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="f605d-195">Параметры</span><span class="sxs-lookup"><span data-stu-id="f605d-195">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="f605d-196">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="f605d-196">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="f605d-197">Имя файла выходных данных.</span><span class="sxs-lookup"><span data-stu-id="f605d-197">Output filename.</span></span> <span data-ttu-id="f605d-198">К нему добавляется расширение целевого формата.</span><span class="sxs-lookup"><span data-stu-id="f605d-198">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-199">Преобразование файлов `nettrace` в файлы `chromium` или `speedscope` является необратимым.</span><span class="sxs-lookup"><span data-stu-id="f605d-199">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="f605d-200">Файлы `speedscope` и `chromium` не содержат всей информации, необходимой для воссоздания `nettrace` файлов.</span><span class="sxs-lookup"><span data-stu-id="f605d-200">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="f605d-201">Однако команда `convert` сохраняет исходный файл `nettrace`, поэтому не удаляйте этот файл, если вы планируете открывать его в будущем.</span><span class="sxs-lookup"><span data-stu-id="f605d-201">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="f605d-202">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f605d-202">dotnet-trace ps</span></span>

 <span data-ttu-id="f605d-203">Список процессов dotnet, из которых можно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f605d-203">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f605d-204">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f605d-204">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="f605d-205">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="f605d-205">dotnet-trace list-profiles</span></span>

<span data-ttu-id="f605d-206">Список предварительно созданных профилей трассировки с перечислением поставщиков и фильтров в каждом профиле.</span><span class="sxs-lookup"><span data-stu-id="f605d-206">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f605d-207">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f605d-207">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="f605d-208">Сбор трассировки с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f605d-208">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="f605d-209">Для сбора трассировок с помощью `dotnet-trace` выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="f605d-209">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="f605d-210">Получите идентификатор процесса (PID) для трассируемого приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f605d-210">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="f605d-211">В Windows его можно получить, например, через диспетчер задач или с помощью команды `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="f605d-211">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="f605d-212">В Linux можно использовать, например, команду `ps`.</span><span class="sxs-lookup"><span data-stu-id="f605d-212">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="f605d-213">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f605d-213">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="f605d-214">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f605d-214">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="f605d-215">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="f605d-215">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="f605d-216">Чтобы остановить сбор, нажмите клавишу `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="f605d-216">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="f605d-217">`dotnet-trace` завершит запись событий в файл *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="f605d-217">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="f605d-218">Запуск дочернего приложения и получение трассировки от запуска с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f605d-218">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f605d-219">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f605d-219">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="f605d-220">Иногда бывает полезно получить трассировку процесса от запуска.</span><span class="sxs-lookup"><span data-stu-id="f605d-220">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="f605d-221">Для приложений, использующих .NET 5.0 или более поздней версии, это можно сделать с помощью dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="f605d-221">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="f605d-222">Это приведет к запуску `hello.exe` с `arg1` и `arg2` в качестве аргументов командной строки и сбору трассировки при запуске среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="f605d-222">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="f605d-223">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="f605d-223">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="f605d-224">Вы можете отключить сбор данных трассировки, нажав клавишу `<Enter>` или `<Ctrl + C>`.</span><span class="sxs-lookup"><span data-stu-id="f605d-224">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="f605d-225">Это также приведет к выходу из `hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="f605d-225">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-226">При запуске `hello.exe` с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать со стандартным stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="f605d-226">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="f605d-227">Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="f605d-227">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="f605d-228">Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.</span><span class="sxs-lookup"><span data-stu-id="f605d-228">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="f605d-229">Использование порта диагностики для сбора данных трассировки из запуска приложения</span><span class="sxs-lookup"><span data-stu-id="f605d-229">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="f605d-230">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f605d-230">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="f605d-231">Порт диагностики — это новый компонент среды выполнения, который появился в .NET 5. Он позволяет запускать трассировку из запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="f605d-231">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="f605d-232">Чтобы сделать это с помощью `dotnet-trace`, можно использовать либо `dotnet-trace collect -- <command>`, как показано в приведенных выше примерах, либо параметр `--diagnostic-port`.</span><span class="sxs-lookup"><span data-stu-id="f605d-232">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="f605d-233">Использование `dotnet-trace <collect|monitor> -- <command>` для запуска приложения в качестве дочернего процесса — самый простой способ быстрой трассировки приложения с момента запуска.</span><span class="sxs-lookup"><span data-stu-id="f605d-233">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="f605d-234">Однако если требуется более точное управление временем трассировки приложения (например, отслеживать приложение только в течение первых 10 минут, а затем продолжать выполнение), или если необходимо взаимодействовать с приложением их интерфейса командной строки, используйте параметр `--diagnostic-port`, который позволяет управлять как отслеживаемым целевым приложением, так и `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="f605d-234">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="f605d-235">Следующая команда заставляет `dotnet-trace` создать сокет диагностики с именем `myport.sock` и ожидать соединения.</span><span class="sxs-lookup"><span data-stu-id="f605d-235">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="f605d-236">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="f605d-236">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="f605d-237">В отдельной консоли запустите целевое приложение с переменной среды `DOTNET_DiagnosticPorts`, для которой задано значение в выходных данных `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="f605d-237">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="f605d-238">Это должно позволить `dotnet-trace` начать трассировку `my-dotnet-app`:</span><span class="sxs-lookup"><span data-stu-id="f605d-238">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="f605d-239">Запуск приложения с помощью `dotnet run` может привести к проблемам: интерфейс командной строки dotnet может порождать множество дочерних процессов, которые не являются вашим приложением, и они могут подключаться к `dotnet-trace` до приложения, в результате чего ваше приложение будет приостановлено во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="f605d-239">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="f605d-240">Рекомендуется использовать автономную версию приложения или запускать его с помощью `dotnet exec`.</span><span class="sxs-lookup"><span data-stu-id="f605d-240">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="f605d-241">Просмотр трассировки, собранной с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f605d-241">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="f605d-242">В Windows файлы *NETTRACE* можно просматривать и анализировать в [PerfView](https://github.com/microsoft/perfview). Если трассировка была собрана на другой платформе, ее файл можно переместить на компьютер с Windows для просмотра в PerfView.</span><span class="sxs-lookup"><span data-stu-id="f605d-242">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="f605d-243">В Linux трассировку можно просмотреть, изменив формат выходных данных с `dotnet-trace` на `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f605d-243">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="f605d-244">Чтобы изменить формат выходного файла, укажите параметр `-f|--format`. При значении `-f speedscope` программа `dotnet-trace` создаст файл `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f605d-244">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="f605d-245">Вы можете выбрать варианты `nettrace` (по умолчанию) или `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f605d-245">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="f605d-246">Файлы `Speedscope` можно открывать с помощью <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="f605d-246">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="f605d-247">Среда выполнения .NET Core создает трассировки в формате `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="f605d-247">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="f605d-248">В формат speedscope (если требуется) они преобразуются уже после завершения трассировки.</span><span class="sxs-lookup"><span data-stu-id="f605d-248">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="f605d-249">Так как некоторые преобразования приводят к потере данных, исходный файл `nettrace` сохраняется рядом с преобразованным файлом.</span><span class="sxs-lookup"><span data-stu-id="f605d-249">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="f605d-250">Использование dotnet-trace для получения значений счетчиков за период времени</span><span class="sxs-lookup"><span data-stu-id="f605d-250">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="f605d-251">Программа `dotnet-trace` позволяет выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="f605d-251">`dotnet-trace` can:</span></span>

* <span data-ttu-id="f605d-252">использовать `EventCounter` для простого мониторинга работоспособности в средах с высокой чувствительностью к производительности,</span><span class="sxs-lookup"><span data-stu-id="f605d-252">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="f605d-253">например рабочих;</span><span class="sxs-lookup"><span data-stu-id="f605d-253">For example, in production.</span></span>
* <span data-ttu-id="f605d-254">собирать трассировки, чтобы их не нужно было просматривать в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="f605d-254">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="f605d-255">Например, если вам нужны значения счетчика производительности из среды выполнения, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f605d-255">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="f605d-256">Эта команда означает, что счетчики среды выполнения будут отслеживаться каждую секунду, то есть реализует не требовательную к ресурсам схему мониторинга работоспособности.</span><span class="sxs-lookup"><span data-stu-id="f605d-256">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="f605d-257">Заменив `EventCounterIntervalSec=1` большим значением (например, 60), вы получите трассировку данных счетчиков меньшего объема и с меньшим уровнем детализации.</span><span class="sxs-lookup"><span data-stu-id="f605d-257">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="f605d-258">Следующая команда сокращает накладные расходы и размер трассировки сильнее, чем предыдущая:</span><span class="sxs-lookup"><span data-stu-id="f605d-258">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="f605d-259">Эта команда отключает события среды выполнения и профилировщик управляемого стека.</span><span class="sxs-lookup"><span data-stu-id="f605d-259">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="f605d-260">Использование файла RSP, чтобы не вводить длинные команды</span><span class="sxs-lookup"><span data-stu-id="f605d-260">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="f605d-261">Можно запустить команду `dotnet-trace` с файлом `.rsp`, содержащим аргументы для передачи.</span><span class="sxs-lookup"><span data-stu-id="f605d-261">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="f605d-262">Это может быть полезно при включении поставщиков, для которых требуются длинные аргументы, или при использовании среды оболочки, которая обрезает символы.</span><span class="sxs-lookup"><span data-stu-id="f605d-262">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="f605d-263">Ниже приведен пример поставщика, команда трассировки которого слишком громоздка, чтобы каждый раз набирать ее вручную.</span><span class="sxs-lookup"><span data-stu-id="f605d-263">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="f605d-264">Кроме того, в предыдущем примере аргумент содержит символ `"`.</span><span class="sxs-lookup"><span data-stu-id="f605d-264">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="f605d-265">Так как кавычки в каждой оболочке обрабатываются по-разному, могут возникать различные проблемы.</span><span class="sxs-lookup"><span data-stu-id="f605d-265">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="f605d-266">Например, команда в `zsh` будет отличаться от команды в `cmd`.</span><span class="sxs-lookup"><span data-stu-id="f605d-266">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="f605d-267">Вместо того чтобы вводить ее каждый раз, можно сохранить следующий текст в файл с именем `myprofile.rsp`.</span><span class="sxs-lookup"><span data-stu-id="f605d-267">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="f605d-268">После сохранения файла `myprofile.rsp` можно запустить `dotnet-trace` с этой конфигурацией, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f605d-268">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="f605d-269">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f605d-269">See also</span></span>

- [<span data-ttu-id="f605d-270">Стандартные поставщики событий из .NET</span><span class="sxs-lookup"><span data-stu-id="f605d-270">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
