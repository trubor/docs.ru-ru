---
title: События времени выполнения сборки мусора
description: См. раздел события среды выполнения .NET, собирающие диагностическую информацию, относящуюся к сборщику мусора .NET.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594056"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="c3372-103">События сборки мусора среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="c3372-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="c3372-104">Эти события собирают сведения, относящиеся к сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="c3372-105">Они помогают в диагностике и отладке, включая определение того, сколько раз выполнялась сборка мусора, сколько памяти было освобождено во время сборки мусора и т. д. Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="c3372-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="c3372-106">GCStart_V2 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-106">GCStart_V2 Event</span></span>

<span data-ttu-id="c3372-107">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-108">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-108">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-109">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-111">Informational (4)</span></span>|

<span data-ttu-id="c3372-112">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-112">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-113">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-113">Event</span></span>|<span data-ttu-id="c3372-114">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-114">Event ID</span></span>|<span data-ttu-id="c3372-115">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="c3372-116">1</span><span class="sxs-lookup"><span data-stu-id="c3372-116">1</span></span>|<span data-ttu-id="c3372-117">Сборка мусора начата.</span><span class="sxs-lookup"><span data-stu-id="c3372-117">A garbage collection has started.</span></span>|

<span data-ttu-id="c3372-118">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-118">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-119">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-119">Field name</span></span>|<span data-ttu-id="c3372-120">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-120">Data type</span></span>|<span data-ttu-id="c3372-121">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="c3372-122">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="c3372-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="c3372-123">Поколение, для которого выполняется сборка.</span><span class="sxs-lookup"><span data-stu-id="c3372-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="c3372-124">Причина запуска сборки мусора:</span><span class="sxs-lookup"><span data-stu-id="c3372-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="c3372-125">`0x0` — Выделение кучи для мелких объектов.</span><span class="sxs-lookup"><span data-stu-id="c3372-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="c3372-126">`0x1` Индуцированные.</span><span class="sxs-lookup"><span data-stu-id="c3372-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="c3372-127">`0x2` -Недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="c3372-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="c3372-128">`0x3` Указано.</span><span class="sxs-lookup"><span data-stu-id="c3372-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="c3372-129">`0x4` — Выделение кучи для больших объектов.</span><span class="sxs-lookup"><span data-stu-id="c3372-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="c3372-130">`0x5` — Не хватает свободного пространства (для кучи небольших объектов).</span><span class="sxs-lookup"><span data-stu-id="c3372-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="c3372-131">`0x6` — Не хватает свободного пространства (для кучи больших объектов).</span><span class="sxs-lookup"><span data-stu-id="c3372-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="c3372-132">`0x7` — Вызывается, но не принудительно блокируется.</span><span class="sxs-lookup"><span data-stu-id="c3372-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="c3372-133">`0x0` -Блокирующая сборка мусора произошла за пределами фоновой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="c3372-134">`0x1` — Фоновая сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="c3372-135">`0x2` — Блокирующая сборка мусора произошла во время фоновой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="c3372-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-136">win:UInt16</span></span>|<span data-ttu-id="c3372-137">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="c3372-138">Событие GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="c3372-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="c3372-139">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-140">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-140">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-141">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-143">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-143">Informational (4)</span></span>|

<span data-ttu-id="c3372-144">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-144">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-145">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-145">Event</span></span>|<span data-ttu-id="c3372-146">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-146">Event ID</span></span>|<span data-ttu-id="c3372-147">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="c3372-148">2</span><span class="sxs-lookup"><span data-stu-id="c3372-148">2</span></span>|<span data-ttu-id="c3372-149">Сборка мусора закончена.</span><span class="sxs-lookup"><span data-stu-id="c3372-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="c3372-150">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-150">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-151">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-151">Field name</span></span>|<span data-ttu-id="c3372-152">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-152">Data type</span></span>|<span data-ttu-id="c3372-153">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="c3372-154">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="c3372-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="c3372-155">Поколение, для которого выполнялась сборка.</span><span class="sxs-lookup"><span data-stu-id="c3372-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="c3372-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-156">win:UInt16</span></span>|<span data-ttu-id="c3372-157">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="c3372-158">GCHeapStats_V2 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="c3372-159">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-160">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-160">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-161">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-163">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-163">Informational (4)</span></span>|

