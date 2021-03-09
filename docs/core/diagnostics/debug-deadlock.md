---
title: Отладка взаимоблокировки в .NET Core
description: Руководство по отладке проблемы блокировки в .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 0f5862c9acc4c1ae892caf29cea2ca484116cabf
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105588"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="aae6d-103">Отладка взаимоблокировки в .NET Core</span><span class="sxs-lookup"><span data-stu-id="aae6d-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="aae6d-104">**Эта статья относится к: ✔️** пакету SDK для .NET Core 3.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="aae6d-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="aae6d-105">В этом руководстве описано, как выполнить отладку взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="aae6d-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="aae6d-106">Используя предоставленный пример [веб-приложения ASP.NET Core](/samples/dotnet/samples/diagnostic-scenarios) в репозитории исходного кода, можно намеренно вызвать взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="aae6d-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="aae6d-107">Конечная точка перестанет отвечать на запросы, и в ней будут накапливаться потоки.</span><span class="sxs-lookup"><span data-stu-id="aae6d-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="aae6d-108">Вы узнаете, как использовать различные средства для анализа проблемы, такие как основные дампы, анализ основного дампа и трассировка процесса.</span><span class="sxs-lookup"><span data-stu-id="aae6d-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="aae6d-109">В этом руководстве рассмотрены следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="aae6d-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="aae6d-110">Изучение зависания приложения</span><span class="sxs-lookup"><span data-stu-id="aae6d-110">Investigate an app hang</span></span>
> - <span data-ttu-id="aae6d-111">Создание основного файла дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-111">Generate a core dump file</span></span>
> - <span data-ttu-id="aae6d-112">Анализ потоков процесса в файле дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="aae6d-113">Анализ стеков вызовов и блоков синхронизации</span><span class="sxs-lookup"><span data-stu-id="aae6d-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="aae6d-114">Диагностика и устранение взаимоблокировки</span><span class="sxs-lookup"><span data-stu-id="aae6d-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aae6d-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="aae6d-115">Prerequisites</span></span>

<span data-ttu-id="aae6d-116">В этом учебнике используется:</span><span class="sxs-lookup"><span data-stu-id="aae6d-116">The tutorial uses:</span></span>

