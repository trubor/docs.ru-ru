---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RemotingServerSendingReply'
title: Метод ICorProfilerCallback::RemotingServerSendingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: 236a707fcbc051a3d00c408f71f3b4f9f452c220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788882"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="7c9fe-103">Метод ICorProfilerCallback::RemotingServerSendingReply</span><span class="sxs-lookup"><span data-stu-id="7c9fe-103">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>

<span data-ttu-id="7c9fe-104">Уведомляет профилировщик о том, что процесс завершил обработку запроса удаленного вызова метода и собирается передать ответ через канал.</span><span class="sxs-lookup"><span data-stu-id="7c9fe-104">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9fe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7c9fe-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9fe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7c9fe-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="7c9fe-107">окне Указатель на идентификатор GUID, который будет соответствовать значению, указанному в параметре [ICorProfilerCallback:: ремотингклиентрецеивингрепли](icorprofilercallback-remotingclientreceivingreply-method.md) в следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="7c9fe-107">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="7c9fe-108">Файлы Cookie GUID удаленного взаимодействия активны.</span><span class="sxs-lookup"><span data-stu-id="7c9fe-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="7c9fe-109">Канал проходит успешную передачу сообщения.</span><span class="sxs-lookup"><span data-stu-id="7c9fe-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="7c9fe-110">Файлы Cookie GUID активны в процессе на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="7c9fe-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="7c9fe-111">Это позволяет легко связывать вызовы удаленного взаимодействия и создавать логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="7c9fe-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="7c9fe-112">окне Значение, равное, `true` Если вызов является асинхронным; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="7c9fe-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9fe-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7c9fe-113">Requirements</span></span>  

 <span data-ttu-id="7c9fe-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9fe-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9fe-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c9fe-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c9fe-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9fe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9fe-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9fe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9fe-118">См. также</span><span class="sxs-lookup"><span data-stu-id="7c9fe-118">See also</span></span>

- [<span data-ttu-id="7c9fe-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="7c9fe-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
