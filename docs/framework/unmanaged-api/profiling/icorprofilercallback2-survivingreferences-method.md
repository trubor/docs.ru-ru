---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: SurvivingReferences'
title: Метод ICorProfilerCallback2::SurvivingReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
ms.openlocfilehash: 64edaf5388aeb0bded3de8e8bbde0bf7a5159ed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799061"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="87f05-103">Метод ICorProfilerCallback2::SurvivingReferences</span><span class="sxs-lookup"><span data-stu-id="87f05-103">ICorProfilerCallback2::SurvivingReferences Method</span></span>

<span data-ttu-id="87f05-104">Предоставляет информацию о структуре объектов в куче в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="87f05-104">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f05-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="87f05-105">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f05-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="87f05-106">Parameters</span></span>  

 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="87f05-107">[in] Количество блоков смежных объектов, оставшихся в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="87f05-107">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="87f05-108">То есть значение `cSurvivingObjectIDRanges` является размером массивов `objectIDRangeStart` и `cObjectIDRangeLength`, в которых хранятся идентификаторы `ObjectID` и длины каждого блока объектов соответственно.</span><span class="sxs-lookup"><span data-stu-id="87f05-108">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="87f05-109">Следующие два аргумента `SurvivingReferences` являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="87f05-109">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="87f05-110">Иными словами, `objectIDRangeStart` и `cObjectIDRangeLength` относятся к одному и тому же блоку смежных объектов.</span><span class="sxs-lookup"><span data-stu-id="87f05-110">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="87f05-111">[in] Массив значений `ObjectID`, каждое из которых является начальным адресом блока смежных активных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="87f05-111">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="87f05-112">[in] Массив целых чисел, каждое из которых представляет размер оставшегося блока смежных объектов в памяти.</span><span class="sxs-lookup"><span data-stu-id="87f05-112">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="87f05-113">Размер указывается для каждого блока, ссылка на который имеется в массиве `objectIDRangeStart`.</span><span class="sxs-lookup"><span data-stu-id="87f05-113">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87f05-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="87f05-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="87f05-115">Этот метод сообщает размеры как `MAX_ULONG` для объектов с размером более 4 Гб на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="87f05-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="87f05-116">Для объектов, размер которых превышает 4 ГБ, используйте вместо него метод [ICorProfilerCallback4:: SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87f05-116">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="87f05-117">Для определения того, уцелел ли объект после сборки мусора, элементы массивов `objectIDRangeStart` и `cObjectIDRangeLength` должны интерпретироваться следующим образом.</span><span class="sxs-lookup"><span data-stu-id="87f05-117">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="87f05-118">Предположим, что значение `ObjectID` (`ObjectID`) находится в следующем диапазоне:</span><span class="sxs-lookup"><span data-stu-id="87f05-118">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="87f05-119">При любом значении `i`, находящемся в указанном ниже диапазоне, объект уцелел после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="87f05-119">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="87f05-120">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="87f05-120">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="87f05-121">Сборка мусора без сжатия освобождает память, занятую "мертвыми" объектами, но не сжимает освобожденное пространство.</span><span class="sxs-lookup"><span data-stu-id="87f05-121">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="87f05-122">В результате этого память возвращается в кучу, но активные объекты не перемещаются.</span><span class="sxs-lookup"><span data-stu-id="87f05-122">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="87f05-123">Среда CLR вызывает метод `SurvivingReferences` для выполнения сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="87f05-123">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="87f05-124">Для сжатия сборок мусора вместо этого вызывается метод [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87f05-124">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="87f05-125">Отдельная операция сборки мусора может предусматривать сжатие для одного поколения и не предусматривать — для другого.</span><span class="sxs-lookup"><span data-stu-id="87f05-125">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="87f05-126">Для сборки мусора в каком-либо конкретном поколении профилировщик получит либо обратный вызов `SurvivingReferences`, либо обратный вызов `MovedReferences` (но не оба вызова).</span><span class="sxs-lookup"><span data-stu-id="87f05-126">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="87f05-127">Несколько обратных вызовов `SurvivingReferences` может быть получено в ходе определенной сборки мусора из-за ограниченной внутренней буферизации, нескольких потоков отчетов в случае сборки мусора на сервере и по другим причинам.</span><span class="sxs-lookup"><span data-stu-id="87f05-127">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="87f05-128">При получении нескольких обратных вызовов во время сборки мусора информация накапливается — все ссылки, сообщаемые в обратных вызовах `SurvivingReferences`, сохранятся после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="87f05-128">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f05-129">Требования</span><span class="sxs-lookup"><span data-stu-id="87f05-129">Requirements</span></span>  

 <span data-ttu-id="87f05-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f05-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f05-131">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87f05-131">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87f05-132">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87f05-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87f05-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f05-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f05-134">См. также</span><span class="sxs-lookup"><span data-stu-id="87f05-134">See also</span></span>

- [<span data-ttu-id="87f05-135">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="87f05-135">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="87f05-136">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="87f05-136">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="87f05-137">Метод SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="87f05-137">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
