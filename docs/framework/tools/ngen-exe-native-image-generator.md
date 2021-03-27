---
title: Ngen.exe (генератор образов в машинном коде)
description: Узнайте о Ngen.exe, генераторе образов в машинном коде. Повысьте производительность управляемого приложения, создавая образы в машинном код и выполняя установку в локальный кэш образов в машинном коде.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: dcf22b1840be5dd91b8ad2224871b8a22efb1183
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653885"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="4a3fa-104">Ngen.exe (генератор образов в машинном коде)</span><span class="sxs-lookup"><span data-stu-id="4a3fa-104">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="4a3fa-105">Генератор образов в машинном коде (Ngen.exe) — это средство повышения быстродействия управляемых приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-105">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="4a3fa-106">Программа Ngen.exe создает образы в машинном коде, представляющие собой файлы, содержащие компилированный, специфический для процессора машинный код, и устанавливает их в кэш образов в машинном коде на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-106">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="4a3fa-107">Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-107">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-108">Ngen.exe компилирует образы в машинном коде для сборок, предназначенных только для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-108">Ngen.exe compiles native images for assemblies that target the .NET Framework only.</span></span> <span data-ttu-id="4a3fa-109">Аналогичным генератором образов в машинном коде для .NET Core является [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-109">The equivalent native image generator for .NET Core is [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).</span></span>

<span data-ttu-id="4a3fa-110">Изменения в программе NGen.exe для .NET Framework 4:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-110">Changes to Ngen.exe in the .NET Framework 4:</span></span>

- <span data-ttu-id="4a3fa-111">Теперь программа NGen.exe компилирует сборки с полным доверием, и политика разграничения доступа кода (CAS) больше не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-111">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="4a3fa-112">Образы в машинном коде, созданные с помощью NGen.exe, нельзя загружать в приложения, выполняющиеся в режиме частичного доверия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-112">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="4a3fa-113">Изменения в программе NGen.exe для .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-113">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="4a3fa-114">При установке сборки также устанавливаются ее зависимости, что упрощает синтаксис Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-114">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="4a3fa-115">Образы в машинном коде теперь могут использоваться совместно в различных доменах приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-115">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="4a3fa-116">Новое действие, `update`, заново создает образы, ставшие недействительными.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-116">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="4a3fa-117">Служба может отложить выполнение действий, используя для создания и установки образов время простоя компьютера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-117">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="4a3fa-118">Были устранены некоторые причины недействительности образов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-118">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="4a3fa-119">Для Windows 8 см. раздел [Задача образов в машинном коде](#native-image-task).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-119">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="4a3fa-120">Подробнее об использовании программы Ngen.exe и службы образов в машинном коде см. в разделе [Служба образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-120">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-121">Синтаксис Ngen.exe для .NET Framework версий 1.0 и 1.1 см. в разделе [Генератор образов в машинном коде (Ngen.exe), традиционный синтаксис](/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-121">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="4a3fa-122">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-122">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4a3fa-123">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-123">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="4a3fa-124">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-124">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="4a3fa-125">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a3fa-125">Syntax</span></span>

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="4a3fa-126">Действия</span><span class="sxs-lookup"><span data-stu-id="4a3fa-126">Actions</span></span>

<span data-ttu-id="4a3fa-127">В следующей таблице показан синтаксис каждого из действий `action`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-127">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="4a3fa-128">Описания отдельных частей параметра `action` см. в таблицах [Аргументы](#ArgumentTable), [Уровни приоритета](#PriorityTable), [Сценарии](#ScenarioTable) и [Конфигурации](#ConfigTable).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-128">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="4a3fa-129">В таблице [Параметры](#OptionTable) описываются параметр `options` и ключи справки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-129">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="4a3fa-130">Действие</span><span class="sxs-lookup"><span data-stu-id="4a3fa-130">Action</span></span>|<span data-ttu-id="4a3fa-131">Описание</span><span class="sxs-lookup"><span data-stu-id="4a3fa-131">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="4a3fa-132">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-132">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="4a3fa-133">Формирует образы в машинном коде для сборки и ее зависимостей, а затем устанавливает образы в кэш образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-133">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="4a3fa-134">Если задан ключ `/queue`, действие помещается в очередь службы образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-134">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="4a3fa-135">Приоритет по умолчанию равен 3.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-135">The default priority is 3.</span></span> <span data-ttu-id="4a3fa-136">См. таблицу [Уровни приоритета](#PriorityTable).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-136">See the [Priority Levels](#PriorityTable) table.</span></span>|
|<span data-ttu-id="4a3fa-137">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-137">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="4a3fa-138">Удаляет образы в машинном коде для сборки и ее зависимостей из кэша образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-138">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="4a3fa-139">Для удаления одного образа и его зависимостей используются те же аргументы командной строки, что и для установки образа.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-139">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="4a3fa-140">**Примечание.**  Начиная с .NET Framework 4, действие `uninstall` \* не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-140">**Note:**  Starting with the .NET Framework 4, the action `uninstall` \* is no longer supported.</span></span>|
|<span data-ttu-id="4a3fa-141">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-141">`update` [`/queue`]</span></span>|<span data-ttu-id="4a3fa-142">Обновляет образы в машинном коде, ставшие недействительными.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-142">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="4a3fa-143">Если указан ключ `/queue`, обновления помещаются в очередь службы образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-143">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="4a3fa-144">Обновления всегда планируются с приоритетом 3, поэтому они выполняются во время простоя компьютера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-144">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|<span data-ttu-id="4a3fa-145">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-145">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="4a3fa-146">Отображает состояние образов в машинном коде для сборки и ее зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-146">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="4a3fa-147">Если аргумент не указан, отображается все содержимое кэша образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-147">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|<span data-ttu-id="4a3fa-148">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-148">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="4a3fa-149">-или-</span><span class="sxs-lookup"><span data-stu-id="4a3fa-149">-or-</span></span><br /><br /> <span data-ttu-id="4a3fa-150">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="4a3fa-150">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="4a3fa-151">Выполняет поставленные в очередь задания компиляции.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-151">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="4a3fa-152">Если указан приоритет, выполняются задания компиляции с большим или равным приоритетом.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-152">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="4a3fa-153">Если приоритет не задан, выполняются все поставленные в очередь задания компиляции.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-153">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|<span data-ttu-id="4a3fa-154">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="4a3fa-154">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="4a3fa-155">Приостанавливает работу службы образов в машинном коде, разрешает продолжение выполнения приостановленной службы или запрашивает состояние службы.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-155">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="4a3fa-156">Аргументы</span><span class="sxs-lookup"><span data-stu-id="4a3fa-156">Arguments</span></span>

|<span data-ttu-id="4a3fa-157">Аргумент</span><span class="sxs-lookup"><span data-stu-id="4a3fa-157">Argument</span></span>|<span data-ttu-id="4a3fa-158">Описание</span><span class="sxs-lookup"><span data-stu-id="4a3fa-158">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="4a3fa-159">Полное отображаемое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-159">The full display name of the assembly.</span></span> <span data-ttu-id="4a3fa-160">Например, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-160">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="4a3fa-161">**Примечание.**  Для действий `myAssembly` и `display` разработчик может предоставить имя частичной сборки, например `uninstall`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-161">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="4a3fa-162">В командной строке программы Ngen.exe может быть указана только одна сборка.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-162">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="4a3fa-163">Явный путь для сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-163">The explicit path of the assembly.</span></span> <span data-ttu-id="4a3fa-164">Можно указать полный или относительный путь.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-164">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="4a3fa-165">Если имя файла задано без пути, сборка должна находиться в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-165">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="4a3fa-166">В командной строке программы Ngen.exe может быть указана только одна сборка.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-166">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="4a3fa-167">Уровни приоритета</span><span class="sxs-lookup"><span data-stu-id="4a3fa-167">Priority Levels</span></span>

|<span data-ttu-id="4a3fa-168">Приоритет</span><span class="sxs-lookup"><span data-stu-id="4a3fa-168">Priority</span></span>|<span data-ttu-id="4a3fa-169">Описание</span><span class="sxs-lookup"><span data-stu-id="4a3fa-169">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="4a3fa-170">Образы в машинном коде создаются и устанавливаются немедленно, не дожидаясь периода простоя.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-170">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="4a3fa-171">Образы в машинном коде генерируются и устанавливаются, не дожидаясь периода простоя, но после завершения всех действий и их зависимостей действий с приоритетом 1.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-171">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="4a3fa-172">Образы в машинном коде устанавливаются, когда служба образов в машинном коде обнаружит, что компьютер находится в режиме простоя.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-172">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="4a3fa-173">См. раздел [Служба образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-173">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="4a3fa-174">Сценарии</span><span class="sxs-lookup"><span data-stu-id="4a3fa-174">Scenarios</span></span>

|<span data-ttu-id="4a3fa-175">Сценарий</span><span class="sxs-lookup"><span data-stu-id="4a3fa-175">Scenario</span></span>|<span data-ttu-id="4a3fa-176">Описание</span><span class="sxs-lookup"><span data-stu-id="4a3fa-176">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="4a3fa-177">Создает образы в машинном коде, которые можно использовать с отладчиком.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-177">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="4a3fa-178">Создает образы в машинном коде, которые можно использовать с профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-178">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="4a3fa-179">Создает минимальное число образов в машинном коде, которое требуется в соответствии с параметрами конкретного сценария.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-179">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="4a3fa-180">Config</span><span class="sxs-lookup"><span data-stu-id="4a3fa-180">Config</span></span>

|<span data-ttu-id="4a3fa-181">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="4a3fa-181">Configuration</span></span>|<span data-ttu-id="4a3fa-182">Описание</span><span class="sxs-lookup"><span data-stu-id="4a3fa-182">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="4a3fa-183">`/ExeConfig:` `exePath`</span><span class="sxs-lookup"><span data-stu-id="4a3fa-183">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="4a3fa-184">Используется конфигурация указанной исполняемой сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-184">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="4a3fa-185">При привязке к зависимостям программа Ngen.exe должна принимать те же решения, что и загрузчик.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-185">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="4a3fa-186">Когда общий компонент загружается во время выполнения с помощью метода <xref:System.Reflection.Assembly.Load%2A>, файл конфигурации приложения определяет зависимости, загруженные для общего компонента, например версию загруженной зависимости.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-186">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="4a3fa-187">Ключ `/ExeConfig` указывает программе Ngen.exe, какие зависимости будут загружаться во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-187">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|<span data-ttu-id="4a3fa-188">`/AppBase:` `directoryPath`</span><span class="sxs-lookup"><span data-stu-id="4a3fa-188">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="4a3fa-189">При обнаружении зависимостей используйте указанный каталог в качестве базовой папки приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-189">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="4a3fa-190">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a3fa-190">Options</span></span>

|<span data-ttu-id="4a3fa-191">Параметр</span><span class="sxs-lookup"><span data-stu-id="4a3fa-191">Option</span></span>|<span data-ttu-id="4a3fa-192">Описание:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-192">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="4a3fa-193">Отключает загрузочный баннер корпорации Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-193">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="4a3fa-194">Отключает отображение сообщений об успешно выполненных операциях.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-194">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="4a3fa-195">Отображает подробные сведения для отладки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-195">Display detailed information for debugging.</span></span> <span data-ttu-id="4a3fa-196">**Примечание.**  Из-за ограничений операционных систем Windows 98 и Windows Millennium Edition этот параметр отображает намного меньше сведений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-196">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|
|<span data-ttu-id="4a3fa-197">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="4a3fa-197">`/help`, `/?`</span></span>|<span data-ttu-id="4a3fa-198">Отображает синтаксис команды и параметры для текущего выпуска.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-198">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a3fa-199">Примечания</span><span class="sxs-lookup"><span data-stu-id="4a3fa-199">Remarks</span></span>

<span data-ttu-id="4a3fa-200">Для запуска Ngen.exe требуются права администратора.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-200">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="4a3fa-201">Не запускайте программу NGen.exe в сборках с неполным доверием.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-201">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="4a3fa-202">Начиная с .NET Framework 4, программа NGen.exe компилирует сборки с полным доверием, а политика управления доступом для кода (CAS) больше не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-202">Starting with the .NET Framework 4, Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="4a3fa-203">Начиная с .NET Framework 4 образы в машинном коде, созданные с помощью NGen.exe, нельзя загружать в приложения, выполняющиеся в режиме частичного доверия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-203">Starting with the .NET Framework 4, the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="4a3fa-204">Вместо этого вызывается JIT-компилятор.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-204">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="4a3fa-205">Программа Ngen.exe создает образы в машинном коде для сборки, указанной аргументом `assemblyname`, для действия `install` и всех его зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-205">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="4a3fa-206">Зависимости определяются по ссылкам в манифесте сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-206">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="4a3fa-207">Единственный сценарий, в котором необходимо задавать зависимость отдельно, — это когда приложение загружает зависимость с помощью отражения, например путем вызова метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-207">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a3fa-208">Не используйте метод <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> с образами в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-208">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="4a3fa-209">Образ, загруженный этим методом, не может использоваться другими сборками в контексте выполнения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-209">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="4a3fa-210">Программа Ngen.exe ведет подсчет зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-210">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="4a3fa-211">Например, пусть и `MyAssembly.exe` и `YourAssembly.exe` установлены в кэше образов в машинном коде и содержат ссылки на `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-211">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="4a3fa-212">При удалении `MyAssembly.exe` библиотека `OurDependency.dll` не удаляется.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-212">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="4a3fa-213">Она удаляется только после удаления `YourAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-213">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="4a3fa-214">При создании образа в машинном коде для сборки из глобального кэша сборок необходимо указать ее отображаемое имя.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-214">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="4a3fa-215">См. раздел <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-215">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4a3fa-216">Образы в машинном коде, созданные программой Ngen.exe, могут совместно использоваться в доменах приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-216">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="4a3fa-217">Это означает, что программу Ngen.exe можно использовать в сценариях приложений, требующих совместного использования сборок в доменах приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-217">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="4a3fa-218">Чтобы определить независимость от домена, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-218">To specify domain neutrality:</span></span>

- <span data-ttu-id="4a3fa-219">Примените к своему приложению атрибут <xref:System.LoaderOptimizationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-219">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="4a3fa-220">При создании сведений о настройке для нового домена приложений задайте свойство <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-220">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="4a3fa-221">При загрузке одной и той же сборки в несколько доменов приложений всегда используйте программный код, независимый от домена.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-221">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="4a3fa-222">Если образ в машинном коде, загруженный в общий домен приложения, загружается в неиспользуемый совместно домен, его использование невозможно.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-222">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-223">Независимый от домена код не может быть выгружен, и быстродействие может слегка снизиться, особенно при доступе к статическим членам.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-223">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="4a3fa-224">В этом разделе примечаний</span><span class="sxs-lookup"><span data-stu-id="4a3fa-224">In this Remarks section:</span></span>

- [<span data-ttu-id="4a3fa-225">Формирование образов для различных сценариев</span><span class="sxs-lookup"><span data-stu-id="4a3fa-225">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="4a3fa-226">Определение случаев использования образов в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-226">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="4a3fa-227">Оптимизация использования памяти</span><span class="sxs-lookup"><span data-stu-id="4a3fa-227">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="4a3fa-228">Ускорение запуска приложения</span><span class="sxs-lookup"><span data-stu-id="4a3fa-228">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="4a3fa-229">Обзор аспектов использования</span><span class="sxs-lookup"><span data-stu-id="4a3fa-229">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="4a3fa-230">Важность базовых адресов сборок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-230">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="4a3fa-231">Жесткая привязка</span><span class="sxs-lookup"><span data-stu-id="4a3fa-231">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="4a3fa-232">Задание для зависимости подсказки, касающейся привязки</span><span class="sxs-lookup"><span data-stu-id="4a3fa-232">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="4a3fa-233">Задание для сборки подсказки для привязки по умолчанию</span><span class="sxs-lookup"><span data-stu-id="4a3fa-233">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="4a3fa-234">Отложенная обработка</span><span class="sxs-lookup"><span data-stu-id="4a3fa-234">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="4a3fa-235">Образы в машинном коде и JIT-компиляция</span><span class="sxs-lookup"><span data-stu-id="4a3fa-235">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="4a3fa-236">Недействительные образы</span><span class="sxs-lookup"><span data-stu-id="4a3fa-236">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="4a3fa-237">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-237">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="4a3fa-238">Средство просмотра журнала привязки сборок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-238">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="4a3fa-239">Помощник по отладке управляемого кода JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="4a3fa-239">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="4a3fa-240">Отказ от формирования образа в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-240">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="4a3fa-241">Формирование образов для различных сценариев</span><span class="sxs-lookup"><span data-stu-id="4a3fa-241">Generating images for     different scenarios</span></span>

<span data-ttu-id="4a3fa-242">После создания образа в машинном коде для сборки среда выполнения автоматически пытается обнаружить и использовать этот образ в машинном коде при каждом запуске сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-242">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="4a3fa-243">В зависимости от сценариев использования может быть создано несколько образов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-243">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="4a3fa-244">Например, при запуске сборки в рамках сценария отладки или профилирования среда выполнения ищет образ в машинном коде, созданный с параметрами `/Debug` или `/Profile`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-244">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="4a3fa-245">Если найти соответствующий образ в машинном коде не удается, среда выполнения возвращается к стандартной схеме JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-245">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="4a3fa-246">Единственным способом отладки образов в машинном коде является создание образа в машинном коде с параметром `/Debug`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-246">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="4a3fa-247">Действие `uninstall` также распознает сценарии, позволяя удалить все или только выбранные сценарии.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-247">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="4a3fa-248">Определение случаев использования образов в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-248">Determining when to Use native images</span></span>

<span data-ttu-id="4a3fa-249">Образы в машинном коде могут повысить производительность в двух областях: оптимизация использования памяти и уменьшение времени запуска.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-249">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-250">Производительность образов в машинном коде зависит от множества факторов, усложняющих анализ, например: шаблоны доступа к коду и данным, количество вызовов, выполняемых через границы модуля, и количество зависимостей, уже загруженных другими приложениями.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-250">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="4a3fa-251">Единственным способом определить, обеспечивают ли образы в машинном коде преимущество для конкретного приложения, являются тщательные измерения производительности в основных сценариях развертывания.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-251">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="4a3fa-252">Оптимизация использования памяти</span><span class="sxs-lookup"><span data-stu-id="4a3fa-252">Improved memory use</span></span>

<span data-ttu-id="4a3fa-253">Использование образов в машинном коде может заметно повысить эффективность использования памяти в ситуациях, когда код используется одновременно несколькими процессами.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-253">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="4a3fa-254">Образы в машинном коде являются файлами Windows PE, поэтому несколько процессов могут совместно использовать одну копию DLL-файла. Напротив, образ в машинном коде, созданный JIT-компилятором, хранится в выделенной памяти и не может быть использован совместно.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-254">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="4a3fa-255">Преимущества совместно используемых кодовых страниц также распространяются на приложения, выполняемые с использованием служб терминалов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-255">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="4a3fa-256">Кроме того, отсутствие необходимости загружать JIT-компилятор экономит определенный объем памяти для каждого экземпляра приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-256">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="4a3fa-257">Ускорение запуска приложения</span><span class="sxs-lookup"><span data-stu-id="4a3fa-257">Faster application startup</span></span>

<span data-ttu-id="4a3fa-258">Предварительная компиляция сборок с помощью программы Ngen.exe может уменьшить время запуска некоторых приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-258">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="4a3fa-259">В общем случае, преимущество достигается благодаря тому, что приложения совместно используют сборки компонентов, так как после запуска первого приложения общие компоненты оказываются уже загруженными в память для последующих приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-259">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="4a3fa-260">При холодном запуске, когда все сборки в приложении должны загружаться с жесткого диска, использование образов в машинном коде не обеспечивает таких преимуществ, поскольку основное значение имеет время доступа к жесткому диску.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-260">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="4a3fa-261">На время запуска может повлиять жесткая привязка, поскольку все образы, жестко привязанные к главной сборке приложения, должны загружаться в одно и то же время.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-261">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-262">До .NET Framework 3.5 с пакетом обновления 1 (SP1) необходимо было помещать общие компоненты со строгими именами в глобальный кэш сборок, так как загрузчик выполняет дополнительную проверку сборок со строгими именами, отсутствующих в глобальном кэше сборок, фактически сводя на нет уменьшение времени запуска, создаваемое за счет использования образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-262">Before the .NET Framework 3.5 Service Pack 1, you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="4a3fa-263">За счет ряда усовершенствований, которые впервые появились в NET Framework 3.5 SP1, была исключена дополнительная проверка.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-263">Optimizations that were introduced in the .NET Framework 3.5 SP1 removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="4a3fa-264">Обзор аспектов использования</span><span class="sxs-lookup"><span data-stu-id="4a3fa-264">Summary of usage considerations</span></span>

<span data-ttu-id="4a3fa-265">Следующие общие положения и аспекты использования приложений могут помочь принять решение, следует ли тратить ресурсы на оценку применения образов в машинном коде для разрабатываемого приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-265">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="4a3fa-266">Образы в машинном коде загружаются быстрее чем CIL, поскольку они не требуют множества операций запуска, таких как JIT-компиляция и проверка безопасности типа.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-266">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="4a3fa-267">За счет устранения JIT-компилятора из процесса разработки образы в машинном коде требуют меньшего первоначального объема работы.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-267">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="4a3fa-268">Образы в машинном коде обеспечивают совместное использование кода несколькими процессами.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-268">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="4a3fa-269">Образам в машинном коде требуется больше места на жестком диске по сравнению со сборками CIL. Кроме того, их создание может занимать значительное время.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-269">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="4a3fa-270">Образы в машинном коде необходимо обслуживать.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-270">Native images must be maintained.</span></span>

  - <span data-ttu-id="4a3fa-271">При обслуживании исходной сборки или одной из ее зависимостей образы необходимо создавать заново.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-271">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="4a3fa-272">Для одной сборки может понадобиться несколько образов в машинном коде, используемых в различных приложениях или различных сценариях.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-272">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="4a3fa-273">Например, сведения о конфигурации в двух приложениях могут привести к различным решениям привязки для одной и той же зависимой сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-273">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="4a3fa-274">Образы в машинном коде должны создаваться администратором, то есть под учетной записью Windows в группе "Администраторы".</span><span class="sxs-lookup"><span data-stu-id="4a3fa-274">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="4a3fa-275">Помимо этих общих положений, при рассмотрении преимуществ использования образов в машинном коде с точки зрения производительности необходимо учитывать суть разрабатываемого приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-275">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="4a3fa-276">Если приложение выполняется в среде, в которой используется множество общих компонентов, образы в машинном коде обеспечивают совместное использование компонентов несколькими процессами.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-276">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="4a3fa-277">Если приложение использует несколько доменов приложений, образы в машинном коде обеспечивают совместное использование кодовых страниц в нескольких доменах.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-277">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4a3fa-278">В .NET Framework версий 1.0 и 1.1 совместное использование образов в машинном коде в нескольких доменах приложений невозможно.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-278">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="4a3fa-279">Однако в версии 2.0 и более поздних версиях ситуация изменилась.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-279">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="4a3fa-280">Если приложение работает в среде сервера терминалов, образы в машинном коде обеспечивают совместное использование кодовых страниц.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-280">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="4a3fa-281">При компиляции в образы в машинном коде большие приложения обычно получают ряд преимуществ.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-281">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="4a3fa-282">В свою очередь, небольшие приложения особой выгоды обычно не получают.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-282">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="4a3fa-283">Для приложений с длительным сроком выполнения JIT-компиляция во время выполнения обеспечивает немного лучшую производительность, чем образы в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-283">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="4a3fa-284">(Жесткая привязка может в определенной степени уменьшить эту разницу в производительности.)</span><span class="sxs-lookup"><span data-stu-id="4a3fa-284">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="4a3fa-285">Важность базовых адресов сборок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-285">Importance of assembly base addresses</span></span>

<span data-ttu-id="4a3fa-286">Поскольку образы в машинном коде являются файлами Windows PE, они подвержены тем же проблемам изменения базовых адресов, что и другие исполняемые файлы.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-286">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="4a3fa-287">При использовании жесткой привязки влияние перемещения на производительность становится еще более заметным.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-287">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="4a3fa-288">Чтобы задать базовый адрес для образа в машинном коде, с помощью соответствующего параметра компилятора можно задать базовый адрес сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-288">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="4a3fa-289">Программа Ngen.exe использует этот базовый адрес для образа в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-289">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-290">Образы в машинном коде по размеру больше управляемых сборок, используемых для их создания.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-290">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="4a3fa-291">Базовые адреса должны быть рассчитаны с учетом таких увеличенных размеров.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-291">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="4a3fa-292">Для просмотра предпочитаемого базового адреса образа в машинном коде можно использовать такую программу, как dumpbin.exe.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-292">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="4a3fa-293">Жесткая привязка</span><span class="sxs-lookup"><span data-stu-id="4a3fa-293">Hard binding</span></span>

<span data-ttu-id="4a3fa-294">Жесткая привязка увеличивает производительность и уменьшает объем работы для образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-294">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="4a3fa-295">Недостаток жесткой привязки состоит в том, что при загрузке сборки должны загружаться все образы, жестко привязанные к сборке.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-295">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="4a3fa-296">Для большого приложения это может заметно увеличить время запуска.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-296">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="4a3fa-297">Жесткая привязка подходит для зависимостей, загруженных во всех сценариях приложения, критичных для производительности.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-297">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="4a3fa-298">Как и для других аспектов использования образов в машинном коде, единственным способом определить, повышает ли жесткая привязка производительность приложения, являются тщательные измерения производительности.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-298">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="4a3fa-299">Атрибуты <xref:System.Runtime.CompilerServices.DependencyAttribute> и <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> позволяют предоставить программе Ngen.exe подсказки, касающиеся жесткой привязки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-299">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-300">Эти атрибуты являются подсказками для программы Ngen.exe, а не командами.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-300">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="4a3fa-301">Их использование не гарантирует выполнения жесткой привязки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-301">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="4a3fa-302">В будущих выпусках значение этих атрибутов может измениться.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-302">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="4a3fa-303">Задание для зависимости подсказки, касающейся привязки</span><span class="sxs-lookup"><span data-stu-id="4a3fa-303">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="4a3fa-304">Примените атрибут <xref:System.Runtime.CompilerServices.DependencyAttribute> к сборке, чтобы указать вероятность того, что указанная зависимость будет загружаться.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-304">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="4a3fa-305"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> указывает, что жесткая привязка подходит, <xref:System.Runtime.CompilerServices.LoadHint.Default> указывает, что для зависимости должно использоваться значение по умолчанию, и <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> указывает, что жесткая привязка не подходит.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-305"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="4a3fa-306">В следующем коде показаны атрибуты для сборки с двумя зависимостями.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-306">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="4a3fa-307">Первая зависимость (Assembly1) является подходящим кандидатом для жесткой привязки, а вторая (Assembly2) — нет.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-307">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

<span data-ttu-id="4a3fa-308">Имя сборки не включает в себя расширение имени файла.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-308">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="4a3fa-309">Разрешается использовать отображаемые имена.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-309">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="4a3fa-310">Задание для сборки подсказки для привязки по умолчанию</span><span class="sxs-lookup"><span data-stu-id="4a3fa-310">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="4a3fa-311">Подсказки для привязки по умолчанию необходимы только для сборок, которые будут использоваться немедленно и часто любым приложением, связанным с этими сборками зависимостями.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-311">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="4a3fa-312">Чтобы определить необходимость использования жесткой привязки, к таким сборкам можно применить атрибут <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> с <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-312">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-313">Не стоит применять атрибут <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> к DLL-сборкам, не подпадающим под эту категорию, поскольку применение атрибута с любым значением, отличным от <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>, аналогично полному отсутствию атрибута.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-313">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="4a3fa-314">Корпорация Майкрософт использует атрибут <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> для указания того, что жесткая привязка является значением по умолчанию для очень небольшого числа сборок в .NET Framework, например "mscorlib.dll".</span><span class="sxs-lookup"><span data-stu-id="4a3fa-314">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="4a3fa-315">Отложенная обработка</span><span class="sxs-lookup"><span data-stu-id="4a3fa-315">Deferred processing</span></span>

<span data-ttu-id="4a3fa-316">Создание образов в машинном коде для очень большого приложения может занять значительное время.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-316">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="4a3fa-317">Аналогичным образом, изменения общего компонента или настроек компьютера могут потребовать обновления многих образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-317">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="4a3fa-318">Для действий `install` и `update` предусмотрен параметр `/queue`, который помещает операцию в очередь для отложенного выполнения службой образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-318">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="4a3fa-319">Кроме того, программа Ngen.exe предусматривает действия `queue` и `executeQueuedItems`, которые дают определенные возможности управления этой службой.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-319">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="4a3fa-320">Подробнее см. в разделе [Служба образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-320">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="4a3fa-321">Образы в машинном коде и JIT-компиляция</span><span class="sxs-lookup"><span data-stu-id="4a3fa-321">Native images and JIT compilation</span></span>

<span data-ttu-id="4a3fa-322">Если программа Ngen.exe обнаруживает в сборке методы, которые она не может создать, эти методы исключаются из этого образа.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-322">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="4a3fa-323">Когда среда выполнения выполняет сборку, то при обнаружении метода, отсутствующего в образе в машинном коде, выполняется JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-323">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="4a3fa-324">Кроме того, образы в машинном коде не используются, если сборка была модернизирована или по какой-либо причине стала недействительной.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-324">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="4a3fa-325">Недействительные образы</span><span class="sxs-lookup"><span data-stu-id="4a3fa-325">Invalid images</span></span>

<span data-ttu-id="4a3fa-326">При использовании программы Ngen.exe для создания образа сборки в машинном коде результат зависит от заданных параметров командной строки и определенных настроек компьютера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-326">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="4a3fa-327">В число этих параметров входят следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-327">These settings include the following:</span></span>

- <span data-ttu-id="4a3fa-328">Версия .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-328">The version of the .NET Framework.</span></span>

- <span data-ttu-id="4a3fa-329">Версия операционной системы в случае перехода с семейства Windows 9x на семейство Windows NT.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-329">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

- <span data-ttu-id="4a3fa-330">Полное удостоверение сборки (оно изменяется при перекомпиляции).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-330">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="4a3fa-331">Полное удостоверение всех сборок, на которые ссылается данная сборка (оно изменяется при перекомпиляции).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-331">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="4a3fa-332">Факторы безопасности.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-332">Security factors.</span></span>

<span data-ttu-id="4a3fa-333">Программа Ngen.exe сохраняет эти сведения при создании образа в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-333">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="4a3fa-334">При выполнении сборки среда выполнения просматривает созданный образ в машинном коде на предмет таких параметров и сравнивает их с текущими параметрами среды компьютера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-334">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="4a3fa-335">Если среда выполнения не находит соответствующий образ в машинном коде, выполняется JIT-компиляция.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-335">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="4a3fa-336">Изменения следующих параметров компьютера и среды приводят к тому, что образы устаревают, то есть становятся непригодными для использования.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-336">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="4a3fa-337">Версия .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-337">The version of the .NET Framework.</span></span>

     <span data-ttu-id="4a3fa-338">При обновлении .NET Framework все образы в машинном коде, созданные с помощью программы Ngen.exe, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-338">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="4a3fa-339">По этой причине, чтобы гарантировать повторное создание всех образов в машинном коде, все обновления .NET Framework выполняют команду `Ngen Update`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-339">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="4a3fa-340">Платформа .NET Framework автоматически создает новые образы в машинном коде для библиотек .NET Framework, которые она устанавливает.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-340">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="4a3fa-341">Версия операционной системы в случае перехода с семейства Windows 9x на семейство Windows NT.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-341">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

     <span data-ttu-id="4a3fa-342">Например, при изменении версии операционной системы компьютера с Windows 98 на Windows XP все образы в машинном коде, хранящиеся в кэше образов в машинном коде, становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-342">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="4a3fa-343">Тем не менее при изменении версии операционной системы с Windows 2000 на Windows XP образы остаются действительными.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-343">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>

- <span data-ttu-id="4a3fa-344">Полное удостоверение сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-344">The exact identity of the assembly.</span></span>

     <span data-ttu-id="4a3fa-345">При перекомпиляции сборки соответствующий образ в машинном коде устаревает.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-345">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="4a3fa-346">Полное удостоверение всех сборок, на которые ссылается данная сборка.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-346">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="4a3fa-347">При обновлении управляемой сборки все образы в машинном коде, прямо или косвенно зависящие от этой сборки, становятся недействительными и требуют повторного создания.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-347">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="4a3fa-348">Это относится и к обычным ссылкам, и к зависимостям с жесткой привязкой.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-348">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="4a3fa-349">При любом обновлении программного обеспечения программа установки должна выполнить команду `Ngen Update`, чтобы гарантировать повторное создание всех зависимых образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-349">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="4a3fa-350">Факторы безопасности.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-350">Security factors.</span></span>

     <span data-ttu-id="4a3fa-351">Изменение политики безопасности на компьютере, сопровождающееся отменой разрешений, выданных сборке ранее, может привести к устареванию ранее скомпилированного образа сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-351">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="4a3fa-352">Подробную информацию об управлении доступом для кода в среде CLR и об использовании разрешений см. в разделе [Управление доступом для кода](../misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-352">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="4a3fa-353">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-353">Troubleshooting</span></span>

<span data-ttu-id="4a3fa-354">Следующие разделы по устранению неполадок позволяют понять, какие образы в машинном коде используются, а какие — не могут использоваться для вашего приложения, определить, когда JIT-компилятор начинает компиляцию метода, а также демонстрируют, как отказаться от компиляции образов в машинном коде указанных методов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-354">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="4a3fa-355">средство просмотра журнала привязки сборок</span><span class="sxs-lookup"><span data-stu-id="4a3fa-355">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="4a3fa-356">Проверить, используются ли в приложении образы в машинном коде, можно с помощью [Fuslogvw.exe (средства просмотра журнала привязок сборки)](fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-356">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="4a3fa-357">Выберите **Образы в машинном коде** в поле **Категории журнала** в окне средства просмотра журнала привязок.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-357">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="4a3fa-358">Программа Fuslogvw.exe предоставляет сведения о причинах отклонения образа в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-358">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="4a3fa-359">Помощник по отладке управляемого кода JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="4a3fa-359">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="4a3fa-360">Чтобы определить, когда JIT-компилятор начинает компиляцию функции, можно использовать помощник по отладке управляемого кода [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-360">You can use the [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="4a3fa-361">Отказ от формирования образа в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-361">Opting out of native image generation</span></span>

<span data-ttu-id="4a3fa-362">В некоторых случаях NGen.exe может испытывать трудности при создании образа в машинном коде для конкретного метода. Кроме того, может быть удобнее выполнить JIT-компиляцию метода вместо компиляции в образ в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-362">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="4a3fa-363">В этом случае можно использовать атрибут `System.Runtime.BypassNGenAttribute`, чтобы запретить программе NGen.exe формирование образа в машинном коде для конкретного метода.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-363">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="4a3fa-364">Атрибут необходимо применять по отдельности к каждому методу, код которого не нужно включать в образ в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-364">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="4a3fa-365">NGen.exe распознает атрибут и не создает код в образе в машинном коде для соответствующего метода.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-365">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="4a3fa-366">Тем не менее обратите внимание, что `BypassNGenAttribute` не определен как тип в библиотеке классов .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-366">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="4a3fa-367">Для использования атрибута в коде, его необходимо сначала определить следующим образом.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-367">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="4a3fa-368">Затем можно применить атрибут индивидуально для каждого метода.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-368">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="4a3fa-369">Следующий пример указывает генератору образов в машинном коде, что ему не следует формировать образ в машинном коде для метода `ExampleClass.ToJITCompile`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-369">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="4a3fa-370">Примеры</span><span class="sxs-lookup"><span data-stu-id="4a3fa-370">Examples</span></span>

<span data-ttu-id="4a3fa-371">Следующая команда создает образ в машинном коде для приложения `ClientApp.exe`, расположенного в текущем каталоге, и устанавливает образ в кэш образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-371">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="4a3fa-372">Если для сборки существует файл конфигурации, программа Ngen.exe использует его.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-372">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="4a3fa-373">Кроме того, образы в машинном коде создаются для всех DLL-файлов, на которые ссылается программа `ClientApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-373">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```console
ngen install ClientApp.exe
```

<span data-ttu-id="4a3fa-374">Образ, установленный с программой Ngen.exe, также называется корнем.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-374">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="4a3fa-375">Корень может быть приложением или общим компонентом.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-375">A root can be an application or a shared component.</span></span>

<span data-ttu-id="4a3fa-376">Следующая команда создает образ в машинном коде для `MyAssembly.exe` с указанным путем.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-376">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```console
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="4a3fa-377">При поиске сборок и их зависимостей программа Ngen.exe использует ту же самую логику тестирования, что и среда CLR.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-377">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="4a3fa-378">По умолчанию каталог, содержащий приложение `ClientApp.exe`, используется в качестве базового каталога приложения, с которого начинается тестирование всех сборок.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-378">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="4a3fa-379">Это поведение можно переопределить с помощью параметра `/AppBase`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-379">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-380">Поведение программы Ngen.exe было изменено по сравнению с .NET Framework версий 1.0 и 1.1, где в качестве базового каталога приложения использовался текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-380">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="4a3fa-381">Сборка может использовать зависимость без ссылки, например, если она загружает DLL-файл с помощью метода <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-381">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4a3fa-382">С помощью параметра `/ExeConfig` для такого DLL-файла можно создать образ в машинном коде, используя сведения о конфигурации для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-382">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="4a3fa-383">Следующая команда создает образ в машинном коде для `MyLib.dll,`, используя сведения о конфигурации из `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-383">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="4a3fa-384">Сборки, установленные таким способом, не удаляются при удалении приложения.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-384">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="4a3fa-385">Чтобы удалить зависимость, следует использовать те же параметры командной строки, которые использовались при ее установке.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-385">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="4a3fa-386">Следующая команда удаляет `MyLib.dll` из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-386">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="4a3fa-387">Чтобы создать образ в машинном коде для сборки в глобальном кэше сборок, следует использовать отображаемое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-387">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="4a3fa-388">Пример:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-388">For example:</span></span>

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="4a3fa-389">Программа NGen.exe создает отдельный набор образов для каждого устанавливаемого сценария.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-389">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="4a3fa-390">Например, следующие команды устанавливают полный набор образов в машинном коде для обычной работы, другой полный набор для отладки, а третий — для профилирования.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-390">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="4a3fa-391">Отображение кэша образов в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-391">Displaying the Native Image Cache</span></span>

<span data-ttu-id="4a3fa-392">Образы в машинном коде, установленные в кэш, можно отобразить с помощью программы Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-392">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="4a3fa-393">Следующая команда отображает все образы в машинном коде, находящиеся в кэше образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-393">The following command displays all native images in the native image cache.</span></span>

```console
ngen display
```

<span data-ttu-id="4a3fa-394">Действие `display` выводит сначала все корневые сборки, а затем выводит список всех образов в машинном коде на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-394">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="4a3fa-395">Чтобы отобразить сведения только об этой сборке, можно использовать простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-395">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="4a3fa-396">Следующая команда выводит все образы в кэше образов в машинном коде, соответствующие неполному имени `MyAssembly`, их зависимости и все корни с зависимостями от `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-396">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```console
ngen display MyAssembly
```

<span data-ttu-id="4a3fa-397">Знание того, что корни зависят от общей сборки компонентов, полезно при определении влияния действия `update` после обновления общего компонента.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-397">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="4a3fa-398">Если задано расширение файла сборки, необходимо либо указать путь, либо выполнить программу Ngen.exe из каталога, в котором находится сборка.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-398">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```console
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="4a3fa-399">Следующая команда выводит все образы в машинном коде с именем `MyAssembly` и версией 1.0.0.0, содержащиеся в кэше образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-399">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="4a3fa-400">Обновление образов</span><span class="sxs-lookup"><span data-stu-id="4a3fa-400">Updating Images</span></span>

<span data-ttu-id="4a3fa-401">Образы обычно обновляются после обновления общего компонента.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-401">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="4a3fa-402">Для обновления всех образов в машинном коде, которые были изменены или для которых были изменены зависимости, используется действие `update` без аргументов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-402">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```console
ngen update
```

<span data-ttu-id="4a3fa-403">Обновление всех образов может занять длительное время.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-403">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="4a3fa-404">С помощью параметра `/queue` можно поставить обновления в очередь выполнения службы образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-404">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="4a3fa-405">Подробнее о параметре `/queue` и приоритетах установки см. в разделе [Служба образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-405">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```console
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="4a3fa-406">Удаление образов</span><span class="sxs-lookup"><span data-stu-id="4a3fa-406">Uninstalling Images</span></span>

<span data-ttu-id="4a3fa-407">Программа Ngen.exe поддерживает список зависимостей, поэтому общие компоненты удаляются, только когда удалены все сборки, зависимые от этих компонентов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-407">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="4a3fa-408">Кроме того, общий компонент не удаляется, если он установлен как корень.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-408">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="4a3fa-409">Следующая команда удаляет все сценарии для корня `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-409">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp
```

<span data-ttu-id="4a3fa-410">Удалить конкретные сценарии можно с помощью действия `uninstall`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-410">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="4a3fa-411">Следующая команда удаляет все сценарии отладки для `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-411">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="4a3fa-412">При удалении сценариев `/debug` не удаляется сценарий, включающий и `/profile`, и `/debug.`</span><span class="sxs-lookup"><span data-stu-id="4a3fa-412">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>

<span data-ttu-id="4a3fa-413">Следующая команда удаляет все сценарии для конкретной версии `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-413">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="4a3fa-414">Следующая команда удаляет все сценарии для `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` или только сценарий отладки для этой сборки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-414">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="4a3fa-415">Как и в случае действия `install`, предоставление расширения требует либо выполнения программы Ngen.exe из каталога, содержащего сборку, либо указания полного пути.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-415">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="4a3fa-416">Примеры, связанные со службой образов в машинном коде, см. в разделе [Служба образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-416">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="4a3fa-417">Задача образов в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-417">Native Image Task</span></span>

<span data-ttu-id="4a3fa-418">Задача образов в машинном коде — это задача Windows, которая создает и поддерживает образы в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-418">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="4a3fa-419">Задача образов в машинном коде автоматически создает и освобождает образы в машинном коде в поддерживаемых сценариях.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-419">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="4a3fa-420">Она также позволяет установщикам использовать программу [Ngen.exe (генератор образов в машинном коде)](ngen-exe-native-image-generator.md) для отложенного создания и обновления образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-420">It also enables installers to use [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="4a3fa-421">Задача образов в машинном коде регистрируется однократно для каждой архитектуры ЦП, поддерживаемой на компьютере, чтобы обеспечить компиляцию приложений для каждой целевой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-421">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="4a3fa-422">Имя задачи</span><span class="sxs-lookup"><span data-stu-id="4a3fa-422">Task name</span></span>|<span data-ttu-id="4a3fa-423">32-разрядный компьютер</span><span class="sxs-lookup"><span data-stu-id="4a3fa-423">32-bit computer</span></span>|<span data-ttu-id="4a3fa-424">64-разрядный компьютер</span><span class="sxs-lookup"><span data-stu-id="4a3fa-424">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="4a3fa-425">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="4a3fa-425">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="4a3fa-426">да</span><span class="sxs-lookup"><span data-stu-id="4a3fa-426">Yes</span></span>|<span data-ttu-id="4a3fa-427">да</span><span class="sxs-lookup"><span data-stu-id="4a3fa-427">Yes</span></span>|
|<span data-ttu-id="4a3fa-428">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="4a3fa-428">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="4a3fa-429">Нет</span><span class="sxs-lookup"><span data-stu-id="4a3fa-429">No</span></span>|<span data-ttu-id="4a3fa-430">Да</span><span class="sxs-lookup"><span data-stu-id="4a3fa-430">Yes</span></span>|

<span data-ttu-id="4a3fa-431">Задача образов в машинном коде доступна в .NET Framework 4.5 и более поздних версий при выполнении в ОС Windows 8 или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-431">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="4a3fa-432">В более ранних версиях Windows платформа .NET Framework использует [службу образов в машинном коде](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="4a3fa-432">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="4a3fa-433">Время жизни задачи</span><span class="sxs-lookup"><span data-stu-id="4a3fa-433">Task Lifetime</span></span>

<span data-ttu-id="4a3fa-434">Как правило, планировщик заданий Windows запускает задачу образов в машинном коде каждую ночь, когда компьютер бездействует.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-434">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="4a3fa-435">Задача проверяет любые отложенные действия, помещенные в очередь установщиками приложений, любые отложенные запросы на обновление образов в машинном коде и любые операции автоматического создания образов.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-435">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="4a3fa-436">Задача завершает невыполненные операции, а затем завершает работу.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-436">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="4a3fa-437">Если компьютер выводится из состояния бездействия во время выполнении задачи, она прерывается.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-437">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="4a3fa-438">Задачу образов в машинном коде можно также запустить вручную из интерфейса планировщика заданий или посредством вызовов NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-438">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="4a3fa-439">Если задача запускается одним из этих способов, ее выполнение продолжается при выводе компьютера из состояния бездействия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-439">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="4a3fa-440">Образам, созданным вручную с помощью NGen.exe, назначаются приоритеты, что обеспечивает предсказуемость поведения установщиков приложений.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-440">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="4a3fa-441">Служба образов в машинном коде</span><span class="sxs-lookup"><span data-stu-id="4a3fa-441">Native Image Service</span></span>

<span data-ttu-id="4a3fa-442">Служба образов в машинном коде — это служба Windows, которая создает и поддерживает образы в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-442">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="4a3fa-443">Она позволяет разработчикам откладывать установку и обновление образов в машинном коде и выполнять эти процедуры позже, когда компьютер простаивает.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-443">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="4a3fa-444">Как правило, служба образов в машинном коде запускается программой установки (установщиком) приложения или обновления.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-444">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="4a3fa-445">Для действий с приоритетом 3 служба выполняется во время простоя компьютера.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-445">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="4a3fa-446">Служба сохраняет свое состояние и может при необходимости возобновлять работу после перезагрузки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-446">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="4a3fa-447">Для нескольких компиляций образов может быть организована очередь.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-447">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="4a3fa-448">Служба также взаимодействует с командой Ngen.exe, выполняемой вручную.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-448">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="4a3fa-449">Команды, выполняемые вручную, имеют приоритет над фоновыми действиями.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-449">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="4a3fa-450">В операционной системе Windows Vista служба образов в машинном коде имеет имя "Microsoft.NET Framework NGEN v2.0.50727_X86" или "Microsoft.NET Framework NGEN v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="4a3fa-450">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="4a3fa-451">Во всех более ранних версиях Microsoft Windows ее имя — ".NET Runtime Optimization Service v2.0.50727_X86" или ".NET Runtime Optimization Service v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="4a3fa-451">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="4a3fa-452">Запуск отложенных операций</span><span class="sxs-lookup"><span data-stu-id="4a3fa-452">Launching Deferred Operations</span></span>

<span data-ttu-id="4a3fa-453">Перед началом установки или обновления рекомендуется приостановить службу.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-453">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="4a3fa-454">Это позволит заблокировать ее на время, пока установщик будет копировать файлы или помещать сборки в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-454">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="4a3fa-455">Для приостановки службы используется следующая командная строка Ngen.exe:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-455">The following Ngen.exe command line pauses the service:</span></span>

```console
ngen queue pause
```

<span data-ttu-id="4a3fa-456">После того как все отложенные операции поставлены в очередь, работу службы можно возобновить с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-456">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```console
ngen queue continue
```

<span data-ttu-id="4a3fa-457">Чтобы отложить создание образов в машинном коде при установке нового приложения или обновлении общего компонента, используйте параметр `/queue` с действием `install` или `update`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-457">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="4a3fa-458">Следующие командные строки Ngen.exe позволяют установить образ общего компонента в машинном коде и выполнить обновление всех корней, которых это может касаться:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-458">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```console
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="4a3fa-459">Действие `update` заново создает все образы в машинном коде, которые стали недействительными, а не только те, которые используют `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-459">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="4a3fa-460">Если в приложении слишком много корней, можно учитывать приоритеты отложенных действий.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-460">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="4a3fa-461">Приведенные ниже команды создают очередь для установки трех корней.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-461">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="4a3fa-462">Первой устанавливается сборка `Assembly1`, не дожидаясь периода бездействия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-462">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="4a3fa-463">Сборка `Assembly2` также устанавливается без ожидания бездействия, но после завершения всех действий с приоритетом 1.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-463">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="4a3fa-464">Сборка `Assembly3` устанавливается, когда служба обнаруживает, что компьютер бездействует.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-464">`Assembly3` is installed when the service detects that the computer is idle.</span></span>

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="4a3fa-465">Вы можете задать синхронное выполнение действий, находящихся в очереди, с помощью действия `executeQueuedItems`.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-465">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="4a3fa-466">Если задать необязательный приоритет, это действие затронет только те действия в очереди, которые имеют такой же или более низкий приоритет.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-466">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="4a3fa-467">По умолчанию подразумевается приоритет 3, поэтому следующая команда Ngen.exe обработает все действия в очереди немедленно и не вернет управление, пока они не закончатся:</span><span class="sxs-lookup"><span data-stu-id="4a3fa-467">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```console
ngen executeQueuedItems
```

<span data-ttu-id="4a3fa-468">Синхронные команды выполняются программой Ngen.exe и не используют службу образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-468">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="4a3fa-469">Можно выполнять действия с помощью Ngen.exe, пока служба образов в машинном коде работает.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-469">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="4a3fa-470">Завершение работы службы</span><span class="sxs-lookup"><span data-stu-id="4a3fa-470">Service Shutdown</span></span>

<span data-ttu-id="4a3fa-471">После того как служба инициирована выполнением команды Ngen.exe с параметром `/queue`, она продолжает работать в фоновом режиме, пока не будут завершены все действия.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-471">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="4a3fa-472">Служба сохраняет свое состояние и может при необходимости возобновлять работу после перезагрузки.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-472">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="4a3fa-473">Как только служба обнаруживает, что в очереди больше нет действий, она сбрасывает свое состояние, чтобы не запускаться повторно после очередной перезагрузки компьютера, и затем завершает работу.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-473">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="4a3fa-474">Взаимодействие службы с клиентами</span><span class="sxs-lookup"><span data-stu-id="4a3fa-474">Service Interaction with Clients</span></span>

<span data-ttu-id="4a3fa-475">В версии .NET Framework 2.0 взаимодействие со службой образов в машинном коде может осуществляться только через программу командной строки Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-475">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="4a3fa-476">Используйте эту программу в скриптах установки для управления очередями действий, выполняемых службой образов в машинном коде, и для взаимодействия с этой службой.</span><span class="sxs-lookup"><span data-stu-id="4a3fa-476">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a3fa-477">См. также</span><span class="sxs-lookup"><span data-stu-id="4a3fa-477">See also</span></span>

- [<span data-ttu-id="4a3fa-478">Инструменты</span><span class="sxs-lookup"><span data-stu-id="4a3fa-478">Tools</span></span>](index.md)
- [<span data-ttu-id="4a3fa-479">Процесс управляемого выполнения</span><span class="sxs-lookup"><span data-stu-id="4a3fa-479">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="4a3fa-480">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="4a3fa-480">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="4a3fa-481">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="4a3fa-481">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
