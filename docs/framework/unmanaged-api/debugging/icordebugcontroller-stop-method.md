---
description: 'Дополнительные сведения о методе: ICorDebugController:: останавливаться'
title: Метод ICorDebugController::Stop
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: 613fd81a03114580ae3d826a94d855023895b694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764610"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="438f2-103">Метод ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="438f2-103">ICorDebugController::Stop Method</span></span>

<span data-ttu-id="438f2-104">Выполняет совместную работу во всех потоках, где выполняется управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="438f2-104">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="438f2-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="438f2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="438f2-106">Parameters</span></span>  

 `dwTimeoutIgnored`  
 <span data-ttu-id="438f2-107">Не используется.</span><span class="sxs-lookup"><span data-stu-id="438f2-107">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="438f2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="438f2-108">Remarks</span></span>  

 <span data-ttu-id="438f2-109">`Stop` выполняет совместную работу всех потоков, выполняющих управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="438f2-109">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="438f2-110">Во время сеанса отладки, доступного только для управляемого кода, неуправляемые потоки могут продолжать выполняться (но будут заблокированы при попытке вызвать управляемый код).</span><span class="sxs-lookup"><span data-stu-id="438f2-110">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="438f2-111">Во время сеанса отладки взаимодействия неуправляемые потоки также будут остановлены.</span><span class="sxs-lookup"><span data-stu-id="438f2-111">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="438f2-112">`dwTimeoutIgnored`Значение в настоящее время игнорируется и обрабатывается как БЕСконечное (-1).</span><span class="sxs-lookup"><span data-stu-id="438f2-112">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="438f2-113">Если совместная остановка завершается сбоем из-за взаимоблокировки, все потоки приостанавливаются и возвращается E_TIMEOUT.</span><span class="sxs-lookup"><span data-stu-id="438f2-113">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="438f2-114">`Stop` — единственный синхронный метод в API отладки.</span><span class="sxs-lookup"><span data-stu-id="438f2-114">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="438f2-115">Когда `Stop` функция возвращает S_OK, процесс останавливается.</span><span class="sxs-lookup"><span data-stu-id="438f2-115">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="438f2-116">Обратный вызов не предоставляется для уведомления прослушивателей об ошибке.</span><span class="sxs-lookup"><span data-stu-id="438f2-116">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="438f2-117">Отладчик должен вызвать [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , чтобы разрешить возобновление процесса.</span><span class="sxs-lookup"><span data-stu-id="438f2-117">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="438f2-118">Отладчик поддерживает счетчик "останавливается".</span><span class="sxs-lookup"><span data-stu-id="438f2-118">The debugger maintains a stop counter.</span></span> <span data-ttu-id="438f2-119">Когда счетчик переходит в нулевое значение, контроллер возобновляется.</span><span class="sxs-lookup"><span data-stu-id="438f2-119">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="438f2-120">Каждый вызов `Stop` или каждый отправленный обратный вызов увеличивает счетчик.</span><span class="sxs-lookup"><span data-stu-id="438f2-120">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="438f2-121">Каждый вызов `ICorDebugController::Continue` уменьшает значение счетчика.</span><span class="sxs-lookup"><span data-stu-id="438f2-121">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438f2-122">Требования</span><span class="sxs-lookup"><span data-stu-id="438f2-122">Requirements</span></span>  

 <span data-ttu-id="438f2-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="438f2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438f2-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="438f2-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="438f2-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="438f2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="438f2-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="438f2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438f2-127">См. также</span><span class="sxs-lookup"><span data-stu-id="438f2-127">See also</span></span>
