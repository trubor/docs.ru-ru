---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионкатчерентер'
title: Метод ICorProfilerCallback::ExceptionCatcherEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 3a813936a7d1f3a5041e192c85d02b37976e3388
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657636"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="aee4a-103">Метод ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="aee4a-103">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="aee4a-104">Уведомляет профилировщик о том, что управление передается соответствующему `catch` блоку.</span><span class="sxs-lookup"><span data-stu-id="aee4a-104">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee4a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aee4a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aee4a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aee4a-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="aee4a-107">\[in] идентификатор функции, содержащей `catch` блок.</span><span class="sxs-lookup"><span data-stu-id="aee4a-107">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="aee4a-108">\[в] идентификатор обрабатываемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aee4a-108">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="aee4a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="aee4a-109">Remarks</span></span>  

 <span data-ttu-id="aee4a-110">`ExceptionCatcherEnter`Метод вызывается только в том случае, если точка перехвата находится в коде, скомпилированном с JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="aee4a-110">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="aee4a-111">Исключение, перехваченное в неуправляемом коде или во внутреннем коде среды выполнения, не будет вызывать это уведомление.</span><span class="sxs-lookup"><span data-stu-id="aee4a-111">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="aee4a-112">`objectId`Значение передается снова, так как сборка мусора могла переместить объект с момента получения `ExceptionThrown` уведомления.</span><span class="sxs-lookup"><span data-stu-id="aee4a-112">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="aee4a-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="aee4a-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="aee4a-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="aee4a-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="aee4a-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="aee4a-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee4a-116">Требования</span><span class="sxs-lookup"><span data-stu-id="aee4a-116">Requirements</span></span>  

 <span data-ttu-id="aee4a-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aee4a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee4a-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aee4a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aee4a-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aee4a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aee4a-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee4a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee4a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="aee4a-121">See also</span></span>

- [<span data-ttu-id="aee4a-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="aee4a-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="aee4a-123">Метод ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="aee4a-123">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