<span data-ttu-id="c3372-164">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-164">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-165">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-165">Event</span></span>|<span data-ttu-id="c3372-166">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-166">Event ID</span></span>|<span data-ttu-id="c3372-167">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="c3372-168">4</span><span class="sxs-lookup"><span data-stu-id="c3372-168">4</span></span>|<span data-ttu-id="c3372-169">Показывает статистику кучи по завершении каждой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="c3372-170">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-170">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-171">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-171">Field name</span></span>|<span data-ttu-id="c3372-172">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-172">Data type</span></span>|<span data-ttu-id="c3372-173">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="c3372-174">Размер области памяти поколения 0 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="c3372-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="c3372-175">Число байт, которые были переданы из поколения 0 в поколение 1.</span><span class="sxs-lookup"><span data-stu-id="c3372-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="c3372-176">Размер области памяти поколения 1 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="c3372-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="c3372-177">Число байт, которые были переданы из поколения 1 в поколение 2.</span><span class="sxs-lookup"><span data-stu-id="c3372-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="c3372-178">Размер области памяти поколения 2 (в байтах).</span><span class="sxs-lookup"><span data-stu-id="c3372-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="c3372-179">Число байт, оставшихся в поколении 2 после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="c3372-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="c3372-180">Размер кучи больших объектов (в байтах).</span><span class="sxs-lookup"><span data-stu-id="c3372-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="c3372-181">Число байт, оставшихся в куче больших объектов после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="c3372-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="c3372-182">Общий размер (в байтах) объектов, которые готовы к завершению.</span><span class="sxs-lookup"><span data-stu-id="c3372-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="c3372-183">Количество объектов, которые готовы к завершению.</span><span class="sxs-lookup"><span data-stu-id="c3372-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="c3372-184">Количество закрепленных (неподвижных) объектов.</span><span class="sxs-lookup"><span data-stu-id="c3372-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="c3372-185">Количество используемых блоков синхронизации.</span><span class="sxs-lookup"><span data-stu-id="c3372-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="c3372-186">Число используемых дескрипторов сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-187">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="c3372-188">Размер кучи закрепленных объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="c3372-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="c3372-189">Число байтов, сохранившихся в куче закрепленных объектов после последней сборки.</span><span class="sxs-lookup"><span data-stu-id="c3372-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="c3372-190">GCCreateSegment_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="c3372-191">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-192">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-192">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-193">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-195">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-195">Informational (4)</span></span>|

<span data-ttu-id="c3372-196">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-196">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-197">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-197">Event</span></span>|<span data-ttu-id="c3372-198">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-198">Event ID</span></span>|<span data-ttu-id="c3372-199">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="c3372-200">5</span><span class="sxs-lookup"><span data-stu-id="c3372-200">5</span></span>|<span data-ttu-id="c3372-201">Был создан новый сегмент сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="c3372-202">Кроме того, при включении трассировки для уже работающего процесса это событие создается для каждого существующего сегмента.</span><span class="sxs-lookup"><span data-stu-id="c3372-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="c3372-203">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-203">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-204">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-204">Field name</span></span>|<span data-ttu-id="c3372-205">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-205">Data type</span></span>|<span data-ttu-id="c3372-206">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="c3372-207">Адрес сегмента.</span><span class="sxs-lookup"><span data-stu-id="c3372-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="c3372-208">Размер сегмента.</span><span class="sxs-lookup"><span data-stu-id="c3372-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="c3372-209">0x0 — куча маленьких объектов.</span><span class="sxs-lookup"><span data-stu-id="c3372-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="c3372-210">0x1 — куча больших объектов.</span><span class="sxs-lookup"><span data-stu-id="c3372-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="c3372-211">0x2 — куча только для чтения.</span><span class="sxs-lookup"><span data-stu-id="c3372-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-212">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="c3372-213">Обратите внимание, что размер сегментов, выделенных сборщиком мусора, зависит от реализации и может быть изменен в любое время, в том числе при периодических обновлениях.</span><span class="sxs-lookup"><span data-stu-id="c3372-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="c3372-214">Приложение не должно делать никаких допущений относительно размера определенного сегмента, полагаться на него или пытаться настроить объем памяти, доступный для выделения сегментов.</span><span class="sxs-lookup"><span data-stu-id="c3372-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="c3372-215">GCFreeSegment_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="c3372-216">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-217">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-217">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-218">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-220">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-220">Informational (4)</span></span>|

