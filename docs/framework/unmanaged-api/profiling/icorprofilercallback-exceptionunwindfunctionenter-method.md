---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ExceptionUnwindFunctionEnter'
title: Метод ICorProfilerCallback::ExceptionUnwindFunctionEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 665684b08ec272f26a468f5635c40cf64ce4981a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760500"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="55db7-103">Метод ICorProfilerCallback::ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="55db7-103">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>

<span data-ttu-id="55db7-104">Уведомляет профилировщик о том, что фаза очистки обработки исключений началась для очистки функции.</span><span class="sxs-lookup"><span data-stu-id="55db7-104">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55db7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55db7-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55db7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="55db7-106">Parameters</span></span>

<span data-ttu-id="55db7-107">`functionId` окне Идентификатор перевернутой функции.</span><span class="sxs-lookup"><span data-stu-id="55db7-107">`functionId` [in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="55db7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="55db7-108">Remarks</span></span>  

 <span data-ttu-id="55db7-109">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="55db7-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="55db7-110">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="55db7-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="55db7-111">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="55db7-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55db7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="55db7-112">Requirements</span></span>  

 <span data-ttu-id="55db7-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55db7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55db7-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55db7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55db7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55db7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55db7-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55db7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55db7-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="55db7-117">See also</span></span>

- [<span data-ttu-id="55db7-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="55db7-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="55db7-119">Метод ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="55db7-119">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
