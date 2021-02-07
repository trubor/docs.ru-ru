---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Обжектсаллокатедбикласс'
title: Метод ICorProfilerCallback::ObjectsAllocatedByClass
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: df9f3dde27664de7db4afb264b221f640753ddb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745064"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="bcf9c-103">Метод ICorProfilerCallback::ObjectsAllocatedByClass</span><span class="sxs-lookup"><span data-stu-id="bcf9c-103">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="bcf9c-104">Уведомляет профилировщик о количестве экземпляров каждого указанного класса, созданных с момента последнего сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-104">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf9c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bcf9c-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcf9c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bcf9c-106">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="bcf9c-107">окне Размер `classIds` `cObjects` массивов и.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-107">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="bcf9c-108">окне Массив идентификаторов классов, где каждый идентификатор указывает класс с одним или несколькими экземплярами.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-108">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="bcf9c-109">окне Массив целых чисел, где каждое целое число указывает количество экземпляров для соответствующего класса в `classIds` массиве.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-109">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcf9c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="bcf9c-110">Remarks</span></span>  

 <span data-ttu-id="bcf9c-111">`classIds` `cObjects` Массивы и являются параллельными массивами.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-111">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="bcf9c-112">Например, `classIds[i]` и `cObjects[i]` сослаться на один и тот же класс.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-112">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="bcf9c-113">Если с момента предыдущего сбора мусора экземпляр класса не был создан, класс опускается.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-113">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="bcf9c-114">`ObjectsAllocatedByClass`Обратный вызов не будет сообщать объекты, выделенные в куче больших объектов.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-114">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="bcf9c-115">Числа, сообщаемые, `ObjectsAllocatedByClass` являются приблизительными.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-115">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="bcf9c-116">Для точного числа счетчиков используйте параметр [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="bcf9c-116">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="bcf9c-117">`classIds`Массив может содержать одну или несколько записей null, если соответствующий `cObjects` массив имеет типы, выгрузка которых выполняется.</span><span class="sxs-lookup"><span data-stu-id="bcf9c-117">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcf9c-118">Требования</span><span class="sxs-lookup"><span data-stu-id="bcf9c-118">Requirements</span></span>  

 <span data-ttu-id="bcf9c-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcf9c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcf9c-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bcf9c-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcf9c-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcf9c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcf9c-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcf9c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcf9c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="bcf9c-123">See also</span></span>

- [<span data-ttu-id="bcf9c-124">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bcf9c-124">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
