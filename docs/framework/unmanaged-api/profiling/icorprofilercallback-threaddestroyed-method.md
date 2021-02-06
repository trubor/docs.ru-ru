---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ThreadDestroyed'
title: Метод ICorProfilerCallback::ThreadDestroyed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 63c8c4c523cb398bd7c766fc41bc669a2d74045e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657196"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="005dc-103">Метод ICorProfilerCallback::ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="005dc-103">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="005dc-104">Уведомляет профилировщик о том, что поток был уничтожен.</span><span class="sxs-lookup"><span data-stu-id="005dc-104">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="005dc-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="005dc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="005dc-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="005dc-107">окне Идентификатор уничтоженного потока.</span><span class="sxs-lookup"><span data-stu-id="005dc-107">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="005dc-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="005dc-108">Remarks</span></span>  

 <span data-ttu-id="005dc-109">`threadId`Значение больше не является допустимым во время этого вызова.</span><span class="sxs-lookup"><span data-stu-id="005dc-109">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="005dc-110">Требования</span><span class="sxs-lookup"><span data-stu-id="005dc-110">Requirements</span></span>  

 <span data-ttu-id="005dc-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="005dc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="005dc-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="005dc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="005dc-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="005dc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="005dc-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="005dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005dc-115">См. также</span><span class="sxs-lookup"><span data-stu-id="005dc-115">See also</span></span>

- [<span data-ttu-id="005dc-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="005dc-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="005dc-117">Метод ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="005dc-117">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
