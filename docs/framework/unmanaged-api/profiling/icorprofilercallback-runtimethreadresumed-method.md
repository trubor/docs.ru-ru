---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RuntimeThreadResumed'
title: Метод ICorProfilerCallback::RuntimeThreadResumed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: a01be057bb442c69890d3b1cb4ebe1f861d2518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657350"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="b3331-103">Метод ICorProfilerCallback::RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="b3331-103">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="b3331-104">Уведомляет профилировщик о том, что указанный поток возобновил работу после приостановки.</span><span class="sxs-lookup"><span data-stu-id="b3331-104">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3331-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3331-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3331-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3331-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="b3331-107">окне Идентификатор возобновленного потока.</span><span class="sxs-lookup"><span data-stu-id="b3331-107">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3331-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b3331-108">Requirements</span></span>  

 <span data-ttu-id="b3331-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3331-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3331-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3331-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3331-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3331-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3331-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3331-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3331-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b3331-113">See also</span></span>

- [<span data-ttu-id="b3331-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b3331-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b3331-115">Метод RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="b3331-115">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
