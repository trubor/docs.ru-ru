---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ThreadCreated'
title: Метод ICorProfilerCallback::ThreadCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 8b6208856b78298f643161cd6bb78773ac86bc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657207"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="96ab2-103">Метод ICorProfilerCallback::ThreadCreated</span><span class="sxs-lookup"><span data-stu-id="96ab2-103">ICorProfilerCallback::ThreadCreated Method</span></span>

<span data-ttu-id="96ab2-104">Уведомляет профилировщик о том, что поток был создан.</span><span class="sxs-lookup"><span data-stu-id="96ab2-104">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ab2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96ab2-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="96ab2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96ab2-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="96ab2-107">окне Идентификатор созданного потока.</span><span class="sxs-lookup"><span data-stu-id="96ab2-107">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96ab2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="96ab2-108">Remarks</span></span>  

 <span data-ttu-id="96ab2-109">`threadId`Значение немедленно является допустимым.</span><span class="sxs-lookup"><span data-stu-id="96ab2-109">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ab2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="96ab2-110">Requirements</span></span>  

 <span data-ttu-id="96ab2-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ab2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ab2-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96ab2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96ab2-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96ab2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ab2-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ab2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ab2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="96ab2-115">See also</span></span>

- [<span data-ttu-id="96ab2-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="96ab2-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="96ab2-117">Метод ThreadDestroyed</span><span class="sxs-lookup"><span data-stu-id="96ab2-117">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
