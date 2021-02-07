---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионунвиндфиналлентер'
title: Метод ICorProfilerCallback::ExceptionUnwindFinallyEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
ms.openlocfilehash: e4a701597b318a387405a152f2c3b4758d616eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706088"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="8877d-103">Метод ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="8877d-103">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>

<span data-ttu-id="8877d-104">Уведомляет профилировщик о том, что фаза очистки при обработке исключений вводит `finally` предложение, содержащееся в указанной функции.</span><span class="sxs-lookup"><span data-stu-id="8877d-104">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8877d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8877d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8877d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8877d-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8877d-107">\[in] идентификатор функции, которая содержит `finally` предложение.</span><span class="sxs-lookup"><span data-stu-id="8877d-107">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="8877d-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="8877d-108">Remarks</span></span>  

 <span data-ttu-id="8877d-109">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="8877d-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8877d-110">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="8877d-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8877d-111">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="8877d-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8877d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8877d-112">Requirements</span></span>  

 <span data-ttu-id="8877d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8877d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8877d-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8877d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8877d-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8877d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8877d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8877d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8877d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8877d-117">See also</span></span>

- [<span data-ttu-id="8877d-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8877d-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8877d-119">Метод GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="8877d-119">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="8877d-120">Метод ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="8877d-120">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
