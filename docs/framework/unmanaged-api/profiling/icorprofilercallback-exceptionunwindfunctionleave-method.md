---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионунвиндфунктионлеаве'
title: Метод ICorProfilerCallback::ExceptionUnwindFunctionLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: f428230b017841e931463057144ef72cc1ead45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705971"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="83480-103">Метод ICorProfilerCallback::ExceptionUnwindFunctionLeave</span><span class="sxs-lookup"><span data-stu-id="83480-103">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>

<span data-ttu-id="83480-104">Уведомляет профилировщик о том, что фаза очистки в обработке исключений завершила очистку функции.</span><span class="sxs-lookup"><span data-stu-id="83480-104">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83480-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83480-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="83480-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="83480-106">Remarks</span></span>  

 <span data-ttu-id="83480-107">При `ExceptionUnwindFunctionLeave` вызове метода экземпляр функции и его данные стека удаляются из стека.</span><span class="sxs-lookup"><span data-stu-id="83480-107">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="83480-108">Профилировщик не должен блокироваться во время этого вызова, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="83480-108">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="83480-109">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="83480-109">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="83480-110">Кроме того, во время этого вызова профилировщик не должен вызывать управляемый код или каким-либо образом вызывает выделение управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="83480-110">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83480-111">Требования</span><span class="sxs-lookup"><span data-stu-id="83480-111">Requirements</span></span>  

 <span data-ttu-id="83480-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83480-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83480-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83480-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83480-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83480-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83480-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83480-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83480-116">См. также</span><span class="sxs-lookup"><span data-stu-id="83480-116">See also</span></span>

- [<span data-ttu-id="83480-117">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="83480-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="83480-118">Метод ExceptionUnwindFunctionEnter</span><span class="sxs-lookup"><span data-stu-id="83480-118">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
