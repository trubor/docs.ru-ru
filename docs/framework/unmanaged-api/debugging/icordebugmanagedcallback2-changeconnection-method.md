---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2:: Чанжеконнектион'
title: Метод ICorDebugManagedCallback2::ChangeConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 854ea7f40cad9bce613b4034afe7688f4aaf4e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790923"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="18455-103">Метод ICorDebugManagedCallback2::ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="18455-103">ICorDebugManagedCallback2::ChangeConnection Method</span></span>

<span data-ttu-id="18455-104">Уведомляет отладчик о том, что набор задач, связанных с указанным соединением, изменился.</span><span class="sxs-lookup"><span data-stu-id="18455-104">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18455-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18455-105">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18455-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="18455-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="18455-107">окне Указатель на объект "ICorDebugProcess", представляющий процесс, содержащий измененное соединение.</span><span class="sxs-lookup"><span data-stu-id="18455-107">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="18455-108">окне Идентификатор измененного соединения.</span><span class="sxs-lookup"><span data-stu-id="18455-108">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18455-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="18455-109">Remarks</span></span>  

 <span data-ttu-id="18455-110">`ChangeConnection`Обратный вызов будет срабатывать в одном из следующих случаев.</span><span class="sxs-lookup"><span data-stu-id="18455-110">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="18455-111">При присоединении отладчика к процессу, который содержит соединения.</span><span class="sxs-lookup"><span data-stu-id="18455-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="18455-112">В этом случае среда выполнения создаст и отправит событие [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) и `ChangeConnection` событие для каждого соединения в процессе.</span><span class="sxs-lookup"><span data-stu-id="18455-112">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="18455-113">`ChangeConnection`Событие создается для каждого существующего соединения независимо от того, изменился ли набор задач этого соединения с момента его создания.</span><span class="sxs-lookup"><span data-stu-id="18455-113">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="18455-114">Когда узел вызывает [ICLRDebugManager:: SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) в [API размещения](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="18455-114">When a host calls [ICLRDebugManager::SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="18455-115">Отладчик должен проверить все потоки в процессе, чтобы получить новые изменения.</span><span class="sxs-lookup"><span data-stu-id="18455-115">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18455-116">Требования</span><span class="sxs-lookup"><span data-stu-id="18455-116">Requirements</span></span>  

 <span data-ttu-id="18455-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18455-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18455-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18455-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18455-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18455-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18455-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18455-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18455-121">См. также</span><span class="sxs-lookup"><span data-stu-id="18455-121">See also</span></span>

- [<span data-ttu-id="18455-122">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="18455-122">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="18455-123">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="18455-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