<span data-ttu-id="c3372-221">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-221">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-222">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-222">Event</span></span>|<span data-ttu-id="c3372-223">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-223">Event ID</span></span>|<span data-ttu-id="c3372-224">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="c3372-225">6</span><span class="sxs-lookup"><span data-stu-id="c3372-225">6</span></span>|<span data-ttu-id="c3372-226">Сегмент сборки мусора был освобожден.</span><span class="sxs-lookup"><span data-stu-id="c3372-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="c3372-227">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-227">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-228">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-228">Field name</span></span>|<span data-ttu-id="c3372-229">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-229">Data type</span></span>|<span data-ttu-id="c3372-230">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="c3372-231">Адрес сегмента.</span><span class="sxs-lookup"><span data-stu-id="c3372-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-232">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="c3372-233">GCRestartEEBegin_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="c3372-234">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-235">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-235">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-236">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-238">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-238">Informational (4)</span></span>|

<span data-ttu-id="c3372-239">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-239">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-240">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-240">Event</span></span>|<span data-ttu-id="c3372-241">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-241">Event ID</span></span>|<span data-ttu-id="c3372-242">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="c3372-243">7</span><span class="sxs-lookup"><span data-stu-id="c3372-243">7</span></span>|<span data-ttu-id="c3372-244">Началось возобновление приостановленной среды CLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="c3372-245">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="c3372-246">GCRestartEEEnd_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="c3372-247">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-248">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-248">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-249">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-251">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-251">Informational (4)</span></span>|

<span data-ttu-id="c3372-252">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-252">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-253">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-253">Event</span></span>|<span data-ttu-id="c3372-254">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-254">Event Id</span></span>|<span data-ttu-id="c3372-255">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="c3372-256">3</span><span class="sxs-lookup"><span data-stu-id="c3372-256">3</span></span>|<span data-ttu-id="c3372-257">Возобновление приостановленной среды CLR завершено.</span><span class="sxs-lookup"><span data-stu-id="c3372-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="c3372-258">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="c3372-259">GCSuspendEEEnd_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="c3372-260">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-261">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-261">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-262">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-264">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-264">Informational (4)</span></span>|

<span data-ttu-id="c3372-265">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-265">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-266">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-266">Event</span></span>|<span data-ttu-id="c3372-267">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-267">Event ID</span></span>|<span data-ttu-id="c3372-268">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="c3372-269">8</span><span class="sxs-lookup"><span data-stu-id="c3372-269">8</span></span>|<span data-ttu-id="c3372-270">Завершена приостановка механизма выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="c3372-271">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="c3372-272">GCSuspendEEBegin_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="c3372-273">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-274">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-274">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-275">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-277">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-277">Informational (4)</span></span>|

