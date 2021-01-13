---
title: Средство диагностики dotnet-counters — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-counter для нерегламентированного мониторинга работоспособности и анализа производительности первого уровня.
ms.date: 11/17/2020
ms.openlocfilehash: 89695c77e7913d41f030890be7cc00947e42fa3a
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856059"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="2f057-103">Исследование счетчиков производительности (dotnet-counter)</span><span class="sxs-lookup"><span data-stu-id="2f057-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="2f057-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="2f057-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="2f057-105">Установка</span><span class="sxs-lookup"><span data-stu-id="2f057-105">Install</span></span>

<span data-ttu-id="2f057-106">Есть два способа загрузки и установки `dotnet-counters`:</span><span class="sxs-lookup"><span data-stu-id="2f057-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="2f057-107">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="2f057-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="2f057-108">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-counters) `dotnet-counters`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="2f057-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="2f057-109">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="2f057-109">**Direct download:**</span></span>

  <span data-ttu-id="2f057-110">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="2f057-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="2f057-111">OS</span><span class="sxs-lookup"><span data-stu-id="2f057-111">OS</span></span>  | <span data-ttu-id="2f057-112">Платформа</span><span class="sxs-lookup"><span data-stu-id="2f057-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="2f057-113">Windows</span><span class="sxs-lookup"><span data-stu-id="2f057-113">Windows</span></span> | <span data-ttu-id="2f057-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="2f057-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="2f057-115">macOS</span><span class="sxs-lookup"><span data-stu-id="2f057-115">macOS</span></span>   | [<span data-ttu-id="2f057-116">x64</span><span class="sxs-lookup"><span data-stu-id="2f057-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="2f057-117">Linux</span><span class="sxs-lookup"><span data-stu-id="2f057-117">Linux</span></span>   | <span data-ttu-id="2f057-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="2f057-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="2f057-119">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="2f057-119">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="2f057-120">Описание</span><span class="sxs-lookup"><span data-stu-id="2f057-120">Description</span></span>

<span data-ttu-id="2f057-121">`dotnet-counters` — это средство мониторинга производительности и первого уровня анализа производительности.</span><span class="sxs-lookup"><span data-stu-id="2f057-121">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="2f057-122">Оно умеет отслеживать значения счетчиков производительности, опубликованные через API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="2f057-122">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="2f057-123">Например, вы можете быстро отслеживать такие параметры, как загрузка ЦП или частота возникновения исключений в приложении .NET Core, чтобы обнаружить подозрительное поведение перед началом более серьезных расследований с помощью `PerfView` или `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="2f057-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="2f057-124">Параметры</span><span class="sxs-lookup"><span data-stu-id="2f057-124">Options</span></span>

- **`--version`**

  <span data-ttu-id="2f057-125">Отображение версии служебной программы dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="2f057-125">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2f057-126">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="2f057-126">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="2f057-127">Команды</span><span class="sxs-lookup"><span data-stu-id="2f057-127">Commands</span></span>

| <span data-ttu-id="2f057-128">Команда</span><span class="sxs-lookup"><span data-stu-id="2f057-128">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="2f057-129">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="2f057-129">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="2f057-130">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="2f057-130">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="2f057-131">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="2f057-131">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="2f057-132">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="2f057-132">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="2f057-133">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="2f057-133">dotnet-counters collect</span></span>

<span data-ttu-id="2f057-134">Периодический сбор выбранных значений счетчиков и их экспорт в указанном формате файла для последующей обработки.</span><span class="sxs-lookup"><span data-stu-id="2f057-134">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2f057-135">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="2f057-135">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="2f057-136">Параметры</span><span class="sxs-lookup"><span data-stu-id="2f057-136">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="2f057-137">Идентификатор процесса, из которого нужно получить данные счетчика.</span><span class="sxs-lookup"><span data-stu-id="2f057-137">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="2f057-138">Имя процесса, из которого нужно получить данные счетчика.</span><span class="sxs-lookup"><span data-stu-id="2f057-138">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="2f057-139">Имя создаваемого порта диагностики.</span><span class="sxs-lookup"><span data-stu-id="2f057-139">The name of the diagnostic port to create.</span></span> <span data-ttu-id="2f057-140">Сведения об использовании этого параметра для запуска счетчиков мониторинга во время запуска приложения см. в разделе [Использование порта диагностики](#using-diagnostic-port).</span><span class="sxs-lookup"><span data-stu-id="2f057-140">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="2f057-141">Время (в секундах) между обновлением значений отображаемых счетчиков</span><span class="sxs-lookup"><span data-stu-id="2f057-141">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="2f057-142">Список счетчиков, разделенный запятыми.</span><span class="sxs-lookup"><span data-stu-id="2f057-142">A comma-separated list of counters.</span></span> <span data-ttu-id="2f057-143">Вы можете объявить счетчики как `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="2f057-143">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="2f057-144">Если `provider_name` используется без соответствующего списка счетчиков, отображаются все счетчики от поставщика.</span><span class="sxs-lookup"><span data-stu-id="2f057-144">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="2f057-145">Для обнаружения имен поставщиков и счетчиков используйте команду [dotnet-counters list](#dotnet-counters-list).</span><span class="sxs-lookup"><span data-stu-id="2f057-145">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="2f057-146">Экспортируемый формат.</span><span class="sxs-lookup"><span data-stu-id="2f057-146">The format to be exported.</span></span> <span data-ttu-id="2f057-147">В настоящее время доступно: csv, json.</span><span class="sxs-lookup"><span data-stu-id="2f057-147">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="2f057-148">Имя выходного файла.</span><span class="sxs-lookup"><span data-stu-id="2f057-148">The name of the output file.</span></span>

- <span data-ttu-id="2f057-149">**`-- <command>` (только для целевых приложений, использующих .NET 5.0 или более поздней версии)**</span><span class="sxs-lookup"><span data-stu-id="2f057-149">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="2f057-150">После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0.</span><span class="sxs-lookup"><span data-stu-id="2f057-150">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="2f057-151">`dotnet-counters` запустит процесс с указанной командой и соберет запрошенные метрики.</span><span class="sxs-lookup"><span data-stu-id="2f057-151">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="2f057-152">Это часто бывает полезно для сбора метрик для пути запуска приложения и может использоваться для диагностики и отслеживания проблем, происходящих незадолго до основной точки входа или вскоре после нее.</span><span class="sxs-lookup"><span data-stu-id="2f057-152">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2f057-153">При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении.</span><span class="sxs-lookup"><span data-stu-id="2f057-153">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="2f057-154">Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="2f057-154">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2f057-155">При запуске исполняемого файла .NET с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать с его stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="2f057-155">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="2f057-156">Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="2f057-156">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="2f057-157">Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.</span><span class="sxs-lookup"><span data-stu-id="2f057-157">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="2f057-158">Если необходимо использовать stdin/stdout, можно применить параметр `--diagnostic-port`.</span><span class="sxs-lookup"><span data-stu-id="2f057-158">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="2f057-159">Дополнительные сведения см. в разделе [Использование порта диагностики](#using-diagnostic-port).</span><span class="sxs-lookup"><span data-stu-id="2f057-159">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="2f057-160">Примеры</span><span class="sxs-lookup"><span data-stu-id="2f057-160">Examples</span></span>

- <span data-ttu-id="2f057-161">Сбор всех счетчиков с интервалом обновления в 3 секунды и создание CSV-файла в качестве выходных данных:</span><span class="sxs-lookup"><span data-stu-id="2f057-161">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="2f057-162">Запустите `dotnet mvc.dll` как дочерний процесс и начните сбор счетчиков времени выполнения и счетчиков размещения ASP.NET Core из запуска и сохраните их в виде выходных данных JSON:</span><span class="sxs-lookup"><span data-stu-id="2f057-162">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="2f057-163">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="2f057-163">dotnet-counters list</span></span>

<span data-ttu-id="2f057-164">Отображение списка имен и описаний счетчиков, сгруппированных по поставщикам.</span><span class="sxs-lookup"><span data-stu-id="2f057-164">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2f057-165">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="2f057-165">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="2f057-166">Пример</span><span class="sxs-lookup"><span data-stu-id="2f057-166">Example</span></span>

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
> <span data-ttu-id="2f057-167">Счетчики `Microsoft.AspNetCore.Hosting` отображаются при обнаружении процессов, поддерживающих эти счетчики, например при запуске приложения ASP.NET Core на хост-компьютере.</span><span class="sxs-lookup"><span data-stu-id="2f057-167">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="2f057-168">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="2f057-168">dotnet-counters monitor</span></span>

<span data-ttu-id="2f057-169">Отображение периодически обновляемых значений для выбранных счетчиков.</span><span class="sxs-lookup"><span data-stu-id="2f057-169">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2f057-170">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="2f057-170">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="2f057-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="2f057-171">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="2f057-172">Идентификатор отслеживаемого процесса.</span><span class="sxs-lookup"><span data-stu-id="2f057-172">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="2f057-173">Имя отслеживаемого процесса.</span><span class="sxs-lookup"><span data-stu-id="2f057-173">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="2f057-174">Имя создаваемого порта диагностики.</span><span class="sxs-lookup"><span data-stu-id="2f057-174">The name of the diagnostic port to create.</span></span> <span data-ttu-id="2f057-175">Сведения об использовании этого параметра для запуска счетчиков мониторинга во время запуска приложения см. в разделе [Использование порта диагностики](#using-diagnostic-port).</span><span class="sxs-lookup"><span data-stu-id="2f057-175">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="2f057-176">Время (в секундах) между обновлением значений отображаемых счетчиков</span><span class="sxs-lookup"><span data-stu-id="2f057-176">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="2f057-177">Список счетчиков, разделенный запятыми.</span><span class="sxs-lookup"><span data-stu-id="2f057-177">A comma-separated list of counters.</span></span> <span data-ttu-id="2f057-178">Вы можете объявить счетчики как `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="2f057-178">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="2f057-179">Если `provider_name` используется без соответствующего списка счетчиков, отображаются все счетчики от поставщика.</span><span class="sxs-lookup"><span data-stu-id="2f057-179">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="2f057-180">Для обнаружения имен поставщиков и счетчиков используйте команду [dotnet-counters list](#dotnet-counters-list).</span><span class="sxs-lookup"><span data-stu-id="2f057-180">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="2f057-181">**`-- <command>` (только для целевых приложений, использующих .NET 5.0 или более поздней версии)**</span><span class="sxs-lookup"><span data-stu-id="2f057-181">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="2f057-182">После параметров конфигурации коллекции пользователь может добавить `--`, а затем команду для запуска приложения .NET с помощью среды выполнения версии не ниже 5.0.</span><span class="sxs-lookup"><span data-stu-id="2f057-182">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="2f057-183">`dotnet-counters` запустит процесс с указанной командой и будет отслеживать запрошенные метрики.</span><span class="sxs-lookup"><span data-stu-id="2f057-183">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="2f057-184">Это часто бывает полезно для сбора метрик для пути запуска приложения и может использоваться для диагностики и отслеживания проблем, происходящих незадолго до основной точки входа или вскоре после нее.</span><span class="sxs-lookup"><span data-stu-id="2f057-184">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2f057-185">При использовании этого параметра выполняется мониторинг первого процесса .NET 5.0, который передает результаты обратно в средство. Это означает, что если команда запускает несколько приложений .NET, данные будут собираться только о первом приложении.</span><span class="sxs-lookup"><span data-stu-id="2f057-185">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="2f057-186">Поэтому рекомендуется использовать этот параметр для автономных приложений или с помощью параметра `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="2f057-186">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2f057-187">При запуске исполняемого файла .NET с помощью dotnet-trace выполняется перенаправление входных и выходных данных, и вы не сможете взаимодействовать с его stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="2f057-187">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="2f057-188">Выход из средства с помощью клавиш CTRL+C или SIGTERM приведет к безопасному завершению работы средства и дочернего процесса.</span><span class="sxs-lookup"><span data-stu-id="2f057-188">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="2f057-189">Если дочерний процесс завершает работу до средства, средство также завершит работу, а трассировка будет доступна для безопасного просмотра.</span><span class="sxs-lookup"><span data-stu-id="2f057-189">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="2f057-190">Если необходимо использовать stdin/stdout, можно применить параметр `--diagnostic-port`.</span><span class="sxs-lookup"><span data-stu-id="2f057-190">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="2f057-191">Дополнительные сведения см. в разделе [Использование порта диагностики](#using-diagnostic-port).</span><span class="sxs-lookup"><span data-stu-id="2f057-191">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="2f057-192">Примеры</span><span class="sxs-lookup"><span data-stu-id="2f057-192">Examples</span></span>

- <span data-ttu-id="2f057-193">Мониторинг всех счетчиков из `System.Runtime` с интервалом обновления 3 секунды:</span><span class="sxs-lookup"><span data-stu-id="2f057-193">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="2f057-194">Мониторинг только счетчиков использования ЦП и размера кучи GC из `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="2f057-194">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="2f057-195">Мониторинг значений `EventCounter` из определяемых пользователем `EventSource`:</span><span class="sxs-lookup"><span data-stu-id="2f057-195">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="2f057-196">Дополнительные сведения см. в статье [Руководство. Измерение производительности с помощью EventCounters в .NET Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="2f057-196">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="2f057-197">Просмотр всех известных счетчиков, доступных в `dotnet-counters`:</span><span class="sxs-lookup"><span data-stu-id="2f057-197">View all well-known counters that are available in `dotnet-counters`:</span></span>

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

- <span data-ttu-id="2f057-198">Просмотр всех известных счетчиков, доступных в `dotnet-counters` для приложений .NET 5:</span><span class="sxs-lookup"><span data-stu-id="2f057-198">View all well-known counters that are available in `dotnet-counters` for .NET 5 apps:</span></span>

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

- <span data-ttu-id="2f057-199">Запустите `my-aspnet-server.exe` и отслеживайте число сборок, загруженных при запуске (только для .NET 5.0 или более поздних версий):</span><span class="sxs-lookup"><span data-stu-id="2f057-199">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="2f057-200">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2f057-200">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="2f057-201">Запустите `my-aspnet-server.exe` с `arg1` и `arg2` в качестве аргументов командной строки и отслеживайте рабочий набор и размер кучи сборки мусора при запуске (только для .NET 5.0 или более поздней версии):</span><span class="sxs-lookup"><span data-stu-id="2f057-201">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="2f057-202">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2f057-202">This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="2f057-203">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="2f057-203">dotnet-counters ps</span></span>

<span data-ttu-id="2f057-204">Отображение списка процессов dotnet, которые можно отслеживать.</span><span class="sxs-lookup"><span data-stu-id="2f057-204">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2f057-205">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="2f057-205">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="2f057-206">Пример</span><span class="sxs-lookup"><span data-stu-id="2f057-206">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="2f057-207">Использование порта диагностики</span><span class="sxs-lookup"><span data-stu-id="2f057-207">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="2f057-208">Это работает только для приложений, использующих .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2f057-208">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="2f057-209">Порт диагностики — это новый компонент среды выполнения, который появился в .NET 5. Он позволяет запускать мониторинг или сбор данных счетчиков во время запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="2f057-209">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="2f057-210">Чтобы сделать это с помощью `dotnet-counters`, можно использовать либо `dotnet-counters <collect|monitor> -- <command>`, как показано в приведенных выше примерах, либо параметр `--diagnostic-port`.</span><span class="sxs-lookup"><span data-stu-id="2f057-210">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="2f057-211">Использование `dotnet-counters <collect|monitor> -- <command>` для запуска приложения в качестве дочернего процесса — самый простой способ быстрого отслеживания приложения с момента запуска.</span><span class="sxs-lookup"><span data-stu-id="2f057-211">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="2f057-212">Однако если требуется более точное управление временем отслеживания приложения (например, отслеживать приложение только в течение первых 10 минут, а затем продолжать выполнение), или если необходимо взаимодействовать с приложением их интерфейса командной строки, используйте параметр `--diagnostic-port`, который позволяет управлять как отслеживаемым целевым приложением, так и `dotnet-counters`.</span><span class="sxs-lookup"><span data-stu-id="2f057-212">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="2f057-213">Следующая команда заставляет dotnet-counters создать сокет диагностики с именем `myport.sock` и ожидать соединения.</span><span class="sxs-lookup"><span data-stu-id="2f057-213">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="2f057-214">Выходные данные:</span><span class="sxs-lookup"><span data-stu-id="2f057-214">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="2f057-215">В отдельной консоли запустите целевое приложение с переменной среды `DOTNET_DiagnosticPorts`, для которой задано значение в выходных данных `dotnet-counters`.</span><span class="sxs-lookup"><span data-stu-id="2f057-215">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="2f057-216">Это должно позволить `dotnet-counters` запустить сбор данных счетчиков в `my-dotnet-app`:</span><span class="sxs-lookup"><span data-stu-id="2f057-216">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="2f057-217">Запуск приложения с помощью `dotnet run` может привести к проблемам: интерфейс командной строки dotnet может порождать множество дочерних процессов, которые не являются вашим приложением, и они могут подключаться к `dotnet-counters` до приложения, в результате чего ваше приложение будет приостановлено во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2f057-217">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="2f057-218">Рекомендуется использовать автономную версию приложения или запускать его с помощью `dotnet exec`.</span><span class="sxs-lookup"><span data-stu-id="2f057-218">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
