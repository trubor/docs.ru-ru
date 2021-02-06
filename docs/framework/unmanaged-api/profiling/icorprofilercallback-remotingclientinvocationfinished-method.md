---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ремотингклиентинвокатионфинишед'
title: Метод ICorProfilerCallback::RemotingClientInvocationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
ms.openlocfilehash: bc15139e10b7634c50604d9a05ba290566145c21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648016"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="aef00-103">Метод ICorProfilerCallback::RemotingClientInvocationFinished</span><span class="sxs-lookup"><span data-stu-id="aef00-103">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>

<span data-ttu-id="aef00-104">Уведомляет профилировщик о том, что вызов удаленного взаимодействия был выполнен до завершения на клиенте.</span><span class="sxs-lookup"><span data-stu-id="aef00-104">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef00-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aef00-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="aef00-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="aef00-106">Remarks</span></span>  

 <span data-ttu-id="aef00-107">Если вызов удаленного взаимодействия был синхронным, он также выполняется до завершения на сервере.</span><span class="sxs-lookup"><span data-stu-id="aef00-107">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="aef00-108">Если вызов удаленного взаимодействия был асинхронным, то при обработке вызова может быть по-прежнему ожидаемый ответ.</span><span class="sxs-lookup"><span data-stu-id="aef00-108">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="aef00-109">Если ожидается ответ, он будет выполняться как вызов метода [ICorProfilerCallback:: ремотингклиентрецеивингрепли](icorprofilercallback-remotingclientreceivingreply-method.md) и дополнительный вызов метода `RemotingClientInvocationFinished` для указания необходимой дополнительной обработки асинхронного вызова.</span><span class="sxs-lookup"><span data-stu-id="aef00-109">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="aef00-110">Каждая из следующих пар обратных вызовов будет выполняться в одном потоке:</span><span class="sxs-lookup"><span data-stu-id="aef00-110">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="aef00-111">`RemotingClientInvocationStarted` и [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="aef00-111">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="aef00-112">[ICorProfilerCallback:: ремотингклиентрецеивингрепли](icorprofilercallback-remotingclientreceivingreply-method.md) и [ICorProfilerCallback:: ремотингклиентинвокатионфинишед](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="aef00-112">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="aef00-113">[ICorProfilerCallback:: RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) и [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="aef00-113">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="aef00-114">При использовании обратных вызовов удаленного взаимодействия следует учитывать следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="aef00-114">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="aef00-115">Выполнение функции удаленного взаимодействия не отражается API-интерфейсом профилировщика, поэтому уведомления для функций, которые вызываются из клиента и выполняются на сервере, не получаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="aef00-115">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="aef00-116">Фактический вызов происходит через прокси-объект; для профилировщика отображается, что определенные функции JIT-скомпилированы, но никогда не используются.</span><span class="sxs-lookup"><span data-stu-id="aef00-116">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="aef00-117">Профилировщик не получает точные уведомления о событиях асинхронного удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="aef00-117">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef00-118">Требования</span><span class="sxs-lookup"><span data-stu-id="aef00-118">Requirements</span></span>  

 <span data-ttu-id="aef00-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef00-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef00-120">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aef00-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aef00-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef00-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aef00-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef00-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef00-123">См. также</span><span class="sxs-lookup"><span data-stu-id="aef00-123">See also</span></span>

- [<span data-ttu-id="aef00-124">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="aef00-124">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
