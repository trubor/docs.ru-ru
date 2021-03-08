---
title: Отладка высокой загрузки ЦП в .NET Core
description: Руководство по отладке высокой загрузки ЦП в .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 3ba07f0bb40f8128c091fa427b957d824c07bcd5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105366"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="2ee51-103">Отладка высокой загрузки ЦП в .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee51-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="2ee51-104">**Эта статья относится к: ✔️** пакету SDK для .NET Core 3.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="2ee51-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="2ee51-105">В этом руководстве описано, как выполнить отладку в случае чрезмерной загрузки ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="2ee51-106">Используя предоставленный пример [веб-приложения ASP.NET Core](/samples/dotnet/samples/diagnostic-scenarios) в репозитории исходного кода, можно намеренно вызвать взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="2ee51-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="2ee51-107">Конечная точка перестанет отвечать на запросы, и в ней будут накапливаться потоки.</span><span class="sxs-lookup"><span data-stu-id="2ee51-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="2ee51-108">Вы узнаете, как использовать различные средства для диагностики проблемы в этом сценарии на основе ряда ключевых диагностических данных.</span><span class="sxs-lookup"><span data-stu-id="2ee51-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="2ee51-109">В этом руководстве рассмотрены следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="2ee51-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2ee51-110">Выяснение причины высокой загрузки ЦП</span><span class="sxs-lookup"><span data-stu-id="2ee51-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="2ee51-111">Определение загрузки ЦП с помощью [dotnet-counters](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="2ee51-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="2ee51-112">Использование [dotnet-trace](dotnet-trace.md) для создания трассировки</span><span class="sxs-lookup"><span data-stu-id="2ee51-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="2ee51-113">Профилирование производительности в PerfView</span><span class="sxs-lookup"><span data-stu-id="2ee51-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="2ee51-114">Диагностика и устранение причины чрезмерной загрузки ЦП</span><span class="sxs-lookup"><span data-stu-id="2ee51-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ee51-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="2ee51-115">Prerequisites</span></span>

<span data-ttu-id="2ee51-116">В этом учебнике используется:</span><span class="sxs-lookup"><span data-stu-id="2ee51-116">The tutorial uses:</span></span>

- <span data-ttu-id="2ee51-117">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="2ee51-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="2ee51-118">[Пример целевого объекта отладки ](/samples/dotnet/samples/diagnostic-scenarios) для активации сценария.</span><span class="sxs-lookup"><span data-stu-id="2ee51-118">[Sample debug target](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="2ee51-119">[dotnet-trace](dotnet-trace.md) для вывода списка процессов и создания профиля.</span><span class="sxs-lookup"><span data-stu-id="2ee51-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="2ee51-120">[dotnet-counters](dotnet-counters.md) для мониторинга загрузки ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="2ee51-121">Счетчики ЦПУ</span><span class="sxs-lookup"><span data-stu-id="2ee51-121">CPU counters</span></span>

<span data-ttu-id="2ee51-122">Прежде чем начать сбор диагностических данных, необходимо воспроизвести условие высокой загрузки ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="2ee51-123">Запустите [пример приложения](/samples/dotnet/samples/diagnostic-scenarios) из корневого каталога примера с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="2ee51-123">Run the [sample application](/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="2ee51-124">Чтобы узнать ИД процесса, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="2ee51-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="2ee51-125">Запишите ИД процесса, отображаемый в выходных данных команды.</span><span class="sxs-lookup"><span data-stu-id="2ee51-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="2ee51-126">Наш ИД процесса — `22884`, но ваш будет другим.</span><span class="sxs-lookup"><span data-stu-id="2ee51-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="2ee51-127">Чтобы проверить текущую загрузку ЦП, выполните команду [dotnet-counters](dotnet-counters.md):</span><span class="sxs-lookup"><span data-stu-id="2ee51-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="2ee51-128">`refresh-interval` — это время в секундах между опросами счетчиком значений ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="2ee51-129">Результат выполнения должен быть аналогичен следующему:</span><span class="sxs-lookup"><span data-stu-id="2ee51-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="2ee51-130">Сразу же после запуска веб-приложения ЦП совсем не используется и его загрузка отображается как равная `0%`.</span><span class="sxs-lookup"><span data-stu-id="2ee51-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="2ee51-131">Перейдите по маршруту `api/diagscenario/highcpu`, используя `60000` в качестве параметра маршрута:</span><span class="sxs-lookup"><span data-stu-id="2ee51-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

`https://localhost:5001/api/diagscenario/highcpu/60000`

<span data-ttu-id="2ee51-132">Теперь выполните команду [dotnet-counters](dotnet-counters.md) повторно.</span><span class="sxs-lookup"><span data-stu-id="2ee51-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="2ee51-133">Чтобы отслеживать только `cpu-usage`, укажите `System.Runtime[cpu-usage]` как часть команды.</span><span class="sxs-lookup"><span data-stu-id="2ee51-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor --counters System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="2ee51-134">Вы увидите увеличение загрузки ЦП, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2ee51-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="2ee51-135">В течение всего запроса загрузка ЦП будет колебаться на уровне 25 %.</span><span class="sxs-lookup"><span data-stu-id="2ee51-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="2ee51-136">В зависимости от настройки главного компьютера следует ожидать изменения загрузки ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="2ee51-137">Чтобы визуализировать еще более высокий уровень загрузки ЦП, можно запустить эту конечную точку на нескольких вкладках браузера одновременно.</span><span class="sxs-lookup"><span data-stu-id="2ee51-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="2ee51-138">На этом этапе можно с уверенностью сказать, что ЦП работает с большей загрузкой, чем ожидается.</span><span class="sxs-lookup"><span data-stu-id="2ee51-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="2ee51-139">Создание трассировки</span><span class="sxs-lookup"><span data-stu-id="2ee51-139">Trace generation</span></span>

<span data-ttu-id="2ee51-140">При анализе медленного запроса требуется средство диагностики, которое позволяет получить представление о том, что делает код.</span><span class="sxs-lookup"><span data-stu-id="2ee51-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="2ee51-141">Стандартным инструментом является профилировщик, и вы можете выбрать различные параметры профилировщика.</span><span class="sxs-lookup"><span data-stu-id="2ee51-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="2ee51-142">Linux</span><span class="sxs-lookup"><span data-stu-id="2ee51-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="2ee51-143">Средство `perf` можно использовать для создания профилей приложений .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee51-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="2ee51-144">Выйдите из предыдущего [примера целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios).</span><span class="sxs-lookup"><span data-stu-id="2ee51-144">Exit the previous instance of the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="2ee51-145">Задайте переменную среды `COMPlus_PerfMapEnabled`, чтобы приложение .NET Core создало файл `map` в каталоге `/tmp`.</span><span class="sxs-lookup"><span data-stu-id="2ee51-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="2ee51-146">`perf` использует этот файл `map` для сопоставления адреса ЦП с функциями, созданными JIT-компилятором, по имени.</span><span class="sxs-lookup"><span data-stu-id="2ee51-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="2ee51-147">Дополнительные сведения см. в разделе [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map) (Запись карты производительности).</span><span class="sxs-lookup"><span data-stu-id="2ee51-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="2ee51-148">Запустите [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios) в том же сеансе терминала.</span><span class="sxs-lookup"><span data-stu-id="2ee51-148">Run the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="2ee51-149">Повторно запустите конечную точку API (`https://localhost:5001/api/diagscenario/highcpu/60000`) с высокой загрузкой ЦП.</span><span class="sxs-lookup"><span data-stu-id="2ee51-149">Exercise the high CPU API endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="2ee51-150">Пока она выполняется в рамках 1-минутного запроса, запустите команду `perf` с ИД процесса:</span><span class="sxs-lookup"><span data-stu-id="2ee51-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="2ee51-151">Команда `perf` активирует процесс сбора данных производительности.</span><span class="sxs-lookup"><span data-stu-id="2ee51-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="2ee51-152">Пусть она выполняется в течение примерно 20–30 секунд. Затем нажмите сочетание клавиш <kbd>CTRL+C</kbd>, чтобы выйти из процесса сбора.</span><span class="sxs-lookup"><span data-stu-id="2ee51-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="2ee51-153">Для просмотра выходных данных трассировки можно использовать ту же команду `perf`.</span><span class="sxs-lookup"><span data-stu-id="2ee51-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="2ee51-154">Вы также можете создать _flame-graph_ с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="2ee51-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="2ee51-155">Эта команда создает файл `flamegraph.svg`, который можно просмотреть в браузере для изучения проблемы с производительностью.</span><span class="sxs-lookup"><span data-stu-id="2ee51-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="2ee51-156">[![Изображение SVG-файла графа пламени](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="2ee51-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="2ee51-157">Windows</span><span class="sxs-lookup"><span data-stu-id="2ee51-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="2ee51-158">В Windows в качестве профилировщика можно использовать средство [dotnet-trace](dotnet-trace.md).</span><span class="sxs-lookup"><span data-stu-id="2ee51-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="2ee51-159">Используя предыдущий [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios), снова запустите конечную точку с высокой загрузкой ЦП (`https://localhost:5001/api/diagscenario/highcpu/60000`).</span><span class="sxs-lookup"><span data-stu-id="2ee51-159">Using the previous [sample debug target](/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU endpoint (`https://localhost:5001/api/diagscenario/highcpu/60000`) again.</span></span> <span data-ttu-id="2ee51-160">Пока она выполняется в рамках 1-минутного запроса, запустите команду `collect`, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2ee51-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="2ee51-161">Пусть средство [dotnet-trace](dotnet-trace.md) выполняется в течение примерно 20–30 секунд. Затем нажмите клавишу <kbd>ВВОД</kbd>, чтобы выйти из процесса сбора.</span><span class="sxs-lookup"><span data-stu-id="2ee51-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="2ee51-162">В результате в той же папке будет создан файл `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="2ee51-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="2ee51-163">Файлы `nettrace` являются отличным способом использования существующих средств анализа в Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee51-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="2ee51-164">Откройте файл `nettrace` с помощью средства [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md), как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="2ee51-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="2ee51-165">[![Изображение средства PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="2ee51-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="2ee51-166">См. также</span><span class="sxs-lookup"><span data-stu-id="2ee51-166">See also</span></span>

- <span data-ttu-id="2ee51-167">[dotnet-trace](dotnet-trace.md) для отображения списка процессов</span><span class="sxs-lookup"><span data-stu-id="2ee51-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="2ee51-168">[dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти</span><span class="sxs-lookup"><span data-stu-id="2ee51-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="2ee51-169">[dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа</span><span class="sxs-lookup"><span data-stu-id="2ee51-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="2ee51-170">dotnet/diagnostics</span><span class="sxs-lookup"><span data-stu-id="2ee51-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="2ee51-171">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="2ee51-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ee51-172">Отладка взаимоблокировки в .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee51-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
