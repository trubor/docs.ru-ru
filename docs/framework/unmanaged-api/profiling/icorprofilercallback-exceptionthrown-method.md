---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ExceptionThrown'
title: Метод ICorProfilerCallback::ExceptionThrown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 77ebca8fbc52ed0c46a4f76fb5cdf6cb2923edaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706140"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="e1b24-103">Метод ICorProfilerCallback::ExceptionThrown</span><span class="sxs-lookup"><span data-stu-id="e1b24-103">ICorProfilerCallback::ExceptionThrown Method</span></span>

<span data-ttu-id="e1b24-104">Уведомляет профилировщик о том, что было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="e1b24-104">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1b24-105">Эта функция вызывается, только если исключение достигает управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="e1b24-105">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b24-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1b24-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1b24-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e1b24-107">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="e1b24-108">\[in] идентификатор объекта, который вызвал исключение.</span><span class="sxs-lookup"><span data-stu-id="e1b24-108">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e1b24-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e1b24-109">Remarks</span></span>  

 <span data-ttu-id="e1b24-110">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="e1b24-110">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e1b24-111">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="e1b24-111">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e1b24-112">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="e1b24-112">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b24-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e1b24-113">Requirements</span></span>  

 <span data-ttu-id="e1b24-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1b24-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b24-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1b24-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1b24-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1b24-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1b24-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b24-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b24-118">См. также</span><span class="sxs-lookup"><span data-stu-id="e1b24-118">See also</span></span>

- [<span data-ttu-id="e1b24-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e1b24-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
