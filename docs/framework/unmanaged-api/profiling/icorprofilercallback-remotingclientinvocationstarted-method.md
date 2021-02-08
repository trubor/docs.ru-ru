---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RemotingClientInvocationStarted'
title: Метод ICorProfilerCallback::RemotingClientInvocationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 3727383c3a23fa9e4327970e84c6ebde4ab14db0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788973"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="fcd8f-103">Метод ICorProfilerCallback::RemotingClientInvocationStarted</span><span class="sxs-lookup"><span data-stu-id="fcd8f-103">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>

<span data-ttu-id="fcd8f-104">Уведомляет профилировщик о начале удаленного вызова.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-104">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd8f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcd8f-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcd8f-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="fcd8f-106">Remarks</span></span>  

 <span data-ttu-id="fcd8f-107">Это событие одинаково для синхронных и асинхронных вызовов.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-107">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="fcd8f-108">Каждая из следующих пар обратных вызовов будет выполняться в одном потоке:</span><span class="sxs-lookup"><span data-stu-id="fcd8f-108">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="fcd8f-109">`RemotingClientInvocationStarted` и [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="fcd8f-109">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="fcd8f-110">[ICorProfilerCallback:: ремотингклиентрецеивингрепли](icorprofilercallback-remotingclientreceivingreply-method.md) и [ICorProfilerCallback:: ремотингклиентинвокатионфинишед](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="fcd8f-110">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="fcd8f-111">[ICorProfilerCallback:: RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) и [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="fcd8f-111">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="fcd8f-112">При использовании обратных вызовов удаленного взаимодействия следует учитывать следующие моменты.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-112">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="fcd8f-113">Выполнение функции удаленного взаимодействия не отражается API-интерфейсом профилировщика, поэтому уведомления для функций, которые вызываются из клиента и выполняются на сервере, не получаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-113">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="fcd8f-114">Фактический вызов происходит через прокси-объект; для профилировщика отображается, что определенные функции JIT-скомпилированы, но никогда не используются.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-114">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="fcd8f-115">Профилировщик не получает точные уведомления о событиях асинхронного удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="fcd8f-115">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd8f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="fcd8f-116">Requirements</span></span>  

 <span data-ttu-id="fcd8f-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd8f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd8f-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcd8f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fcd8f-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcd8f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcd8f-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd8f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd8f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fcd8f-121">See also</span></span>

- [<span data-ttu-id="fcd8f-122">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fcd8f-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
