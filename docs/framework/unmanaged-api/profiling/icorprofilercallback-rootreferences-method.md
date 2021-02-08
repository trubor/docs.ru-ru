---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RootReferences'
title: Метод ICorProfilerCallback::RootReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: e09434c425784e646c9856693abdfd4ac0d49273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788869"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="73099-103">Метод ICorProfilerCallback::RootReferences</span><span class="sxs-lookup"><span data-stu-id="73099-103">ICorProfilerCallback::RootReferences Method</span></span>

<span data-ttu-id="73099-104">Уведомляет профилировщик о получении сведений о корневых ссылках после сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="73099-104">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73099-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73099-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="73099-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="73099-106">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="73099-107">окне Число ссылок в `rootRefIds` массиве.</span><span class="sxs-lookup"><span data-stu-id="73099-107">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="73099-108">окне Массив идентификаторов объектов, ссылающихся либо на статический объект, либо на объект в стеке.</span><span class="sxs-lookup"><span data-stu-id="73099-108">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73099-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="73099-109">Remarks</span></span>  

 <span data-ttu-id="73099-110">`RootReferences`Для уведомления профилировщика вызываются методы и [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73099-110">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="73099-111">Профилировщики обычно реализуют один или другой, но не оба, так как передаваемые сведения `RootReferences2` являются надмножеством переданного `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="73099-111">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="73099-112">`rootRefIds`Массив может содержать пустой объект.</span><span class="sxs-lookup"><span data-stu-id="73099-112">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="73099-113">Например, все ссылки на объекты, объявленные в стеке, рассматриваются сборщиком мусора как корни и всегда будут сообщать о них.</span><span class="sxs-lookup"><span data-stu-id="73099-113">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="73099-114">Идентификаторы объектов, возвращаемые, `RootReferences` недопустимы во время обратного вызова, так как сборка мусора может находиться в процессе перемещения объектов из старых адресов в новые адреса.</span><span class="sxs-lookup"><span data-stu-id="73099-114">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="73099-115">Таким образом, профилировщики не должны пытаться проверять объекты во время `RootReferences` вызова.</span><span class="sxs-lookup"><span data-stu-id="73099-115">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="73099-116">При вызове [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) все объекты были перемещены в новые расположения и могут быть безопасно проверены.</span><span class="sxs-lookup"><span data-stu-id="73099-116">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73099-117">Требования</span><span class="sxs-lookup"><span data-stu-id="73099-117">Requirements</span></span>  

 <span data-ttu-id="73099-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73099-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73099-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73099-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73099-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73099-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73099-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73099-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73099-122">См. также</span><span class="sxs-lookup"><span data-stu-id="73099-122">See also</span></span>

- [<span data-ttu-id="73099-123">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="73099-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
