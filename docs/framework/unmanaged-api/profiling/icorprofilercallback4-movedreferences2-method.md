---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: MovedReferences2'
title: Метод ICorProfilerCallback4::MovedReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 37bd1c91866a583bf4ba04e3e532d0efe5a11fc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788739"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="08d86-103">Метод ICorProfilerCallback4::MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="08d86-103">ICorProfilerCallback4::MovedReferences2 Method</span></span>

<span data-ttu-id="08d86-104">Вызывается для предоставления сведений о структуре объектов в куче в результате сжатия сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="08d86-104">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="08d86-105">Этот метод вызывается, если профилировщик реализовал интерфейс [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="08d86-105">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="08d86-106">Этот обратный вызов заменяет метод [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) , поскольку он может сообщать о больших диапазонах объектов, длина которых превышает то, что может быть выражено в ulong.</span><span class="sxs-lookup"><span data-stu-id="08d86-106">This callback replaces the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d86-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08d86-107">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="08d86-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="08d86-108">Parameters</span></span>  

 `cMovedObjectIDRanges`  
 <span data-ttu-id="08d86-109">[in] Количество блоков смежных объектов, перемещенных в результате сжатия сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="08d86-109">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="08d86-110">Таким образом значение `cMovedObjectIDRanges` представляет общий размер массивов `oldObjectIDRangeStart`, `newObjectIDRangeStart` и `cObjectIDRangeLength`.</span><span class="sxs-lookup"><span data-stu-id="08d86-110">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="08d86-111">Следующие три аргумента `MovedReferences2` являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="08d86-111">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="08d86-112">Другими словами, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]` и `cObjectIDRangeLength[i]` относятся к одному и тому же блоку смежных объектов.</span><span class="sxs-lookup"><span data-stu-id="08d86-112">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="08d86-113">[in] Массив значений `ObjectID`, каждое из которых является старым (до сборки мусора) начальным адресом блока смежных активных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="08d86-113">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="08d86-114">[in] Массив значений `ObjectID`, каждое из которых является новым (после сборки мусора) начальным адресом блока смежных активных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="08d86-114">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="08d86-115">[in] Массив целых чисел, каждое из которых представляет размер блока смежных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="08d86-115">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="08d86-116">Размер указывается для каждого блока, ссылка на который имеется в массивах `oldObjectIDRangeStart` и `newObjectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="08d86-116">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08d86-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="08d86-117">Remarks</span></span>  

 <span data-ttu-id="08d86-118">Сжатие сборки мусора без сжатия освобождает память, занятую "мертвыми" объектами, и сжимает это освобожденное пространство.</span><span class="sxs-lookup"><span data-stu-id="08d86-118">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="08d86-119">В результате динамические объекты могут быть перемещены в кучу, и значения `ObjectID`, распространенные предыдущими уведомлениями, могут измениться.</span><span class="sxs-lookup"><span data-stu-id="08d86-119">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="08d86-120">Предположим, что существующее значение `ObjectID` (`oldObjectID`) находится в следующем диапазоне:</span><span class="sxs-lookup"><span data-stu-id="08d86-120">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="08d86-121">В этом случае смещение от начала диапазона к началу объекта следующее:</span><span class="sxs-lookup"><span data-stu-id="08d86-121">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="08d86-122">Для любого значения параметра `i`, который находится в следующем диапазоне:</span><span class="sxs-lookup"><span data-stu-id="08d86-122">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="08d86-123">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="08d86-123">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="08d86-124">можно вычислить новый `ObjectID` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="08d86-124">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="08d86-125">`newObjectID` = `newObjectIDRangeStart[i]` + ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="08d86-125">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="08d86-126">Ни одно из значений `ObjectID`, переданных `MovedReferences2`, не является допустимым во время самого обратного вызова, потому что сборка мусора может находиться в процессе перемещения объектов из старого в новое расположение.</span><span class="sxs-lookup"><span data-stu-id="08d86-126">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="08d86-127">В связи с этим профилировщикам не следует пытаться проверять объекты во время вызова `MovedReferences2`.</span><span class="sxs-lookup"><span data-stu-id="08d86-127">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="08d86-128">Обратный вызов [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) указывает, что все объекты были перемещены в новые расположения, и проверку можно выполнить.</span><span class="sxs-lookup"><span data-stu-id="08d86-128">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="08d86-129">Если профилировщик реализует интерфейсы [ICorProfilerCallback](icorprofilercallback-interface.md) и [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `MovedReferences2` метод вызывается перед методом [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) , но только в случае `MovedReferences2` успешного возврата методом.</span><span class="sxs-lookup"><span data-stu-id="08d86-129">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="08d86-130">Профилировщики могут возвращать значение HRESULT, указывающее на сбой в методе `MovedReferences2`, что позволяет избежать вызова второго метода.</span><span class="sxs-lookup"><span data-stu-id="08d86-130">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d86-131">Требования</span><span class="sxs-lookup"><span data-stu-id="08d86-131">Requirements</span></span>  

 <span data-ttu-id="08d86-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d86-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d86-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08d86-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08d86-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08d86-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08d86-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d86-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d86-136">См. также</span><span class="sxs-lookup"><span data-stu-id="08d86-136">See also</span></span>

- [<span data-ttu-id="08d86-137">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="08d86-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="08d86-138">Метод MovedReferences</span><span class="sxs-lookup"><span data-stu-id="08d86-138">MovedReferences Method</span></span>](icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="08d86-139">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="08d86-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="08d86-140">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="08d86-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="08d86-141">Профилирование</span><span class="sxs-lookup"><span data-stu-id="08d86-141">Profiling</span></span>](index.md)
