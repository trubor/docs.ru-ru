---
description: 'Дополнительные сведения о методе: ICorProfilerCallback10:: Евентпипепровидеркреатед'
title: 'Метод ICorProfilerCallback10:: Евентпипепровидеркреатед'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeProviderCreated
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 6ce96bf301f1c559923df64edd9dd214c28db918
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231314"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a><span data-ttu-id="2b657-103">Метод ICorProfilerCallback10:: Евентпипепровидеркреатед</span><span class="sxs-lookup"><span data-stu-id="2b657-103">ICorProfilerCallback10::EventPipeProviderCreated Method</span></span>

<span data-ttu-id="2b657-104">Уведомляет профилировщик каждый раз, когда создается поставщик Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="2b657-104">Notifies the profiler whenever an EventPipe provider is created.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="2b657-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b657-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider);
```  
  
## <a name="parameters"></a><span data-ttu-id="2b657-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2b657-106">Parameters</span></span>

<span data-ttu-id="2b657-107">`provider` окне Созданный поставщик.</span><span class="sxs-lookup"><span data-stu-id="2b657-107">`provider` [in] The provider that was created.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b657-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2b657-108">Requirements</span></span>  

<span data-ttu-id="2b657-109">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="2b657-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="2b657-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b657-110">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="2b657-111">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b657-111">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b657-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2b657-112">See also</span></span>

- [<span data-ttu-id="2b657-113">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="2b657-113">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2b657-114">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="2b657-114">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="2b657-115">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="2b657-115">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="2b657-116">ICorProfilerInfo12. Евентпипеаддпровидертосессион, метод</span><span class="sxs-lookup"><span data-stu-id="2b657-116">ICorProfilerInfo12.EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
