---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ObjectAllocated'
title: Метод ICorProfilerCallback::ObjectAllocated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 58b58aeb4bb88d0df32cebc32440317a4d23632d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745168"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="721b1-103">Метод ICorProfilerCallback::ObjectAllocated</span><span class="sxs-lookup"><span data-stu-id="721b1-103">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="721b1-104">Уведомляет профилировщик о том, что память в куче была выделена для объекта.</span><span class="sxs-lookup"><span data-stu-id="721b1-104">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="721b1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="721b1-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="721b1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="721b1-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="721b1-107">окне Идентификатор объекта, для которого была выделена память.</span><span class="sxs-lookup"><span data-stu-id="721b1-107">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="721b1-108">окне Идентификатор класса, экземпляр которого является объектом.</span><span class="sxs-lookup"><span data-stu-id="721b1-108">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="721b1-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="721b1-109">Remarks</span></span>  

 <span data-ttu-id="721b1-110">`ObjectedAllocated`Метод не вызывается для выделений из стека или неуправляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="721b1-110">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="721b1-111">`classId`Параметр может ссылаться на класс в управляемом коде, который еще не был загружен.</span><span class="sxs-lookup"><span data-stu-id="721b1-111">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="721b1-112">Профилировщик получит обратный вызов загрузки класса для этого класса сразу после `ObjectAllocated` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="721b1-112">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="721b1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="721b1-113">Requirements</span></span>  

 <span data-ttu-id="721b1-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="721b1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="721b1-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="721b1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="721b1-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="721b1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="721b1-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="721b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="721b1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="721b1-118">See also</span></span>

- [<span data-ttu-id="721b1-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="721b1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="721b1-120">Метод ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="721b1-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="721b1-121">Метод ClassLoadFinished</span><span class="sxs-lookup"><span data-stu-id="721b1-121">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
