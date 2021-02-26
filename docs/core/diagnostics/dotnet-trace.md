---
title: Средство диагностики dotnet-trace — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-trace для получения трассировки .NET для запущенного процесса без собственного профилировщика с помощью .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: abf98df6e31747ea3e8013fc77b246613a3402ad
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583003"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="6cc84-103">Программа анализа производительности dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="6cc84-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="6cc84-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="6cc84-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="6cc84-105">Установка</span><span class="sxs-lookup"><span data-stu-id="6cc84-105">Install</span></span>

<span data-ttu-id="6cc84-106">Есть два способа загрузки и установки `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="6cc84-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="6cc84-107">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="6cc84-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="6cc84-108">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-trace) `dotnet-trace`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="6cc84-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="6cc84-109">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="6cc84-109">**Direct download:**</span></span>

  <span data-ttu-id="6cc84-110">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="6cc84-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="6cc84-111">OS</span><span class="sxs-lookup"><span data-stu-id="6cc84-111">OS</span></span>  | <span data-ttu-id="6cc84-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="6cc84-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="6cc84-113">Windows</span><span class="sxs-lookup"><span data-stu-id="6cc84-113">Windows</span></span> | <span data-ttu-id="6cc84-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="6cc84-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="6cc84-115">macOS</span><span class="sxs-lookup"><span data-stu-id="6cc84-115">macOS</span></span>   | [<span data-ttu-id="6cc84-116">x64</span><span class="sxs-lookup"><span data-stu-id="6cc84-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="6cc84-117">Linux</span><span class="sxs-lookup"><span data-stu-id="6cc84-117">Linux</span></span>   | <span data-ttu-id="6cc84-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="6cc84-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="6cc84-119">Для использования `dotnet-trace` в приложении x86 необходима соответствующая версия средства для архитектуры x86.</span><span class="sxs-lookup"><span data-stu-id="6cc84-119">To use `dotnet-trace` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6cc84-120">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="6cc84-120">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="6cc84-121">Описание</span><span class="sxs-lookup"><span data-stu-id="6cc84-121">Description</span></span>

<span data-ttu-id="6cc84-122">Программа `dotnet-trace` —</span><span class="sxs-lookup"><span data-stu-id="6cc84-122">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="6cc84-123">это кроссплатформенное средство .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cc84-123">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="6cc84-124">Выполняет сбор трассировок .NET Core для запущенного процесса без встроенного профилировщика.</span><span class="sxs-lookup"><span data-stu-id="6cc84-124">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="6cc84-125">Построен на [`EventPipe`](./eventpipe.md) среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cc84-125">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="6cc84-126">Предоставляет одинаковые возможности в Windows, Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="6cc84-126">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="6cc84-127">Параметры</span><span class="sxs-lookup"><span data-stu-id="6cc84-127">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="6cc84-128">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="6cc84-128">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="6cc84-129">Отображение версии служебной программы dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="6cc84-129">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="6cc84-130">Команды</span><span class="sxs-lookup"><span data-stu-id="6cc84-130">Commands</span></span>

| <span data-ttu-id="6cc84-131">Команда</span><span class="sxs-lookup"><span data-stu-id="6cc84-131">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="6cc84-132">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="6cc84-132">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="6cc84-133">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="6cc84-133">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="6cc84-134">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="6cc84-134">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="6cc84-135">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="6cc84-135">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="6cc84-136">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="6cc84-136">dotnet-trace collect</span></span>

<span data-ttu-id="6cc84-137">Собирает диагностическую трассировку для выполняющегося процесса.</span><span class="sxs-lookup"><span data-stu-id="6cc84-137">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="6cc84-138">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="6cc84-138">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="6cc84-139">Параметры</span><span class="sxs-lookup"><span data-stu-id="6cc84-139">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="6cc84-140">Задает размер кольцевого буфера в памяти (в мегабайтах).</span><span class="sxs-lookup"><span data-stu-id="6cc84-140">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="6cc84-141">По умолчанию используется значение 256 МБ.</span><span class="sxs-lookup"><span data-stu-id="6cc84-141">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="6cc84-142">Уровень детализации создаваемых событий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6cc84-142">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="6cc84-143">Список ключевых слов поставщика среды выполнения CLR, которые должны быть разделены знаками `+`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-143">A list of CLR runtime provider keywords to enable separated by `+` signs.</span></span> <span data-ttu-id="6cc84-144">Это простое сопоставление, позволяющее указывать ключевые слова событий посредством псевдонимов строк, а не их шестнадцатеричных значений.</span><span class="sxs-lookup"><span data-stu-id="6cc84-144">This is a simple mapping that lets you specify event keywords via string aliases rather than their hex values.</span></span> <span data-ttu-id="6cc84-145">Например, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` запрашивает тот же набор событий, что и `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-145">For example, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` requests the same set of events as `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span></span> <span data-ttu-id="6cc84-146">В таблице ниже приведен список доступных ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="6cc84-146">The table below shows the list of available keywords:</span></span>

  | <span data-ttu-id="6cc84-147">Псевдоним строки ключевого слова</span><span class="sxs-lookup"><span data-stu-id="6cc84-147">Keyword String Alias</span></span> | <span data-ttu-id="6cc84-148">Шестнадцатеричное значение ключевого слова</span><span class="sxs-lookup"><span data-stu-id="6cc84-148">Keyword Hex Value</span></span> |
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

  <span data-ttu-id="6cc84-149">Дополнительные сведения о поставщике CLR см. в [справочной документации по поставщику среды выполнения .NET](../../fundamentals/diagnostics/runtime-events.md).</span><span class="sxs-lookup"><span data-stu-id="6cc84-149">You can read about the CLR provider more in detail on the [.NET runtime provider reference documentation](../../fundamentals/diagnostics/runtime-events.md).</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="6cc84-150">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-150">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="6cc84-151">Значение по умолчанию — `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-151">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="6cc84-152">Имя процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="6cc84-152">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="6cc84-153">Имя создаваемого порта диагностики.</span><span class="sxs-lookup"><span data-stu-id="6cc84-153">The name of the diagnostic port to create.</span></span> <span data-ttu-id="6cc84-154">О том, как использовать этот параметр для сбора данных трассировки из запуска приложения, см. в разделе [Использование порта диагностики для сбора данных трассировки из запуска приложения](#use-diagnostic-port-to-collect-a-trace-from-app-startup).</span><span class="sxs-lookup"><span data-stu-id="6cc84-154">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="6cc84-155">Выходной путь для собранных данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-155">The output path for the collected trace data.</span></span> <span data-ttu-id="6cc84-156">Если это значение не указано, по умолчанию используется `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-156">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="6cc84-157">Идентификатор процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="6cc84-157">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="6cc84-158">Заранее определенный именованный набор конфигураций поставщиков, который позволяет кратко указывать типичные сценарии трассировки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-158">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="6cc84-159">Доступны следующие профили.</span><span class="sxs-lookup"><span data-stu-id="6cc84-159">The following profiles are available:</span></span>

 | <span data-ttu-id="6cc84-160">Профиль</span><span class="sxs-lookup"><span data-stu-id="6cc84-160">Profile</span></span> | <span data-ttu-id="6cc84-161">Описание</span><span class="sxs-lookup"><span data-stu-id="6cc84-161">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="6cc84-162">Подходит для отслеживания загрузки ЦП и общих сведений среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="6cc84-162">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="6cc84-163">Этот вариант используется по умолчанию, если другой профиль или поставщики не указаны.</span><span class="sxs-lookup"><span data-stu-id="6cc84-163">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="6cc84-164">Отслеживает коллекции GC и распределения объектов samples.</span><span class="sxs-lookup"><span data-stu-id="6cc84-164">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="6cc84-165">Отслеживает коллекции GC только при очень низких издержках.</span><span class="sxs-lookup"><span data-stu-id="6cc84-165">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="6cc84-166">Список применяемых поставщиков `EventPipe`, разделенный запятыми.</span><span class="sxs-lookup"><span data-stu-id="6cc84-166">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="6cc84-167">Поставщики из этого списка применяются в дополнение к тем, которые подразумеваются в `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-167">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="6cc84-168">При наличии несогласованности по конкретному поставщику указанная здесь конфигурация имеет приоритет над неявной конфигурацией из профиля.</span><span class="sxs-lookup"><span data-stu-id="6cc84-168">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="6cc84-169">Список поставщиков предоставляется в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="6cc84-169">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="6cc84-170">`Provider` имеет формат `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`;</span><span class="sxs-lookup"><span data-stu-id="6cc84-170">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="6cc84-171">`KeyValueArgs` имеет формат `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-171">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

  <span data-ttu-id="6cc84-172">Дополнительные сведения о некоторых известных поставщиках в .NET см. в статье [Стандартные поставщики событий в .NET](./well-known-event-providers.md).</span><span class="sxs-lookup"><span data-stu-id="6cc84-172">To learn more about some of the well-known providers in .NET, refer to [Well-known Event Providers](./well-known-event-providers.md).</span></span>

