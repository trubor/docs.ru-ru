---
title: Параметры конфигурации сборщика мусора
description: Сведения о параметрах времени выполнения, определяющих, как сборщик мусора управляет памятью для приложений .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: c4f55124d9f50146ceac1eea52ce60b0dd77ad1d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875048"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="1c5a6-103">Параметры конфигурации времени выполнения для сборки мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="1c5a6-104">Эта страница содержит сведения о параметрах сборщика мусора (GC), которые можно изменить во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="1c5a6-105">Если вы пытаетесь добиться пиковой производительности запущенных приложений, рекомендуется использовать эти параметры.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="1c5a6-106">Однако значения по умолчанию обеспечивают оптимальную производительность для большинства приложений в типичных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="1c5a6-107">На этой странице параметры упорядочены по группам.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="1c5a6-108">Параметры в каждой группе обычно используются совместно друг с другом для достижения определенного результата.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="1c5a6-109">Эти параметры также могут динамически изменяться приложением во время его выполнения, поэтому любые заданные параметры времени выполнения могут быть переопределены.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="1c5a6-110">Некоторые параметры, такие как [уровень задержки](../../standard/garbage-collection/latency.md), обычно задаются только через API во время разработки.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="1c5a6-111">Такие параметры будут пропущены на этой странице.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="1c5a6-112">Для числовых значений используйте десятичную нотацию для параметров в файле *runtimeconfig.json* и шестнадцатеричную нотацию для параметров переменных среды.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="1c5a6-113">Шестнадцатеричные значения можно указать с помощью префикса "0x" или без него.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="1c5a6-114">Варианты сборки мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-114">Flavors of garbage collection</span></span>

