---
title: Параметры конфигурации отладки и профилирования
description: Сведения о параметрах времени выполнения, определяющих использование отладки и профилирования для приложений .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: dd96862582f13adc19df7572b1865800b18d9954
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875022"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="73aea-103">Параметры конфигурации времени выполнения для отладки и профилирования</span><span class="sxs-lookup"><span data-stu-id="73aea-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="73aea-104">Включение диагностики</span><span class="sxs-lookup"><span data-stu-id="73aea-104">Enable diagnostics</span></span>

- <span data-ttu-id="73aea-105">Указывает, включены или нет отладчик, профилировщик и диагностика EventPipe.</span><span class="sxs-lookup"><span data-stu-id="73aea-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="73aea-106">Если этот параметр не задан, диагностика будет включена.</span><span class="sxs-lookup"><span data-stu-id="73aea-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="73aea-107">Это эквивалентно присвоению значения `1`.</span><span class="sxs-lookup"><span data-stu-id="73aea-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="73aea-108">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-108">Setting name</span></span> | <span data-ttu-id="73aea-109">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="73aea-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="73aea-111">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-111">N/A</span></span> | <span data-ttu-id="73aea-112">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-112">N/A</span></span> |
| <span data-ttu-id="73aea-113">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="73aea-114">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="73aea-114">`1` - enabled</span></span><br/><span data-ttu-id="73aea-115">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="73aea-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="73aea-116">Включить профилирование</span><span class="sxs-lookup"><span data-stu-id="73aea-116">Enable profiling</span></span>

- <span data-ttu-id="73aea-117">Указывает, включено ли профилирование для текущего выполняющегося процесса.</span><span class="sxs-lookup"><span data-stu-id="73aea-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="73aea-118">Если этот параметр не задан, профилирование будет отключено.</span><span class="sxs-lookup"><span data-stu-id="73aea-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="73aea-119">Это эквивалентно присвоению значения `0`.</span><span class="sxs-lookup"><span data-stu-id="73aea-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="73aea-120">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-120">Setting name</span></span> | <span data-ttu-id="73aea-121">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="73aea-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="73aea-123">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-123">N/A</span></span> | <span data-ttu-id="73aea-124">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-124">N/A</span></span> |
| <span data-ttu-id="73aea-125">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="73aea-126">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="73aea-126">`0` - disabled</span></span><br/><span data-ttu-id="73aea-127">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="73aea-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="73aea-128">Profiler GUID (GUID профилировщика)</span><span class="sxs-lookup"><span data-stu-id="73aea-128">Profiler GUID</span></span>

- <span data-ttu-id="73aea-129">Указывает идентификатор GUID профилировщика, загружаемый в выполняющийся процесс.</span><span class="sxs-lookup"><span data-stu-id="73aea-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="73aea-130">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-130">Setting name</span></span> | <span data-ttu-id="73aea-131">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-132">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="73aea-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="73aea-133">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-133">N/A</span></span> | <span data-ttu-id="73aea-134">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-134">N/A</span></span> |
| <span data-ttu-id="73aea-135">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="73aea-136">*string-guid*</span><span class="sxs-lookup"><span data-stu-id="73aea-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="73aea-137">Profiler location (Расположение профилировщика)</span><span class="sxs-lookup"><span data-stu-id="73aea-137">Profiler location</span></span>

- <span data-ttu-id="73aea-138">Указывает путь к библиотеке DLL профилировщика, загружаемой в выполняющийся процесс (либо 32- или 64-разрядный процесс).</span><span class="sxs-lookup"><span data-stu-id="73aea-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="73aea-139">Если задано более одной переменной, приоритет имеют учитывающие разрядность переменные.</span><span class="sxs-lookup"><span data-stu-id="73aea-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="73aea-140">Они указывают, какой разрядности профилировщик следует загрузить.</span><span class="sxs-lookup"><span data-stu-id="73aea-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="73aea-141">Дополнительные сведения см. в разделе [Поиск библиотеки профилировщика](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="73aea-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="73aea-142">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-142">Setting name</span></span> | <span data-ttu-id="73aea-143">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-144">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="73aea-145">*string-path*</span><span class="sxs-lookup"><span data-stu-id="73aea-145">*string-path*</span></span> |
| <span data-ttu-id="73aea-146">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="73aea-147">*string-path*</span><span class="sxs-lookup"><span data-stu-id="73aea-147">*string-path*</span></span> |
| <span data-ttu-id="73aea-148">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="73aea-149">*string-path*</span><span class="sxs-lookup"><span data-stu-id="73aea-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="73aea-150">Write perf map (Запись карты производительности)</span><span class="sxs-lookup"><span data-stu-id="73aea-150">Write perf map</span></span>

- <span data-ttu-id="73aea-151">Включает или отключает запись */tmp/perf-$pid.map* в системах Linux.</span><span class="sxs-lookup"><span data-stu-id="73aea-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="73aea-152">Если этот параметр не задан, запись карты производительности будет отключена.</span><span class="sxs-lookup"><span data-stu-id="73aea-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="73aea-153">Это эквивалентно присвоению значения `0`.</span><span class="sxs-lookup"><span data-stu-id="73aea-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="73aea-154">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-154">Setting name</span></span> | <span data-ttu-id="73aea-155">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="73aea-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="73aea-157">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-157">N/A</span></span> | <span data-ttu-id="73aea-158">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-158">N/A</span></span> |
| <span data-ttu-id="73aea-159">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="73aea-160">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="73aea-160">`0` - disabled</span></span><br/><span data-ttu-id="73aea-161">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="73aea-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="73aea-162">Perf log markers (Маркеры журналов производительности)</span><span class="sxs-lookup"><span data-stu-id="73aea-162">Perf log markers</span></span>

- <span data-ttu-id="73aea-163">Включает или отключает указанный сигнал, который будет принят и проигнорирован в качестве маркера в журналах производительности.</span><span class="sxs-lookup"><span data-stu-id="73aea-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="73aea-164">Если этот параметр не задан, указанный сигнал не будет проигнорирован.</span><span class="sxs-lookup"><span data-stu-id="73aea-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="73aea-165">Это эквивалентно присвоению значения `0`.</span><span class="sxs-lookup"><span data-stu-id="73aea-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="73aea-166">Имя параметра</span><span class="sxs-lookup"><span data-stu-id="73aea-166">Setting name</span></span> | <span data-ttu-id="73aea-167">Значения</span><span class="sxs-lookup"><span data-stu-id="73aea-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="73aea-168">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="73aea-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="73aea-169">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-169">N/A</span></span> | <span data-ttu-id="73aea-170">Н/Д</span><span class="sxs-lookup"><span data-stu-id="73aea-170">N/A</span></span> |
| <span data-ttu-id="73aea-171">**Переменная среды**</span><span class="sxs-lookup"><span data-stu-id="73aea-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="73aea-172">`0` — отключено</span><span class="sxs-lookup"><span data-stu-id="73aea-172">`0` - disabled</span></span><br/><span data-ttu-id="73aea-173">`1` — включено</span><span class="sxs-lookup"><span data-stu-id="73aea-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="73aea-174">Этот параметр игнорируется, если параметр [COMPlus_PerfMapEnabled](#write-perf-map) не задан или имеет значение `0` (т. е. отключен).</span><span class="sxs-lookup"><span data-stu-id="73aea-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
