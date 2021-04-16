---
title: События среды выполнения сборки мусора
description: Сведения о событиях среды выполнения .NET, собирающих диагностическую информацию, относящуюся к сборщику мусора .NET.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594056"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="58b89-103">События сборки мусора среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="58b89-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="58b89-104">Эти события собирают сведения, относящиеся к сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="58b89-105">Они помогают в диагностике и отладке, включая определение того, сколько раз выполнялась сборка мусора, сколько памяти было освобождено во время сборки мусора и т. д. Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [Ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="58b89-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="58b89-106">Событие GCStart_V2</span><span class="sxs-lookup"><span data-stu-id="58b89-106">GCStart_V2 Event</span></span>

<span data-ttu-id="58b89-107">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-108">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-108">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-109">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-111">Informational (4)</span></span>|

<span data-ttu-id="58b89-112">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-112">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-113">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-113">Event</span></span>|<span data-ttu-id="58b89-114">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-114">Event ID</span></span>|<span data-ttu-id="58b89-115">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="58b89-116">1</span><span class="sxs-lookup"><span data-stu-id="58b89-116">1</span></span>|<span data-ttu-id="58b89-117">Сборка мусора начата.</span><span class="sxs-lookup"><span data-stu-id="58b89-117">A garbage collection has started.</span></span>|

<span data-ttu-id="58b89-118">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-118">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-119">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-119">Field name</span></span>|<span data-ttu-id="58b89-120">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-120">Data type</span></span>|<span data-ttu-id="58b89-121">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="58b89-122">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="58b89-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="58b89-123">Поколение, для которого выполняется сборка.</span><span class="sxs-lookup"><span data-stu-id="58b89-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="58b89-124">Причина запуска сборки мусора:</span><span class="sxs-lookup"><span data-stu-id="58b89-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="58b89-125">`0x0` — выделение кучи маленьких объектов.</span><span class="sxs-lookup"><span data-stu-id="58b89-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="58b89-126">`0x1` — принудительная.</span><span class="sxs-lookup"><span data-stu-id="58b89-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="58b89-127">`0x2` — нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="58b89-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="58b89-128">`0x3` — пусто.</span><span class="sxs-lookup"><span data-stu-id="58b89-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="58b89-129">`0x4` — выделение кучи больших объектов.</span><span class="sxs-lookup"><span data-stu-id="58b89-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="58b89-130">`0x5` — недостаточно места (для кучи маленьких объектов).</span><span class="sxs-lookup"><span data-stu-id="58b89-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="58b89-131">`0x6` — недостаточно места (для кучи больших объектов).</span><span class="sxs-lookup"><span data-stu-id="58b89-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="58b89-132">`0x7` — принудительная, но не блокирующая.</span><span class="sxs-lookup"><span data-stu-id="58b89-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="58b89-133">`0x0` — блокирующая сборка мусора произошла за пределами фоновой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="58b89-134">`0x1` — фоновая сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="58b89-135">`0x2` — блокирующая сборка мусора произошла во время фоновой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="58b89-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-136">win:UInt16</span></span>|<span data-ttu-id="58b89-137">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="58b89-138">Событие GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="58b89-139">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-140">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-140">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-141">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-143">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-143">Informational (4)</span></span>|

<span data-ttu-id="58b89-144">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-144">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-145">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-145">Event</span></span>|<span data-ttu-id="58b89-146">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-146">Event ID</span></span>|<span data-ttu-id="58b89-147">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="58b89-148">2</span><span class="sxs-lookup"><span data-stu-id="58b89-148">2</span></span>|<span data-ttu-id="58b89-149">Сборка мусора закончена.</span><span class="sxs-lookup"><span data-stu-id="58b89-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="58b89-150">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-150">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-151">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-151">Field name</span></span>|<span data-ttu-id="58b89-152">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-152">Data type</span></span>|<span data-ttu-id="58b89-153">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="58b89-154">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="58b89-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="58b89-155">Поколение, для которого выполнялась сборка.</span><span class="sxs-lookup"><span data-stu-id="58b89-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="58b89-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-156">win:UInt16</span></span>|<span data-ttu-id="58b89-157">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="58b89-158">Событие GCHeapStats_V2</span><span class="sxs-lookup"><span data-stu-id="58b89-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="58b89-159">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-160">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-160">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-161">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-163">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-163">Informational (4)</span></span>|

<span data-ttu-id="58b89-164">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-164">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-165">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-165">Event</span></span>|<span data-ttu-id="58b89-166">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-166">Event ID</span></span>|<span data-ttu-id="58b89-167">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="58b89-168">4</span><span class="sxs-lookup"><span data-stu-id="58b89-168">4</span></span>|<span data-ttu-id="58b89-169">Показывает статистику кучи по завершении каждой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="58b89-170">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-170">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-171">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-171">Field name</span></span>|<span data-ttu-id="58b89-172">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-172">Data type</span></span>|<span data-ttu-id="58b89-173">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="58b89-174">Размер области памяти поколения 0 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="58b89-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="58b89-175">Число байт, которые были переданы из поколения 0 в поколение 1.</span><span class="sxs-lookup"><span data-stu-id="58b89-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="58b89-176">Размер области памяти поколения 1 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="58b89-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="58b89-177">Число байт, которые были переданы из поколения 1 в поколение 2.</span><span class="sxs-lookup"><span data-stu-id="58b89-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="58b89-178">Размер области памяти поколения 2 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="58b89-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="58b89-179">Число байт, оставшихся в поколении 2 после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="58b89-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="58b89-180">Размер кучи больших объектов (в байтах).</span><span class="sxs-lookup"><span data-stu-id="58b89-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="58b89-181">Число байт, оставшихся в куче больших объектов после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="58b89-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="58b89-182">Общий размер (в байтах) объектов, которые готовы к завершению.</span><span class="sxs-lookup"><span data-stu-id="58b89-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="58b89-183">Количество объектов, которые готовы к завершению.</span><span class="sxs-lookup"><span data-stu-id="58b89-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="58b89-184">Количество закрепленных (неподвижных) объектов.</span><span class="sxs-lookup"><span data-stu-id="58b89-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="58b89-185">Количество используемых блоков синхронизации.</span><span class="sxs-lookup"><span data-stu-id="58b89-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="58b89-186">Число используемых дескрипторов сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-187">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="58b89-188">Размер кучи закрепленных объектов (в байтах).</span><span class="sxs-lookup"><span data-stu-id="58b89-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="58b89-189">Число байт, оставшихся в куче закрепленных объектов после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="58b89-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="58b89-190">Событие GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="58b89-191">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-192">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-192">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-193">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-195">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-195">Informational (4)</span></span>|

<span data-ttu-id="58b89-196">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-196">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-197">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-197">Event</span></span>|<span data-ttu-id="58b89-198">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-198">Event ID</span></span>|<span data-ttu-id="58b89-199">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="58b89-200">5</span><span class="sxs-lookup"><span data-stu-id="58b89-200">5</span></span>|<span data-ttu-id="58b89-201">Был создан новый сегмент сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="58b89-202">Кроме того, при включении трассировки для уже работающего процесса это событие создается для каждого существующего сегмента.</span><span class="sxs-lookup"><span data-stu-id="58b89-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="58b89-203">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-203">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-204">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-204">Field name</span></span>|<span data-ttu-id="58b89-205">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-205">Data type</span></span>|<span data-ttu-id="58b89-206">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="58b89-207">Адрес сегмента.</span><span class="sxs-lookup"><span data-stu-id="58b89-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="58b89-208">Размер сегмента.</span><span class="sxs-lookup"><span data-stu-id="58b89-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="58b89-209">0x0 — куча маленьких объектов.</span><span class="sxs-lookup"><span data-stu-id="58b89-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="58b89-210">0x1 — куча больших объектов.</span><span class="sxs-lookup"><span data-stu-id="58b89-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="58b89-211">0x2 — куча только для чтения.</span><span class="sxs-lookup"><span data-stu-id="58b89-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-212">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="58b89-213">Обратите внимание, что размер сегментов, выделенных сборщиком мусора, зависит от реализации и может быть изменен в любое время, в том числе при периодических обновлениях.</span><span class="sxs-lookup"><span data-stu-id="58b89-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="58b89-214">Приложение не должно делать никаких допущений относительно размера определенного сегмента, полагаться на него или пытаться настроить объем памяти, доступный для выделения сегментов.</span><span class="sxs-lookup"><span data-stu-id="58b89-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="58b89-215">Событие GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="58b89-216">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-217">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-217">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-218">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-220">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-220">Informational (4)</span></span>|

<span data-ttu-id="58b89-221">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-221">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-222">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-222">Event</span></span>|<span data-ttu-id="58b89-223">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-223">Event ID</span></span>|<span data-ttu-id="58b89-224">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="58b89-225">6</span><span class="sxs-lookup"><span data-stu-id="58b89-225">6</span></span>|<span data-ttu-id="58b89-226">Сегмент сборки мусора был освобожден.</span><span class="sxs-lookup"><span data-stu-id="58b89-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="58b89-227">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-227">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-228">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-228">Field name</span></span>|<span data-ttu-id="58b89-229">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-229">Data type</span></span>|<span data-ttu-id="58b89-230">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="58b89-231">Адрес сегмента.</span><span class="sxs-lookup"><span data-stu-id="58b89-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-232">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="58b89-233">Событие GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="58b89-234">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-235">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-235">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-236">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-238">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-238">Informational (4)</span></span>|

<span data-ttu-id="58b89-239">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-239">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-240">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-240">Event</span></span>|<span data-ttu-id="58b89-241">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-241">Event ID</span></span>|<span data-ttu-id="58b89-242">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="58b89-243">7</span><span class="sxs-lookup"><span data-stu-id="58b89-243">7</span></span>|<span data-ttu-id="58b89-244">Началось возобновление приостановленной среды CLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="58b89-245">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="58b89-246">Событие GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="58b89-247">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-248">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-248">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-249">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-251">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-251">Informational (4)</span></span>|

<span data-ttu-id="58b89-252">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-252">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-253">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-253">Event</span></span>|<span data-ttu-id="58b89-254">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-254">Event Id</span></span>|<span data-ttu-id="58b89-255">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="58b89-256">3</span><span class="sxs-lookup"><span data-stu-id="58b89-256">3</span></span>|<span data-ttu-id="58b89-257">Возобновление приостановленной среды CLR завершено.</span><span class="sxs-lookup"><span data-stu-id="58b89-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="58b89-258">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="58b89-259">GCSuspendEEEnd_V1 event</span><span class="sxs-lookup"><span data-stu-id="58b89-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="58b89-260">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-261">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-261">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-262">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-264">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-264">Informational (4)</span></span>|

<span data-ttu-id="58b89-265">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-265">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-266">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-266">Event</span></span>|<span data-ttu-id="58b89-267">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-267">Event ID</span></span>|<span data-ttu-id="58b89-268">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="58b89-269">8</span><span class="sxs-lookup"><span data-stu-id="58b89-269">8</span></span>|<span data-ttu-id="58b89-270">Завершена приостановка механизма выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="58b89-271">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="58b89-272">Событие GCSuspendEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="58b89-273">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-274">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-274">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-275">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-277">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-277">Informational (4)</span></span>|

<span data-ttu-id="58b89-278">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-278">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-279">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-279">Event</span></span>|<span data-ttu-id="58b89-280">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-280">Event ID</span></span>|<span data-ttu-id="58b89-281">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="58b89-282">8</span><span class="sxs-lookup"><span data-stu-id="58b89-282">8</span></span>|<span data-ttu-id="58b89-283">Началась приостановка механизма выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="58b89-284">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-284">Field name</span></span>|<span data-ttu-id="58b89-285">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-285">Data type</span></span>|<span data-ttu-id="58b89-286">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="58b89-287">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="58b89-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="58b89-288">Причина приостановки EE.</span><span class="sxs-lookup"><span data-stu-id="58b89-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="58b89-289">`0x0`: приостановка по другой причине.</span><span class="sxs-lookup"><span data-stu-id="58b89-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="58b89-290">`0x1`: приостановка для GC.</span><span class="sxs-lookup"><span data-stu-id="58b89-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="58b89-291">`0x2`: приостановка для завершения работы AppDomain.</span><span class="sxs-lookup"><span data-stu-id="58b89-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="58b89-292">`0x3`: приостановка для пошагового выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="58b89-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="58b89-293">`0x4`: приостановка для завершения работы.</span><span class="sxs-lookup"><span data-stu-id="58b89-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="58b89-294">`0x5`: приостановка для отладчика.</span><span class="sxs-lookup"><span data-stu-id="58b89-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="58b89-295">`0x6`: приостановка для подготовки GC.</span><span class="sxs-lookup"><span data-stu-id="58b89-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="58b89-296">`0x7`: приостановка для очистки отладчика.</span><span class="sxs-lookup"><span data-stu-id="58b89-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="58b89-297">Событие GCAllocationTick_V3</span><span class="sxs-lookup"><span data-stu-id="58b89-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="58b89-298">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-299">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-299">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-300">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-302">Подробный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-302">Verbose (4)</span></span>|

<span data-ttu-id="58b89-303">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-303">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-304">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-304">Event</span></span>|<span data-ttu-id="58b89-305">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-305">Event ID</span></span>|<span data-ttu-id="58b89-306">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="58b89-307">10</span><span class="sxs-lookup"><span data-stu-id="58b89-307">10</span></span>|<span data-ttu-id="58b89-308">Каждый раз выделяется около 100 КБ.</span><span class="sxs-lookup"><span data-stu-id="58b89-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="58b89-309">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-309">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-310">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-310">Field name</span></span>|<span data-ttu-id="58b89-311">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-311">Data type</span></span>|<span data-ttu-id="58b89-312">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="58b89-313">Размер выделения в байтах.</span><span class="sxs-lookup"><span data-stu-id="58b89-313">The allocation size, in bytes.</span></span> <span data-ttu-id="58b89-314">Это значение является точным для выделений, размер которых меньше длины ULONG (4 294 967 295 байт).</span><span class="sxs-lookup"><span data-stu-id="58b89-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="58b89-315">Если выделение больше, это поле содержит усеченное значение.</span><span class="sxs-lookup"><span data-stu-id="58b89-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="58b89-316">Используйте `AllocationAmount64` для очень больших выделений.</span><span class="sxs-lookup"><span data-stu-id="58b89-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="58b89-317">`0x0` — выделение маленького объекта (выделение в куче маленьких объектов).</span><span class="sxs-lookup"><span data-stu-id="58b89-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="58b89-318">`0x1` — выделение большого объекта (выделение в куче больших объектов).</span><span class="sxs-lookup"><span data-stu-id="58b89-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="58b89-319">Размер выделения в байтах.</span><span class="sxs-lookup"><span data-stu-id="58b89-319">The allocation size, in bytes.</span></span> <span data-ttu-id="58b89-320">Это значение является точным для очень больших выделений.</span><span class="sxs-lookup"><span data-stu-id="58b89-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="58b89-321">Адрес MethodTable.</span><span class="sxs-lookup"><span data-stu-id="58b89-321">The address of the MethodTable.</span></span> <span data-ttu-id="58b89-322">Если в ходе этого события было выделено несколько типов объектов, указывается адрес MethodTable, соответствующий последнему выделенному объекту (объекту, вызвавшему превышение порогового значения 100 КБ).</span><span class="sxs-lookup"><span data-stu-id="58b89-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="58b89-323">Имя выделенного типа.</span><span class="sxs-lookup"><span data-stu-id="58b89-323">The name of the type that was allocated.</span></span> <span data-ttu-id="58b89-324">Если в ходе этого события было выделено несколько типов объектов, указывается тип последнего выделенного объекта (объекта, вызвавшего превышение порогового значения 100 КБ).</span><span class="sxs-lookup"><span data-stu-id="58b89-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="58b89-325">Куча, в которой был выделен объект.</span><span class="sxs-lookup"><span data-stu-id="58b89-325">The heap where the object was allocated.</span></span> <span data-ttu-id="58b89-326">Это значение равно 0 (нулю) при выполнении сборки мусора на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="58b89-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="58b89-327">Адрес последнего выделенного объекта.</span><span class="sxs-lookup"><span data-stu-id="58b89-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-328">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="58b89-329">Событие GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="58b89-330">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-331">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-331">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-332">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-334">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-334">Informational (4)</span></span>|
|<span data-ttu-id="58b89-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="58b89-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="58b89-336">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-336">Informational (4)</span></span>|

<span data-ttu-id="58b89-337">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-337">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-338">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-338">Event</span></span>|<span data-ttu-id="58b89-339">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-339">Event ID</span></span>|<span data-ttu-id="58b89-340">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="58b89-341">11</span><span class="sxs-lookup"><span data-stu-id="58b89-341">11</span></span>|<span data-ttu-id="58b89-342">Был создан параллельный поток сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="58b89-343">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="58b89-344">Событие GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="58b89-345">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-346">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-346">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-347">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-349">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-349">Informational (4)</span></span>|
|<span data-ttu-id="58b89-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="58b89-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="58b89-351">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-351">Informational (4)</span></span>|

<span data-ttu-id="58b89-352">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-352">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-353">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-353">Event</span></span>|<span data-ttu-id="58b89-354">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-354">Event ID</span></span>|<span data-ttu-id="58b89-355">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="58b89-356">12</span><span class="sxs-lookup"><span data-stu-id="58b89-356">12</span></span>|<span data-ttu-id="58b89-357">Параллельный поток сборки мусора был завершен.</span><span class="sxs-lookup"><span data-stu-id="58b89-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="58b89-358">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="58b89-359">Событие GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="58b89-360">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-361">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-361">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-362">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-364">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-364">Informational (4)</span></span>|

<span data-ttu-id="58b89-365">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-365">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-366">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-366">Event</span></span>|<span data-ttu-id="58b89-367">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-367">Event ID</span></span>|<span data-ttu-id="58b89-368">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="58b89-369">14</span><span class="sxs-lookup"><span data-stu-id="58b89-369">14</span></span>|<span data-ttu-id="58b89-370">Начало выполнения методов завершения.</span><span class="sxs-lookup"><span data-stu-id="58b89-370">The start of running finalizers.</span></span>|

<span data-ttu-id="58b89-371">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="58b89-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="58b89-372">Событие GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="58b89-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="58b89-373">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-374">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-374">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-375">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-377">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-377">Informational (4)</span></span>|

<span data-ttu-id="58b89-378">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-378">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-379">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-379">Event</span></span>|<span data-ttu-id="58b89-380">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-380">Event ID</span></span>|<span data-ttu-id="58b89-381">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="58b89-382">13</span><span class="sxs-lookup"><span data-stu-id="58b89-382">13</span></span>|<span data-ttu-id="58b89-383">Завершение выполнения методов завершения.</span><span class="sxs-lookup"><span data-stu-id="58b89-383">The end of running finalizers.</span></span>|

<span data-ttu-id="58b89-384">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-384">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-385">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-385">Field name</span></span>|<span data-ttu-id="58b89-386">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-386">Data type</span></span>|<span data-ttu-id="58b89-387">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="58b89-388">Число выполненных методов завершения.</span><span class="sxs-lookup"><span data-stu-id="58b89-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="58b89-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-389">win:UInt16</span></span>|<span data-ttu-id="58b89-390">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="58b89-391">Событие SetGCHandle</span><span class="sxs-lookup"><span data-stu-id="58b89-391">SetGCHandle event</span></span>

<span data-ttu-id="58b89-392">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-393">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-393">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-394">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-395">`GCHandleKeyword` (0x2)</span><span class="sxs-lookup"><span data-stu-id="58b89-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="58b89-396">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-396">Informational (4)</span></span>|

<span data-ttu-id="58b89-397">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-397">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-398">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-398">Event</span></span>|<span data-ttu-id="58b89-399">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-399">Event ID</span></span>|<span data-ttu-id="58b89-400">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="58b89-401">30</span><span class="sxs-lookup"><span data-stu-id="58b89-401">30</span></span>|<span data-ttu-id="58b89-402">Дескриптор сборки мусора установлен.</span><span class="sxs-lookup"><span data-stu-id="58b89-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="58b89-403">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-403">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-404">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-404">Field name</span></span>|<span data-ttu-id="58b89-405">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-405">Data type</span></span>|<span data-ttu-id="58b89-406">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="58b89-407">Адрес выделенного дескриптора.</span><span class="sxs-lookup"><span data-stu-id="58b89-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="58b89-408">Адрес объекта, дескриптор которого был создан.</span><span class="sxs-lookup"><span data-stu-id="58b89-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="58b89-409">Тип установленного дескриптора сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="58b89-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="58b89-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="58b89-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="58b89-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="58b89-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="58b89-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="58b89-413">`0x3`: Pinned</span><span class="sxs-lookup"><span data-stu-id="58b89-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="58b89-414">`0x4`: Variable</span><span class="sxs-lookup"><span data-stu-id="58b89-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="58b89-415">`0x5`: RefCounted</span><span class="sxs-lookup"><span data-stu-id="58b89-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="58b89-416">`0x6`: Dependent</span><span class="sxs-lookup"><span data-stu-id="58b89-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="58b89-417">`0x7`: AsyncPinned</span><span class="sxs-lookup"><span data-stu-id="58b89-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="58b89-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="58b89-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="58b89-419">Генерация объекта, дескриптор которого был создан.</span><span class="sxs-lookup"><span data-stu-id="58b89-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="58b89-420">Идентификатор AppDomain.</span><span class="sxs-lookup"><span data-stu-id="58b89-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-421">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="58b89-422">Событие DestroyGCHandle</span><span class="sxs-lookup"><span data-stu-id="58b89-422">DestroyGCHandle event</span></span>

<span data-ttu-id="58b89-423">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-424">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-424">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-425">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-426">`GCHandleKeyword` (0x2)</span><span class="sxs-lookup"><span data-stu-id="58b89-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="58b89-427">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-427">Informational (4)</span></span>|

<span data-ttu-id="58b89-428">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-428">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-429">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-429">Event</span></span>|<span data-ttu-id="58b89-430">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-430">Event ID</span></span>|<span data-ttu-id="58b89-431">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="58b89-432">31</span><span class="sxs-lookup"><span data-stu-id="58b89-432">31</span></span>|<span data-ttu-id="58b89-433">Дескриптор GC удален.</span><span class="sxs-lookup"><span data-stu-id="58b89-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="58b89-434">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-434">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-435">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-435">Field name</span></span>|<span data-ttu-id="58b89-436">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-436">Data type</span></span>|<span data-ttu-id="58b89-437">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="58b89-438">Адрес удаленного дескриптора.</span><span class="sxs-lookup"><span data-stu-id="58b89-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="58b89-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-439">win:UInt16</span></span>|<span data-ttu-id="58b89-440">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="58b89-441">Событие PinObjectAtGCTime</span><span class="sxs-lookup"><span data-stu-id="58b89-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="58b89-442">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-443">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-443">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-444">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-446">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="58b89-446">Verbose (5)</span></span>|

<span data-ttu-id="58b89-447">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-447">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-448">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-448">Event</span></span>|<span data-ttu-id="58b89-449">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-449">Event ID</span></span>|<span data-ttu-id="58b89-450">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="58b89-451">33</span><span class="sxs-lookup"><span data-stu-id="58b89-451">33</span></span>|<span data-ttu-id="58b89-452">Объект был закреплен во время сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="58b89-453">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-453">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-454">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-454">Field name</span></span>|<span data-ttu-id="58b89-455">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-455">Data type</span></span>|<span data-ttu-id="58b89-456">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="58b89-457">Адрес дескриптора.</span><span class="sxs-lookup"><span data-stu-id="58b89-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="58b89-458">Адрес закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="58b89-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="58b89-459">Размер закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="58b89-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="58b89-460">Имя типа закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="58b89-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-461">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="58b89-462">Событие GCTriggered</span><span class="sxs-lookup"><span data-stu-id="58b89-462">GCTriggered event</span></span>

<span data-ttu-id="58b89-463">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-464">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-464">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-465">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-467">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="58b89-467">Verbose (5)</span></span>|

<span data-ttu-id="58b89-468">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-468">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-469">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-469">Event</span></span>|<span data-ttu-id="58b89-470">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-470">Event ID</span></span>|<span data-ttu-id="58b89-471">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="58b89-472">33</span><span class="sxs-lookup"><span data-stu-id="58b89-472">33</span></span>|<span data-ttu-id="58b89-473">Сборка мусора активирована.</span><span class="sxs-lookup"><span data-stu-id="58b89-473">A GC has been triggered.</span></span>|

<span data-ttu-id="58b89-474">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-474">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-475">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-475">Field name</span></span>|<span data-ttu-id="58b89-476">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-476">Data type</span></span>|<span data-ttu-id="58b89-477">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="58b89-478">Причина активации сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="58b89-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="58b89-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="58b89-480">`0x1`: Induced</span><span class="sxs-lookup"><span data-stu-id="58b89-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="58b89-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="58b89-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="58b89-482">`0x3`: Empty</span><span class="sxs-lookup"><span data-stu-id="58b89-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="58b89-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="58b89-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="58b89-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="58b89-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="58b89-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="58b89-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="58b89-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="58b89-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="58b89-487">`0x8`: Stress</span><span class="sxs-lookup"><span data-stu-id="58b89-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="58b89-488">`0x9`: InducedLowMemory</span><span class="sxs-lookup"><span data-stu-id="58b89-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-489">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="58b89-490">Событие IncreaseMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="58b89-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="58b89-491">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-492">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-492">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-493">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-495">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-495">Information (4)</span></span>|

<span data-ttu-id="58b89-496">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-496">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-497">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-497">Event</span></span>|<span data-ttu-id="58b89-498">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-498">Event ID</span></span>|<span data-ttu-id="58b89-499">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="58b89-500">200</span><span class="sxs-lookup"><span data-stu-id="58b89-500">200</span></span>|<span data-ttu-id="58b89-501">Повысилась нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="58b89-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="58b89-502">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-502">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-503">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-503">Field Name</span></span>|<span data-ttu-id="58b89-504">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-504">Data type</span></span>|<span data-ttu-id="58b89-505">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="58b89-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-506">win:UInt16</span></span>|<span data-ttu-id="58b89-507">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="58b89-508">Событие DecreaseMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="58b89-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="58b89-509">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-510">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-510">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-511">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-513">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-513">Information (4)</span></span>|

<span data-ttu-id="58b89-514">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-514">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-515">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-515">Event</span></span>|<span data-ttu-id="58b89-516">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-516">Event ID</span></span>|<span data-ttu-id="58b89-517">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="58b89-518">201</span><span class="sxs-lookup"><span data-stu-id="58b89-518">201</span></span>|<span data-ttu-id="58b89-519">Уменьшилась нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="58b89-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="58b89-520">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-520">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-521">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-521">Field Name</span></span>|<span data-ttu-id="58b89-522">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-522">Data type</span></span>|<span data-ttu-id="58b89-523">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="58b89-524">Освобождено байт.</span><span class="sxs-lookup"><span data-stu-id="58b89-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-525">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="58b89-526">Событие GCMarkWithType</span><span class="sxs-lookup"><span data-stu-id="58b89-526">GCMarkWithType event</span></span>

<span data-ttu-id="58b89-527">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-528">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-528">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-529">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-531">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="58b89-531">Information (4)</span></span>|

<span data-ttu-id="58b89-532">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-532">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-533">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-533">Event</span></span>|<span data-ttu-id="58b89-534">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-534">Event ID</span></span>|<span data-ttu-id="58b89-535">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="58b89-536">202</span><span class="sxs-lookup"><span data-stu-id="58b89-536">202</span></span>|<span data-ttu-id="58b89-537">Корень сборки мусора был помечен на этапе пометки сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="58b89-538">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-538">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-539">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-539">Field Name</span></span>|<span data-ttu-id="58b89-540">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-540">Data type</span></span>|<span data-ttu-id="58b89-541">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="58b89-542">Номер кучи.</span><span class="sxs-lookup"><span data-stu-id="58b89-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="58b89-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="58b89-543">win:UInt16</span></span>|<span data-ttu-id="58b89-544">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="58b89-545">Корневой тип сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="58b89-545">The GC root type.</span></span><br/><br/><span data-ttu-id="58b89-546">`0x0`: Stack</span><span class="sxs-lookup"><span data-stu-id="58b89-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="58b89-547">`0x1`: Finalizer</span><span class="sxs-lookup"><span data-stu-id="58b89-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="58b89-548">`0x2`: Handle</span><span class="sxs-lookup"><span data-stu-id="58b89-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="58b89-549">`0x3`: Older</span><span class="sxs-lookup"><span data-stu-id="58b89-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="58b89-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="58b89-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="58b89-551">`0x5`: Overflow</span><span class="sxs-lookup"><span data-stu-id="58b89-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="58b89-552">Число помеченных байт.</span><span class="sxs-lookup"><span data-stu-id="58b89-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="58b89-553">Событие GCJoin_V2</span><span class="sxs-lookup"><span data-stu-id="58b89-553">GCJoin_V2 event</span></span>

<span data-ttu-id="58b89-554">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="58b89-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="58b89-555">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="58b89-555">Keyword for raising the event</span></span>|<span data-ttu-id="58b89-556">Level</span><span class="sxs-lookup"><span data-stu-id="58b89-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="58b89-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="58b89-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="58b89-558">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="58b89-558">Verbose (5)</span></span>|

<span data-ttu-id="58b89-559">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="58b89-559">The following table shows the event information:</span></span>

|<span data-ttu-id="58b89-560">Событие</span><span class="sxs-lookup"><span data-stu-id="58b89-560">Event</span></span>|<span data-ttu-id="58b89-561">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="58b89-561">Event ID</span></span>|<span data-ttu-id="58b89-562">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="58b89-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="58b89-563">203</span><span class="sxs-lookup"><span data-stu-id="58b89-563">203</span></span>|<span data-ttu-id="58b89-564">Поток сборки мусора присоединен.</span><span class="sxs-lookup"><span data-stu-id="58b89-564">A GC thread joined.</span></span>|

<span data-ttu-id="58b89-565">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="58b89-565">The following table shows the event data:</span></span>

|<span data-ttu-id="58b89-566">Имя поля</span><span class="sxs-lookup"><span data-stu-id="58b89-566">Field name</span></span>|<span data-ttu-id="58b89-567">Тип данных</span><span class="sxs-lookup"><span data-stu-id="58b89-567">Data type</span></span>|<span data-ttu-id="58b89-568">Описание</span><span class="sxs-lookup"><span data-stu-id="58b89-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="58b89-569">Номер кучи</span><span class="sxs-lookup"><span data-stu-id="58b89-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="58b89-570">Указывает, инициируется ли это событие в начале соединения или при окончании соединения (`0x0` для начала соединения, `0x1` для окончания соединения)</span><span class="sxs-lookup"><span data-stu-id="58b89-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="58b89-571">Тип соединения.</span><span class="sxs-lookup"><span data-stu-id="58b89-571">The join type.</span></span> <br/><br/><span data-ttu-id="58b89-572">`0x0`: последнее соединение</span><span class="sxs-lookup"><span data-stu-id="58b89-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="58b89-573">`0x1`: соединение</span><span class="sxs-lookup"><span data-stu-id="58b89-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="58b89-574">`0x2`: перезапуск</span><span class="sxs-lookup"><span data-stu-id="58b89-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="58b89-575">`0x3`: первое обратное соединение</span><span class="sxs-lookup"><span data-stu-id="58b89-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="58b89-576">`0x4`: обратное соединение</span><span class="sxs-lookup"><span data-stu-id="58b89-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="58b89-577">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="58b89-577">Unique ID for the instance of CoreCLR.</span></span>|
