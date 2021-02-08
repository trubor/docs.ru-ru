---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ремотингклиентрецеивингрепли'
title: Метод ICorProfilerCallback::RemotingClientReceivingReply
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 4c1d42baa9f4381b66c9be75afa239899ae81b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788947"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="a1636-103">Метод ICorProfilerCallback::RemotingClientReceivingReply</span><span class="sxs-lookup"><span data-stu-id="a1636-103">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>

<span data-ttu-id="a1636-104">Уведомляет профилировщик о завершении серверной части удаленного вызова, а также о получении и обработке ответа клиентом.</span><span class="sxs-lookup"><span data-stu-id="a1636-104">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1636-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a1636-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="a1636-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a1636-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="a1636-107">окне Значение, которое будет соответствовать значению, указанному в параметре [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) в следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="a1636-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="a1636-108">Файлы Cookie GUID удаленного взаимодействия активны.</span><span class="sxs-lookup"><span data-stu-id="a1636-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="a1636-109">Канал проходит успешную передачу сообщения.</span><span class="sxs-lookup"><span data-stu-id="a1636-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="a1636-110">Файлы Cookie GUID активны в процессе на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="a1636-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="a1636-111">Это позволяет легко связывать вызовы удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a1636-111">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a1636-112">окне Значение, равное, `true` Если вызов является асинхронным; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a1636-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1636-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a1636-113">Requirements</span></span>  

 <span data-ttu-id="a1636-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1636-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1636-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1636-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1636-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1636-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1636-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1636-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1636-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a1636-118">See also</span></span>

- [<span data-ttu-id="a1636-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a1636-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
