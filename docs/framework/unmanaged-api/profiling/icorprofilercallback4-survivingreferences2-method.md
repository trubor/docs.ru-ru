---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: SurvivingReferences2'
title: Метод ICorProfilerCallback4::SurvivingReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: d092729c77b0c4feb253bb2f54968f7ff8bdbb2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788687"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="403c5-103">Метод ICorProfilerCallback4::SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="403c5-103">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>

<span data-ttu-id="403c5-104">Предоставляет информацию о структуре объектов в куче в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="403c5-104">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="403c5-105">Этот метод вызывается, если профилировщик реализовал интерфейс [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="403c5-105">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="403c5-106">Этот обратный вызов заменяет метод [ICorProfilerCallback2:: SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) , так как он может сообщать о больших диапазонах объектов, длина которых превышает то, что может быть выражено в ulong.</span><span class="sxs-lookup"><span data-stu-id="403c5-106">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="403c5-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="403c5-107">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="403c5-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="403c5-108">Parameters</span></span>  

 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="403c5-109">[in] Количество блоков смежных объектов, оставшихся в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="403c5-109">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="403c5-110">То есть значение `cSurvivingObjectIDRanges` является размером массивов `objectIDRangeStart` и `cObjectIDRangeLength`, в которых хранятся идентификаторы `ObjectID` и длины каждого блока объектов соответственно.</span><span class="sxs-lookup"><span data-stu-id="403c5-110">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="403c5-111">Следующие два аргумента `SurvivingReferences2` являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="403c5-111">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="403c5-112">Иными словами, `objectIDRangeStart` и `cObjectIDRangeLength` относятся к одному и тому же блоку смежных объектов.</span><span class="sxs-lookup"><span data-stu-id="403c5-112">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="403c5-113">[in] Массив значений `ObjectID`, каждое из которых является начальным адресом блока смежных активных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="403c5-113">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="403c5-114">[in] Массив целых чисел, каждое из которых представляет размер оставшегося блока смежных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="403c5-114">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="403c5-115">Размер указывается для каждого блока, ссылка на который имеется в массиве `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="403c5-115">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="403c5-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="403c5-116">Remarks</span></span>  

 <span data-ttu-id="403c5-117">Для определения того, уцелел ли объект после сборки мусора, элементы массивов `objectIDRangeStart` и `cObjectIDRangeLength` должны интерпретироваться следующим образом.</span><span class="sxs-lookup"><span data-stu-id="403c5-117">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="403c5-118">Предположим, что значение `ObjectID` (`ObjectID`) находится в следующем диапазоне:</span><span class="sxs-lookup"><span data-stu-id="403c5-118">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="403c5-119">При любом значении `i`, находящемся в указанном ниже диапазоне, объект уцелел после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="403c5-119">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="403c5-120">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="403c5-120">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="403c5-121">Сборка мусора без сжатия освобождает память, занятую "мертвыми" объектами, но не сжимает освобожденное пространство.</span><span class="sxs-lookup"><span data-stu-id="403c5-121">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="403c5-122">В результате этого память возвращается в кучу, но активные объекты не перемещаются.</span><span class="sxs-lookup"><span data-stu-id="403c5-122">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="403c5-123">Среда CLR вызывает метод `SurvivingReferences2` для выполнения сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="403c5-123">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="403c5-124">Для сжатия сборок мусора вместо нее вызывается [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="403c5-124">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="403c5-125">Отдельная операция сборки мусора может предусматривать сжатие для одного поколения и не предусматривать — для другого.</span><span class="sxs-lookup"><span data-stu-id="403c5-125">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="403c5-126">Для сборки мусора в любом конкретном поколении профилировщик получит либо обратный вызов `SurvivingReferences2` , либо обратный вызов [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) , но не оба.</span><span class="sxs-lookup"><span data-stu-id="403c5-126">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="403c5-127">Несколько обратных вызовов `SurvivingReferences2` может быть получено в ходе определенной сборки мусора из-за ограниченной внутренней буферизации, нескольких обратных вызовов во время сборки мусора на сервере и по другим причинам.</span><span class="sxs-lookup"><span data-stu-id="403c5-127">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="403c5-128">При получении нескольких обратных вызовов во время сборки мусора информация накапливается — все ссылки, сообщаемые в обратных вызовах `SurvivingReferences2`, сохранятся после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="403c5-128">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="403c5-129">Если профилировщик реализует интерфейсы [ICorProfilerCallback](icorprofilercallback-interface.md) и [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `SurvivingReferences2` метод вызывается перед методом [ICorProfilerCallback2:: SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) , но только в случае `SurvivingReferences2` успешного возврата.</span><span class="sxs-lookup"><span data-stu-id="403c5-129">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="403c5-130">Профилировщики могут возвращать значение HRESULT, указывающее на сбой метода `SurvivingReferences2`, что позволяет избежать вызова второго метода.</span><span class="sxs-lookup"><span data-stu-id="403c5-130">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="403c5-131">Требования</span><span class="sxs-lookup"><span data-stu-id="403c5-131">Requirements</span></span>  

 <span data-ttu-id="403c5-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="403c5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="403c5-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="403c5-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="403c5-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="403c5-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="403c5-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="403c5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="403c5-136">См. также</span><span class="sxs-lookup"><span data-stu-id="403c5-136">See also</span></span>

- [<span data-ttu-id="403c5-137">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="403c5-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="403c5-138">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="403c5-138">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="403c5-139">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="403c5-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
