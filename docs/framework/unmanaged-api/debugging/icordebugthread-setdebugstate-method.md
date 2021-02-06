---
description: 'Дополнительные сведения о методе ICorDebugThread:: SetDebugState'
title: Метод ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: 40339cbce8d30617738151c0a32466c2361e3a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658806"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="78a9a-103">Метод ICorDebugThread::SetDebugState</span><span class="sxs-lookup"><span data-stu-id="78a9a-103">ICorDebugThread::SetDebugState Method</span></span>

<span data-ttu-id="78a9a-104">Устанавливает флаги, описывающие состояние отладки этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="78a9a-104">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a9a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78a9a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78a9a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="78a9a-106">Parameters</span></span>  

 `state`  
 <span data-ttu-id="78a9a-107">окне Побитовое сочетание значений перечисления Кордебугсреадстате, определяющих состояние отладки этого потока.</span><span class="sxs-lookup"><span data-stu-id="78a9a-107">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78a9a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="78a9a-108">Remarks</span></span>  

 <span data-ttu-id="78a9a-109">`SetDebugState` Задает текущее состояние отладки потока.</span><span class="sxs-lookup"><span data-stu-id="78a9a-109">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="78a9a-110">("Текущее состояние отладки" представляет состояние отладки, если процесс должен быть продолжен, а не фактическое текущее состояние.) Нормальное значение для этого параметра — THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="78a9a-110">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="78a9a-111">Только отладчик может повлиять на состояние отладки потока.</span><span class="sxs-lookup"><span data-stu-id="78a9a-111">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="78a9a-112">Состояния отладки проявляются последними, поэтому, если вы хотите, чтобы поток THREAD_SUSPENDed более одного раза, можно установить его один раз, а затем не беспокоиться о нем.</span><span class="sxs-lookup"><span data-stu-id="78a9a-112">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="78a9a-113">Приостановка потоков и возобновление процесса могут привести к взаимоблокировке, хотя обычно маловероятно.</span><span class="sxs-lookup"><span data-stu-id="78a9a-113">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="78a9a-114">Это встроенное качество потоков и процессов, а именно-проектирование.</span><span class="sxs-lookup"><span data-stu-id="78a9a-114">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="78a9a-115">Отладчик может асинхронно приостанавливать и возобновлять потоки, чтобы нарушить взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="78a9a-115">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="78a9a-116">Если пользовательское состояние потока включает USER_UNSAFE_POINT, поток может блокировать сборку мусора (GC).</span><span class="sxs-lookup"><span data-stu-id="78a9a-116">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="78a9a-117">Это означает, что приостановленный поток имеет намного более высокий шанс возникновения взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="78a9a-117">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="78a9a-118">Это может не влиять на события отладки, уже поставленные в очередь.</span><span class="sxs-lookup"><span data-stu-id="78a9a-118">This may not affect debug events already queued.</span></span> <span data-ttu-id="78a9a-119">Таким образом, отладчик должен очистить всю очередь событий (вызвав [ICorDebugController:: хаскуеуедкаллбаккс](icordebugcontroller-hasqueuedcallbacks-method.md)) перед приостановкой или возобновлением потоков.</span><span class="sxs-lookup"><span data-stu-id="78a9a-119">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="78a9a-120">В противном случае он может получить события в потоке, который предположительно уже приостановлен.</span><span class="sxs-lookup"><span data-stu-id="78a9a-120">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a9a-121">Требования</span><span class="sxs-lookup"><span data-stu-id="78a9a-121">Requirements</span></span>  

 <span data-ttu-id="78a9a-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78a9a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a9a-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78a9a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78a9a-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78a9a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78a9a-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a9a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