<span data-ttu-id="1c5a6-115">Два основных варианта сборки мусора — это сборка мусора рабочей станции и сборка мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="1c5a6-116">Дополнительные сведения о различиях между этими двумя вариантами см. в статье [Сборка мусора рабочей станции и сборка мусора сервера](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="1c5a6-117">Подвиды сборки мусора представлены фоновым и непараллельным выполнением.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="1c5a6-118">Чтобы выбрать варианты сборки мусора, используйте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-118">Use the following settings to select flavors of garbage collection:</span></span>

- [<span data-ttu-id="1c5a6-119">Сборка мусора рабочей станции и сервера</span><span class="sxs-lookup"><span data-stu-id="1c5a6-119">Workstation vs. server GC</span></span>](#workstation-vs-server)
- [<span data-ttu-id="1c5a6-120">Фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-120">Background GC</span></span>](#background-gc)

### <a name="workstation-vs-server"></a><span data-ttu-id="1c5a6-121">Рабочая станция и сервер</span><span class="sxs-lookup"><span data-stu-id="1c5a6-121">Workstation vs. server</span></span>

- <span data-ttu-id="1c5a6-122">Указывает, использует ли приложение сборку мусора рабочей станции или сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-122">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="1c5a6-123">По умолчанию: сборка мусора рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-123">Default: Workstation garbage collection.</span></span> <span data-ttu-id="1c5a6-124">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-124">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="1c5a6-125">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-125">Setting name</span></span> | <span data-ttu-id="1c5a6-126">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-126">Values</span></span> | <span data-ttu-id="1c5a6-127">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-127">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-128">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="1c5a6-129">`false` — рабочая станция</span><span class="sxs-lookup"><span data-stu-id="1c5a6-129">`false` - workstation</span></span><br/><span data-ttu-id="1c5a6-130">`true` — сервер</span><span class="sxs-lookup"><span data-stu-id="1c5a6-130">`true` - server</span></span> | <span data-ttu-id="1c5a6-131">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-131">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-132">**Свойство MSBuild**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-132">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="1c5a6-133">`false` — рабочая станция</span><span class="sxs-lookup"><span data-stu-id="1c5a6-133">`false` - workstation</span></span><br/><span data-ttu-id="1c5a6-134">`true` — сервер</span><span class="sxs-lookup"><span data-stu-id="1c5a6-134">`true` - server</span></span> | <span data-ttu-id="1c5a6-135">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-135">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-136">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-136">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="1c5a6-137">`0` — рабочая станция</span><span class="sxs-lookup"><span data-stu-id="1c5a6-137">`0` - workstation</span></span><br/><span data-ttu-id="1c5a6-138">`1` — сервер</span><span class="sxs-lookup"><span data-stu-id="1c5a6-138">`1` - server</span></span> | <span data-ttu-id="1c5a6-139">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-139">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-140">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-140">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-141">GCServer</span><span class="sxs-lookup"><span data-stu-id="1c5a6-141">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="1c5a6-142">`false` — рабочая станция</span><span class="sxs-lookup"><span data-stu-id="1c5a6-142">`false` - workstation</span></span><br/><span data-ttu-id="1c5a6-143">`true` — сервер</span><span class="sxs-lookup"><span data-stu-id="1c5a6-143">`true` - server</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="1c5a6-144">Примеры</span><span class="sxs-lookup"><span data-stu-id="1c5a6-144">Examples</span></span>

<span data-ttu-id="1c5a6-145">Файл *runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-145">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="1c5a6-146">Файл проекта:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-146">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="background-gc"></a><span data-ttu-id="1c5a6-147">Фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-147">Background GC</span></span>

- <span data-ttu-id="1c5a6-148">Указывает, включена ли фоновая (параллельная) сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-148">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="1c5a6-149">По умолчанию: фоновая сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-149">Default: Use background GC.</span></span> <span data-ttu-id="1c5a6-150">Это эквивалентно присвоению значения `true`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-150">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="1c5a6-151">Дополнительные сведения см. в статье [Фоновая сборка мусора](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-151">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="1c5a6-152">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-152">Setting name</span></span> | <span data-ttu-id="1c5a6-153">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-153">Values</span></span> | <span data-ttu-id="1c5a6-154">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-154">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-155">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-155">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="1c5a6-156">`true` —фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-156">`true` - background GC</span></span><br/><span data-ttu-id="1c5a6-157">`false` — непараллельная сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="1c5a6-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-159">**Свойство MSBuild**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-159">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="1c5a6-160">`true` —фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-160">`true` - background GC</span></span><br/><span data-ttu-id="1c5a6-161">`false` — непараллельная сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="1c5a6-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-163">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-163">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="1c5a6-164">`1` —фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-164">`1` - background GC</span></span><br/><span data-ttu-id="1c5a6-165">`0` — непараллельная сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-165">`0` - non-concurrent GC</span></span> | <span data-ttu-id="1c5a6-166">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-166">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-167">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-167">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-168">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="1c5a6-168">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="1c5a6-169">`true` —фоновая сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-169">`true` - background GC</span></span><br/><span data-ttu-id="1c5a6-170">`false` — непараллельная сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-170">`false` - non-concurrent GC</span></span> |  |

#### <a name="examples"></a><span data-ttu-id="1c5a6-171">Примеры</span><span class="sxs-lookup"><span data-stu-id="1c5a6-171">Examples</span></span>

<span data-ttu-id="1c5a6-172">Файл *runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-172">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="1c5a6-173">Файл проекта:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-173">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="1c5a6-174">Управление использованием ресурсов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-174">Manage resource usage</span></span>

<span data-ttu-id="1c5a6-175">Используйте следующие параметры для управления использованием памяти и ЦП в сборщике мусора:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-175">Use the following settings to manage the garbage collector's memory and processor usage:</span></span>

- [<span data-ttu-id="1c5a6-176">Сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-176">Affinitize</span></span>](#affinitize)
- [<span data-ttu-id="1c5a6-177">Сходство маски</span><span class="sxs-lookup"><span data-stu-id="1c5a6-177">Affinitize mask</span></span>](#affinitize-mask)
- [<span data-ttu-id="1c5a6-178">Сходство диапазонов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-178">Affinitize ranges</span></span>](#affinitize-ranges)
- [<span data-ttu-id="1c5a6-179">Группы ЦП</span><span class="sxs-lookup"><span data-stu-id="1c5a6-179">CPU groups</span></span>](#cpu-groups)
- [<span data-ttu-id="1c5a6-180">Число куч</span><span class="sxs-lookup"><span data-stu-id="1c5a6-180">Heap count</span></span>](#heap-count)
- [<span data-ttu-id="1c5a6-181">Ограничение кучи</span><span class="sxs-lookup"><span data-stu-id="1c5a6-181">Heap limit</span></span>](#heap-limit)
- [<span data-ttu-id="1c5a6-182">Ограничение кучи в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-182">Heap limit percent</span></span>](#heap-limit-percent)
- [<span data-ttu-id="1c5a6-183">Потребление большого объема памяти в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-183">High memory percent</span></span>](#high-memory-percent)
- [<span data-ttu-id="1c5a6-184">Ограничения для отдельных куч объектов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-184">Per-object-heap limits</span></span>](#per-object-heap-limits)
- [<span data-ttu-id="1c5a6-185">Ограничения для отдельных куч объектов в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-185">Per-object-heap limit percents</span></span>](#per-object-heap-limit-percents)
- [<span data-ttu-id="1c5a6-186">Сохранение виртуальной машины</span><span class="sxs-lookup"><span data-stu-id="1c5a6-186">Retain VM</span></span>](#retain-vm)

<span data-ttu-id="1c5a6-187">Дополнительные сведения о некоторых из этих параметров см. в записи блога о [компромиссе между сборкой мусора рабочей станции и сервера](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-187">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="heap-count"></a><span data-ttu-id="1c5a6-188">Число куч</span><span class="sxs-lookup"><span data-stu-id="1c5a6-188">Heap count</span></span>

- <span data-ttu-id="1c5a6-189">Ограничивает число куч, создаваемых сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-189">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="1c5a6-190">Применяется только к сборке мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-190">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="1c5a6-191">Если включено [сходство процессоров сборки мусора](#affinitize), что используется по умолчанию, параметр счетчика куч реализует сходство `n` куч/потоков сборки мусора с первыми `n` процессорами.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-191">If [GC processor affinity](#affinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="1c5a6-192">(Используйте параметры [сходства маски](#affinitize-mask) или [сходства диапазонов](#affinitize-ranges), чтобы указать, для каких именно процессоров следует реализовать сходство.)</span><span class="sxs-lookup"><span data-stu-id="1c5a6-192">(Use the [affinitize mask](#affinitize-mask) or [affinitize ranges](#affinitize-ranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="1c5a6-193">Если [сходство процессоров сборки мусора](#affinitize) отключено, этот параметр будет ограничивать количество куч сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-193">If [GC processor affinity](#affinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="1c5a6-194">Дополнительные сведения см. в [примечаниях по GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-194">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="1c5a6-195">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-195">Setting name</span></span> | <span data-ttu-id="1c5a6-196">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-196">Values</span></span> | <span data-ttu-id="1c5a6-197">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-197">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-198">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-198">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="1c5a6-199">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-199">*decimal value*</span></span> | <span data-ttu-id="1c5a6-200">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-200">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-201">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-201">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="1c5a6-202">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-202">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-203">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-203">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-204">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-204">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-205">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="1c5a6-205">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="1c5a6-206">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-206">*decimal value*</span></span> | <span data-ttu-id="1c5a6-207">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c5a6-207">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="1c5a6-208">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-208">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="1c5a6-209">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-209">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-210">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-210">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-211">Например, чтобы ограничить число куч значением 16, для JSON-файла нужно указать 16, а для переменной среды — 0x10 или 10.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-211">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="affinitize-mask"></a><span data-ttu-id="1c5a6-212">Сходство маски</span><span class="sxs-lookup"><span data-stu-id="1c5a6-212">Affinitize mask</span></span>

- <span data-ttu-id="1c5a6-213">Указывает конкретные процессоры, которые должны использоваться потоками сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-213">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="1c5a6-214">Если [сходство процессоров](#affinitize) отключено, этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-214">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="1c5a6-215">Применяется только к сборке мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-215">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="1c5a6-216">Это значение представляет собой битовую маску, которая определяет доступные процессу процессоры.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-216">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="1c5a6-217">Например, десятичное значение 1023 (или шестнадцатеричное значение 0x3FF или 3FF, если вы используете переменную среды), равно 0011 1111 1111 в двоичной нотации.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-217">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="1c5a6-218">При этом будут использоваться первые 10 процессоров.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-218">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="1c5a6-219">Чтобы указать следующие 10 процессоров, то есть процессоры 10–19, задайте десятичное значение 1047552 (или шестнадцатеричное значение 0xFFC00 или FFC00), которое эквивалентно двоичному значению 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-219">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="1c5a6-220">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-220">Setting name</span></span> | <span data-ttu-id="1c5a6-221">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-221">Values</span></span> | <span data-ttu-id="1c5a6-222">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-222">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-223">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-223">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="1c5a6-224">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-224">*decimal value*</span></span> | <span data-ttu-id="1c5a6-225">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-225">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-226">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-226">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="1c5a6-227">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-227">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-228">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-228">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-229">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-229">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-230">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="1c5a6-230">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="1c5a6-231">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-231">*decimal value*</span></span> | <span data-ttu-id="1c5a6-232">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c5a6-232">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="1c5a6-233">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-233">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="affinitize-ranges"></a><span data-ttu-id="1c5a6-234">Сходство диапазонов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-234">Affinitize ranges</span></span>

- <span data-ttu-id="1c5a6-235">Указывает список процессоров, используемых для потоков сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-235">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="1c5a6-236">Этот параметр аналогичен [System.GC.HeapAffinitizeMask](#affinitize-mask), за исключением того, что он позволяет указать больше 64 процессоров.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-236">This setting is similar to [System.GC.HeapAffinitizeMask](#affinitize-mask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="1c5a6-237">Для операционных систем Windows добавьте к номеру или диапазону процессоров префикс в виде соответствующей [группы ЦП](/windows/win32/procthread/processor-groups), например "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="1c5a6-237">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="1c5a6-238">Если [сходство процессоров](#affinitize) отключено, этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-238">If [GC processor affinity](#affinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="1c5a6-239">Применяется только к сборке мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-239">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="1c5a6-240">Дополнительные сведения см. в записи об [улучшении конфигурации ЦП для сборки мусора на компьютерах, имеющих более 64 ЦП](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/), в блоге Майони Стивенс (Maoni Stephens).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-240">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="1c5a6-241">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-241">Setting name</span></span> | <span data-ttu-id="1c5a6-242">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-242">Values</span></span> | <span data-ttu-id="1c5a6-243">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-243">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-244">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-244">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="1c5a6-245">Разделенный запятыми список номеров процессоров или диапазонов номеров процессоров.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-245">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="1c5a6-246">Пример для Unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="1c5a6-246">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="1c5a6-247">Пример для Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="1c5a6-247">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="1c5a6-248">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-248">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-249">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-249">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="1c5a6-250">Разделенный запятыми список номеров процессоров или диапазонов номеров процессоров.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-250">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="1c5a6-251">Пример для Unix: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="1c5a6-251">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="1c5a6-252">Пример для Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="1c5a6-252">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="1c5a6-253">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-253">.NET Core 3.0</span></span> |

<span data-ttu-id="1c5a6-254">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-254">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="cpu-groups"></a><span data-ttu-id="1c5a6-255">Группы ЦП</span><span class="sxs-lookup"><span data-stu-id="1c5a6-255">CPU groups</span></span>

- <span data-ttu-id="1c5a6-256">Указывает, использует ли сборщик мусора [группы ЦП](/windows/win32/procthread/processor-groups).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-256">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="1c5a6-257">Когда 64-разрядный компьютер с Windows имеет несколько групп ЦП, то есть доступно более 64 процессоров, включение этого элемента расширяет действие сборки мусора на все группы ЦП.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-257">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="1c5a6-258">Сборщик мусора использует все ядра для создания и балансировки куч.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-258">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="1c5a6-259">Применяется только к сборке мусора сервера в 64-разрядных операционных системах Windows.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-259">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="1c5a6-260">По умолчанию: сборка мусора не распространяется на группы ЦП.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-260">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="1c5a6-261">Это эквивалентно присвоению значения `0`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-261">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="1c5a6-262">Дополнительные сведения см. в записи об [улучшении конфигурации ЦП для сборки мусора на компьютерах, имеющих более 64 ЦП](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/), в блоге Майони Стивенс (Maoni Stephens).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-262">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="1c5a6-263">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-263">Setting name</span></span> | <span data-ttu-id="1c5a6-264">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-264">Values</span></span> | <span data-ttu-id="1c5a6-265">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-265">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-266">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-266">**runtimeconfig.json**</span></span> | `System.GC.CpuGroup` | <span data-ttu-id="1c5a6-267">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-267">`0` - disabled</span></span><br/><span data-ttu-id="1c5a6-268">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-268">`1` - enabled</span></span> | <span data-ttu-id="1c5a6-269">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-269">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-270">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-270">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="1c5a6-271">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-271">`0` - disabled</span></span><br/><span data-ttu-id="1c5a6-272">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-272">`1` - enabled</span></span> | <span data-ttu-id="1c5a6-273">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-273">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-274">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-274">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-275">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="1c5a6-275">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="1c5a6-276">`false` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-276">`false` - disabled</span></span><br/><span data-ttu-id="1c5a6-277">`true` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-277">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="1c5a6-278">Чтобы настроить среду CLR для распределения потоков из пула потоков по всем группам ЦП, включите параметр [Элемент Thread_UseAllCpuGroups](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-278">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="1c5a6-279">Для приложений .NET Core этот параметр можно включить, задав для переменной среды `COMPlus_Thread_UseAllCpuGroups` значение `1`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-279">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="affinitize"></a><span data-ttu-id="1c5a6-280">Сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-280">Affinitize</span></span>

- <span data-ttu-id="1c5a6-281">Указывает, следует ли *реализовать сходство* потоков сборки мусора с процессорами.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-281">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="1c5a6-282">Реализация сходства потока сборки мусора означает, что он может выполняться только на определенном ЦП.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-282">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="1c5a6-283">Куча создается для каждого потока сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-283">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="1c5a6-284">Применяется только к сборке мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-284">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="1c5a6-285">По умолчанию: реализация сходства потоков сборки мусора с процессорами.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-285">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="1c5a6-286">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-286">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="1c5a6-287">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-287">Setting name</span></span> | <span data-ttu-id="1c5a6-288">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-288">Values</span></span> | <span data-ttu-id="1c5a6-289">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-289">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-290">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-290">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="1c5a6-291">`false` — реализовать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-291">`false` - affinitize</span></span><br/><span data-ttu-id="1c5a6-292">`true` — не реализовывать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-292">`true` - don't affinitize</span></span> | <span data-ttu-id="1c5a6-293">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-293">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-294">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-294">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="1c5a6-295">`0` — реализовать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-295">`0` - affinitize</span></span><br/><span data-ttu-id="1c5a6-296">`1` — не реализовывать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-296">`1` - don't affinitize</span></span> | <span data-ttu-id="1c5a6-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-298">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-298">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-299">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="1c5a6-299">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="1c5a6-300">`false` — реализовать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-300">`false` - affinitize</span></span><br/><span data-ttu-id="1c5a6-301">`true` — не реализовывать сходство</span><span class="sxs-lookup"><span data-stu-id="1c5a6-301">`true` - don't affinitize</span></span> | <span data-ttu-id="1c5a6-302">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="1c5a6-302">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="1c5a6-303">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-303">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="heap-limit"></a><span data-ttu-id="1c5a6-304">Ограничение кучи</span><span class="sxs-lookup"><span data-stu-id="1c5a6-304">Heap limit</span></span>

- <span data-ttu-id="1c5a6-305">Указывает максимальный размер фиксации в байтах для кучи сборки мусора и учета сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-305">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="1c5a6-306">Этот параметр применим только к 64-разрядным компьютерам.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-306">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="1c5a6-307">Если настроены [ограничения для отдельных куч объектов](#per-object-heap-limits), этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-307">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="1c5a6-308">Значение по умолчанию, которое применяется только в определенных случаях, превышает 20 МБ или 75 % предельного объема памяти в контейнере.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-308">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="1c5a6-309">Значение по умолчанию применяется, если:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-309">The default value applies if:</span></span>

  - <span data-ttu-id="1c5a6-310">процесс выполняется в контейнере с заданным предельным объемом памяти;</span><span class="sxs-lookup"><span data-stu-id="1c5a6-310">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="1c5a6-311">параметр [System.GC.HeapHardLimitPercent](#heap-limit-percent) не задан.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-311">[System.GC.HeapHardLimitPercent](#heap-limit-percent) is not set.</span></span>

| | <span data-ttu-id="1c5a6-312">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-312">Setting name</span></span> | <span data-ttu-id="1c5a6-313">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-313">Values</span></span> | <span data-ttu-id="1c5a6-314">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-314">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-315">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-315">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="1c5a6-316">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-316">*decimal value*</span></span> | <span data-ttu-id="1c5a6-317">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-317">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-318">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-318">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="1c5a6-319">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-319">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-320">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-320">.NET Core 3.0</span></span> |

<span data-ttu-id="1c5a6-321">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-321">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="1c5a6-322">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-322">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-323">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-323">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-324">Например, чтобы задать для куч жесткое ограничение в 200 мебибайт (Миб), для JSON-файла нужно указать значение 209715200, а для переменной среды — значение 0xC800000 или C800000.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-324">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="heap-limit-percent"></a><span data-ttu-id="1c5a6-325">Ограничение кучи в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-325">Heap limit percent</span></span>

- <span data-ttu-id="1c5a6-326">Указывает допустимое использование кучи сборки мусора в процентах от общего объема физической памяти.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-326">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="1c5a6-327">Если также задан параметр [System.GC.HeapHardLimit](#heap-limit), этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-327">If [System.GC.HeapHardLimit](#heap-limit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="1c5a6-328">Этот параметр применим только к 64-разрядным компьютерам.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-328">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="1c5a6-329">Если процесс выполняется в контейнере с заданным предельным объемом памяти, процентная доля вычисляется как процент от этого объема памяти.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-329">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="1c5a6-330">Если настроены [ограничения для отдельных куч объектов](#per-object-heap-limits), этот параметр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-330">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="1c5a6-331">Значение по умолчанию, которое применяется только в определенных случаях, не превышает 20 МБ или 75 % предельного объема памяти в контейнере.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-331">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="1c5a6-332">Значение по умолчанию применяется, если:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-332">The default value applies if:</span></span>

  - <span data-ttu-id="1c5a6-333">процесс выполняется в контейнере с заданным предельным объемом памяти;</span><span class="sxs-lookup"><span data-stu-id="1c5a6-333">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="1c5a6-334">параметр [System.GC.HeapHardLimit](#heap-limit) не задан.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-334">[System.GC.HeapHardLimit](#heap-limit) is not set.</span></span>

| | <span data-ttu-id="1c5a6-335">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-335">Setting name</span></span> | <span data-ttu-id="1c5a6-336">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-336">Values</span></span> | <span data-ttu-id="1c5a6-337">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-337">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-338">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-338">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="1c5a6-339">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-339">*decimal value*</span></span> | <span data-ttu-id="1c5a6-340">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-340">.NET Core 3.0</span></span> |
| <span data-ttu-id="1c5a6-341">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-341">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="1c5a6-342">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-342">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-343">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-343">.NET Core 3.0</span></span> |

<span data-ttu-id="1c5a6-344">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-344">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="1c5a6-345">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-345">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-346">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-346">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-347">Например, чтобы ограничить использование кучи значением 30 %, для JSON-файла нужно указать 30, а для переменной среды — 0x1E или 1E.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-347">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="1c5a6-348">Ограничения для отдельных куч объектов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-348">Per-object-heap limits</span></span>

<span data-ttu-id="1c5a6-349">Вы можете настраивать допустимый объем использования кучи в ходе сборки мусора для отдельных куч объектов.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-349">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="1c5a6-350">Это можно сделать для кучи больших (LOH), малых (SOH) и закрепленных (POH) объектов.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-350">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="1c5a6-351">Если задано значение любого из этих параметров (`COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH` или `COMPLUS_GCHeapHardLimitPOH`), также необходимо указать значения `COMPLUS_GCHeapHardLimitSOH` и `COMPLUS_GCHeapHardLimitLOH`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-351">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="1c5a6-352">Если этого не сделать, во время выполнения произойдет сбой инициализации.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-352">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="1c5a6-353">Значение по умолчанию для `COMPLUS_GCHeapHardLimitPOH` равно 0.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-353">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="1c5a6-354">Параметры `COMPLUS_GCHeapHardLimitSOH` и `COMPLUS_GCHeapHardLimitLOH` не имеют значений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-354">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="1c5a6-355">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-355">Setting name</span></span> | <span data-ttu-id="1c5a6-356">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-356">Values</span></span> | <span data-ttu-id="1c5a6-357">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-358">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOH` | <span data-ttu-id="1c5a6-359">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-359">*decimal value*</span></span> | <span data-ttu-id="1c5a6-360">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-360">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-361">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-361">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="1c5a6-362">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-362">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-363">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-363">.NET 5.0</span></span> |

| | <span data-ttu-id="1c5a6-364">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-364">Setting name</span></span> | <span data-ttu-id="1c5a6-365">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-365">Values</span></span> | <span data-ttu-id="1c5a6-366">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-366">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-367">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-367">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOH` | <span data-ttu-id="1c5a6-368">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-368">*decimal value*</span></span> | <span data-ttu-id="1c5a6-369">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-369">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-370">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-370">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="1c5a6-371">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-371">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-372">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-372">.NET 5.0</span></span> |

| | <span data-ttu-id="1c5a6-373">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-373">Setting name</span></span> | <span data-ttu-id="1c5a6-374">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-374">Values</span></span> | <span data-ttu-id="1c5a6-375">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-375">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-376">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-376">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOH` | <span data-ttu-id="1c5a6-377">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-377">*decimal value*</span></span> | <span data-ttu-id="1c5a6-378">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-378">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-379">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-379">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="1c5a6-380">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-380">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-381">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-381">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="1c5a6-382">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-382">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-383">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-383">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-384">Например, чтобы задать для куч жесткое ограничение в 200 мебибайт (Миб), для JSON-файла нужно указать значение 209715200, а для переменной среды — значение 0xC800000 или C800000.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-384">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="per-object-heap-limit-percents"></a><span data-ttu-id="1c5a6-385">Ограничения для отдельных куч объектов в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-385">Per-object-heap limit percents</span></span>

<span data-ttu-id="1c5a6-386">Вы можете настраивать допустимый объем использования кучи в ходе сборки мусора для отдельных куч объектов.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-386">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="1c5a6-387">Это можно сделать для кучи больших (LOH), малых (SOH) и закрепленных (POH) объектов.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-387">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

- <span data-ttu-id="1c5a6-388">Если задано значение любого из этих параметров (`COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent` или `COMPLUS_GCHeapHardLimitPOHPercent`), также необходимо указать значения `COMPLUS_GCHeapHardLimitSOHPercent` и `COMPLUS_GCHeapHardLimitLOHPercent`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-388">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="1c5a6-389">Если этого не сделать, во время выполнения произойдет сбой инициализации.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-389">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="1c5a6-390">Эти параметры игнорируются, если заданы значения параметров `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH` и `COMPLUS_GCHeapHardLimitPOH`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-390">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="1c5a6-391">Значение 1 означает, что при сборке мусора используется 1 % от общего объема физической памяти для соответствующей кучи объектов.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-391">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="1c5a6-392">Задаваемое значение должно быть больше нуля и меньше 100.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-392">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="1c5a6-393">Кроме того, сумма всех трех процентных значений должна быть меньше 100.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-393">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="1c5a6-394">В противном случае во время выполнения произойдет сбой инициализации.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-394">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="1c5a6-395">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-395">Setting name</span></span> | <span data-ttu-id="1c5a6-396">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-396">Values</span></span> | <span data-ttu-id="1c5a6-397">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-397">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-398">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-398">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitSOHPercent` | <span data-ttu-id="1c5a6-399">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-399">*decimal value*</span></span> | <span data-ttu-id="1c5a6-400">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-400">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-401">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-401">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="1c5a6-402">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-402">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-403">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-403">.NET 5.0</span></span> |

| | <span data-ttu-id="1c5a6-404">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-404">Setting name</span></span> | <span data-ttu-id="1c5a6-405">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-405">Values</span></span> | <span data-ttu-id="1c5a6-406">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-406">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-407">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-407">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitLOHPercent` | <span data-ttu-id="1c5a6-408">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-408">*decimal value*</span></span> | <span data-ttu-id="1c5a6-409">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-409">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-410">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-410">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="1c5a6-411">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-411">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-412">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-412">.NET 5.0</span></span> |

| | <span data-ttu-id="1c5a6-413">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-413">Setting name</span></span> | <span data-ttu-id="1c5a6-414">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-414">Values</span></span> | <span data-ttu-id="1c5a6-415">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-416">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPOHPercent` | <span data-ttu-id="1c5a6-417">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-417">*decimal value*</span></span> | <span data-ttu-id="1c5a6-418">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-418">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-419">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-419">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="1c5a6-420">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-420">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-421">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-421">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="1c5a6-422">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-422">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-423">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-423">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-424">Например, чтобы ограничить использование кучи значением 30 %, для JSON-файла нужно указать 30, а для переменной среды — 0x1E или 1E.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-424">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="high-memory-percent"></a><span data-ttu-id="1c5a6-425">Потребление большого объема памяти в процентах</span><span class="sxs-lookup"><span data-stu-id="1c5a6-425">High memory percent</span></span>

<span data-ttu-id="1c5a6-426">Потребление памяти обозначается в процентах использования физической памяти.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-426">Memory load is indicated by the percentage of physical memory in use.</span></span> <span data-ttu-id="1c5a6-427">По умолчанию, когда использование физической памяти достигает **90 %** , сборка мусора начинает работать активнее и становится более компактной, чтобы избежать подкачки.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-427">By default, when the physical memory load reaches **90%**, garbage collection becomes more aggressive about doing full, compacting garbage collections to avoid paging.</span></span> <span data-ttu-id="1c5a6-428">Пока загрузка памяти составляет менее 90 %, сборщик мусора вместо фоновых выполняет полные сборки мусора, паузы при которых короче, зато общий размер кучи намного сокращается.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-428">When memory load is below 90%, GC favors background collections for full garbage collections, which have shorter pauses but don't reduce the total heap size by much.</span></span> <span data-ttu-id="1c5a6-429">На компьютерах с большим объемом памяти (80 ГБ или более) порог загрузки по умолчанию составляет от 90 до 97 %.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-429">On machines with a significant amount of memory (80GB or more), the default load threshold is between 90% and 97%.</span></span>

<span data-ttu-id="1c5a6-430">Максимальное пороговое значение загрузки памяти можно изменить с помощью `COMPlus_GCHighMemPercent` переменной среды или параметра конфигурации JSON `System.GC.HighMemoryPercent`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-430">The high memory load threshold can be adjusted by the `COMPlus_GCHighMemPercent` environment variable or `System.GC.HighMemoryPercent` JSON configuration setting.</span></span> <span data-ttu-id="1c5a6-431">Чтобы изменить размер кучи, скорректируйте пороговое значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-431">Consider adjusting the threshold if you want to control heap size.</span></span> <span data-ttu-id="1c5a6-432">Например, если основной процесс выполняется на компьютере с 64 ГБ памяти, будет разумно, чтобы сборщик мусора начинал реагировать, когда доступной памяти становится 10 %.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-432">For example, for the dominant process on a machine with 64GB of memory, it's reasonable for GC to start reacting when there's 10% of memory available.</span></span> <span data-ttu-id="1c5a6-433">А вот при небольших процессах, например, когда процесс задействует только 1 ГБ памяти, сборщик мусора может комфортно работать, даже если доступной памяти меньше 10 %.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-433">But for smaller processes, for example, a process that only consumes 1GB of memory, GC can comfortably run with less than 10% of memory available.</span></span> <span data-ttu-id="1c5a6-434">Для таких небольших процессов можно устанавливать более высокое пороговое значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-434">For these smaller processes, consider setting the threshold higher.</span></span> <span data-ttu-id="1c5a6-435">С другой стороны, если вы хотите уменьшить размер кучи для процессов побольше (даже при достаточном объеме физической памяти), уменьшите это пороговое значение, чтобы сборщик мусора начинал сжимать кучу раньше.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-435">On the other hand, if you want larger processes to have smaller heap sizes (even when there's plenty of physical memory available), lowering this threshold is an effective way for GC to react sooner to compact the heap down.</span></span>

> [!NOTE]
> <span data-ttu-id="1c5a6-436">Для процессов, выполняемых в контейнере, сборщик мусора считает физическую память, исходя из ограничения контейнера.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-436">For processes running in a container, GC considers the physical memory based on the container limit.</span></span>

| | <span data-ttu-id="1c5a6-437">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-437">Setting name</span></span> | <span data-ttu-id="1c5a6-438">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-438">Values</span></span> | <span data-ttu-id="1c5a6-439">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-439">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-440">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-440">**runtimeconfig.json**</span></span> | `System.GC.HighMemoryPercent` | <span data-ttu-id="1c5a6-441">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-441">*decimal value*</span></span> | <span data-ttu-id="1c5a6-442">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-442">.NET 5.0</span></span> |
| <span data-ttu-id="1c5a6-443">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-443">**Environment variable**</span></span> | `COMPlus_GCHighMemPercent` | <span data-ttu-id="1c5a6-444">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-444">*hexadecimal value*</span></span> | |

> [!TIP]
> <span data-ttu-id="1c5a6-445">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-445">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-446">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-446">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-447">Например, чтобы задать пороговое значение загрузки памяти в 75 %, для JSON-файла нужно указать значение 75, а для переменной среды — 0x4B или 4B.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-447">For example, to set the high memory threshold to 75%, the values would be 75 for the JSON file and 0x4B or 4B for the environment variable.</span></span>

### <a name="retain-vm"></a><span data-ttu-id="1c5a6-448">Сохранение виртуальной машины</span><span class="sxs-lookup"><span data-stu-id="1c5a6-448">Retain VM</span></span>

- <span data-ttu-id="1c5a6-449">Настраивает, будут ли удаляемые сегменты помещаться в список ожидания для будущего использования или возвращаться операционной системе (ОС).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-449">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="1c5a6-450">По умолчанию: возвращение сегментов операционной системе.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-450">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="1c5a6-451">Это эквивалентно присвоению значения `false`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-451">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="1c5a6-452">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-452">Setting name</span></span> | <span data-ttu-id="1c5a6-453">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-453">Values</span></span> | <span data-ttu-id="1c5a6-454">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-454">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-455">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-455">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="1c5a6-456">`false` — возвращение операционной системе</span><span class="sxs-lookup"><span data-stu-id="1c5a6-456">`false` - release to OS</span></span><br/><span data-ttu-id="1c5a6-457">`true` — помещение в режим ожидания</span><span class="sxs-lookup"><span data-stu-id="1c5a6-457">`true` - put on standby</span></span> | <span data-ttu-id="1c5a6-458">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-458">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-459">**Свойство MSBuild**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-459">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="1c5a6-460">`false` — возвращение операционной системе</span><span class="sxs-lookup"><span data-stu-id="1c5a6-460">`false` - release to OS</span></span><br/><span data-ttu-id="1c5a6-461">`true` — помещение в режим ожидания</span><span class="sxs-lookup"><span data-stu-id="1c5a6-461">`true` - put on standby</span></span> | <span data-ttu-id="1c5a6-462">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-462">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-463">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-463">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="1c5a6-464">`0` — возвращение операционной системе</span><span class="sxs-lookup"><span data-stu-id="1c5a6-464">`0` - release to OS</span></span><br/><span data-ttu-id="1c5a6-465">`1` — помещение в режим ожидания</span><span class="sxs-lookup"><span data-stu-id="1c5a6-465">`1` - put on standby</span></span> | <span data-ttu-id="1c5a6-466">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-466">.NET Core 1.0</span></span> |

#### <a name="examples"></a><span data-ttu-id="1c5a6-467">Примеры</span><span class="sxs-lookup"><span data-stu-id="1c5a6-467">Examples</span></span>

<span data-ttu-id="1c5a6-468">Файл *runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-468">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="1c5a6-469">Файл проекта:</span><span class="sxs-lookup"><span data-stu-id="1c5a6-469">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="1c5a6-470">Большие страницы</span><span class="sxs-lookup"><span data-stu-id="1c5a6-470">Large pages</span></span>

- <span data-ttu-id="1c5a6-471">Указывает, следует ли использовать большие страницы, когда задано жесткое ограничение куч.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-471">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="1c5a6-472">По умолчанию: не следует использовать большие страницы, если задан фиксированный предел кучи.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-472">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="1c5a6-473">Это эквивалентно присвоению значения `0`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-473">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="1c5a6-474">Это экспериментальный параметр.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-474">This is an experimental setting.</span></span>

| | <span data-ttu-id="1c5a6-475">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-475">Setting name</span></span> | <span data-ttu-id="1c5a6-476">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-476">Values</span></span> | <span data-ttu-id="1c5a6-477">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-477">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-478">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-478">**runtimeconfig.json**</span></span> | <span data-ttu-id="1c5a6-479">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-479">N/A</span></span> | <span data-ttu-id="1c5a6-480">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-480">N/A</span></span> | <span data-ttu-id="1c5a6-481">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-481">N/A</span></span> |
| <span data-ttu-id="1c5a6-482">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-482">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="1c5a6-483">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-483">`0` - disabled</span></span><br/><span data-ttu-id="1c5a6-484">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-484">`1` - enabled</span></span> | <span data-ttu-id="1c5a6-485">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-485">.NET Core 3.0</span></span> |

## <a name="allow-large-objects"></a><span data-ttu-id="1c5a6-486">Разрешить большие объекты</span><span class="sxs-lookup"><span data-stu-id="1c5a6-486">Allow large objects</span></span>

- <span data-ttu-id="1c5a6-487">Настраивает для сборщика мусора на 64-разрядных платформах поддержку массивов, размер которых превышает 2 гигабайта (ГБ).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-487">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="1c5a6-488">По умолчанию: сборка мусора поддерживает массивы размером более 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-488">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="1c5a6-489">Это эквивалентно присвоению значения `1`.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-489">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="1c5a6-490">В будущей версии .NET этот параметр может быть объявлен устаревшим.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-490">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="1c5a6-491">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-491">Setting name</span></span> | <span data-ttu-id="1c5a6-492">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-492">Values</span></span> | <span data-ttu-id="1c5a6-493">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-493">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-494">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-494">**runtimeconfig.json**</span></span> | <span data-ttu-id="1c5a6-495">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-495">N/A</span></span> | <span data-ttu-id="1c5a6-496">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-496">N/A</span></span> | <span data-ttu-id="1c5a6-497">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-497">N/A</span></span> |
| <span data-ttu-id="1c5a6-498">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-498">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="1c5a6-499">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-499">`1` - enabled</span></span><br/> <span data-ttu-id="1c5a6-500">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-500">`0` - disabled</span></span> | <span data-ttu-id="1c5a6-501">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-501">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-502">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-502">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-503">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="1c5a6-503">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="1c5a6-504">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-504">`1` - enabled</span></span><br/> <span data-ttu-id="1c5a6-505">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="1c5a6-505">`0` - disabled</span></span> | <span data-ttu-id="1c5a6-506">.NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="1c5a6-506">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="1c5a6-507">Пороговое значение кучи больших объектов</span><span class="sxs-lookup"><span data-stu-id="1c5a6-507">Large object heap threshold</span></span>

- <span data-ttu-id="1c5a6-508">Указывает пороговый размер (в байтах), при котором объекты попадают в кучу больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-508">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="1c5a6-509">Пороговое значение по умолчанию — 85 000 байт.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-509">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="1c5a6-510">Указанное значение должно быть больше порогового значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-510">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="1c5a6-511">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-511">Setting name</span></span> | <span data-ttu-id="1c5a6-512">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-512">Values</span></span> | <span data-ttu-id="1c5a6-513">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-513">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-514">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-514">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="1c5a6-515">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-515">*decimal value*</span></span> | <span data-ttu-id="1c5a6-516">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-516">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-517">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-517">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="1c5a6-518">*Шестнадцатеричное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-518">*hexadecimal value*</span></span> | <span data-ttu-id="1c5a6-519">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1c5a6-519">.NET Core 1.0</span></span> |
| <span data-ttu-id="1c5a6-520">**app.config для .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-520">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="1c5a6-521">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="1c5a6-521">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="1c5a6-522">*Десятичное значение*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-522">*decimal value*</span></span> | <span data-ttu-id="1c5a6-523">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="1c5a6-523">.NET Framework 4.8</span></span> |

<span data-ttu-id="1c5a6-524">Пример.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-524">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="1c5a6-525">Если вы задаете параметр в *runtimeconfig.json*, укажите десятичное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-525">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="1c5a6-526">Если вы задаете параметр в виде переменной среды, укажите шестнадцатеричное значение.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-526">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="1c5a6-527">Например, чтобы задать порог размера в 120 000 байт, для JSON-файла нужно указать значение 120000, а для переменной среды — значение 0x1D4C0 или 1D4C0.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-527">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="1c5a6-528">Автономный сборщик мусора</span><span class="sxs-lookup"><span data-stu-id="1c5a6-528">Standalone GC</span></span>

- <span data-ttu-id="1c5a6-529">Указывает путь к библиотеке, содержащей сборщик мусора, который среда выполнения намеревается загрузить.</span><span class="sxs-lookup"><span data-stu-id="1c5a6-529">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="1c5a6-530">Дополнительные сведения см. в статье [Проектирования загрузчика автономного сборщика мусора](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="1c5a6-530">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/main/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="1c5a6-531">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="1c5a6-531">Setting name</span></span> | <span data-ttu-id="1c5a6-532">Значения</span><span class="sxs-lookup"><span data-stu-id="1c5a6-532">Values</span></span> | <span data-ttu-id="1c5a6-533">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="1c5a6-533">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="1c5a6-534">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-534">**runtimeconfig.json**</span></span> | <span data-ttu-id="1c5a6-535">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-535">N/A</span></span> | <span data-ttu-id="1c5a6-536">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-536">N/A</span></span> | <span data-ttu-id="1c5a6-537">Н/Д</span><span class="sxs-lookup"><span data-stu-id="1c5a6-537">N/A</span></span> |
| <span data-ttu-id="1c5a6-538">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="1c5a6-538">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="1c5a6-539">*string_path*</span><span class="sxs-lookup"><span data-stu-id="1c5a6-539">*string_path*</span></span> | <span data-ttu-id="1c5a6-540">.NET Core 2.0;</span><span class="sxs-lookup"><span data-stu-id="1c5a6-540">.NET Core 2.0</span></span> |
