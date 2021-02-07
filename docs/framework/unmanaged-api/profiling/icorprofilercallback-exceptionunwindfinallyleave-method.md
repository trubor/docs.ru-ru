---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Exceptionunwindfinallyleave-'
title: Метод ICorProfilerCallback::ExceptionUnwindFinallyLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: dd3916d1e250344dbbc707a2ba3ef21a4877415f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706114"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="0c159-103">Метод ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="0c159-103">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="0c159-104">Уведомляет профилировщик о том, что фаза очистки в обработке исключений содержит `finally` предложение.</span><span class="sxs-lookup"><span data-stu-id="0c159-104">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c159-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c159-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c159-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c159-106">Remarks</span></span>  

 <span data-ttu-id="0c159-107">Профилировщик не должен блокироваться во время этого вызова, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="0c159-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0c159-108">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="0c159-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0c159-109">Кроме того, во время этого вызова профилировщик не должен вызывать управляемый код или каким-либо образом вызывает выделение управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="0c159-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c159-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0c159-110">Requirements</span></span>  

 <span data-ttu-id="0c159-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c159-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c159-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c159-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c159-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c159-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c159-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c159-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c159-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0c159-115">See also</span></span>

- [<span data-ttu-id="0c159-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0c159-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0c159-117">Метод ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="0c159-117">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