- <span data-ttu-id="6cc84-173">**`-- <command>` (только для целевых приложений, использующих .NET 5.0)**</span><span class="sxs-lookup"><span data-stu-id="6cc84-173">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="6cc84-174">После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0.</span><span class="sxs-lookup"><span data-stu-id="6cc84-174">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="6cc84-175">Это может быть полезно при диагностике проблем, происходящих на ранних этапах процесса, таких как проблема с производительностью при запуске или ошибки загрузчика и модуля привязки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-175">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6cc84-176">При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении.</span><span class="sxs-lookup"><span data-stu-id="6cc84-176">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="6cc84-177">Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-177">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-178">Для больших приложений остановка трассировки может занять много времени (до нескольких минут).</span><span class="sxs-lookup"><span data-stu-id="6cc84-178">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="6cc84-179">Среде выполнения необходимо передать кэш типов для всего управляемого кода, захваченного при трассировке.</span><span class="sxs-lookup"><span data-stu-id="6cc84-179">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-180">В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-trace` будут совместно использовать одну и ту же переменную среды `TMPDIR`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-180">On Linux and macOS, this command expects the target application and `dotnet-trace` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="6cc84-181">В противном случае время ожидания команды истечет.</span><span class="sxs-lookup"><span data-stu-id="6cc84-181">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-182">Чтобы получить трассировку с помощью `dotnet-trace`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя.</span><span class="sxs-lookup"><span data-stu-id="6cc84-182">To collect a trace using `dotnet-trace`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="6cc84-183">В противном случае средство не сможет установить соединение с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="6cc84-183">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-184">Если появится сообщение об ошибке, подобное сообщению `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, вы пытаетесь использовать средство `dotnet-trace`, разрядность которого не соответствует требуемой целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="6cc84-184">If you see an error message similar to the following one: `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, you are trying to use `dotnet-trace` that has mismatched bitness against the target process.</span></span> <span data-ttu-id="6cc84-185">Скачайте средство с соответствующей разрядностью по ссылке, приведенной в разделе [Установка](#install).</span><span class="sxs-lookup"><span data-stu-id="6cc84-185">Make sure to download the correct bitness of the tool in the [install](#install) link.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="6cc84-186">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="6cc84-186">dotnet-trace convert</span></span>

<span data-ttu-id="6cc84-187">Преобразует трассировки `nettrace` в альтернативные форматы для использования с другими средствами анализа трассировок.</span><span class="sxs-lookup"><span data-stu-id="6cc84-187">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="6cc84-188">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="6cc84-188">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="6cc84-189">Аргументы</span><span class="sxs-lookup"><span data-stu-id="6cc84-189">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="6cc84-190">Исходный файл трассировки для преобразования.</span><span class="sxs-lookup"><span data-stu-id="6cc84-190">Input trace file to be converted.</span></span> <span data-ttu-id="6cc84-191">По умолчанию используется значение *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="6cc84-191">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="6cc84-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="6cc84-192">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="6cc84-193">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-193">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="6cc84-194">Имя файла выходных данных.</span><span class="sxs-lookup"><span data-stu-id="6cc84-194">Output filename.</span></span> <span data-ttu-id="6cc84-195">К нему добавляется расширение целевого формата.</span><span class="sxs-lookup"><span data-stu-id="6cc84-195">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-196">Преобразование файлов `nettrace` в файлы `chromium` или `speedscope` является необратимым.</span><span class="sxs-lookup"><span data-stu-id="6cc84-196">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="6cc84-197">Файлы `speedscope` и `chromium` не содержат всей информации, необходимой для воссоздания `nettrace` файлов.</span><span class="sxs-lookup"><span data-stu-id="6cc84-197">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="6cc84-198">Однако команда `convert` сохраняет исходный файл `nettrace`, поэтому не удаляйте этот файл, если вы планируете открывать его в будущем.</span><span class="sxs-lookup"><span data-stu-id="6cc84-198">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="6cc84-199">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="6cc84-199">dotnet-trace ps</span></span>

 <span data-ttu-id="6cc84-200">Список процессов dotnet, из которых можно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="6cc84-200">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="6cc84-201">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="6cc84-201">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="6cc84-202">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="6cc84-202">dotnet-trace list-profiles</span></span>

<span data-ttu-id="6cc84-203">Список предварительно созданных профилей трассировки с перечислением поставщиков и фильтров в каждом профиле.</span><span class="sxs-lookup"><span data-stu-id="6cc84-203">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="6cc84-204">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="6cc84-204">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="6cc84-205">Сбор трассировки с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="6cc84-205">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="6cc84-206">Для сбора трассировок с помощью `dotnet-trace` выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="6cc84-206">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="6cc84-207">Получите идентификатор процесса (PID) для трассируемого приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6cc84-207">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="6cc84-208">В Windows его можно получить, например, через диспетчер задач или с помощью команды `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-208">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="6cc84-209">В Linux можно использовать, например, команду `ps`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-209">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="6cc84-210">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="6cc84-210">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="6cc84-211">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="6cc84-211">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="6cc84-212">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="6cc84-212">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="6cc84-213">Чтобы остановить сбор, нажмите клавишу `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-213">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="6cc84-214">`dotnet-trace` завершит запись событий в файл *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="6cc84-214">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="6cc84-215">Запуск дочернего приложения и получение трассировки от запуска с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="6cc84-215">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc84-216">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="6cc84-216">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="6cc84-217">Иногда бывает полезно получить трассировку процесса от запуска.</span><span class="sxs-lookup"><span data-stu-id="6cc84-217">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="6cc84-218">Для приложений, использующих .NET 5.0 или более поздней версии, это можно сделать с помощью dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="6cc84-218">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="6cc84-219">Это приведет к запуску `hello.exe` с `arg1` и `arg2` в качестве аргументов командной строки и сбору трассировки при запуске среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="6cc84-219">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="6cc84-220">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="6cc84-220">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="6cc84-221">Вы можете отключить сбор данных трассировки, нажав клавишу `<Enter>` или `<Ctrl + C>`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-221">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="6cc84-222">Это также приведет к выходу из `hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-222">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-223">При запуске `hello.exe` с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать со стандартным stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="6cc84-223">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="6cc84-224">Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="6cc84-224">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="6cc84-225">Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.</span><span class="sxs-lookup"><span data-stu-id="6cc84-225">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="6cc84-226">Использование порта диагностики для сбора данных трассировки из запуска приложения</span><span class="sxs-lookup"><span data-stu-id="6cc84-226">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6cc84-227">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="6cc84-227">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="6cc84-228">Порт диагностики — это новый компонент среды выполнения, который появился в .NET 5. Он позволяет запускать трассировку из запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="6cc84-228">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="6cc84-229">Чтобы сделать это с помощью `dotnet-trace`, можно использовать либо `dotnet-trace collect -- <command>`, как показано в приведенных выше примерах, либо параметр `--diagnostic-port`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-229">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="6cc84-230">Использование `dotnet-trace <collect|monitor> -- <command>` для запуска приложения в качестве дочернего процесса — самый простой способ быстрой трассировки приложения с момента запуска.</span><span class="sxs-lookup"><span data-stu-id="6cc84-230">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="6cc84-231">Однако если требуется более точное управление временем трассировки приложения (например, отслеживать приложение только в течение первых 10 минут, а затем продолжать выполнение), или если необходимо взаимодействовать с приложением их интерфейса командной строки, используйте параметр `--diagnostic-port`, который позволяет управлять как отслеживаемым целевым приложением, так и `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-231">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="6cc84-232">Следующая команда заставляет `dotnet-trace` создать сокет диагностики с именем `myport.sock` и ожидать соединения.</span><span class="sxs-lookup"><span data-stu-id="6cc84-232">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="6cc84-233">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="6cc84-233">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="6cc84-234">В отдельной консоли запустите целевое приложение с переменной среды `DOTNET_DiagnosticPorts`, для которой задано значение в выходных данных `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-234">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="6cc84-235">Это должно позволить `dotnet-trace` начать трассировку `my-dotnet-app`:</span><span class="sxs-lookup"><span data-stu-id="6cc84-235">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="6cc84-236">Запуск приложения с помощью `dotnet run` может привести к проблемам: интерфейс командной строки dotnet может порождать множество дочерних процессов, которые не являются вашим приложением, и они могут подключаться к `dotnet-trace` до приложения, в результате чего ваше приложение будет приостановлено во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="6cc84-236">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="6cc84-237">Рекомендуется использовать автономную версию приложения или запускать его с помощью `dotnet exec`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-237">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="6cc84-238">Просмотр трассировки, собранной с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="6cc84-238">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="6cc84-239">В Windows файлы *NETTRACE* можно просматривать и анализировать в [PerfView](https://github.com/microsoft/perfview). Если трассировка была собрана на другой платформе, ее файл можно переместить на компьютер с Windows для просмотра в PerfView.</span><span class="sxs-lookup"><span data-stu-id="6cc84-239">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="6cc84-240">В Linux трассировку можно просмотреть, изменив формат выходных данных с `dotnet-trace` на `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-240">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="6cc84-241">Чтобы изменить формат выходного файла, укажите параметр `-f|--format`. При значении `-f speedscope` программа `dotnet-trace` создаст файл `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-241">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="6cc84-242">Вы можете выбрать варианты `nettrace` (по умолчанию) или `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-242">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="6cc84-243">Файлы `Speedscope` можно открывать с помощью <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="6cc84-243">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="6cc84-244">Среда выполнения .NET Core создает трассировки в формате `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-244">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="6cc84-245">В формат speedscope (если требуется) они преобразуются уже после завершения трассировки.</span><span class="sxs-lookup"><span data-stu-id="6cc84-245">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="6cc84-246">Так как некоторые преобразования приводят к потере данных, исходный файл `nettrace` сохраняется рядом с преобразованным файлом.</span><span class="sxs-lookup"><span data-stu-id="6cc84-246">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="6cc84-247">Использование dotnet-trace для получения значений счетчиков за период времени</span><span class="sxs-lookup"><span data-stu-id="6cc84-247">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="6cc84-248">Программа `dotnet-trace` позволяет выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="6cc84-248">`dotnet-trace` can:</span></span>

* <span data-ttu-id="6cc84-249">использовать `EventCounter` для простого мониторинга работоспособности в средах с высокой чувствительностью к производительности,</span><span class="sxs-lookup"><span data-stu-id="6cc84-249">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="6cc84-250">например рабочих;</span><span class="sxs-lookup"><span data-stu-id="6cc84-250">For example, in production.</span></span>
* <span data-ttu-id="6cc84-251">собирать трассировки, чтобы их не нужно было просматривать в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="6cc84-251">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="6cc84-252">Например, если вам нужны значения счетчика производительности из среды выполнения, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="6cc84-252">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="6cc84-253">Эта команда означает, что счетчики среды выполнения будут отслеживаться каждую секунду, то есть реализует не требовательную к ресурсам схему мониторинга работоспособности.</span><span class="sxs-lookup"><span data-stu-id="6cc84-253">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="6cc84-254">Заменив `EventCounterIntervalSec=1` большим значением (например, 60), вы получите трассировку данных счетчиков меньшего объема и с меньшим уровнем детализации.</span><span class="sxs-lookup"><span data-stu-id="6cc84-254">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="6cc84-255">Следующая команда сокращает накладные расходы и размер трассировки сильнее, чем предыдущая:</span><span class="sxs-lookup"><span data-stu-id="6cc84-255">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="6cc84-256">Эта команда отключает события среды выполнения и профилировщик управляемого стека.</span><span class="sxs-lookup"><span data-stu-id="6cc84-256">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="6cc84-257">Использование файла RSP, чтобы не вводить длинные команды</span><span class="sxs-lookup"><span data-stu-id="6cc84-257">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="6cc84-258">Можно запустить команду `dotnet-trace` с файлом `.rsp`, содержащим аргументы для передачи.</span><span class="sxs-lookup"><span data-stu-id="6cc84-258">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="6cc84-259">Это может быть полезно при включении поставщиков, для которых требуются длинные аргументы, или при использовании среды оболочки, которая обрезает символы.</span><span class="sxs-lookup"><span data-stu-id="6cc84-259">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="6cc84-260">Ниже приведен пример поставщика, команда трассировки которого слишком громоздка, чтобы каждый раз набирать ее вручную.</span><span class="sxs-lookup"><span data-stu-id="6cc84-260">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="6cc84-261">Кроме того, в предыдущем примере аргумент содержит символ `"`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-261">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="6cc84-262">Так как кавычки в каждой оболочке обрабатываются по-разному, могут возникать различные проблемы.</span><span class="sxs-lookup"><span data-stu-id="6cc84-262">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="6cc84-263">Например, команда в `zsh` будет отличаться от команды в `cmd`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-263">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="6cc84-264">Вместо того чтобы вводить ее каждый раз, можно сохранить следующий текст в файл с именем `myprofile.rsp`.</span><span class="sxs-lookup"><span data-stu-id="6cc84-264">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="6cc84-265">После сохранения файла `myprofile.rsp` можно запустить `dotnet-trace` с этой конфигурацией, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="6cc84-265">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="6cc84-266">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6cc84-266">See also</span></span>

- [<span data-ttu-id="6cc84-267">Стандартные поставщики событий из .NET</span><span class="sxs-lookup"><span data-stu-id="6cc84-267">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
