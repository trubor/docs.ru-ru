---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RemotingServerReceivingMessage'
title: Метод ICorProfilerCallback::RemotingServerReceivingMessage
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 5efa706d934158d09796dfab40b132a334c10ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788895"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="3aaf4-103">Метод ICorProfilerCallback::RemotingServerReceivingMessage</span><span class="sxs-lookup"><span data-stu-id="3aaf4-103">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>

<span data-ttu-id="3aaf4-104">Уведомляет профилировщик о том, что процесс получил удаленный вызов метода или запрос на активацию.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-104">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aaf4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3aaf4-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aaf4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3aaf4-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="3aaf4-107">окне Значение, которое будет соответствовать значению, указанному в параметре [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) в следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="3aaf4-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="3aaf4-108">Файлы Cookie GUID удаленного взаимодействия активны.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="3aaf4-109">Канал проходит успешную передачу сообщения.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="3aaf4-110">Файлы Cookie GUID активны в процессе на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="3aaf4-111">Это позволяет легко связывать вызовы удаленного взаимодействия и создавать логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="3aaf4-112">окне Значение, равное, `true` Если вызов является асинхронным; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="3aaf4-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aaf4-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="3aaf4-113">Remarks</span></span>  

 <span data-ttu-id="3aaf4-114">Если запрос сообщения является асинхронным, запрос может обслуживаться любым произвольным потоком.</span><span class="sxs-lookup"><span data-stu-id="3aaf4-114">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aaf4-115">Требования</span><span class="sxs-lookup"><span data-stu-id="3aaf4-115">Requirements</span></span>  

 <span data-ttu-id="3aaf4-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aaf4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aaf4-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3aaf4-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3aaf4-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3aaf4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3aaf4-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aaf4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aaf4-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3aaf4-120">See also</span></span>

- [<span data-ttu-id="3aaf4-121">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3aaf4-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
