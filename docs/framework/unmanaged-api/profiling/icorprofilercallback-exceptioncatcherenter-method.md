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
ms.openlocfilehash: f9ea2b44e7a783f9b21f4aa385585dfebc48b1d4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760526"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="c2d1f-103">Метод ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="c2d1f-103">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="c2d1f-104">Уведомляет профилировщик о том, что управление передается соответствующему `catch` блоку.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-104">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d1f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2d1f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2d1f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2d1f-106">Parameters</span></span>

<span data-ttu-id="c2d1f-107">`functionId` окне Идентификатор функции, содержащей `catch` блок.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-107">`functionId` [in] The identifier of the function containing the `catch` block.</span></span>
  
<span data-ttu-id="c2d1f-108">`objectId` окне Идентификатор обрабатываемого исключения.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-108">`objectId` [in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2d1f-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c2d1f-109">Remarks</span></span>  

 <span data-ttu-id="c2d1f-110">`ExceptionCatcherEnter`Метод вызывается только в том случае, если точка перехвата находится в коде, скомпилированном с JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-110">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="c2d1f-111">Исключение, перехваченное в неуправляемом коде или во внутреннем коде среды выполнения, не будет вызывать это уведомление.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-111">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="c2d1f-112">`objectId`Значение передается снова, так как сборка мусора могла переместить объект с момента получения `ExceptionThrown` уведомления.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-112">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="c2d1f-113">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c2d1f-114">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c2d1f-115">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="c2d1f-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d1f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c2d1f-116">Requirements</span></span>  

 <span data-ttu-id="c2d1f-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d1f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d1f-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2d1f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2d1f-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d1f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d1f-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d1f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d1f-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c2d1f-121">See also</span></span>

- [<span data-ttu-id="c2d1f-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c2d1f-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c2d1f-123">Метод ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="c2d1f-123">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