- <span data-ttu-id="aae6d-117">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="aae6d-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>
- <span data-ttu-id="aae6d-118">[Пример целевого объекта отладки — веб-приложение](/samples/dotnet/samples/diagnostic-scenarios) для активации сценария</span><span class="sxs-lookup"><span data-stu-id="aae6d-118">[Sample debug target - web app](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="aae6d-119">[dotnet-trace](dotnet-trace.md) для отображения списка процессов</span><span class="sxs-lookup"><span data-stu-id="aae6d-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="aae6d-120">[dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="aae6d-121">Создание основного дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-121">Core dump generation</span></span>

<span data-ttu-id="aae6d-122">Чтобы определить причину, по которой приложение перестало отвечать на запросы, можно использовать основной дамп или дамп памяти, который позволяет проверять состояние потоков и любые возможные блокировки, вызывающие конфликты.</span><span class="sxs-lookup"><span data-stu-id="aae6d-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="aae6d-123">Запустите [пример приложения отладки](/samples/dotnet/samples/diagnostic-scenarios) из корневого каталога примера с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="aae6d-123">Run the [sample debug](/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="aae6d-124">Чтобы узнать ИД процесса, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="aae6d-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="aae6d-125">Запишите ИД процесса, отображаемый в выходных данных команды.</span><span class="sxs-lookup"><span data-stu-id="aae6d-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="aae6d-126">Наш ИД процесса — `4807`, но ваш будет другим.</span><span class="sxs-lookup"><span data-stu-id="aae6d-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="aae6d-127">Перейдите по следующему URL-адресу, который является конечной точкой API на примере сайта:</span><span class="sxs-lookup"><span data-stu-id="aae6d-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

`https://localhost:5001/api/diagscenario/deadlock`

<span data-ttu-id="aae6d-128">Запрос API к сайту зависает и не отвечает.</span><span class="sxs-lookup"><span data-stu-id="aae6d-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="aae6d-129">Пусть запрос выполняется около 10–15 секунд</span><span class="sxs-lookup"><span data-stu-id="aae6d-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="aae6d-130">Затем создайте основной дамп с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="aae6d-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="aae6d-131">Linux</span><span class="sxs-lookup"><span data-stu-id="aae6d-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="aae6d-132">Windows</span><span class="sxs-lookup"><span data-stu-id="aae6d-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="aae6d-133">Анализ основного дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-133">Analyze the core dump</span></span>

<span data-ttu-id="aae6d-134">Чтобы запустить анализ основного дампа, откройте основной дамп, выполнив следующую команду `dotnet-dump analyze`.</span><span class="sxs-lookup"><span data-stu-id="aae6d-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="aae6d-135">Аргумент — это путь к файлу основного дампа, который был собран ранее.</span><span class="sxs-lookup"><span data-stu-id="aae6d-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="aae6d-136">Так как вы имеете дело с потенциальным зависанием, необходимо получить общее представление об активности потока в процессе.</span><span class="sxs-lookup"><span data-stu-id="aae6d-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="aae6d-137">Можно использовать команду `threads`, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="aae6d-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="aae6d-138">В выходных данных представлены все потоки, выполняющиеся в процессе со связанным ИД потока отладчика и ИД потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="aae6d-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="aae6d-139">Согласно выходным данным имеется более 300 потоков.</span><span class="sxs-lookup"><span data-stu-id="aae6d-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="aae6d-140">Далее нужно понять, что именно выполняют потоки в настоящее время. Для этого следует получить стек вызовов каждого потока.</span><span class="sxs-lookup"><span data-stu-id="aae6d-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="aae6d-141">Для вывода стеков вызовов можно использовать команду `clrstack`.</span><span class="sxs-lookup"><span data-stu-id="aae6d-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="aae6d-142">Может быть выведен один либо все стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="aae6d-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="aae6d-143">Используйте следующую команду, чтобы вывести все стеки вызовов для всех потоков в процессе:</span><span class="sxs-lookup"><span data-stu-id="aae6d-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="aae6d-144">Репрезентативная часть выходных данных выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aae6d-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="aae6d-145">Если взглянуть на стеки вызовов для всех потоков, которых более 300 , можно заметить, что большинство потоков совместно используют общий стек вызовов:</span><span class="sxs-lookup"><span data-stu-id="aae6d-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="aae6d-146">Похоже, стек вызовов указывает, что запрос поступил в метод взаимоблокировки, который, в свою очередь, вызывает `Monitor.ReliableEnter`.</span><span class="sxs-lookup"><span data-stu-id="aae6d-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="aae6d-147">Этот метод означает, что потоки пытаются получить блокировку монитора.</span><span class="sxs-lookup"><span data-stu-id="aae6d-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="aae6d-148">Они ожидают доступности блокировки.</span><span class="sxs-lookup"><span data-stu-id="aae6d-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="aae6d-149">Скорее всего, она заблокирована другим потоком.</span><span class="sxs-lookup"><span data-stu-id="aae6d-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="aae6d-150">Далее нужно определить, какой поток на самом деле содержит блокировку монитора.</span><span class="sxs-lookup"><span data-stu-id="aae6d-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="aae6d-151">Так как мониторы обычно хранят сведения о блокировках в таблице блока синхронизации, для получения дополнительных сведений можно использовать команду `syncblk`.</span><span class="sxs-lookup"><span data-stu-id="aae6d-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="aae6d-152">Нас интересуют столбцы — **MonitorHeld** и **Сведения о владеющем потоке**.</span><span class="sxs-lookup"><span data-stu-id="aae6d-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="aae6d-153">Столбец **MonitorHeld** показывает, была ли блокировка монитора получена потоком, и отображает количество ожидающих потоков.</span><span class="sxs-lookup"><span data-stu-id="aae6d-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="aae6d-154">В столбце **Сведения о владеющем потоке** отображается поток, который в настоящее время владеет блокировкой монитора.</span><span class="sxs-lookup"><span data-stu-id="aae6d-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="aae6d-155">Столбец сведений о потоке имеет три разных подчиненных столбца.</span><span class="sxs-lookup"><span data-stu-id="aae6d-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="aae6d-156">Во втором подчиненном столбце отображается идентификатор потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="aae6d-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="aae6d-157">На этом этапе нам известно, что два разных потока (0x5634 и 0x51d4) владеют блокировкой монитора.</span><span class="sxs-lookup"><span data-stu-id="aae6d-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="aae6d-158">Далее нам нужно понять, что происходит с этими потоками.</span><span class="sxs-lookup"><span data-stu-id="aae6d-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="aae6d-159">Необходимо проверить, не зависли ли они, удерживая блокировку на неопределенное время.</span><span class="sxs-lookup"><span data-stu-id="aae6d-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="aae6d-160">Давайте воспользуемся командами `setthread` и `clrstack`, чтобы переключиться на каждый из потоков и отобразить стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="aae6d-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="aae6d-161">Чтобы просмотреть первый поток, выполните команду `setthread` и найдите индекс потока 0x5634 (у нас был индекс 28).</span><span class="sxs-lookup"><span data-stu-id="aae6d-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="aae6d-162">Функция взаимоблокировки ожидает получения блокировки, но она уже владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="aae6d-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="aae6d-163">Она находится в состоянии взаимоблокировки, ожидая уже имеющуюся блокировку.</span><span class="sxs-lookup"><span data-stu-id="aae6d-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="aae6d-164">Второй поток аналогичен первому.</span><span class="sxs-lookup"><span data-stu-id="aae6d-164">The second thread is similar.</span></span> <span data-ttu-id="aae6d-165">Он также пытается получить блокировку, которой уже владеет.</span><span class="sxs-lookup"><span data-stu-id="aae6d-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="aae6d-166">Оставшиеся ожидающие потоки, которых более 300, скорее всего, также ожидают одну из блокировок, вызвавших взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="aae6d-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="aae6d-167">См. также</span><span class="sxs-lookup"><span data-stu-id="aae6d-167">See also</span></span>

- <span data-ttu-id="aae6d-168">[dotnet-trace](dotnet-trace.md) для отображения списка процессов</span><span class="sxs-lookup"><span data-stu-id="aae6d-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="aae6d-169">[dotnet-counters](dotnet-counters.md) для проверки использования управляемой памяти</span><span class="sxs-lookup"><span data-stu-id="aae6d-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="aae6d-170">[dotnet-dump](dotnet-dump.md) для сбора и анализа файла дампа</span><span class="sxs-lookup"><span data-stu-id="aae6d-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="aae6d-171">dotnet/diagnostics</span><span class="sxs-lookup"><span data-stu-id="aae6d-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="aae6d-172">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="aae6d-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aae6d-173">Общие сведения о средствах диагностики в .NET Core</span><span class="sxs-lookup"><span data-stu-id="aae6d-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
