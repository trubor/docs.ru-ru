---
title: Трассировка приложений .NET с помощью PerfCollect.
description: Руководство по сбору трассировки с помощью PerfCollect в .NET.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: d6ee77fea5c419e00e684e8b1472278f752544b0
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874190"
---
# <a name="trace-net-applications-with-perfcollect"></a><span data-ttu-id="5f05e-103">Трассировка приложений .NET с помощью PerfCollect</span><span class="sxs-lookup"><span data-stu-id="5f05e-103">Trace .NET applications with PerfCollect</span></span>

<span data-ttu-id="5f05e-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="5f05e-104">**This article applies to: ✔️** .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="5f05e-105">При возникновении проблем с производительностью в Linux сбор данных трассировки с `perfcollect` можно использовать для получения подробных сведений о том, что произошло на компьютере, когда возникла проблема с производительностью.</span><span class="sxs-lookup"><span data-stu-id="5f05e-105">When performance problems are encountered on Linux, collecting a trace with `perfcollect` can be used to gather detailed information about what was happening on the machine at the time of the performance problem.</span></span>

<span data-ttu-id="5f05e-106">`perfcollect` — это скрипт Bash, использующий [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) для сбора событий, записываемых из среды выполнения, или [EventSource](xref:System.Diagnostics.Tracing.EventListener), а также [perf](https://perf.wiki.kernel.org/) для сбора образцов ЦП целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="5f05e-106">`perfcollect` is a bash script that leverages [Linux Tracing Tookit-Next Generation (LTTng)](https://lttng.org) to collect events written from the runtime or any [EventSource](xref:System.Diagnostics.Tracing.EventListener), as well as [perf](https://perf.wiki.kernel.org/) to collect CPU samples of the target process.</span></span>

## <a name="prepare-your-machine"></a><span data-ttu-id="5f05e-107">Подготовка компьютера</span><span class="sxs-lookup"><span data-stu-id="5f05e-107">Prepare your machine</span></span>

<span data-ttu-id="5f05e-108">Выполните следующие действия, чтобы подготовить компьютер к собранию трассировки производительности с `perfcollect`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-108">Follow these steps to prepare your machine to collect a performance trace with `perfcollect`.</span></span>

> [!NOTE]
> <span data-ttu-id="5f05e-109">В среде контейнера у контейнера должно быть разрешение `SYS_ADMIN`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-109">If you are in a container environment, your container needs to have `SYS_ADMIN` capability.</span></span> <span data-ttu-id="5f05e-110">Дополнительные сведения о трассировке приложений в контейнерах с помощью PerfCollect см. в разделе [Сбор диагностики в контейнерах](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="5f05e-110">For more information on tracing applications inside containers using PerfCollect, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

1. <span data-ttu-id="5f05e-111">Загрузите `perfcollect`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-111">Download `perfcollect`.</span></span>

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. <span data-ttu-id="5f05e-112">Сделайте файл скрипта исполняемым.</span><span class="sxs-lookup"><span data-stu-id="5f05e-112">Make the script executable.</span></span>

    > ```bash
    > chmod +x perfcollect
    > ```

3. <span data-ttu-id="5f05e-113">Установите необходимые компоненты для трассировки — фактические библиотеки трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-113">Install tracing prerequisites - these are the actual tracing libraries.</span></span>

    > ```bash
    > sudo ./perfcollect install
    > ```

    <span data-ttu-id="5f05e-114">На компьютере будут установлены следующие необходимые компоненты:</span><span class="sxs-lookup"><span data-stu-id="5f05e-114">This will install the following prerequisites on your machine:</span></span>

    1. <span data-ttu-id="5f05e-115">`perf`: подсистема событий производительности Linux и сопутствующее приложение для сбора и просмотра в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="5f05e-115">`perf`: the Linux Performance Events subsystem and companion user-mode collection/viewer application.</span></span> <span data-ttu-id="5f05e-116">`perf` является частью источника ядра Linux, но обычно не устанавливается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5f05e-116">`perf` is part of the Linux kernel source, but is not usually installed by default.</span></span>

    2. <span data-ttu-id="5f05e-117">`LTTng`: используется для записи данных событий, возникших во время выполнения CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f05e-117">`LTTng`: Used to capture event data emitted at runtime by CoreCLR.</span></span> <span data-ttu-id="5f05e-118">Эти данные затем используются для анализа поведения различных компонентов среды выполнения, таких как GC, JIT и пул потоков.</span><span class="sxs-lookup"><span data-stu-id="5f05e-118">This data is then used to analyze the behavior of various runtime components such as the GC, JIT, and thread pool.</span></span>

<span data-ttu-id="5f05e-119">Последние версии .NET Core и средство производительности Linux поддерживают автоматическое разрешение имен методов для кода платформы.</span><span class="sxs-lookup"><span data-stu-id="5f05e-119">Recent versions of .NET Core and the Linux perf tool support automatic resolution of method names for framework code.</span></span> <span data-ttu-id="5f05e-120">Если вы работаете с .NET Core версии 3.1 или более ранней, потребуется дополнительный шаг.</span><span class="sxs-lookup"><span data-stu-id="5f05e-120">If you are working with .NET Core version 3.1 or less, an extra step is necessary.</span></span> <span data-ttu-id="5f05e-121">Дополнительные сведения см. в разделе [Разрешение символов платформы](#resolve-framework-symbols).</span><span class="sxs-lookup"><span data-stu-id="5f05e-121">See [Resolving Framework Symbols](#resolve-framework-symbols) for details.</span></span>

<span data-ttu-id="5f05e-122">Для разрешения имен методов в собственных библиотеках DLL времени выполнения (например, libcoreclr.so) `perfcollect` будет разрешать символы при преобразовании данных, но только в том случае, если символы для этих двоичных файлов существуют.</span><span class="sxs-lookup"><span data-stu-id="5f05e-122">For resolving method names of native runtime DLLs (such as libcoreclr.so), `perfcollect` will resolve symbols for them when it converts the data, but only if the symbols for these binaries are present.</span></span> <span data-ttu-id="5f05e-123">Дополнительные сведения см. в разделе [Получение символов для собственной среды выполнения](#get-symbols-for-the-native-runtime).</span><span class="sxs-lookup"><span data-stu-id="5f05e-123">See [Getting Symbols for the Native Runtime](#get-symbols-for-the-native-runtime) section for details.</span></span>

## <a name="collect-a-trace"></a><span data-ttu-id="5f05e-124">Сбор трассировки</span><span class="sxs-lookup"><span data-stu-id="5f05e-124">Collect a trace</span></span>

1. <span data-ttu-id="5f05e-125">Понадобится две оболочки: одна для управления трассировкой, или **[Trace]** , и одна для запуска приложения, или **[App]** .</span><span class="sxs-lookup"><span data-stu-id="5f05e-125">Have two shells available - one for controlling tracing, referred to as **[Trace]**, and one for running the application, referred to as **[App]**.</span></span>

2. <span data-ttu-id="5f05e-126">**[Trace]** Запустите сбор.</span><span class="sxs-lookup"><span data-stu-id="5f05e-126">**[Trace]** Start collection.</span></span>

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    <span data-ttu-id="5f05e-127">Ожидаемые выходные данные:</span><span class="sxs-lookup"><span data-stu-id="5f05e-127">Expected Output:</span></span>

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. <span data-ttu-id="5f05e-128">**[App]** Настройте оболочку приложения со следующими переменными среды — это позволяет отслеживать конфигурацию CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f05e-128">**[App]** Set up the application shell with the following environment variables - this enables tracing configuration of CoreCLR.</span></span>

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. <span data-ttu-id="5f05e-129">**[App]** Запустите приложение. Пусть оно выполняется до тех пор, пока вы не соберете данные о проблеме с производительностью.</span><span class="sxs-lookup"><span data-stu-id="5f05e-129">**[App]** Run the app - let it run as long as you need to in order to capture the performance problem.</span></span> <span data-ttu-id="5f05e-130">Приложение должно выполняться столько, сколько это необходимо для захвата периода, когда возникла соответствующая проблема с производительностью.</span><span class="sxs-lookup"><span data-stu-id="5f05e-130">The exact length can be as short as you need as long as it sufficiently captures the window of time where the performance problem you want to investigate occurs.</span></span>

    > ```bash
    > dotnet run
    > ```

5. <span data-ttu-id="5f05e-131">**[Trace]** Прекратите сбор, нажав клавиши CTRL+C.</span><span class="sxs-lookup"><span data-stu-id="5f05e-131">**[Trace]** Stop collection - hit CTRL+C.</span></span>

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    <span data-ttu-id="5f05e-132">Сжатый файл трассировки теперь хранится в текущем рабочем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5f05e-132">The compressed trace file is now stored in the current working directory.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="5f05e-133">Просмотр трассировки</span><span class="sxs-lookup"><span data-stu-id="5f05e-133">View a trace</span></span>

<span data-ttu-id="5f05e-134">Существует несколько вариантов просмотра собранных данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-134">There are a number of options for viewing the trace that was collected.</span></span> <span data-ttu-id="5f05e-135">Удобнее всего просматривать трассировки с помощью [PerfView](https://aka.ms/perfview) в Windows, но их можно просматривать непосредственно в Linux с помощью `PerfCollect` или `TraceCompass`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-135">Traces are best viewed using [PerfView](https://aka.ms/perfview) on Windows, but they can be viewed directly on Linux using `PerfCollect` itself or `TraceCompass`.</span></span>

### <a name="use-perfcollect-to-view-the-trace-file"></a><span data-ttu-id="5f05e-136">Использование PerfCollect для просмотра файла трассировки</span><span class="sxs-lookup"><span data-stu-id="5f05e-136">Use PerfCollect to view the trace file</span></span>

<span data-ttu-id="5f05e-137">Для просмотра собранной трассировки можно использовать PerfCollect.</span><span class="sxs-lookup"><span data-stu-id="5f05e-137">You can use perfcollect itself to view the trace that you collected.</span></span> <span data-ttu-id="5f05e-138">Для этого воспользуйтесь следующей командой:</span><span class="sxs-lookup"><span data-stu-id="5f05e-138">To do this, use the following command:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip
```

<span data-ttu-id="5f05e-139">По умолчанию при этом отображается трассировка ЦП приложения с помощью `perf`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-139">By default, this will show the CPU trace of the application using `perf`.</span></span>

<span data-ttu-id="5f05e-140">Чтобы изучить события, собранные с помощью `LTTng`, можно передать флаг `-viewer lttng` и просмотреть отдельные события:</span><span class="sxs-lookup"><span data-stu-id="5f05e-140">To look at the events that were collected via `LTTng`, you can pass in the flag `-viewer lttng` to see the individual events:</span></span>

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

<span data-ttu-id="5f05e-141">Для вывода полезных данных событий будет использоваться средство просмотра `babeltrace`:</span><span class="sxs-lookup"><span data-stu-id="5f05e-141">This will use `babeltrace` viewer to print the events payload:</span></span>

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a><span data-ttu-id="5f05e-142">Открытие файла трассировки с помощью PerfView</span><span class="sxs-lookup"><span data-stu-id="5f05e-142">Use PerfView to open the trace file</span></span>

<span data-ttu-id="5f05e-143">Чтобы просмотреть общее представление примера ЦП и событий, можно использовать `PerfView` на компьютере Windows.</span><span class="sxs-lookup"><span data-stu-id="5f05e-143">To see an aggregate view of both the CPU sample and the events, you can use `PerfView` on a Windows machine.</span></span>

1. <span data-ttu-id="5f05e-144">Скопируйте файл trace.zip из Linux на компьютер Windows.</span><span class="sxs-lookup"><span data-stu-id="5f05e-144">Copy the trace.zip file from Linux to a Windows machine.</span></span>

2. <span data-ttu-id="5f05e-145">Скачайте PerfView с <https://aka.ms/perfview>.</span><span class="sxs-lookup"><span data-stu-id="5f05e-145">Download PerfView from <https://aka.ms/perfview>.</span></span>

3. <span data-ttu-id="5f05e-146">Запуск PerfView.exe</span><span class="sxs-lookup"><span data-stu-id="5f05e-146">Run PerfView.exe</span></span>

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

<span data-ttu-id="5f05e-147">PerfView будет отображать список поддерживаемых представлений в зависимости от данных, содержащихся в файле трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-147">PerfView will display the list of views that are supported based on the data contained in the trace file.</span></span>

- <span data-ttu-id="5f05e-148">Для изучения ресурсов ЦП выберите **CPU stacks**.</span><span class="sxs-lookup"><span data-stu-id="5f05e-148">For CPU investigations, choose **CPU stacks**.</span></span>

- <span data-ttu-id="5f05e-149">Для получения подробных сведений о сборке мусора выберите **GCStats**.</span><span class="sxs-lookup"><span data-stu-id="5f05e-149">For detailed GC information, choose **GCStats**.</span></span>

- <span data-ttu-id="5f05e-150">Чтобы получить сведения о JIT для каждого процесса, модуля или метода, выберите **JITStats**.</span><span class="sxs-lookup"><span data-stu-id="5f05e-150">For per-process/module/method JIT information, choose **JITStats**.</span></span>

- <span data-ttu-id="5f05e-151">Если представления для необходимой информации нет, можно попробовать найти события в представлении необработанных событий.</span><span class="sxs-lookup"><span data-stu-id="5f05e-151">If there is not a view for the information you need, you can try looking for the events in the raw events view.</span></span>  <span data-ttu-id="5f05e-152">Выберите **События**.</span><span class="sxs-lookup"><span data-stu-id="5f05e-152">Choose **Events**.</span></span>

<span data-ttu-id="5f05e-153">Дополнительные сведения о том, как интерпретировать представления в PerfView, нажмите на ссылку справки в самом представлении или в главном окне PerfView выберите **Справка-> Руководство пользователя**.</span><span class="sxs-lookup"><span data-stu-id="5f05e-153">For more information on how to interpret views in PerfView, see help links in the view itself, or from the main window in PerfView, choose **Help->Users Guide**.</span></span>

> [!NOTE]
> <span data-ttu-id="5f05e-154">События, записанные через API <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> (включая события из Framework), не будут включать данные об имени поставщика.</span><span class="sxs-lookup"><span data-stu-id="5f05e-154">Events written via <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> API (including the events from Framework) won't show up under their provider name.</span></span> <span data-ttu-id="5f05e-155">Они записываются как события `EventSourceEvent` от поставщика `Microsoft-Windows-DotNETRuntime`, а для их полезных данных выполняется сериализация в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="5f05e-155">Instead, they are written as `EventSourceEvent` events under `Microsoft-Windows-DotNETRuntime` provider and their payloads are JSON serialized.</span></span>

### <a name="use-tracecompass-to-open-the-trace-file"></a><span data-ttu-id="5f05e-156">Открытие файла трассировки с помощью TraceCompass</span><span class="sxs-lookup"><span data-stu-id="5f05e-156">Use TraceCompass to open the trace file</span></span>

<span data-ttu-id="5f05e-157">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) — это еще один вариант, который можно использовать для просмотра трассировок.</span><span class="sxs-lookup"><span data-stu-id="5f05e-157">[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) is another option you can use to view the traces.</span></span> <span data-ttu-id="5f05e-158">`TraceCompass` работает на компьютерах Linux, поэтому вам не нужно перемещать трассировку на компьютер Windows.</span><span class="sxs-lookup"><span data-stu-id="5f05e-158">`TraceCompass` works on Linux machines as well, so you don't need to move your trace over to a Windows machine.</span></span> <span data-ttu-id="5f05e-159">Чтобы открыть файл трассировки с помощью `TraceCompass`, необходимо распаковать его.</span><span class="sxs-lookup"><span data-stu-id="5f05e-159">To use `TraceCompass` to open your trace file, you will need to unzip the file.</span></span>

```bash
unzip myTrace.trace.zip
```

<span data-ttu-id="5f05e-160">`perfcollect` сохранит записанную трассировку LTTng в формате файла CTF в подкаталоге в `lttngTrace`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-160">`perfcollect` will save the LTTng trace it collected into a CTF file format in a subdirectory in the `lttngTrace`.</span></span> <span data-ttu-id="5f05e-161">В частности, файл CTF будет находиться в аналогичном каталоге: `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-161">Specifically, the CTF file will be located in a directory that looks like `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\`.</span></span>

<span data-ttu-id="5f05e-162">Вы можете открыть файл трассировки CTF в `TraceCompass`, выбрав `File -> Open Trace` и файл `metadata`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-162">You can open the CTF trace file in `TraceCompass` by selecting `File -> Open Trace` and select the `metadata` file.</span></span>

<span data-ttu-id="5f05e-163">Подробности см. в [документации по `TraceCompass`](https://www.eclipse.org/tracecompass/).</span><span class="sxs-lookup"><span data-stu-id="5f05e-163">For more details, please refer to [`TraceCompass` documentation](https://www.eclipse.org/tracecompass/).</span></span>

## <a name="resolve-framework-symbols"></a><span data-ttu-id="5f05e-164">Разрешение символов платформы</span><span class="sxs-lookup"><span data-stu-id="5f05e-164">Resolve framework symbols</span></span>

<span data-ttu-id="5f05e-165">Символы платформы должны создаваться вручную во время сбора трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-165">Framework symbols need to be manually generated at the time the trace is collected.</span></span> <span data-ttu-id="5f05e-166">Они отличаются от символов на уровне приложения, так как платформа предварительно компилируется во время JIT-компиляции кода приложения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-166">They are different than app-level symbols because the framework is pre-compiled while app code is just-in-time-compiled.</span></span> <span data-ttu-id="5f05e-167">Для кода платформы, предварительно скомпилированного в машинный код, необходимо вызвать `crossgen`, который знает, как создать сопоставление из машинного кода с именами методов.</span><span class="sxs-lookup"><span data-stu-id="5f05e-167">For framework code that was precompiled to native code, you need to call `crossgen` that knows how to generate the mapping from the native code to the name of the methods.</span></span>

<span data-ttu-id="5f05e-168">`perfcollect` может обработать большую часть сведений автоматически, но требуется `crossgen`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-168">`perfcollect` can handle most of the details for you, but it needs to have `crossgen` available.</span></span> <span data-ttu-id="5f05e-169">По умолчанию он не устанавливается вместе с дистрибутивом .NET.</span><span class="sxs-lookup"><span data-stu-id="5f05e-169">By default it is not installed with .NET distribution.</span></span> <span data-ttu-id="5f05e-170">Если `crossgen` отсутствует, `perfcollect` выдает предупреждение и ссылается на эти инструкции.</span><span class="sxs-lookup"><span data-stu-id="5f05e-170">If `crossgen` is not there, `perfcollect` warns you and refers you to these instructions.</span></span> <span data-ttu-id="5f05e-171">Чтобы устранить эту проблему, необходимо получить нужную версию crossgen для используемой среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-171">To fix things you need to fetch exactly the right version of crossgen for the runtime you are using.</span></span> <span data-ttu-id="5f05e-172">Если вы поместите инструмент crossgen в тот же каталог, что и библиотеки DLL среды выполнения .NET (например, libcoreclr.so), `perfcollect` может найти его и добавить символы платформы в файл трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-172">If you place the crossgen tool in the same directory as the .NET Runtime DLLs (for example, libcoreclr.so), then `perfcollect` can find it and add the framework symbols to the trace file for you.</span></span>

<span data-ttu-id="5f05e-173">Обычно при создании приложения .NET оно просто создает библиотеку DLL для написанного кода, используя общую копию среды выполнения для остального.</span><span class="sxs-lookup"><span data-stu-id="5f05e-173">Normally when you create a .NET application, it just generates the DLL for the code you wrote, using a shared copy of the runtime for the rest.</span></span>   <span data-ttu-id="5f05e-174">Однако вы также можете создать так называемую "автономную" версию приложения, которая содержит все библиотеки DLL среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-174">However you can also generate what is called a 'self-contained' version of an application and this contains all runtime DLLs.</span></span> <span data-ttu-id="5f05e-175">`crossgen` является частью пакета NuGet, который используется для создания автономных приложений, поэтому один из способов получить правильную версию `crossgen` — создать автономный пакет приложения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-175">`crossgen` is part of the NuGet package that is used to create self-contained apps, so one way of getting the right version of `crossgen` is to create a self-contained package of your application.</span></span>

<span data-ttu-id="5f05e-176">Пример:</span><span class="sxs-lookup"><span data-stu-id="5f05e-176">For example:</span></span>

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

<span data-ttu-id="5f05e-177">В результате будет создано новое приложение Hello World, собранное как автономное приложение.</span><span class="sxs-lookup"><span data-stu-id="5f05e-177">This creates a new Hello World application and builds it as a self-contained app.</span></span>

<span data-ttu-id="5f05e-178">В качестве побочного эффекта создания автономного приложения средство DotNet загрузит пакет NuGet с именем runtime.linux-x64.microsoft.netcore.app и поместит его в каталог ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, где VERSION — номер версии среды выполнения .NET Core (например, 2.1.0).</span><span class="sxs-lookup"><span data-stu-id="5f05e-178">As a side effect of creating the self-contained application the dotnet tool will download a NuGet package called runtime.linux-x64.microsoft.netcore.app and place it in the directory ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, where VERSION is the version number of your .NET Core runtime (for example, 2.1.0).</span></span> <span data-ttu-id="5f05e-179">Здесь находится каталог средств, в котором расположен нужный вам инструмент crossgen.</span><span class="sxs-lookup"><span data-stu-id="5f05e-179">Under that is a tools directory and inside there is the crossgen tool you need.</span></span> <span data-ttu-id="5f05e-180">Начиная с .NET Core 3.0 пакет расположен в папке ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span><span class="sxs-lookup"><span data-stu-id="5f05e-180">Starting with .NET Core 3.0, the package location is ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.</span></span>

<span data-ttu-id="5f05e-181">Средство `crossgen` необходимо разместить рядом со средой выполнения, которая фактически используется приложением.</span><span class="sxs-lookup"><span data-stu-id="5f05e-181">The `crossgen` tool needs to be put next to the runtime that is actually used by your application.</span></span> <span data-ttu-id="5f05e-182">Обычно приложение использует общую версию .NET Core, установленную в папке /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION, где VERSION — это номер версии среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="5f05e-182">Typically your app uses the shared version of .NET Core that is installed at /usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION where VERSION is the version number of the .NET Runtime.</span></span> <span data-ttu-id="5f05e-183">Это общее расположение, поэтому для его изменения необходимо иметь права суперпользователя.</span><span class="sxs-lookup"><span data-stu-id="5f05e-183">This is a shared location, so you need to be super-user to modify it.</span></span> <span data-ttu-id="5f05e-184">Если VERSION имеет значение 2.1.0, команды для обновления `crossgen` будут выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5f05e-184">If the VERSION is 2.1.0 the commands to update `crossgen` would be:</span></span>

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

<span data-ttu-id="5f05e-185">После этого `perfcollect` будет использовать crossgen для включения символов платформы.</span><span class="sxs-lookup"><span data-stu-id="5f05e-185">Once you have done this, `perfcollect` will use crossgen to include framework symbols.</span></span> <span data-ttu-id="5f05e-186">Предупреждение, которое раньше выдавалось `perfcollect`, исчезнет.</span><span class="sxs-lookup"><span data-stu-id="5f05e-186">The warning that `perfcollect` used to issue should go away.</span></span> <span data-ttu-id="5f05e-187">Это необходимо сделать только один раз для каждого компьютера (пока не будет обновлена среда выполнения).</span><span class="sxs-lookup"><span data-stu-id="5f05e-187">This only has to be one once per machine (until you update your runtime).</span></span>

### <a name="alternative-turn-off-use-of-precompiled-code"></a><span data-ttu-id="5f05e-188">Альтернатива: отключить использование предварительно скомпилированного кода</span><span class="sxs-lookup"><span data-stu-id="5f05e-188">Alternative: Turn off use of precompiled code</span></span>

<span data-ttu-id="5f05e-189">Если у вас нет возможности обновить среду выполнения .NET (для добавления `crossgen`) или если описанная выше процедура по какой-то причине не сработала, существует другой подход к получению символов платформы.</span><span class="sxs-lookup"><span data-stu-id="5f05e-189">If you don't have the ability to update the .NET Runtime (to add `crossgen`), or if the above procedure did not work for some reason, there is another approach to getting framework symbols.</span></span> <span data-ttu-id="5f05e-190">Укажите, что среда выполнения не должна использовать предварительно скомпилированный код платформы.</span><span class="sxs-lookup"><span data-stu-id="5f05e-190">You can tell the runtime to simply not use the precompiled framework code.</span></span> <span data-ttu-id="5f05e-191">Для кода будет использоваться JIT-компиляция, а `crossgen` не потребуется.</span><span class="sxs-lookup"><span data-stu-id="5f05e-191">The code will be Just-In-Time compiled and `crossgen` is not needed.</span></span>

> [!NOTE]
> <span data-ttu-id="5f05e-192">Этот подход может увеличить время запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-192">Choosing this approach may increase the startup time for your application.</span></span>

<span data-ttu-id="5f05e-193">Для этого можно добавить следующую переменную среды:</span><span class="sxs-lookup"><span data-stu-id="5f05e-193">To do this, you can add the following environment variable:</span></span>

```bash
export COMPlus_ZapDisable=1
```

<span data-ttu-id="5f05e-194">После этого изменения вы получите символы для всего кода .NET.</span><span class="sxs-lookup"><span data-stu-id="5f05e-194">With this change, you should get the symbols for all .NET code.</span></span>

## <a name="get-symbols-for-the-native-runtime"></a><span data-ttu-id="5f05e-195">Получение символов для собственной среды выполнения</span><span class="sxs-lookup"><span data-stu-id="5f05e-195">Get symbols for the native runtime</span></span>

<span data-ttu-id="5f05e-196">В большинстве случаев вы заинтересованы в своем коде, который `perfcollect` разрешает по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5f05e-196">Most of the time you are interested in your own code, which `perfcollect` resolves by default.</span></span> <span data-ttu-id="5f05e-197">Иногда бывает полезно понять, что происходит внутри библиотек DLL .NET (как указано в последнем разделе), но иногда интересно узнать, что происходит в библиотеках собственной среды выполнения (обычно это libcoreclr.so).</span><span class="sxs-lookup"><span data-stu-id="5f05e-197">Sometimes it is useful to see what is going on inside the .NET DLLs (which is what the last section was about), but sometimes what is going on in the native runtime dlls (typically libcoreclr.so), is interesting.</span></span>  <span data-ttu-id="5f05e-198">`perfcollect` будет разрешать символы при преобразовании данных, но только если символы для этих собственных библиотек DLL присутствуют (и находятся рядом с библиотекой, для которой они предназначены).</span><span class="sxs-lookup"><span data-stu-id="5f05e-198">`perfcollect` will resolve the symbols for these when it converts its data, but only if the symbols for these native DLLs are present (and are beside the library they are for).</span></span>

<span data-ttu-id="5f05e-199">Для этого существует глобальная команда [dotnet-symbol](https://github.com/dotnet/symstore/blob/main/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension).</span><span class="sxs-lookup"><span data-stu-id="5f05e-199">There is a global command called [dotnet-symbol](https://github.com/dotnet/symstore/blob/main/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) that does this.</span></span> <span data-ttu-id="5f05e-200">Чтобы использовать dotnet-symbol для получения собственных символов среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="5f05e-200">To use dotnet-symbol to get native runtime symbols:</span></span>

1. <span data-ttu-id="5f05e-201">Установите `dotnet-symbol`:</span><span class="sxs-lookup"><span data-stu-id="5f05e-201">Install `dotnet-symbol`:</span></span>

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. <span data-ttu-id="5f05e-202">Скачайте символы.</span><span class="sxs-lookup"><span data-stu-id="5f05e-202">Download the symbols.</span></span> <span data-ttu-id="5f05e-203">Если установлена версия среды выполнения .NET Core 2.1.0, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="5f05e-203">If your installed version of the .NET Core runtime is 2.1.0, the command to do this is:</span></span>

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. <span data-ttu-id="5f05e-204">Скопируйте символы в правильное место.</span><span class="sxs-lookup"><span data-stu-id="5f05e-204">Copy the symbols to the correct place.</span></span>

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    <span data-ttu-id="5f05e-205">Если это не удается сделать из-за отсутствия доступа на запись к соответствующему каталогу, можно использовать `perf buildid-cache` для добавления символов.</span><span class="sxs-lookup"><span data-stu-id="5f05e-205">If this cannot be done because you do not have write access to the appropriate directory, you can use `perf buildid-cache` to add the symbols.</span></span>

<span data-ttu-id="5f05e-206">После этого необходимо получить символьные имена для собственных библиотек DLL при запуске `perfcollect`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-206">After this, you should get symbolic names for the native dlls when you run `perfcollect`.</span></span>

## <a name="collect-in-a-docker-container"></a><span data-ttu-id="5f05e-207">Сборка в контейнере Docker</span><span class="sxs-lookup"><span data-stu-id="5f05e-207">Collect in a Docker container</span></span>

<span data-ttu-id="5f05e-208">Дополнительные сведения об использовании `perfcollect` в средах контейнеров см. в разделе [Сбор диагностики в контейнерах](./diagnostics-in-containers.md).</span><span class="sxs-lookup"><span data-stu-id="5f05e-208">For more information on how to use `perfcollect` in container environments, see [Collect diagnostics in containers](./diagnostics-in-containers.md).</span></span>

## <a name="learn-more-about-collection-options"></a><span data-ttu-id="5f05e-209">Подробнее о параметрах сбора</span><span class="sxs-lookup"><span data-stu-id="5f05e-209">Learn more about collection options</span></span>

<span data-ttu-id="5f05e-210">Можно указать следующие необязательные флаги с `perfcollect`, чтобы обеспечить более качественную диагностику.</span><span class="sxs-lookup"><span data-stu-id="5f05e-210">You can specify the following optional flags with `perfcollect` to better suit your diagnostic needs.</span></span>

### <a name="collect-for-a-specific-duration"></a><span data-ttu-id="5f05e-211">Сбор в течение определенного периода времени</span><span class="sxs-lookup"><span data-stu-id="5f05e-211">Collect for a specific duration</span></span>

<span data-ttu-id="5f05e-212">Если требуется получить трассировку за определенное время, можно использовать параметр `-collectsec`, после которого следует число, указывающее общее количество секунд для получения трассировки.</span><span class="sxs-lookup"><span data-stu-id="5f05e-212">When you want to collect a trace for a specific duration, you can use `-collectsec` option followed by a number specifying the total seconds to collect a trace for.</span></span>

### <a name="collect-threadtime-traces"></a><span data-ttu-id="5f05e-213">Получение трассировок времени потока</span><span class="sxs-lookup"><span data-stu-id="5f05e-213">Collect threadtime traces</span></span>

<span data-ttu-id="5f05e-214">Указав `-threadtime` с `perfcollect`, можно получить данные об использовании ЦП для каждого потока.</span><span class="sxs-lookup"><span data-stu-id="5f05e-214">Specifying `-threadtime` with `perfcollect` lets you collect per-thread CPU usage data.</span></span> <span data-ttu-id="5f05e-215">Это позволяет анализировать, на что каждый поток тратит время ЦП.</span><span class="sxs-lookup"><span data-stu-id="5f05e-215">This lets you analyze where every thread was spending its CPU time.</span></span>

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a><span data-ttu-id="5f05e-216">Сбор трассировок для управляемой памяти и производительности сборщика мусора</span><span class="sxs-lookup"><span data-stu-id="5f05e-216">Collect traces for managed memory and garbage collector performance</span></span>

<span data-ttu-id="5f05e-217">Следующие параметры позволяют специально собирать события сборки мусора из среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-217">The following options let you specifically collect the GC events from the runtime.</span></span>

* `perfcollect collect -gccollectonly`

<span data-ttu-id="5f05e-218">Сбор только минимального набора событий коллекции сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="5f05e-218">Collect only a minimal set of GC Collection events.</span></span> <span data-ttu-id="5f05e-219">Это наименее подробный профиль сбора коллекции сборки мусора с наименьшим влиянием на производительность целевого приложения.</span><span class="sxs-lookup"><span data-stu-id="5f05e-219">This is the least verbose GC eventing collection profile with the lowest impact on the target app's performance.</span></span> <span data-ttu-id="5f05e-220">Эта команда аналогична команде `PerfView.exe /GCCollectOnly collect` в PerfView.</span><span class="sxs-lookup"><span data-stu-id="5f05e-220">This command is analogous to `PerfView.exe /GCCollectOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gconly`

<span data-ttu-id="5f05e-221">Сбор более подробных событий коллекции сборки мусора с помощью JIT, загрузчика и событий исключений.</span><span class="sxs-lookup"><span data-stu-id="5f05e-221">Collect more verbose GC collection events with JIT, Loader, and Exception events.</span></span> <span data-ttu-id="5f05e-222">Запрос более подробных событий (таких как сведения о выделении памяти и сведения о присоединении к сборке мусора), который влияет на производительность целевого приложения больше, чем вариант `-gccollectonly`.</span><span class="sxs-lookup"><span data-stu-id="5f05e-222">This requests more verbose events (such as the allocation information and GC join information) and will have more impact to the target app's performance than `-gccollectonly` option.</span></span> <span data-ttu-id="5f05e-223">Эта команда аналогична команде `PerfView.exe /GCOnly collect` в PerfView.</span><span class="sxs-lookup"><span data-stu-id="5f05e-223">This command is analogous to `PerfView.exe /GCOnly collect` command in PerfView.</span></span>

* `perfcollect collect -gcwithheap`

<span data-ttu-id="5f05e-224">Сбор самых подробных событий коллекции сбора мусора, а также отслеживание выживания и перемещения кучи.</span><span class="sxs-lookup"><span data-stu-id="5f05e-224">Collect the most verbose GC collection events which tracks the heap survival and movements as well.</span></span> <span data-ttu-id="5f05e-225">Это позволяет выполнить подробный анализ поведения сборки мусора, но при этом обеспечивает высокую производительность, поскольку длительность каждой сборки мусора может оказаться больше чем в два раза.</span><span class="sxs-lookup"><span data-stu-id="5f05e-225">This gives in-depth analysis of the GC behavior but will incur high performance cost as each GC can take more than two times longer.</span></span> <span data-ttu-id="5f05e-226">Следует понимать влияние этого варианта трассировки на производительность при трассировке в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="5f05e-226">It is recommended you understand the performance implication of using this trace option when tracing in production environments.</span></span>
