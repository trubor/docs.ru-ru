---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ObjectReferences'
title: Метод ICorProfilerCallback::ObjectReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 55ea6fae87ecb6534af322fc9d5055c8a247f37a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745116"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="83a0d-103">Метод ICorProfilerCallback::ObjectReferences</span><span class="sxs-lookup"><span data-stu-id="83a0d-103">ICorProfilerCallback::ObjectReferences Method</span></span>

<span data-ttu-id="83a0d-104">Уведомляет профилировщик об объектах в памяти, на которые ссылается указанный объект.</span><span class="sxs-lookup"><span data-stu-id="83a0d-104">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a0d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83a0d-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a0d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83a0d-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="83a0d-107">окне Идентификатор объекта, ссылающегося на объекты.</span><span class="sxs-lookup"><span data-stu-id="83a0d-107">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="83a0d-108">окне Идентификатор класса, экземпляр которого является указанным объектом.</span><span class="sxs-lookup"><span data-stu-id="83a0d-108">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="83a0d-109">окне Количество объектов, на которые ссылается указанный объект (то есть количество элементов в `objectRefIds` массиве).</span><span class="sxs-lookup"><span data-stu-id="83a0d-109">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="83a0d-110">окне Массив идентификаторов объектов, на которые ссылается `objectId` .</span><span class="sxs-lookup"><span data-stu-id="83a0d-110">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83a0d-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="83a0d-111">Remarks</span></span>  

 <span data-ttu-id="83a0d-112">`ObjectReferences`Метод вызывается для каждого объекта, остающегося в куче после завершения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83a0d-112">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="83a0d-113">Если профилировщик возвращает ошибку из этого обратного вызова, службы профилирования будут прекращены вызовом этого обратного вызова до следующей сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83a0d-113">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="83a0d-114">`ObjectReferences`Обратный вызов можно использовать в сочетании с обратным вызовом [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) , чтобы создать полный граф ссылки на объект для среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="83a0d-114">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="83a0d-115">Общеязыковая среда выполнения (CLR) гарантирует, что в методе каждый раз сообщается ссылка на каждый объект `ObjectReferences` .</span><span class="sxs-lookup"><span data-stu-id="83a0d-115">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="83a0d-116">Идентификаторы объектов, возвращаемые, `ObjectReferences` недопустимы во время обратного вызова, так как сборка мусора может находиться в процессе перемещения объектов.</span><span class="sxs-lookup"><span data-stu-id="83a0d-116">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="83a0d-117">Таким образом, профилировщики не должны пытаться проверять объекты во время `ObjectReferences` вызова.</span><span class="sxs-lookup"><span data-stu-id="83a0d-117">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="83a0d-118">При вызове [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) сборка мусора завершается, и проверка может быть безопасно выполнена.</span><span class="sxs-lookup"><span data-stu-id="83a0d-118">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="83a0d-119">Значение NULL `ClassId` указывает, что `objectId` имеет тип, который выгружается.</span><span class="sxs-lookup"><span data-stu-id="83a0d-119">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a0d-120">Требования</span><span class="sxs-lookup"><span data-stu-id="83a0d-120">Requirements</span></span>  

 <span data-ttu-id="83a0d-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a0d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a0d-122">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83a0d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83a0d-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83a0d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83a0d-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a0d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a0d-125">См. также</span><span class="sxs-lookup"><span data-stu-id="83a0d-125">See also</span></span>

- [<span data-ttu-id="83a0d-126">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="83a0d-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
