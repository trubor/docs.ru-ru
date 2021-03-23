---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипестопсессион'
title: 'Метод ICorProfilerInfo12:: Евентпипестопсессион'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeStopSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c1b104f63755bcec52a113be7e2aa9af76ecd34e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805718"
---
# <a name="icorprofilerinfo12eventpipestopsession-method"></a><span data-ttu-id="dccce-103">Метод ICorProfilerInfo12:: Евентпипестопсессион</span><span class="sxs-lookup"><span data-stu-id="dccce-103">ICorProfilerInfo12::EventPipeStopSession Method</span></span>

<span data-ttu-id="dccce-104">Останавливает сеанс Евентпипе, предотвращая запись всех будущих событий в сеанс.</span><span class="sxs-lookup"><span data-stu-id="dccce-104">Stops an EventPipe session, preventing any future events from being written to the session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="dccce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dccce-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeStopSession(
        [in] EVENTPIPE_SESSION session);
```  
  
## <a name="parameters"></a><span data-ttu-id="dccce-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dccce-106">Parameters</span></span>

<span data-ttu-id="dccce-107">`session` окне Идентификатор останавливаемого сеанса.</span><span class="sxs-lookup"><span data-stu-id="dccce-107">`session` [in] The ID of the session to stop.</span></span>

## <a name="requirements"></a><span data-ttu-id="dccce-108">Требования</span><span class="sxs-lookup"><span data-stu-id="dccce-108">Requirements</span></span>  

<span data-ttu-id="dccce-109">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="dccce-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="dccce-110">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dccce-110">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dccce-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dccce-111">See also</span></span>

- [<span data-ttu-id="dccce-112">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="dccce-112">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dccce-113">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="dccce-113">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="dccce-114">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="dccce-114">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
