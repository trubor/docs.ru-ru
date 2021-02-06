---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ExceptionOSHandlerEnter'
title: Метод ICorProfilerCallback::ExceptionOSHandlerEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: 88dfd062451c63265716e7cf4c04292aa15f91ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657623"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="3d103-103">Метод ICorProfilerCallback::ExceptionOSHandlerEnter</span><span class="sxs-lookup"><span data-stu-id="3d103-103">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="3d103-104">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="3d103-104">Not implemented.</span></span> <span data-ttu-id="3d103-105">Профилировщик, которому требуются сведения о неуправляемом исключении, должен получить эти сведения с помощью других средств.</span><span class="sxs-lookup"><span data-stu-id="3d103-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d103-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d103-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3d103-107">Требования</span><span class="sxs-lookup"><span data-stu-id="3d103-107">Requirements</span></span>  

 <span data-ttu-id="3d103-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d103-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d103-109">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d103-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d103-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d103-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d103-111">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d103-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d103-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3d103-112">See also</span></span>

- [<span data-ttu-id="3d103-113">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3d103-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
