---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: RemotingServerInvocationReturned'
title: Метод ICorProfilerCallback::RemotingServerInvocationReturned
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
ms.openlocfilehash: 97f9fda42059ac66fc3a29689adc252556798e4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788921"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="df31a-103">Метод ICorProfilerCallback::RemotingServerInvocationReturned</span><span class="sxs-lookup"><span data-stu-id="df31a-103">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>

<span data-ttu-id="df31a-104">Уведомляет профилировщик о том, что процесс завершил вызов метода в ответ на запрос удаленного вызова метода.</span><span class="sxs-lookup"><span data-stu-id="df31a-104">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df31a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="df31a-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="df31a-106">Требования</span><span class="sxs-lookup"><span data-stu-id="df31a-106">Requirements</span></span>  

 <span data-ttu-id="df31a-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df31a-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df31a-108">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df31a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df31a-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df31a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df31a-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df31a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df31a-111">См. также</span><span class="sxs-lookup"><span data-stu-id="df31a-111">See also</span></span>

- [<span data-ttu-id="df31a-112">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="df31a-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