<span data-ttu-id="c3372-278">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-278">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-279">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-279">Event</span></span>|<span data-ttu-id="c3372-280">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-280">Event ID</span></span>|<span data-ttu-id="c3372-281">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="c3372-282">8</span><span class="sxs-lookup"><span data-stu-id="c3372-282">8</span></span>|<span data-ttu-id="c3372-283">Началась приостановка механизма выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="c3372-284">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-284">Field name</span></span>|<span data-ttu-id="c3372-285">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-285">Data type</span></span>|<span data-ttu-id="c3372-286">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="c3372-287">Сборка мусора, *n*-я по счету.</span><span class="sxs-lookup"><span data-stu-id="c3372-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="c3372-288">Причина приостановки EE.</span><span class="sxs-lookup"><span data-stu-id="c3372-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="c3372-289">`0x0`: Приостановка для других</span><span class="sxs-lookup"><span data-stu-id="c3372-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="c3372-290">`0x1`: Приостановка для GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="c3372-291">`0x2`: Suspend для завершения работы AppDomain.</span><span class="sxs-lookup"><span data-stu-id="c3372-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="c3372-292">`0x3`: Приостановка для пошагового шага кода.</span><span class="sxs-lookup"><span data-stu-id="c3372-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="c3372-293">`0x4`: Приостановка для завершения работы.</span><span class="sxs-lookup"><span data-stu-id="c3372-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="c3372-294">`0x5`: Приостановка для отладчика.</span><span class="sxs-lookup"><span data-stu-id="c3372-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="c3372-295">`0x6`: Приостановка для подготовки GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="c3372-296">`0x7`: Приостановка для очистки отладчика</span><span class="sxs-lookup"><span data-stu-id="c3372-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="c3372-297">GCAllocationTick_V3 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="c3372-298">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-299">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-299">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-300">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-302">Verbose (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-302">Verbose (4)</span></span>|

<span data-ttu-id="c3372-303">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-303">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-304">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-304">Event</span></span>|<span data-ttu-id="c3372-305">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-305">Event ID</span></span>|<span data-ttu-id="c3372-306">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="c3372-307">10</span><span class="sxs-lookup"><span data-stu-id="c3372-307">10</span></span>|<span data-ttu-id="c3372-308">Каждый раз выделяется около 100 КБ.</span><span class="sxs-lookup"><span data-stu-id="c3372-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="c3372-309">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-309">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-310">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-310">Field name</span></span>|<span data-ttu-id="c3372-311">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-311">Data type</span></span>|<span data-ttu-id="c3372-312">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="c3372-313">Размер выделения в байтах.</span><span class="sxs-lookup"><span data-stu-id="c3372-313">The allocation size, in bytes.</span></span> <span data-ttu-id="c3372-314">Это значение является точным для выделений, размер которых меньше длины ULONG (4 294 967 295 байт).</span><span class="sxs-lookup"><span data-stu-id="c3372-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="c3372-315">Если выделение больше, это поле содержит усеченное значение.</span><span class="sxs-lookup"><span data-stu-id="c3372-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="c3372-316">Используйте `AllocationAmount64` для очень больших выделений.</span><span class="sxs-lookup"><span data-stu-id="c3372-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="c3372-317">`0x0` — Выделение малых объектов (выделение находится в куче небольших объектов).</span><span class="sxs-lookup"><span data-stu-id="c3372-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="c3372-318">`0x1` — Выделение больших объектов (выделение в куче больших объектов).</span><span class="sxs-lookup"><span data-stu-id="c3372-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="c3372-319">Размер выделения в байтах.</span><span class="sxs-lookup"><span data-stu-id="c3372-319">The allocation size, in bytes.</span></span> <span data-ttu-id="c3372-320">Это значение является точным для очень больших выделений.</span><span class="sxs-lookup"><span data-stu-id="c3372-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="c3372-321">Адрес MethodTable.</span><span class="sxs-lookup"><span data-stu-id="c3372-321">The address of the MethodTable.</span></span> <span data-ttu-id="c3372-322">Если в ходе этого события было выделено несколько типов объектов, указывается адрес MethodTable, соответствующий последнему выделенному объекту (объекту, вызвавшему превышение порогового значения 100 КБ).</span><span class="sxs-lookup"><span data-stu-id="c3372-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="c3372-323">Имя выделенного типа.</span><span class="sxs-lookup"><span data-stu-id="c3372-323">The name of the type that was allocated.</span></span> <span data-ttu-id="c3372-324">Если в ходе этого события было выделено несколько типов объектов, указывается тип последнего выделенного объекта (объекта, вызвавшего превышение порогового значения 100 КБ).</span><span class="sxs-lookup"><span data-stu-id="c3372-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="c3372-325">Куча, в которой был выделен объект.</span><span class="sxs-lookup"><span data-stu-id="c3372-325">The heap where the object was allocated.</span></span> <span data-ttu-id="c3372-326">Это значение равно 0 (нулю) при выполнении сборки мусора на рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="c3372-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="c3372-327">Адрес последнего выделенного объекта.</span><span class="sxs-lookup"><span data-stu-id="c3372-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-328">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="c3372-329">GCCreateConcurrentThread_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="c3372-330">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-331">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-331">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-332">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-334">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-334">Informational (4)</span></span>|
|<span data-ttu-id="c3372-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c3372-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c3372-336">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-336">Informational (4)</span></span>|

<span data-ttu-id="c3372-337">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-337">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-338">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-338">Event</span></span>|<span data-ttu-id="c3372-339">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-339">Event ID</span></span>|<span data-ttu-id="c3372-340">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="c3372-341">11</span><span class="sxs-lookup"><span data-stu-id="c3372-341">11</span></span>|<span data-ttu-id="c3372-342">Был создан параллельный поток сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="c3372-343">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="c3372-344">GCTerminateConcurrentThread_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="c3372-345">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-346">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-346">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-347">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-349">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-349">Informational (4)</span></span>|
|<span data-ttu-id="c3372-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c3372-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c3372-351">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-351">Informational (4)</span></span>|

<span data-ttu-id="c3372-352">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-352">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-353">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-353">Event</span></span>|<span data-ttu-id="c3372-354">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-354">Event ID</span></span>|<span data-ttu-id="c3372-355">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="c3372-356">12</span><span class="sxs-lookup"><span data-stu-id="c3372-356">12</span></span>|<span data-ttu-id="c3372-357">Параллельный поток сборки мусора был завершен.</span><span class="sxs-lookup"><span data-stu-id="c3372-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="c3372-358">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="c3372-359">GCFinalizersBegin_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="c3372-360">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-361">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-361">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-362">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-364">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-364">Informational (4)</span></span>|

<span data-ttu-id="c3372-365">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-365">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-366">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-366">Event</span></span>|<span data-ttu-id="c3372-367">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-367">Event ID</span></span>|<span data-ttu-id="c3372-368">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="c3372-369">14</span><span class="sxs-lookup"><span data-stu-id="c3372-369">14</span></span>|<span data-ttu-id="c3372-370">Начало выполнения методов завершения.</span><span class="sxs-lookup"><span data-stu-id="c3372-370">The start of running finalizers.</span></span>|

<span data-ttu-id="c3372-371">Это событие не содержит данных о событиях.</span><span class="sxs-lookup"><span data-stu-id="c3372-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="c3372-372">GCFinalizersEnd_V1 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="c3372-373">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-374">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-374">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-375">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-377">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-377">Informational (4)</span></span>|

<span data-ttu-id="c3372-378">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-378">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-379">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-379">Event</span></span>|<span data-ttu-id="c3372-380">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-380">Event ID</span></span>|<span data-ttu-id="c3372-381">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="c3372-382">13</span><span class="sxs-lookup"><span data-stu-id="c3372-382">13</span></span>|<span data-ttu-id="c3372-383">Завершение выполнения методов завершения.</span><span class="sxs-lookup"><span data-stu-id="c3372-383">The end of running finalizers.</span></span>|

<span data-ttu-id="c3372-384">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-384">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-385">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-385">Field name</span></span>|<span data-ttu-id="c3372-386">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-386">Data type</span></span>|<span data-ttu-id="c3372-387">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="c3372-388">Число выполненных методов завершения.</span><span class="sxs-lookup"><span data-stu-id="c3372-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="c3372-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-389">win:UInt16</span></span>|<span data-ttu-id="c3372-390">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="c3372-391">Событие Сетгчандле</span><span class="sxs-lookup"><span data-stu-id="c3372-391">SetGCHandle event</span></span>

<span data-ttu-id="c3372-392">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-393">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-393">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-394">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-395">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="c3372-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="c3372-396">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-396">Informational (4)</span></span>|

<span data-ttu-id="c3372-397">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-397">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-398">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-398">Event</span></span>|<span data-ttu-id="c3372-399">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-399">Event ID</span></span>|<span data-ttu-id="c3372-400">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="c3372-401">30</span><span class="sxs-lookup"><span data-stu-id="c3372-401">30</span></span>|<span data-ttu-id="c3372-402">Установлен обработчик GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="c3372-403">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-403">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-404">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-404">Field name</span></span>|<span data-ttu-id="c3372-405">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-405">Data type</span></span>|<span data-ttu-id="c3372-406">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="c3372-407">Адрес выделенного маркера.</span><span class="sxs-lookup"><span data-stu-id="c3372-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="c3372-408">Адрес объекта, маркер которого был создан.</span><span class="sxs-lookup"><span data-stu-id="c3372-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="c3372-409">Тип установленного обработчика GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="c3372-410">`0x0`: Веакшорт</span><span class="sxs-lookup"><span data-stu-id="c3372-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="c3372-411">`0x1`: Веаклонг</span><span class="sxs-lookup"><span data-stu-id="c3372-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="c3372-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="c3372-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="c3372-413">`0x3`: Закреплено</span><span class="sxs-lookup"><span data-stu-id="c3372-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="c3372-414">`0x4`: Переменная</span><span class="sxs-lookup"><span data-stu-id="c3372-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="c3372-415">`0x5`: Рефкаунтед</span><span class="sxs-lookup"><span data-stu-id="c3372-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="c3372-416">`0x6`: Зависимый</span><span class="sxs-lookup"><span data-stu-id="c3372-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="c3372-417">`0x7`: Асинкпиннед</span><span class="sxs-lookup"><span data-stu-id="c3372-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="c3372-418">`0x8`: Дескриптор sizedref</span><span class="sxs-lookup"><span data-stu-id="c3372-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="c3372-419">Поколение объекта, маркер которого был создан.</span><span class="sxs-lookup"><span data-stu-id="c3372-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="c3372-420">Идентификатор AppDomain.</span><span class="sxs-lookup"><span data-stu-id="c3372-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-421">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="c3372-422">Событие Дестройгчандле</span><span class="sxs-lookup"><span data-stu-id="c3372-422">DestroyGCHandle event</span></span>

<span data-ttu-id="c3372-423">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-424">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-424">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-425">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-426">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="c3372-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="c3372-427">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-427">Informational (4)</span></span>|

<span data-ttu-id="c3372-428">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-428">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-429">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-429">Event</span></span>|<span data-ttu-id="c3372-430">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-430">Event ID</span></span>|<span data-ttu-id="c3372-431">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="c3372-432">31</span><span class="sxs-lookup"><span data-stu-id="c3372-432">31</span></span>|<span data-ttu-id="c3372-433">Уничтоженный обработчик GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="c3372-434">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-434">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-435">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-435">Field name</span></span>|<span data-ttu-id="c3372-436">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-436">Data type</span></span>|<span data-ttu-id="c3372-437">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="c3372-438">Адрес уничтоженного маркера.</span><span class="sxs-lookup"><span data-stu-id="c3372-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="c3372-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-439">win:UInt16</span></span>|<span data-ttu-id="c3372-440">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="c3372-441">Событие Пинобжектатгктиме</span><span class="sxs-lookup"><span data-stu-id="c3372-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="c3372-442">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-443">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-443">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-444">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-446">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="c3372-446">Verbose (5)</span></span>|

<span data-ttu-id="c3372-447">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-447">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-448">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-448">Event</span></span>|<span data-ttu-id="c3372-449">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-449">Event ID</span></span>|<span data-ttu-id="c3372-450">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="c3372-451">33</span><span class="sxs-lookup"><span data-stu-id="c3372-451">33</span></span>|<span data-ttu-id="c3372-452">Объект был закреплен во время сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c3372-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="c3372-453">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-453">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-454">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-454">Field name</span></span>|<span data-ttu-id="c3372-455">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-455">Data type</span></span>|<span data-ttu-id="c3372-456">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="c3372-457">Адрес маркера.</span><span class="sxs-lookup"><span data-stu-id="c3372-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="c3372-458">Адрес закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="c3372-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="c3372-459">Размер закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="c3372-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="c3372-460">Имя типа закрепленного объекта.</span><span class="sxs-lookup"><span data-stu-id="c3372-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-461">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="c3372-462">Событие Гктригжеред</span><span class="sxs-lookup"><span data-stu-id="c3372-462">GCTriggered event</span></span>

<span data-ttu-id="c3372-463">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-464">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-464">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-465">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-467">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="c3372-467">Verbose (5)</span></span>|

<span data-ttu-id="c3372-468">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-468">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-469">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-469">Event</span></span>|<span data-ttu-id="c3372-470">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-470">Event ID</span></span>|<span data-ttu-id="c3372-471">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="c3372-472">33</span><span class="sxs-lookup"><span data-stu-id="c3372-472">33</span></span>|<span data-ttu-id="c3372-473">Запущен GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-473">A GC has been triggered.</span></span>|

<span data-ttu-id="c3372-474">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-474">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-475">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-475">Field name</span></span>|<span data-ttu-id="c3372-476">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-476">Data type</span></span>|<span data-ttu-id="c3372-477">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="c3372-478">Причина активации GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="c3372-479">`0x0`: Аллоксмалл</span><span class="sxs-lookup"><span data-stu-id="c3372-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="c3372-480">`0x1`: Принудительно</span><span class="sxs-lookup"><span data-stu-id="c3372-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="c3372-481">`0x2`: Ловмемори</span><span class="sxs-lookup"><span data-stu-id="c3372-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="c3372-482">`0x3`: Пусто</span><span class="sxs-lookup"><span data-stu-id="c3372-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="c3372-483">`0x4`: Аллокларже</span><span class="sxs-lookup"><span data-stu-id="c3372-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="c3372-484">`0x5`: Аутофспацесмаллобжексеап</span><span class="sxs-lookup"><span data-stu-id="c3372-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="c3372-485">`0x6`: Аутофспацеларжеобжексеап</span><span class="sxs-lookup"><span data-stu-id="c3372-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="c3372-486">`0x7`: Индуцеднофорце</span><span class="sxs-lookup"><span data-stu-id="c3372-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="c3372-487">`0x8`: Нагрузка</span><span class="sxs-lookup"><span data-stu-id="c3372-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="c3372-488">`0x9`: Индуцедловмемори</span><span class="sxs-lookup"><span data-stu-id="c3372-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-489">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="c3372-490">Событие Инкреасемеморипрессуре</span><span class="sxs-lookup"><span data-stu-id="c3372-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="c3372-491">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-492">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-492">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-493">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-495">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-495">Information (4)</span></span>|

<span data-ttu-id="c3372-496">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-496">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-497">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-497">Event</span></span>|<span data-ttu-id="c3372-498">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-498">Event ID</span></span>|<span data-ttu-id="c3372-499">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="c3372-500">200</span><span class="sxs-lookup"><span data-stu-id="c3372-500">200</span></span>|<span data-ttu-id="c3372-501">Была увеличена нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="c3372-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="c3372-502">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-502">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-503">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-503">Field Name</span></span>|<span data-ttu-id="c3372-504">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-504">Data type</span></span>|<span data-ttu-id="c3372-505">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="c3372-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-506">win:UInt16</span></span>|<span data-ttu-id="c3372-507">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="c3372-508">Событие Декреасемеморипрессуре</span><span class="sxs-lookup"><span data-stu-id="c3372-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="c3372-509">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-510">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-510">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-511">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-513">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-513">Information (4)</span></span>|

<span data-ttu-id="c3372-514">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-514">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-515">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-515">Event</span></span>|<span data-ttu-id="c3372-516">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-516">Event ID</span></span>|<span data-ttu-id="c3372-517">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="c3372-518">201</span><span class="sxs-lookup"><span data-stu-id="c3372-518">201</span></span>|<span data-ttu-id="c3372-519">Уменьшилась нехватка памяти.</span><span class="sxs-lookup"><span data-stu-id="c3372-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="c3372-520">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-520">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-521">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-521">Field Name</span></span>|<span data-ttu-id="c3372-522">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-522">Data type</span></span>|<span data-ttu-id="c3372-523">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="c3372-524">Освобождено байт.</span><span class="sxs-lookup"><span data-stu-id="c3372-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-525">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="c3372-526">Событие Гкмарквистипе</span><span class="sxs-lookup"><span data-stu-id="c3372-526">GCMarkWithType event</span></span>

<span data-ttu-id="c3372-527">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-528">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-528">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-529">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-531">Информация (4)</span><span class="sxs-lookup"><span data-stu-id="c3372-531">Information (4)</span></span>|

<span data-ttu-id="c3372-532">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-532">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-533">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-533">Event</span></span>|<span data-ttu-id="c3372-534">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-534">Event ID</span></span>|<span data-ttu-id="c3372-535">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="c3372-536">202</span><span class="sxs-lookup"><span data-stu-id="c3372-536">202</span></span>|<span data-ttu-id="c3372-537">Корень GC был помечен на этапе пометки GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="c3372-538">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-538">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-539">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-539">Field Name</span></span>|<span data-ttu-id="c3372-540">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-540">Data type</span></span>|<span data-ttu-id="c3372-541">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="c3372-542">Номер кучи.</span><span class="sxs-lookup"><span data-stu-id="c3372-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="c3372-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c3372-543">win:UInt16</span></span>|<span data-ttu-id="c3372-544">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="c3372-545">Корневой тип GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-545">The GC root type.</span></span><br/><br/><span data-ttu-id="c3372-546">`0x0`: Stack</span><span class="sxs-lookup"><span data-stu-id="c3372-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="c3372-547">`0x1`: Финализатор</span><span class="sxs-lookup"><span data-stu-id="c3372-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="c3372-548">`0x2`: Handle</span><span class="sxs-lookup"><span data-stu-id="c3372-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="c3372-549">`0x3`: Более старая</span><span class="sxs-lookup"><span data-stu-id="c3372-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="c3372-550">`0x4`: Дескриптор sizedref</span><span class="sxs-lookup"><span data-stu-id="c3372-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="c3372-551">`0x5`: Переполнение</span><span class="sxs-lookup"><span data-stu-id="c3372-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="c3372-552">Число помеченных байтов.</span><span class="sxs-lookup"><span data-stu-id="c3372-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="c3372-553">GCJoin_V2 событие</span><span class="sxs-lookup"><span data-stu-id="c3372-553">GCJoin_V2 event</span></span>

<span data-ttu-id="c3372-554">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="c3372-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c3372-555">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="c3372-555">Keyword for raising the event</span></span>|<span data-ttu-id="c3372-556">Level</span><span class="sxs-lookup"><span data-stu-id="c3372-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c3372-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="c3372-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="c3372-558">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="c3372-558">Verbose (5)</span></span>|

<span data-ttu-id="c3372-559">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="c3372-559">The following table shows the event information:</span></span>

|<span data-ttu-id="c3372-560">Событие</span><span class="sxs-lookup"><span data-stu-id="c3372-560">Event</span></span>|<span data-ttu-id="c3372-561">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="c3372-561">Event ID</span></span>|<span data-ttu-id="c3372-562">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="c3372-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="c3372-563">203</span><span class="sxs-lookup"><span data-stu-id="c3372-563">203</span></span>|<span data-ttu-id="c3372-564">Присоединенный поток GC.</span><span class="sxs-lookup"><span data-stu-id="c3372-564">A GC thread joined.</span></span>|

<span data-ttu-id="c3372-565">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="c3372-565">The following table shows the event data:</span></span>

|<span data-ttu-id="c3372-566">Имя поля</span><span class="sxs-lookup"><span data-stu-id="c3372-566">Field name</span></span>|<span data-ttu-id="c3372-567">Тип данных</span><span class="sxs-lookup"><span data-stu-id="c3372-567">Data type</span></span>|<span data-ttu-id="c3372-568">Описание</span><span class="sxs-lookup"><span data-stu-id="c3372-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="c3372-569">Номер кучи</span><span class="sxs-lookup"><span data-stu-id="c3372-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="c3372-570">Указывает, инициируется ли это событие в начале объединения или окончания объединения (для начала присоединение `0x0` , `0x1` для конца объединения)</span><span class="sxs-lookup"><span data-stu-id="c3372-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="c3372-571">Тип объединения.</span><span class="sxs-lookup"><span data-stu-id="c3372-571">The join type.</span></span> <br/><br/><span data-ttu-id="c3372-572">`0x0`: Последнее соединение</span><span class="sxs-lookup"><span data-stu-id="c3372-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="c3372-573">`0x1`: Соединение</span><span class="sxs-lookup"><span data-stu-id="c3372-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="c3372-574">`0x2`: Перезапустить</span><span class="sxs-lookup"><span data-stu-id="c3372-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="c3372-575">`0x3`: Первое обратная связь</span><span class="sxs-lookup"><span data-stu-id="c3372-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="c3372-576">`0x4`: Обратная связь</span><span class="sxs-lookup"><span data-stu-id="c3372-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="c3372-577">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c3372-577">Unique ID for the instance of CoreCLR.</span></span>|
