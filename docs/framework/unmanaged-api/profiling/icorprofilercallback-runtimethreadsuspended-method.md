---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RuntimeThreadSuspended'
title: Метод ICorProfilerCallback::RuntimeThreadSuspended
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: f7c2f5baf5a320375d9a2606ca05b13d522336be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657337"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="bb155-103">Метод ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="bb155-103">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>

<span data-ttu-id="bb155-104">Уведомляет профилировщик о том, что указанный поток был приостановлен или готов к приостановке.</span><span class="sxs-lookup"><span data-stu-id="bb155-104">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb155-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb155-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb155-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bb155-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="bb155-107">окне Идентификатор приостановленного потока.</span><span class="sxs-lookup"><span data-stu-id="bb155-107">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb155-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb155-108">Remarks</span></span>  

 <span data-ttu-id="bb155-109">Это `RuntimeThreadSuspended` уведомление может возникнуть в любое время между методами [ICorProfilerCallback:: рунтимесуспендстартед](icorprofilercallback-runtimesuspendstarted-method.md) и связанными обратными вызовами [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bb155-109">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="bb155-110">Уведомления, которые происходят между [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) и `RuntimeResumeStarted` предназначены для потоков, которые были запущены в неуправляемом коде и были приостановлены при входе в среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="bb155-110">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="bb155-111">Как правило, этот обратный вызов происходит сразу после приостановки потока.</span><span class="sxs-lookup"><span data-stu-id="bb155-111">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="bb155-112">Однако если текущий выполняющийся поток (поток, вызвавший этот обратный вызов) является приостановленным, этот обратный вызов произойдет непосредственно перед приостановкой потока.</span><span class="sxs-lookup"><span data-stu-id="bb155-112">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb155-113">Требования</span><span class="sxs-lookup"><span data-stu-id="bb155-113">Requirements</span></span>  

 <span data-ttu-id="bb155-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb155-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb155-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb155-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb155-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb155-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb155-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb155-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb155-118">См. также</span><span class="sxs-lookup"><span data-stu-id="bb155-118">See also</span></span>

- [<span data-ttu-id="bb155-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bb155-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bb155-120">Метод RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="bb155-120">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
