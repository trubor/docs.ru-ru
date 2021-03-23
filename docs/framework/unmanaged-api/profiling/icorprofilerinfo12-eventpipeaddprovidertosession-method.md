---
description: 'Дополнительные сведения о методе: ICorProfilerInfo12:: Евентпипеаддпровидертосессион'
title: 'Метод ICorProfilerInfo12:: Евентпипеаддпровидертосессион'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805692"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a><span data-ttu-id="acdc2-103">Метод ICorProfilerInfo12:: Евентпипеаддпровидертосессион</span><span class="sxs-lookup"><span data-stu-id="acdc2-103">ICorProfilerInfo12::EventPipeAddProviderToSession Method</span></span>

<span data-ttu-id="acdc2-104">Добавляет поставщик в существующий сеанс Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="acdc2-104">Adds a provider to an existing EventPipe session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="acdc2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="acdc2-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a><span data-ttu-id="acdc2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="acdc2-106">Parameters</span></span>

<span data-ttu-id="acdc2-107">`session` окне Идентификатор сеанса, в который добавляется поставщик.</span><span class="sxs-lookup"><span data-stu-id="acdc2-107">`session` [in] The ID of the session to add the provider to.</span></span>

<span data-ttu-id="acdc2-108">`providerConfig` окне Объект, `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` описывающий поставщика для добавления в сеанс.</span><span class="sxs-lookup"><span data-stu-id="acdc2-108">`providerConfig` [in] A `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` describing the provider to add to the session.</span></span>

## <a name="requirements"></a><span data-ttu-id="acdc2-109">Требования</span><span class="sxs-lookup"><span data-stu-id="acdc2-109">Requirements</span></span>  

<span data-ttu-id="acdc2-110">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="acdc2-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="acdc2-111">**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acdc2-111">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="acdc2-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="acdc2-112">See also</span></span>

- [<span data-ttu-id="acdc2-113">Общие сведения об EventPipe</span><span class="sxs-lookup"><span data-stu-id="acdc2-113">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="acdc2-114">Хорошо известные Евентпровидерс</span><span class="sxs-lookup"><span data-stu-id="acdc2-114">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="acdc2-115">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="acdc2-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="acdc2-116">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="acdc2-116">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="acdc2-117">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="acdc2-117">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="acdc2-118">Структура COR_PRF_EVENTPIPE_PROVIDER_CONFIG</span><span class="sxs-lookup"><span data-stu-id="acdc2-118">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Structure</span></span>](cor-prf-eventpipe-provider-config-structure.md)
