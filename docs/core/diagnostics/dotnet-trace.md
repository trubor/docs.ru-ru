---
title: Средство диагностики dotnet-trace — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-trace для получения трассировки .NET для запущенного процесса без собственного профилировщика с помощью .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: 6bc5ad449f62ed0080ff6b1f401f1871d90cf5ec
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549336"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="f219e-103">Программа анализа производительности dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f219e-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="f219e-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f219e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="f219e-105">Установка</span><span class="sxs-lookup"><span data-stu-id="f219e-105">Install</span></span>

<span data-ttu-id="f219e-106">Есть два способа загрузки и установки `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="f219e-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="f219e-107">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="f219e-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="f219e-108">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-trace) `dotnet-trace`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="f219e-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="f219e-109">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="f219e-109">**Direct download:**</span></span>

  <span data-ttu-id="f219e-110">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="f219e-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="f219e-111">OS</span><span class="sxs-lookup"><span data-stu-id="f219e-111">OS</span></span>  | <span data-ttu-id="f219e-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="f219e-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="f219e-113">Windows</span><span class="sxs-lookup"><span data-stu-id="f219e-113">Windows</span></span> | <span data-ttu-id="f219e-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="f219e-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="f219e-115">macOS</span><span class="sxs-lookup"><span data-stu-id="f219e-115">macOS</span></span>   | [<span data-ttu-id="f219e-116">x64</span><span class="sxs-lookup"><span data-stu-id="f219e-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="f219e-117">Linux</span><span class="sxs-lookup"><span data-stu-id="f219e-117">Linux</span></span>   | <span data-ttu-id="f219e-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="f219e-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="f219e-119">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f219e-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="f219e-120">Описание</span><span class="sxs-lookup"><span data-stu-id="f219e-120">Description</span></span>

<span data-ttu-id="f219e-121">Программа `dotnet-trace` —</span><span class="sxs-lookup"><span data-stu-id="f219e-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="f219e-122">это кроссплатформенное средство .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f219e-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="f219e-123">Выполняет сбор трассировок .NET Core для запущенного процесса без встроенного профилировщика.</span><span class="sxs-lookup"><span data-stu-id="f219e-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="f219e-124">Построен на [`EventPipe`](./eventpipe.md) среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f219e-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="f219e-125">Предоставляет одинаковые возможности в Windows, Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="f219e-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="f219e-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="f219e-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f219e-127">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="f219e-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="f219e-128">Отображение версии служебной программы dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="f219e-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="f219e-129">Команды</span><span class="sxs-lookup"><span data-stu-id="f219e-129">Commands</span></span>

| <span data-ttu-id="f219e-130">Команда</span><span class="sxs-lookup"><span data-stu-id="f219e-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="f219e-131">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="f219e-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="f219e-132">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="f219e-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="f219e-133">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f219e-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="f219e-134">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="f219e-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="f219e-135">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="f219e-135">dotnet-trace collect</span></span>

<span data-ttu-id="f219e-136">Собирает диагностическую трассировку для выполняющегося процесса.</span><span class="sxs-lookup"><span data-stu-id="f219e-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f219e-137">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f219e-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="f219e-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="f219e-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="f219e-139">Задает размер кольцевого буфера в памяти (в мегабайтах).</span><span class="sxs-lookup"><span data-stu-id="f219e-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="f219e-140">По умолчанию используется значение 256 МБ.</span><span class="sxs-lookup"><span data-stu-id="f219e-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="f219e-141">Уровень детализации создаваемых событий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f219e-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="f219e-142">Список вызываемых событий среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f219e-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="f219e-143">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="f219e-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="f219e-144">Значение по умолчанию — `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="f219e-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="f219e-145">Имя процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f219e-145">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="f219e-146">Выходной путь для собранных данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="f219e-146">The output path for the collected trace data.</span></span> <span data-ttu-id="f219e-147">Если это значение не указано, по умолчанию используется `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="f219e-147">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="f219e-148">Идентификатор процесса, из которого нужно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f219e-148">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="f219e-149">Заранее определенный именованный набор конфигураций поставщиков, который позволяет кратко указывать типичные сценарии трассировки.</span><span class="sxs-lookup"><span data-stu-id="f219e-149">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="f219e-150">Доступны следующие профили.</span><span class="sxs-lookup"><span data-stu-id="f219e-150">The following profiles are available:</span></span>

 | <span data-ttu-id="f219e-151">Профиль</span><span class="sxs-lookup"><span data-stu-id="f219e-151">Profile</span></span> | <span data-ttu-id="f219e-152">Описание</span><span class="sxs-lookup"><span data-stu-id="f219e-152">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="f219e-153">Подходит для отслеживания загрузки ЦП и общих сведений среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="f219e-153">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="f219e-154">Этот вариант используется по умолчанию, если другой профиль или поставщики не указаны.</span><span class="sxs-lookup"><span data-stu-id="f219e-154">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="f219e-155">Отслеживает коллекции GC и распределения объектов samples.</span><span class="sxs-lookup"><span data-stu-id="f219e-155">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="f219e-156">Отслеживает коллекции GC только при очень низких издержках.</span><span class="sxs-lookup"><span data-stu-id="f219e-156">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="f219e-157">Список применяемых поставщиков `EventPipe`, разделенный запятыми.</span><span class="sxs-lookup"><span data-stu-id="f219e-157">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="f219e-158">Поставщики из этого списка применяются в дополнение к тем, которые подразумеваются в `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="f219e-158">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="f219e-159">При наличии несогласованности по конкретному поставщику указанная здесь конфигурация имеет приоритет над неявной конфигурацией из профиля.</span><span class="sxs-lookup"><span data-stu-id="f219e-159">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="f219e-160">Список поставщиков предоставляется в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="f219e-160">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="f219e-161">`Provider` имеет формат `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`;</span><span class="sxs-lookup"><span data-stu-id="f219e-161">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="f219e-162">`KeyValueArgs` имеет формат `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="f219e-162">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="f219e-163">**`-- <command>` (только для целевых приложений, использующих .NET 5.0)**</span><span class="sxs-lookup"><span data-stu-id="f219e-163">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="f219e-164">После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0.</span><span class="sxs-lookup"><span data-stu-id="f219e-164">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="f219e-165">Это может быть полезно при диагностике проблем, происходящих на ранних этапах процесса, таких как проблема с производительностью при запуске или ошибки загрузчика и модуля привязки.</span><span class="sxs-lookup"><span data-stu-id="f219e-165">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f219e-166">При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении.</span><span class="sxs-lookup"><span data-stu-id="f219e-166">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="f219e-167">Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="f219e-167">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="f219e-168">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="f219e-168">dotnet-trace convert</span></span>

<span data-ttu-id="f219e-169">Преобразует трассировки `nettrace` в альтернативные форматы для использования с другими средствами анализа трассировок.</span><span class="sxs-lookup"><span data-stu-id="f219e-169">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f219e-170">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f219e-170">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="f219e-171">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f219e-171">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="f219e-172">Исходный файл трассировки для преобразования.</span><span class="sxs-lookup"><span data-stu-id="f219e-172">Input trace file to be converted.</span></span> <span data-ttu-id="f219e-173">По умолчанию используется значение *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="f219e-173">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="f219e-174">Параметры</span><span class="sxs-lookup"><span data-stu-id="f219e-174">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="f219e-175">Задает формат выходных данных для преобразования файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="f219e-175">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="f219e-176">Имя файла выходных данных.</span><span class="sxs-lookup"><span data-stu-id="f219e-176">Output filename.</span></span> <span data-ttu-id="f219e-177">К нему добавляется расширение целевого формата.</span><span class="sxs-lookup"><span data-stu-id="f219e-177">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="f219e-178">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f219e-178">dotnet-trace ps</span></span>

 <span data-ttu-id="f219e-179">Список процессов dotnet, из которых можно получить трассировку.</span><span class="sxs-lookup"><span data-stu-id="f219e-179">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f219e-180">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f219e-180">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="f219e-181">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="f219e-181">dotnet-trace list-profiles</span></span>

<span data-ttu-id="f219e-182">Список предварительно созданных профилей трассировки с перечислением поставщиков и фильтров в каждом профиле.</span><span class="sxs-lookup"><span data-stu-id="f219e-182">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f219e-183">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f219e-183">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="f219e-184">Сбор трассировки с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f219e-184">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="f219e-185">Для сбора трассировок с помощью `dotnet-trace` выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="f219e-185">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="f219e-186">Получите идентификатор процесса (PID) для трассируемого приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f219e-186">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="f219e-187">В Windows его можно получить, например, через диспетчер задач или с помощью команды `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="f219e-187">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="f219e-188">В Linux можно использовать, например, команду `ps`.</span><span class="sxs-lookup"><span data-stu-id="f219e-188">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="f219e-189">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="f219e-189">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="f219e-190">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f219e-190">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="f219e-191">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="f219e-191">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="f219e-192">Чтобы остановить сбор, нажмите клавишу `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="f219e-192">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="f219e-193">`dotnet-trace` завершит запись событий в файл *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="f219e-193">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="f219e-194">Запуск дочернего приложения и получение трассировки от запуска с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f219e-194">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f219e-195">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f219e-195">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="f219e-196">Иногда бывает полезно получить трассировку процесса от запуска.</span><span class="sxs-lookup"><span data-stu-id="f219e-196">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="f219e-197">Для приложений, использующих .NET 5.0 или более поздней версии, это можно сделать с помощью dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="f219e-197">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="f219e-198">Это приведет к запуску `hello.exe` с `arg1` и `arg2` в качестве аргументов командной строки и сбору трассировки при запуске среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="f219e-198">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="f219e-199">Приведенная выше команда создает выходные данные наподобие следующих:</span><span class="sxs-lookup"><span data-stu-id="f219e-199">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="f219e-200">Вы можете отключить сбор данных трассировки, нажав клавишу `<Enter>` или `<Ctrl + C>`.</span><span class="sxs-lookup"><span data-stu-id="f219e-200">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="f219e-201">Это также приведет к выходу из `hello.exe`.</span><span class="sxs-lookup"><span data-stu-id="f219e-201">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="f219e-202">При запуске `hello.exe` с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать со стандартным stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="f219e-202">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="f219e-203">Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="f219e-203">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="f219e-204">Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.</span><span class="sxs-lookup"><span data-stu-id="f219e-204">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="f219e-205">Просмотр трассировки, собранной с помощью dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="f219e-205">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="f219e-206">В Windows файлы *NETTRACE* можно просматривать и анализировать в [PerfView](https://github.com/microsoft/perfview). Если трассировка была собрана на другой платформе, ее файл можно переместить на компьютер с Windows для просмотра в PerfView.</span><span class="sxs-lookup"><span data-stu-id="f219e-206">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="f219e-207">В Linux трассировку можно просмотреть, изменив формат выходных данных с `dotnet-trace` на `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f219e-207">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="f219e-208">Чтобы изменить формат выходного файла, укажите параметр `-f|--format`. При значении `-f speedscope` программа `dotnet-trace` создаст файл `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f219e-208">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="f219e-209">Вы можете выбрать варианты `nettrace` (по умолчанию) или `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="f219e-209">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="f219e-210">Файлы `Speedscope` можно открывать с помощью <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="f219e-210">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="f219e-211">Среда выполнения .NET Core создает трассировки в формате `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="f219e-211">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="f219e-212">В формат speedscope (если требуется) они преобразуются уже после завершения трассировки.</span><span class="sxs-lookup"><span data-stu-id="f219e-212">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="f219e-213">Так как некоторые преобразования приводят к потере данных, исходный файл `nettrace` сохраняется рядом с преобразованным файлом.</span><span class="sxs-lookup"><span data-stu-id="f219e-213">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="f219e-214">Использование dotnet-trace для получения значений счетчиков за период времени</span><span class="sxs-lookup"><span data-stu-id="f219e-214">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="f219e-215">Программа `dotnet-trace` позволяет выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="f219e-215">`dotnet-trace` can:</span></span>

* <span data-ttu-id="f219e-216">использовать `EventCounter` для простого мониторинга работоспособности в средах с высокой чувствительностью к производительности,</span><span class="sxs-lookup"><span data-stu-id="f219e-216">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="f219e-217">например рабочих;</span><span class="sxs-lookup"><span data-stu-id="f219e-217">For example, in production.</span></span>
* <span data-ttu-id="f219e-218">собирать трассировки, чтобы их не нужно было просматривать в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="f219e-218">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="f219e-219">Например, если вам нужны значения счетчика производительности из среды выполнения, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f219e-219">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="f219e-220">Эта команда означает, что счетчики среды выполнения будут отслеживаться каждую секунду, то есть реализует не требовательную к ресурсам схему мониторинга работоспособности.</span><span class="sxs-lookup"><span data-stu-id="f219e-220">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="f219e-221">Заменив `EventCounterIntervalSec=1` большим значением (например, 60), вы получите трассировку данных счетчиков меньшего объема и с меньшим уровнем детализации.</span><span class="sxs-lookup"><span data-stu-id="f219e-221">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="f219e-222">Следующая команда сокращает накладные расходы и размер трассировки сильнее, чем предыдущая:</span><span class="sxs-lookup"><span data-stu-id="f219e-222">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="f219e-223">Эта команда отключает события среды выполнения и профилировщик управляемого стека.</span><span class="sxs-lookup"><span data-stu-id="f219e-223">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="f219e-224">Поставщики .NET</span><span class="sxs-lookup"><span data-stu-id="f219e-224">.NET Providers</span></span>

<span data-ttu-id="f219e-225">Среда выполнения .NET Core поддерживает следующие поставщики .NET.</span><span class="sxs-lookup"><span data-stu-id="f219e-225">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="f219e-226">.NET Core использует одинаковые ключевые слова для включения трассировок `Event Tracing for Windows (ETW)` и `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="f219e-226">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="f219e-227">Имя поставщика</span><span class="sxs-lookup"><span data-stu-id="f219e-227">Provider name</span></span>                            | <span data-ttu-id="f219e-228">Сведения</span><span class="sxs-lookup"><span data-stu-id="f219e-228">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="f219e-229">Поставщик среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f219e-229">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="f219e-230">Ключевые слова среды выполнения CLR</span><span class="sxs-lookup"><span data-stu-id="f219e-230">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="f219e-231">Поставщик очистки</span><span class="sxs-lookup"><span data-stu-id="f219e-231">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="f219e-232">Ключевые слова очистки CLR</span><span class="sxs-lookup"><span data-stu-id="f219e-232">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="f219e-233">Включает пример профилировщика.</span><span class="sxs-lookup"><span data-stu-id="f219e-233">Enables the sample profiler.</span></span> |
