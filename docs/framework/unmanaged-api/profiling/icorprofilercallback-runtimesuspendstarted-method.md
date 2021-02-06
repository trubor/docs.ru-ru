---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Рунтимесуспендстартед'
title: Метод ICorProfilerCallback::RuntimeSuspendStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 7f7ba6a2a8523589b025d98ea925b77d05d8a59d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657428"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="c1367-103">Метод ICorProfilerCallback::RuntimeSuspendStarted</span><span class="sxs-lookup"><span data-stu-id="c1367-103">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="c1367-104">Уведомляет профилировщик о том, что среда выполнения собирается приостановить все потоки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c1367-104">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1367-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c1367-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1367-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c1367-106">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="c1367-107">окне Значение перечисления [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) , указывающее причину приостановки.</span><span class="sxs-lookup"><span data-stu-id="c1367-107">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1367-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c1367-108">Remarks</span></span>  

 <span data-ttu-id="c1367-109">Все потоки среды выполнения, наявляющиеся в неуправляемом коде, могут продолжать выполняться до тех пор, пока они не попытаются повторно войти в среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="c1367-109">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="c1367-110">На этом этапе они также будут приостановлены до тех пор, пока среда выполнения не возобновит работу.</span><span class="sxs-lookup"><span data-stu-id="c1367-110">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="c1367-111">Это также относится к новым потокам, которые вводят среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="c1367-111">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="c1367-112">Все потоки в среде выполнения либо приостанавливаются немедленно, если они уже находятся в коде для преобразования, либо если они запросят приостановить работу в случае, если они достигают кода источника.</span><span class="sxs-lookup"><span data-stu-id="c1367-112">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1367-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c1367-113">Requirements</span></span>  

 <span data-ttu-id="c1367-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1367-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1367-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1367-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1367-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1367-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1367-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1367-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1367-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c1367-118">See also</span></span>

- [<span data-ttu-id="c1367-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c1367-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c1367-120">Метод RuntimeSuspendAborted</span><span class="sxs-lookup"><span data-stu-id="c1367-120">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="c1367-121">Метод RuntimeSuspendFinished</span><span class="sxs-lookup"><span data-stu-id="c1367-121">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
