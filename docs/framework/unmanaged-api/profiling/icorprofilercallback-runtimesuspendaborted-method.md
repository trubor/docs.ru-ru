---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Рунтимесуспендабортед'
title: Метод ICorProfilerCallback::RuntimeSuspendAborted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 892de7ce0b4537f5526a58b6e70f66cd295be2df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788830"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="e1d79-103">Метод ICorProfilerCallback::RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="e1d79-103">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>

<span data-ttu-id="e1d79-104">Уведомляет профилировщик о том, что среда выполнения прервал приостановленную приостановку среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e1d79-104">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d79-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1d79-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1d79-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="e1d79-106">Remarks</span></span>  

 <span data-ttu-id="e1d79-107">Приостановка во время выполнения может быть прервана, если два потока одновременно пытаются приостановить выполнение.</span><span class="sxs-lookup"><span data-stu-id="e1d79-107">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="e1d79-108">Обратный вызов [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) или `RuntimeSuspendAborted` обратный вызов будет выполняться в одном потоке после обратного вызова [ICorProfilerCallback:: рунтимесуспендстартед](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e1d79-108">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="e1d79-109">`RuntimeSuspendAborted`Обратный вызов гарантированно выполняется в том же потоке, что и `RuntimeSuspendStarted` обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="e1d79-109">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d79-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e1d79-110">Requirements</span></span>  

 <span data-ttu-id="e1d79-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d79-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d79-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1d79-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1d79-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1d79-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1d79-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d79-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d79-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e1d79-115">See also</span></span>

- [<span data-ttu-id="e1d79-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e1d79-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
