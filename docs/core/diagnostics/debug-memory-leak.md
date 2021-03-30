---
title: Учебник по выполнению отладки утечки памяти
description: Узнайте, как выполнить отладку утечки памяти в .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: 09777b6c9f80c28e1eec28983d605f2a2e261c92
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872747"
---
# <a name="debug-a-memory-leak-in-net-core"></a><span data-ttu-id="01e6d-103">Отладка утечки памяти в .NET Core</span><span class="sxs-lookup"><span data-stu-id="01e6d-103">Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="01e6d-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="01e6d-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="01e6d-105">Когда приложение ссылается на объекты, которым больше не требуется выполнять нужную задачу, может произойти утечка памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-105">A memory leak may happen when your app references objects that it no longer needs to perform the desired task.</span></span> <span data-ttu-id="01e6d-106">При ссылке на такие объекты сборщик мусора не сможет освободить используемую память, что часто приводит к снижению производительности и может привести к возникновению <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="01e6d-106">Referencing said objects makes the garbage collector to be unable to reclaim the memory used, often resulting in performance degradation and potentially end up throwing a <xref:System.OutOfMemoryException>.</span></span>

<span data-ttu-id="01e6d-107">В этом учебнике демонстрируются средства для анализа утечки памяти в приложении .NET Core с помощью средств CLI для диагностики .NET.</span><span class="sxs-lookup"><span data-stu-id="01e6d-107">This tutorial demonstrates the tools to analyze a memory leak in a .NET Core app using the .NET diagnostics CLI tools.</span></span> <span data-ttu-id="01e6d-108">Если вы используете Windows, для отладки утечек памяти можно [использовать средства диагностики памяти Visual Studio](/visualstudio/profiling/memory-usage).</span><span class="sxs-lookup"><span data-stu-id="01e6d-108">If you are on Windows, you may be able to [use Visual Studio's Memory Diagnostic tools](/visualstudio/profiling/memory-usage) to debug the memory leak.</span></span>

<span data-ttu-id="01e6d-109">Здесь используется пример приложения, в котором намеренно происходит утечка памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-109">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="01e6d-110">Пример предоставляется для выполнения упражнения.</span><span class="sxs-lookup"><span data-stu-id="01e6d-110">The sample is provided as an exercise.</span></span> <span data-ttu-id="01e6d-111">Вы можете проанализировать приложение, в котором также непреднамеренно происходит утечка памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-111">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="01e6d-112">В этом руководстве рассмотрены следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="01e6d-112">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="01e6d-113">Изучение использования управляемой памяти с помощью [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="01e6d-113">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="01e6d-114">Создание файла дампа.</span><span class="sxs-lookup"><span data-stu-id="01e6d-114">Generate a dump file.</span></span>
> - <span data-ttu-id="01e6d-115">Анализ использования памяти с помощью файла дампа.</span><span class="sxs-lookup"><span data-stu-id="01e6d-115">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01e6d-116">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="01e6d-116">Prerequisites</span></span>

<span data-ttu-id="01e6d-117">В этом учебнике используется:</span><span class="sxs-lookup"><span data-stu-id="01e6d-117">The tutorial uses:</span></span>

- <span data-ttu-id="01e6d-118">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="01e6d-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version.</span></span>
- <span data-ttu-id="01e6d-119">[dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-119">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="01e6d-120">[dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа.</span><span class="sxs-lookup"><span data-stu-id="01e6d-120">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="01e6d-121">[Пример целевого приложения отладки](/samples/dotnet/samples/diagnostic-scenarios/) для диагностики.</span><span class="sxs-lookup"><span data-stu-id="01e6d-121">A [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="01e6d-122">В учебнике предполагается, что пример приложения и инструменты установлены и готовы к использованию.</span><span class="sxs-lookup"><span data-stu-id="01e6d-122">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="01e6d-123">Изучение использования управляемой памяти</span><span class="sxs-lookup"><span data-stu-id="01e6d-123">Examine managed memory usage</span></span>

<span data-ttu-id="01e6d-124">Перед началом сбора данных диагностики с целью поиска основной причины, которая привела к данному сценарию, необходимо убедиться в наличии утечки памяти (или ее увеличения).</span><span class="sxs-lookup"><span data-stu-id="01e6d-124">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="01e6d-125">Для этого используйте [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="01e6d-125">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="01e6d-126">Откройте окно консоли и перейдите к каталогу, в который вы скачали и распаковали [пример целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="01e6d-126">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="01e6d-127">Запустите целевой объект:</span><span class="sxs-lookup"><span data-stu-id="01e6d-127">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="01e6d-128">В отдельном окне консоли найдите идентификатор процесса:</span><span class="sxs-lookup"><span data-stu-id="01e6d-128">From a separate console, find the process ID:</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="01e6d-129">Результат должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="01e6d-129">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="01e6d-130">Теперь проверьте использование управляемой памяти с помощью инструмента [dotnet-counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="01e6d-130">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="01e6d-131">`--refresh-interval` задает время между обновлениями (в секундах):</span><span class="sxs-lookup"><span data-stu-id="01e6d-131">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="01e6d-132">Динамические выходные данные должны выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="01e6d-132">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="01e6d-133">Рассмотрите подробнее эту строку:</span><span class="sxs-lookup"><span data-stu-id="01e6d-133">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="01e6d-134">Как видите, сразу после запуска объем управляемой динамической памяти составляет 4 МБ.</span><span class="sxs-lookup"><span data-stu-id="01e6d-134">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="01e6d-135">Теперь перейдите по URL-адресу `https://localhost:5001/api/diagscenario/memleak/20000`.</span><span class="sxs-lookup"><span data-stu-id="01e6d-135">Now, hit the URL `https://localhost:5001/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="01e6d-136">Обратите внимание, что объем использования памяти увеличился до 30 МБ.</span><span class="sxs-lookup"><span data-stu-id="01e6d-136">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="01e6d-137">Просмотрев данные об использовании памяти, вы можете точно определить, что происходит: утечка или увеличение памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-137">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="01e6d-138">Следующим шагом является сбор правильных данных для анализа памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-138">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="01e6d-139">Создание дампа памяти</span><span class="sxs-lookup"><span data-stu-id="01e6d-139">Generate memory dump</span></span>

<span data-ttu-id="01e6d-140">При анализе возможных утечек памяти необходимо получить доступ к динамической памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="01e6d-140">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="01e6d-141">Затем можно анализировать содержимое памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-141">Then you can analyze the memory contents.</span></span> <span data-ttu-id="01e6d-142">Изучив связи между объектами, можно делать предположения о том, почему область памяти не освобождается.</span><span class="sxs-lookup"><span data-stu-id="01e6d-142">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="01e6d-143">Общий источник диагностических данных — это дамп памяти в Windows или эквивалентный основной дамп в Linux.</span><span class="sxs-lookup"><span data-stu-id="01e6d-143">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="01e6d-144">Чтобы создать дамп приложения .NET Core, воспользуйтесь инструментом [dotnet-dump](dotnet-dump.md).</span><span class="sxs-lookup"><span data-stu-id="01e6d-144">To generate a dump of a .NET Core application, you can use the [dotnet-dump](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="01e6d-145">Выполните приведенную ниже команду, чтобы создать основной дамп в Linux для предварительно запущенного [примера целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/):</span><span class="sxs-lookup"><span data-stu-id="01e6d-145">Using the [sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="01e6d-146">В результате в той же папке будет создан основной дамп.</span><span class="sxs-lookup"><span data-stu-id="01e6d-146">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="01e6d-147">Перезапуск неисправного процесса</span><span class="sxs-lookup"><span data-stu-id="01e6d-147">Restart the failed process</span></span>

<span data-ttu-id="01e6d-148">После сбора дампа у вас должно быть достаточно данных для диагностики неисправного процесса.</span><span class="sxs-lookup"><span data-stu-id="01e6d-148">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="01e6d-149">Если неисправный процесс запущен на рабочем сервере, это удачный момент для выполнения краткосрочного исправления проблем путем перезапуска процесса.</span><span class="sxs-lookup"><span data-stu-id="01e6d-149">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="01e6d-150">Вы уже завершили работу с [примером целевого объекта отладки](/samples/dotnet/samples/diagnostic-scenarios/) в рамках этого учебника и можете закрыть этот объект.</span><span class="sxs-lookup"><span data-stu-id="01e6d-150">In this tutorial, you're now done with the [Sample debug target](/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="01e6d-151">Перейдите к терминалу, с которого запущен сервер, и нажмите клавиши <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="01e6d-151">Navigate to the terminal that started the server, and press <kbd>Ctrl+C</kbd>.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="01e6d-152">Анализ основного дампа</span><span class="sxs-lookup"><span data-stu-id="01e6d-152">Analyze the core dump</span></span>

<span data-ttu-id="01e6d-153">Теперь, когда у вас есть основной дамп, используйте инструмент [dotnet-dump](dotnet-dump.md), чтобы проанализировать его:</span><span class="sxs-lookup"><span data-stu-id="01e6d-153">Now that you have a core dump generated, use the [dotnet-dump](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="01e6d-154">Где `core_20190430_185145` — это имя основного дампа, который нужно проанализировать.</span><span class="sxs-lookup"><span data-stu-id="01e6d-154">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="01e6d-155">Если отображается сообщение о том, что *libdl.so* не удалось найти, возможно, потребуется установить пакет *libc6-dev*.</span><span class="sxs-lookup"><span data-stu-id="01e6d-155">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="01e6d-156">Дополнительные сведения см. в статье [Необходимые компоненты для .NET Core в Linux](../install/linux.md).</span><span class="sxs-lookup"><span data-stu-id="01e6d-156">For more information, see [Prerequisites for .NET Core on Linux](../install/linux.md).</span></span>

<span data-ttu-id="01e6d-157">Отобразится командная строка для ввода команд SOS.</span><span class="sxs-lookup"><span data-stu-id="01e6d-157">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="01e6d-158">Как правило, в первую очередь нужно просмотреть общее состояние управляемой динамической памяти:</span><span class="sxs-lookup"><span data-stu-id="01e6d-158">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="01e6d-159">В нашем примере видно, что большинство объектов принадлежат к типу `String` либо `Customer`.</span><span class="sxs-lookup"><span data-stu-id="01e6d-159">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="01e6d-160">Вы можете повторно выполнить команду `dumpheap` с помощью таблицы методов, чтобы получить список всех экземпляров `String`:</span><span class="sxs-lookup"><span data-stu-id="01e6d-160">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="01e6d-161">Теперь можно использовать команду `gcroot` в экземпляре `System.String`, чтобы узнать, как и зачем объект становится корневым.</span><span class="sxs-lookup"><span data-stu-id="01e6d-161">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="01e6d-162">Подождите, так как выполнение этой команды для объема памяти в 30 МБ занимает несколько минут:</span><span class="sxs-lookup"><span data-stu-id="01e6d-162">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="01e6d-163">Как видно, `String` непосредственно содержится в объекте `Customer` и косвенно в объекте `CustomerCache`.</span><span class="sxs-lookup"><span data-stu-id="01e6d-163">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="01e6d-164">Вы можете продолжить разгрузку объектов и увидите, что большинство объектов `String` следуют той же модели.</span><span class="sxs-lookup"><span data-stu-id="01e6d-164">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="01e6d-165">На этом этапе в результате исследования получено достаточно информации, чтобы найти основную причину утечки в коде.</span><span class="sxs-lookup"><span data-stu-id="01e6d-165">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="01e6d-166">Эта общая процедура позволяет определить источник основных утечек памяти.</span><span class="sxs-lookup"><span data-stu-id="01e6d-166">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="01e6d-167">Очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="01e6d-167">Clean up resources</span></span>

<span data-ttu-id="01e6d-168">В этом учебнике вы запустили пример веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="01e6d-168">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="01e6d-169">Работа этого сервера должна быть завершена, как описано в разделе [Перезапуск неисправного процесса](#restart-the-failed-process).</span><span class="sxs-lookup"><span data-stu-id="01e6d-169">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="01e6d-170">Вы также можете удалить созданный файл дампа.</span><span class="sxs-lookup"><span data-stu-id="01e6d-170">You can also delete the dump file that was created.</span></span>

## <a name="see-also"></a><span data-ttu-id="01e6d-171">См. также</span><span class="sxs-lookup"><span data-stu-id="01e6d-171">See also</span></span>

- <span data-ttu-id="01e6d-172">[dotnet-trace](dotnet-trace.md) для отображения списка процессов</span><span class="sxs-lookup"><span data-stu-id="01e6d-172">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="01e6d-173">[dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти</span><span class="sxs-lookup"><span data-stu-id="01e6d-173">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="01e6d-174">[dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа</span><span class="sxs-lookup"><span data-stu-id="01e6d-174">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="01e6d-175">dotnet/diagnostics</span><span class="sxs-lookup"><span data-stu-id="01e6d-175">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/main/documentation/tutorial)
- [<span data-ttu-id="01e6d-176">Отладка утечек памяти с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01e6d-176">Use Visual Studio to debug memory leaks</span></span>](/visualstudio/profiling/memory-usage)

## <a name="next-steps"></a><span data-ttu-id="01e6d-177">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="01e6d-177">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01e6d-178">Отладка высокой загрузки ЦП в .NET Core</span><span class="sxs-lookup"><span data-stu-id="01e6d-178">Debug high CPU in .NET Core</span></span>](debug-highcpu.md)
