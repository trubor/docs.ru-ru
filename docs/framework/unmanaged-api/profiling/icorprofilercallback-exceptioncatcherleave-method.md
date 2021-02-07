---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионкатчерлеаве'
title: Метод ICorProfilerCallback::ExceptionCatcherLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: 402a622dc949ef6f93c0ca5916a0690c6e734bd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706361"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="42281-103">Метод ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="42281-103">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>

<span data-ttu-id="42281-104">Уведомляет профилировщик о том, что управление передается из соответствующего `catch` блока.</span><span class="sxs-lookup"><span data-stu-id="42281-104">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42281-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="42281-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="42281-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="42281-106">Remarks</span></span>  

 <span data-ttu-id="42281-107">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="42281-107">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="42281-108">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="42281-108">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="42281-109">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="42281-109">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42281-110">Требования</span><span class="sxs-lookup"><span data-stu-id="42281-110">Requirements</span></span>  

 <span data-ttu-id="42281-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42281-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42281-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42281-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42281-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42281-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42281-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42281-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42281-115">См. также</span><span class="sxs-lookup"><span data-stu-id="42281-115">See also</span></span>

- [<span data-ttu-id="42281-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="42281-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="42281-117">Метод ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="42281-117">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
