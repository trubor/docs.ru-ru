---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RemotingClientSendingMessage'
title: Метод ICorProfilerCallback::RemotingClientSendingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 3d075b3f3c3ffe63c9d4401bdc182037593b5b19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788934"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="eec32-103">Метод ICorProfilerCallback::RemotingClientSendingMessage</span><span class="sxs-lookup"><span data-stu-id="eec32-103">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>

<span data-ttu-id="eec32-104">Уведомляет профилировщик о том, что клиент отправляет запрос на сервер.</span><span class="sxs-lookup"><span data-stu-id="eec32-104">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec32-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eec32-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eec32-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eec32-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="eec32-107">окне Значение, которое соответствует значению, указанному в параметре [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) в следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="eec32-107">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="eec32-108">Файлы Cookie GUID удаленного взаимодействия активны.</span><span class="sxs-lookup"><span data-stu-id="eec32-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="eec32-109">Канал проходит успешную передачу сообщения.</span><span class="sxs-lookup"><span data-stu-id="eec32-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="eec32-110">Файлы Cookie GUID активны в процессе на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="eec32-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="eec32-111">Это позволяет легко связывать вызовы удаленного взаимодействия и создавать логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="eec32-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="eec32-112">окне Значение, равное, `true` Если вызов является асинхронным; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="eec32-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec32-113">Требования</span><span class="sxs-lookup"><span data-stu-id="eec32-113">Requirements</span></span>  

 <span data-ttu-id="eec32-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eec32-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec32-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eec32-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eec32-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec32-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eec32-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec32-118">См. также</span><span class="sxs-lookup"><span data-stu-id="eec32-118">See also</span></span>

- [<span data-ttu-id="eec32-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="eec32-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
