---
title: Сбор подробных сведений о загрузке сборок — .NET Core
description: Узнайте, как выполнить сбор сведений о загрузке сборок в .NET Core.
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: 505fc827021fe4d34675b2ef5a7fc5746ada1af6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872942"
---
# <a name="collect-detailed-assembly-loading-information"></a><span data-ttu-id="44610-103">Сбор подробных сведений о загрузке сборок</span><span class="sxs-lookup"><span data-stu-id="44610-103">Collect detailed assembly loading information</span></span>

<span data-ttu-id="44610-104">Начиная с .NET 5.0, среда выполнения может создавать события с помощью `EventPipe` с подробными сведениями о [загрузке управляемой сборки](loading-managed.md), которые упрощают диагностику проблем с загрузкой сборок.</span><span class="sxs-lookup"><span data-stu-id="44610-104">Starting with .NET 5.0, the runtime can emit events through `EventPipe` with detailed information about [managed assembly loading](loading-managed.md) to aid in diagnosing assembly loading issues.</span></span> <span data-ttu-id="44610-105">Такие [события](../../fundamentals/diagnostics/runtime-loader-binder-events.md) выдаются поставщиком `Microsoft-Windows-DotNETRuntime` с ключевым словом `AssemblyLoader` (`0x4`).</span><span class="sxs-lookup"><span data-stu-id="44610-105">These [events](../../fundamentals/diagnostics/runtime-loader-binder-events.md) are emitted by the `Microsoft-Windows-DotNETRuntime` provider under the `AssemblyLoader` keyword (`0x4`).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44610-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="44610-106">Prerequisites</span></span>

