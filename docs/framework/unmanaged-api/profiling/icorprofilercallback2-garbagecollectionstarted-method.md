---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: GarbageCollectionStarted'
title: Метод ICorProfilerCallback2::GarbageCollectionStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: 2b57a21dc3a1751b5d4767ea940f64df61af4318
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647886"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="a0542-103">Метод ICorProfilerCallback2::GarbageCollectionStarted</span><span class="sxs-lookup"><span data-stu-id="a0542-103">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>

<span data-ttu-id="a0542-104">Уведомляет профилировщик кода о начале сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a0542-104">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0542-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a0542-105">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0542-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a0542-106">Parameters</span></span>  

 `cGenerations`  
 <span data-ttu-id="a0542-107">окне Общее число записей в `generationCollected` массиве.</span><span class="sxs-lookup"><span data-stu-id="a0542-107">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="a0542-108">окне Массив логических значений, которые относятся к `true` сбору данных, соответствующих индексу массива, при сборе мусора; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="a0542-108">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="a0542-109">Массив индексируется по значению перечисления [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , которое указывает на поколение.</span><span class="sxs-lookup"><span data-stu-id="a0542-109">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="a0542-110">окне Значение перечисления [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , указывающее причину принудительной сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a0542-110">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0542-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a0542-111">Remarks</span></span>  

 <span data-ttu-id="a0542-112">Все обратные вызовы, относящиеся к этой сборке мусора, будут выполняться между `GarbageCollectionStarted` обратным вызовом и соответствующим обратным вызовом [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a0542-112">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="a0542-113">Эти обратные вызовы не должны выполняться в одном потоке.</span><span class="sxs-lookup"><span data-stu-id="a0542-113">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="a0542-114">Профилировщик может быть в безопасности проверять объекты в исходных расположениях во время `GarbageCollectionStarted` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="a0542-114">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="a0542-115">Сборщик мусора начнет перемещать объекты после возврата из `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="a0542-115">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="a0542-116">После возвращения профилировщика из этого обратного вызова профилировщик должен рассматривать все идентификаторы объектов как недопустимые до получения `ICorProfilerCallback2::GarbageCollectionFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="a0542-116">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0542-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a0542-117">Requirements</span></span>  

 <span data-ttu-id="a0542-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0542-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0542-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0542-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0542-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0542-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0542-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0542-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0542-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a0542-122">See also</span></span>

- [<span data-ttu-id="a0542-123">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a0542-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a0542-124">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="a0542-124">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
