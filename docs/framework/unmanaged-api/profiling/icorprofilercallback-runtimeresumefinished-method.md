---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Рунтимересумефинишед'
title: Метод ICorProfilerCallback::RuntimeResumeFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: a8a38ff8372df9890239966c90175d72bda4b09d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788856"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="f8fb6-103">Метод ICorProfilerCallback::RuntimeResumeFinished</span><span class="sxs-lookup"><span data-stu-id="f8fb6-103">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="f8fb6-104">Уведомляет профилировщик о том, что среда выполнения возобновила все потоки среды выполнения и вернула нормальную работу.</span><span class="sxs-lookup"><span data-stu-id="f8fb6-104">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8fb6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8fb6-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8fb6-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8fb6-106">Remarks</span></span>  

 <span data-ttu-id="f8fb6-107">`RuntimeResumeFinished`Обратный вызов не гарантируется в том же потоке, что и обратный вызов [ICorProfilerCallback:: рунтимесуспендстартед](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f8fb6-107">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="f8fb6-108">Однако гарантируется, что она будет выполняться в том же потоке, что и обратный вызов [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f8fb6-108">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8fb6-109">Требования</span><span class="sxs-lookup"><span data-stu-id="f8fb6-109">Requirements</span></span>  

 <span data-ttu-id="f8fb6-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8fb6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8fb6-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8fb6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8fb6-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8fb6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8fb6-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8fb6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fb6-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f8fb6-114">See also</span></span>

- [<span data-ttu-id="f8fb6-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f8fb6-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
