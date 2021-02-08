---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2:: CreateConnection'
title: Метод ICorDebugManagedCallback2::CreateConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: c7ac91217d43531505dc27a20da9cf4534366119
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790910"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="b3021-103">Метод ICorDebugManagedCallback2::CreateConnection</span><span class="sxs-lookup"><span data-stu-id="b3021-103">ICorDebugManagedCallback2::CreateConnection Method</span></span>

<span data-ttu-id="b3021-104">Уведомляет отладчик о создании нового соединения.</span><span class="sxs-lookup"><span data-stu-id="b3021-104">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3021-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3021-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3021-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3021-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="b3021-107">окне Указатель на объект "ICorDebugProcess", представляющий процесс, в котором было создано соединение</span><span class="sxs-lookup"><span data-stu-id="b3021-107">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="b3021-108">окне Идентификатор нового соединения.</span><span class="sxs-lookup"><span data-stu-id="b3021-108">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="b3021-109">окне Указатель на имя нового соединения.</span><span class="sxs-lookup"><span data-stu-id="b3021-109">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3021-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3021-110">Remarks</span></span>  

 <span data-ttu-id="b3021-111">`CreateConnection`Обратный вызов будет срабатывать в одном из следующих случаев.</span><span class="sxs-lookup"><span data-stu-id="b3021-111">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="b3021-112">При присоединении отладчика к процессу, который содержит соединения.</span><span class="sxs-lookup"><span data-stu-id="b3021-112">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="b3021-113">В этом случае среда выполнения создаст и отправит `CreateConnection` событие и событие [ICorDebugManagedCallback2:: чанжеконнектион](icordebugmanagedcallback2-changeconnection-method.md) для каждого соединения в процессе.</span><span class="sxs-lookup"><span data-stu-id="b3021-113">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="b3021-114">Когда узел вызывает [ICLRDebugManager:: бегинконнектион](../hosting/iclrdebugmanager-beginconnection-method.md) в [API размещения](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3021-114">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3021-115">Требования</span><span class="sxs-lookup"><span data-stu-id="b3021-115">Requirements</span></span>  

 <span data-ttu-id="b3021-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3021-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3021-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3021-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3021-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3021-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3021-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3021-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3021-120">См. также</span><span class="sxs-lookup"><span data-stu-id="b3021-120">See also</span></span>

- [<span data-ttu-id="b3021-121">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="b3021-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b3021-122">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b3021-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
