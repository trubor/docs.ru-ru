---
description: 'Дополнительные сведения о: интерфейс ICorDebugController'
title: Интерфейс ICorDebugController
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: 588c41b5b8d87589facd6085655ed0ad415ec3aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710755"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="eca48-103">Интерфейс ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="eca48-103">ICorDebugController Interface</span></span>

<span data-ttu-id="eca48-104">Представляет область (<xref:System.Diagnostics.Process> или <xref:System.AppDomain>), в которой можно осуществлять управление контекстом выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="eca48-104">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eca48-105">Методы</span><span class="sxs-lookup"><span data-stu-id="eca48-105">Methods</span></span>  
  
|<span data-ttu-id="eca48-106">Метод</span><span class="sxs-lookup"><span data-stu-id="eca48-106">Method</span></span>|<span data-ttu-id="eca48-107">Описание</span><span class="sxs-lookup"><span data-stu-id="eca48-107">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="eca48-108">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="eca48-108">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="eca48-109">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="eca48-109">This method is obsolete.</span></span>|  
|[<span data-ttu-id="eca48-110">Метод Continue</span><span class="sxs-lookup"><span data-stu-id="eca48-110">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="eca48-111">Возобновляет выполнение управляемых потоков после вызова [ICorDebugController:: останавливаться](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="eca48-111">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="eca48-112">Метод Detach</span><span class="sxs-lookup"><span data-stu-id="eca48-112">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="eca48-113">Отсоединяет отладчик от процесса или домена приложения.</span><span class="sxs-lookup"><span data-stu-id="eca48-113">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="eca48-114">Метод EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="eca48-114">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="eca48-115">Возвращает перечислитель для активных управляемых потоков в процессе.</span><span class="sxs-lookup"><span data-stu-id="eca48-115">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="eca48-116">Метод HasQueuedCallbacks</span><span class="sxs-lookup"><span data-stu-id="eca48-116">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="eca48-117">Возвращает значение, указывающее, находятся ли в очереди управляемые обратные вызовы для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="eca48-117">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="eca48-118">Метод IsRunning</span><span class="sxs-lookup"><span data-stu-id="eca48-118">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="eca48-119">Возвращает значение, указывающее, выполняются ли в настоящий момент потоки в процессе.</span><span class="sxs-lookup"><span data-stu-id="eca48-119">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="eca48-120">Метод SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="eca48-120">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="eca48-121">Задает состояние отладки всех управляемых потоков в процессе.</span><span class="sxs-lookup"><span data-stu-id="eca48-121">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="eca48-122">Метод завершения</span><span class="sxs-lookup"><span data-stu-id="eca48-122">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="eca48-123">Выполняет совместную работу во всех потоках, где выполняется управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="eca48-123">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="eca48-124">Метод Terminate</span><span class="sxs-lookup"><span data-stu-id="eca48-124">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="eca48-125">Завершает процесс с указанным кодом выхода.</span><span class="sxs-lookup"><span data-stu-id="eca48-125">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eca48-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="eca48-126">Remarks</span></span>  

 <span data-ttu-id="eca48-127">Если `ICorDebugController` управляет процессом, область включает все потоки процесса.</span><span class="sxs-lookup"><span data-stu-id="eca48-127">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="eca48-128">Если управляет `ICorDebugController` доменом приложения, область включает только потоки этого конкретного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="eca48-128">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eca48-129">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="eca48-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca48-130">Требования</span><span class="sxs-lookup"><span data-stu-id="eca48-130">Requirements</span></span>  

 <span data-ttu-id="eca48-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca48-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca48-132">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eca48-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eca48-133">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eca48-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca48-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca48-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca48-135">См. также</span><span class="sxs-lookup"><span data-stu-id="eca48-135">See also</span></span>

- [<span data-ttu-id="eca48-136">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="eca48-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