- <span data-ttu-id="44610-107">[Пакет SDK для .NET 5.0](https://dotnet.microsoft.com/download) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="44610-107">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="44610-108">Средство [dotnet-trace](../diagnostics/dotnet-trace.md).</span><span class="sxs-lookup"><span data-stu-id="44610-108">[dotnet-trace](../diagnostics/dotnet-trace.md) tool.</span></span>

## <a name="collect-a-trace-with-assembly-loading-events"></a><span data-ttu-id="44610-109">Сбор трассировки с помощью событий загрузки сборок</span><span class="sxs-lookup"><span data-stu-id="44610-109">Collect a trace with assembly loading events</span></span>

<span data-ttu-id="44610-110">Чтобы включить события загрузки сборок в среде выполнения и собирать для них трассировки, используйте `dotnet-trace` с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="44610-110">To enable assembly loading events in the runtime and collect a trace of them, use `dotnet-trace` with the following command:</span></span>

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

<span data-ttu-id="44610-111">При этом будет собрана трассировка указанного `<pid>`, которая активирует события `AssemblyLoader` в поставщике `Microsoft-Windows-DotNETRuntime`.</span><span class="sxs-lookup"><span data-stu-id="44610-111">This will collect a trace of the specified `<pid>`, enabling the `AssemblyLoader` events in the `Microsoft-Windows-DotNETRuntime` provider.</span></span> <span data-ttu-id="44610-112">Результатом будет файл `.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="44610-112">The result is a `.nettrace` file.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="44610-113">Просмотр трассировки</span><span class="sxs-lookup"><span data-stu-id="44610-113">View a trace</span></span>

<span data-ttu-id="44610-114">Собранный файл трассировки можно просмотреть в Windows с помощью представления "События" в [PerfView](https://github.com/microsoft/perfview).</span><span class="sxs-lookup"><span data-stu-id="44610-114">The collected trace file can be viewed on Windows using the Events view in [PerfView](https://github.com/microsoft/perfview).</span></span> <span data-ttu-id="44610-115">Все события загрузки сборок будут иметь префикс `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.</span><span class="sxs-lookup"><span data-stu-id="44610-115">All the assembly loading events will be prefixed with `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.</span></span>

## <a name="example-on-windows"></a><span data-ttu-id="44610-116">Пример (в Windows)</span><span class="sxs-lookup"><span data-stu-id="44610-116">Example (on Windows)</span></span>

<span data-ttu-id="44610-117">Здесь используется [пример точек расширения загрузки сборок](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/).</span><span class="sxs-lookup"><span data-stu-id="44610-117">This example uses the [assembly loading extension points sample](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/).</span></span> <span data-ttu-id="44610-118">Приложение пытается загрузить сборку `MyLibrary`, на которую не ссылается приложение и которая поэтому требует обработки в точке расширения загрузки сборок для успешной загрузки.</span><span class="sxs-lookup"><span data-stu-id="44610-118">The application attempts to load an assembly `MyLibrary` - an assembly that is not referenced by the application and thus requires handling in an assembly loading extension point to be successfully loaded.</span></span>

### <a name="collect-the-trace"></a><span data-ttu-id="44610-119">Сбор трассировки</span><span class="sxs-lookup"><span data-stu-id="44610-119">Collect the trace</span></span>

01. <span data-ttu-id="44610-120">Перейдите к каталогу со скачанным примером.</span><span class="sxs-lookup"><span data-stu-id="44610-120">Navigate to the directory with the downloaded sample.</span></span> <span data-ttu-id="44610-121">Выполните сборку приложения с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="44610-121">Build the application with:</span></span>

    ```console
    dotnet build
    ```

01. <span data-ttu-id="44610-122">Запустите приложение с аргументами для приостановки и ожидания нажатия клавиши.</span><span class="sxs-lookup"><span data-stu-id="44610-122">Launch the application with arguments indicating that it should pause, waiting for a key press.</span></span> <span data-ttu-id="44610-123">При возобновлении приложение попытается загрузить сборку `AssemblyLoadContext` по умолчанию, без обработки для успешной загрузки.</span><span class="sxs-lookup"><span data-stu-id="44610-123">On resuming, it will attempt to load the assembly in the default `AssemblyLoadContext` - without the handling necessary for a successful load.</span></span> <span data-ttu-id="44610-124">Перейдите к выходному каталогу и выполните команду:</span><span class="sxs-lookup"><span data-stu-id="44610-124">Navigate to the output directory and run:</span></span>

    ```console
    AssemblyLoading.exe /d default
    ```

01. <span data-ttu-id="44610-125">Найдите идентификатор процесса приложения.</span><span class="sxs-lookup"><span data-stu-id="44610-125">Find the application's process ID.</span></span>

    ```console
    dotnet-trace ps
    ```

    <span data-ttu-id="44610-126">В выходных данных будут указаны доступные процессы.</span><span class="sxs-lookup"><span data-stu-id="44610-126">The output will list the available processes.</span></span> <span data-ttu-id="44610-127">Пример:</span><span class="sxs-lookup"><span data-stu-id="44610-127">For example:</span></span>

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. <span data-ttu-id="44610-128">Подключите `dotnet-trace` к выполняющемуся приложению.</span><span class="sxs-lookup"><span data-stu-id="44610-128">Attach `dotnet-trace` to the running application.</span></span>

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. <span data-ttu-id="44610-129">В окне, где выполняется приложение, нажмите любую клавишу, чтобы продолжить выполнение программы.</span><span class="sxs-lookup"><span data-stu-id="44610-129">In the window running the application, press any key to let the program continue.</span></span> <span data-ttu-id="44610-130">Трассировка будет автоматически прекращена после завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="44610-130">Tracing will automatically stop once the application exits.</span></span>

### <a name="view-the-trace"></a><span data-ttu-id="44610-131">Просмотр трассировки</span><span class="sxs-lookup"><span data-stu-id="44610-131">View the trace</span></span>

<span data-ttu-id="44610-132">Откройте собранную трассировку в [PerfView](https://github.com/microsoft/perfview) и откройте представление "События".</span><span class="sxs-lookup"><span data-stu-id="44610-132">Open the collected trace in [PerfView](https://github.com/microsoft/perfview) and open the Events view.</span></span> <span data-ttu-id="44610-133">Отфильтруйте список событий для отображения событий `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.</span><span class="sxs-lookup"><span data-stu-id="44610-133">Filter the events list to `Microsoft-Windows-DotNETRuntime/AssemblyLoader` events.</span></span>

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="Изображение фильтра загрузчика сборок PerfView":::

<span data-ttu-id="44610-135">Будут показаны все загрузки сборок, которые были выполнены в приложении после начала трассировки.</span><span class="sxs-lookup"><span data-stu-id="44610-135">All assembly loads that occurred in the application after tracing started will be shown.</span></span> <span data-ttu-id="44610-136">Чтобы просмотреть операцию загрузки для нужной сборки в этом примере (`MyLibrary`), мы можем задать дополнительные фильтры.</span><span class="sxs-lookup"><span data-stu-id="44610-136">To inspect the load operation for the assembly of interest for this example - `MyLibrary`, we can do some more filtering.</span></span>

### <a name="assembly-loads"></a><span data-ttu-id="44610-137">Загрузки сборок</span><span class="sxs-lookup"><span data-stu-id="44610-137">Assembly loads</span></span>

<span data-ttu-id="44610-138">Отфильтруйте представление для отображения событий [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) и [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева.</span><span class="sxs-lookup"><span data-stu-id="44610-138">Filter the view to the [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) and [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) events under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="44610-139">Добавьте к представлению столбцы `AssemblyName`, `ActivityID` и `Success`.</span><span class="sxs-lookup"><span data-stu-id="44610-139">Add the columns `AssemblyName`, `ActivityID`, and `Success` to the view.</span></span> <span data-ttu-id="44610-140">Выполните фильтрацию по событиям, содержащим `MyLibrary`.</span><span class="sxs-lookup"><span data-stu-id="44610-140">Filter to events containing `MyLibrary`.</span></span>

:::image type="content" source="media/collect-details/start-stop.png" alt-text="Изображение событий запуска и завершения в PerfView":::

| <span data-ttu-id="44610-142">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-142">Event Name</span></span>             | <span data-ttu-id="44610-143">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-143">AssemblyName</span></span>                                      | <span data-ttu-id="44610-144">Идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="44610-144">ActivityID</span></span> | <span data-ttu-id="44610-145">Успех</span><span class="sxs-lookup"><span data-stu-id="44610-145">Success</span></span> |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-146">//1/2/</span><span class="sxs-lookup"><span data-stu-id="44610-146">//1/2/</span></span>     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-147">//1/2/</span><span class="sxs-lookup"><span data-stu-id="44610-147">//1/2/</span></span>     | <span data-ttu-id="44610-148">False</span><span class="sxs-lookup"><span data-stu-id="44610-148">False</span></span>   |

<span data-ttu-id="44610-149">Вы должны увидеть одну пару `Start`/`Stop` с `Success=False` для события `Stop`, что указывает на сбой операции загрузки.</span><span class="sxs-lookup"><span data-stu-id="44610-149">You should see one `Start`/`Stop` pair with `Success=False` on the `Stop` event, indicating the load operation failed.</span></span> <span data-ttu-id="44610-150">Обратите внимание, что два события имеют одинаковый идентификатор действия.</span><span class="sxs-lookup"><span data-stu-id="44610-150">Note that the two events have the same activity ID.</span></span> <span data-ttu-id="44610-151">Идентификатор действия можно использовать для фильтрации всех остальных событий загрузчика сборок с отображением только тех из них, которые относятся к этой операции загрузки.</span><span class="sxs-lookup"><span data-stu-id="44610-151">The activity ID can be used to filter all the other assembly loader events to just the ones corresponding to this load operation.</span></span>

### <a name="breakdown-of-attempt-to-load"></a><span data-ttu-id="44610-152">Детализация попытки загрузки</span><span class="sxs-lookup"><span data-stu-id="44610-152">Breakdown of attempt to load</span></span>

<span data-ttu-id="44610-153">Чтобы просмотреть детализацию для операции загрузки, отфильтруйте представления по [событиям `ResolutionAttempted`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева.</span><span class="sxs-lookup"><span data-stu-id="44610-153">For a more detailed breakdown of the load operation, filter the view to the [`ResolutionAttempted` events](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="44610-154">Добавьте к представлению столбцы `AssemblyName`, `Stage` и `Result`.</span><span class="sxs-lookup"><span data-stu-id="44610-154">Add the columns `AssemblyName`, `Stage`, and `Result` to the view.</span></span> <span data-ttu-id="44610-155">Выполните фильтрацию по событиям с идентификатором действия из пары `Start`/`Stop`.</span><span class="sxs-lookup"><span data-stu-id="44610-155">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="Изображение событий ResolutionAttempted в PerfView":::

| <span data-ttu-id="44610-157">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-157">Event Name</span></span>                           | <span data-ttu-id="44610-158">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-158">AssemblyName</span></span>                                      | <span data-ttu-id="44610-159">Этап</span><span class="sxs-lookup"><span data-stu-id="44610-159">Stage</span></span>                               | <span data-ttu-id="44610-160">Результат</span><span class="sxs-lookup"><span data-stu-id="44610-160">Result</span></span>             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

<span data-ttu-id="44610-161">Приведенные выше события указывают, что загрузчик сборок попытался разрешить сборку путем поиска в текущем контексте загрузки, запуска логики проверки по умолчанию для сборок управляемого приложения, вызова обработчиков для события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> и вызова обработчиков для <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44610-161">The events above indicate that the assembly loader attempted to resolve the assembly by looking in the current load context, running the default probing logic for managed application assemblies, invoking handlers for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event, and invoking handlers for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44610-162">При выполнении каждого из этих шагов сборка не была найдена.</span><span class="sxs-lookup"><span data-stu-id="44610-162">For all of these steps, the assembly was not found.</span></span>

### <a name="extension-points"></a><span data-ttu-id="44610-163">Точки расширения</span><span class="sxs-lookup"><span data-stu-id="44610-163">Extension points</span></span>

<span data-ttu-id="44610-164">Чтобы узнать, какие точки расширения были вызваны, выполните фильтрацию представления по [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) и [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) в разделе `Microsoft-Windows-DotNETRuntime/AssemblyLoader` с помощью списка событий слева.</span><span class="sxs-lookup"><span data-stu-id="44610-164">To see which extension points were invoked, filter the view to the [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) and [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="44610-165">Добавьте к представлению столбцы `AssemblyName` и `HandlerName`.</span><span class="sxs-lookup"><span data-stu-id="44610-165">Add the columns `AssemblyName` and `HandlerName` to the view.</span></span> <span data-ttu-id="44610-166">Выполните фильтрацию по событиям с идентификатором действия из пары `Start`/`Stop`.</span><span class="sxs-lookup"><span data-stu-id="44610-166">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/extension-point.png" alt-text="Изображение событий точки расширения в PerfView":::

| <span data-ttu-id="44610-168">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-168">Event Name</span></span>                                                  | <span data-ttu-id="44610-169">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-169">AssemblyName</span></span>                                      | <span data-ttu-id="44610-170">HandlerName</span><span class="sxs-lookup"><span data-stu-id="44610-170">HandlerName</span></span>                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

<span data-ttu-id="44610-171">Приведенные выше события указывают на то, что обработчик с именем `OnAssemblyLoadContextResolving` был вызван для события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>, а обработчик с именем `OnAppDomainAssemblyResolve` — для события <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44610-171">The events above indicate that a handler named `OnAssemblyLoadContextResolving` was invoked for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event and a handler named `OnAppDomainAssemblyResolve` was invoked for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

### <a name="collect-another-trace"></a><span data-ttu-id="44610-172">Сбор дополнительной трассировки</span><span class="sxs-lookup"><span data-stu-id="44610-172">Collect another trace</span></span>

<span data-ttu-id="44610-173">Запустите приложение с аргументами, чтобы обработчик события <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> загружал сборку `MyLibrary`.</span><span class="sxs-lookup"><span data-stu-id="44610-173">Run the application with arguments such that its handler for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event will load the `MyLibrary` assembly.</span></span>

```console
AssemblyLoading /d default alc-resolving
```

<span data-ttu-id="44610-174">Соберите и откройте еще один файл `.nettrace`, выполнив [приведенные выше шаги](#collect-the-trace).</span><span class="sxs-lookup"><span data-stu-id="44610-174">Collect and open another `.nettrace` file using the [steps from above](#collect-the-trace).</span></span>

<span data-ttu-id="44610-175">Снова выполните фильтрацию по событиям `Start` и `Stop` для `MyLibrary`.</span><span class="sxs-lookup"><span data-stu-id="44610-175">Filter to the `Start` and `Stop` events for `MyLibrary` again.</span></span> <span data-ttu-id="44610-176">Вы должны увидеть пару `Start`/`Stop` с `Start`/`Stop` между ними.</span><span class="sxs-lookup"><span data-stu-id="44610-176">You should see a `Start`/`Stop` pair with another `Start`/`Stop` between them.</span></span> <span data-ttu-id="44610-177">Внутренняя операция загрузки представляет загрузку, активируемую обработчиком для <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> при вызове <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44610-177">The inner load operation represents the load triggered by the handler for <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> when it called <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44610-178">Вы должны увидеть `Success=True` для события `Stop`, что указывает на успешную операцию загрузки.</span><span class="sxs-lookup"><span data-stu-id="44610-178">This time, you should see `Success=True` on the `Stop` event, indicating the load operation succeeded.</span></span> <span data-ttu-id="44610-179">В поле `ResultAssemblyPath` отображается путь к итоговой сборке.</span><span class="sxs-lookup"><span data-stu-id="44610-179">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="Изображение успешных событий запуска и завершения в PerfView":::

| <span data-ttu-id="44610-181">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-181">Event Name</span></span>             | <span data-ttu-id="44610-182">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-182">AssemblyName</span></span>                                                       | <span data-ttu-id="44610-183">Идентификатор действия</span><span class="sxs-lookup"><span data-stu-id="44610-183">ActivityID</span></span> | <span data-ttu-id="44610-184">Успех</span><span class="sxs-lookup"><span data-stu-id="44610-184">Success</span></span> | <span data-ttu-id="44610-185">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="44610-185">ResultAssemblyPath</span></span>                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-186">//1/2/</span><span class="sxs-lookup"><span data-stu-id="44610-186">//1/2/</span></span>     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-187">//1/2/1/</span><span class="sxs-lookup"><span data-stu-id="44610-187">//1/2/1/</span></span>   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-188">//1/2/1/</span><span class="sxs-lookup"><span data-stu-id="44610-188">//1/2/1/</span></span>   | <span data-ttu-id="44610-189">True</span><span class="sxs-lookup"><span data-stu-id="44610-189">True</span></span>    | <span data-ttu-id="44610-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="44610-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="44610-191">//1/2/</span><span class="sxs-lookup"><span data-stu-id="44610-191">//1/2/</span></span>     | <span data-ttu-id="44610-192">True</span><span class="sxs-lookup"><span data-stu-id="44610-192">True</span></span>    | <span data-ttu-id="44610-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="44610-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="44610-194">Затем можно просмотреть события `ResolutionAttempted` с идентификатором действия из внешней нагрузки, чтобы определить шаг, на котором сборка была успешно разрешена.</span><span class="sxs-lookup"><span data-stu-id="44610-194">We can then look at the `ResolutionAttempted` events with the activity ID from the outer load to determine the step at which the assembly was successfully resolved.</span></span> <span data-ttu-id="44610-195">На этот раз события покажут, что этап `AssemblyLoadContextResolvingEvent` был выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="44610-195">This time, the events will show that the `AssemblyLoadContextResolvingEvent` stage was successful.</span></span> <span data-ttu-id="44610-196">В поле `ResultAssemblyPath` отображается путь к итоговой сборке.</span><span class="sxs-lookup"><span data-stu-id="44610-196">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="Изображение успешных событий ResolutionAttempted в PerfView":::

| <span data-ttu-id="44610-198">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-198">Event Name</span></span>                           | <span data-ttu-id="44610-199">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-199">AssemblyName</span></span>                                      | <span data-ttu-id="44610-200">Этап</span><span class="sxs-lookup"><span data-stu-id="44610-200">Stage</span></span>                               | <span data-ttu-id="44610-201">Результат</span><span class="sxs-lookup"><span data-stu-id="44610-201">Result</span></span>             | <span data-ttu-id="44610-202">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="44610-202">ResultAssemblyPath</span></span> |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | <span data-ttu-id="44610-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="44610-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="44610-204">При просмотре событий `AssemblyLoadContextResolvingHandlerInvoked` станет понятно, что был вызван обработчик с именем `OnAssemblyLoadContextResolving`.</span><span class="sxs-lookup"><span data-stu-id="44610-204">Looking at `AssemblyLoadContextResolvingHandlerInvoked` events will show that the handler named `OnAssemblyLoadContextResolving` was invoked.</span></span> <span data-ttu-id="44610-205">В поле `ResultAssemblyPath` отображается путь к сборке, возвращенной обработчиком.</span><span class="sxs-lookup"><span data-stu-id="44610-205">The `ResultAssemblyPath` field shows the path of the assembly returned by the handler.</span></span>

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="Изображение успешных событий точки расширения в PerfView":::

| <span data-ttu-id="44610-207">Имя события</span><span class="sxs-lookup"><span data-stu-id="44610-207">Event Name</span></span>                                                  | <span data-ttu-id="44610-208">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="44610-208">AssemblyName</span></span>                                      | <span data-ttu-id="44610-209">HandlerName</span><span class="sxs-lookup"><span data-stu-id="44610-209">HandlerName</span></span>                      | <span data-ttu-id="44610-210">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="44610-210">ResultAssemblyPath</span></span> |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | <span data-ttu-id="44610-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="44610-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="44610-212">Обратите внимание, что событие `ResolutionAttempted` с этапом `AppDomainAssemblyResolveEvent` или какие-либо события `AppDomainAssemblyResolveHandlerInvoked` больше не существуют, так как сборка была успешно загружена до достижения шага алгоритма загрузки, вызывающего событие <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44610-212">Note that there is no longer a `ResolutionAttempted` event with the `AppDomainAssemblyResolveEvent` stage or any `AppDomainAssemblyResolveHandlerInvoked` events, as the assembly was successfully loaded before reaching the step of the loading algorithm that raises the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

## <a name="see-also"></a><span data-ttu-id="44610-213">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="44610-213">See also</span></span>

- [<span data-ttu-id="44610-214">События загрузчика сборок</span><span class="sxs-lookup"><span data-stu-id="44610-214">Assembly loader events</span></span>](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [<span data-ttu-id="44610-215">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="44610-215">dotnet-trace</span></span>](../diagnostics/dotnet-trace.md)
- [<span data-ttu-id="44610-216">PerfView</span><span class="sxs-lookup"><span data-stu-id="44610-216">PerfView</span></span>](https://github.com/microsoft/perfview)
