---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback10'
title: Интерфейс ICorProfilerCallback10
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805653"
---
# <a name="icorprofilercallback10-interface"></a><span data-ttu-id="9376d-103">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="9376d-103">ICorProfilerCallback10 Interface</span></span>

 <span data-ttu-id="9376d-104">Подкласс [ICorProfilerCallback9](icorprofilercallback9-interface.md) , предоставляющий методы обратного вызова для уведомления профилировщика о том, что события евентпипе были доставлены в текущий активный сеанс профилировщика.</span><span class="sxs-lookup"><span data-stu-id="9376d-104">A subclass of [ICorProfilerCallback9](icorprofilercallback9-interface.md) that provides callback methods to notify the profiler that EventPipe events have been delivered to the profiler's currently active session.</span></span>
  
## <a name="methods"></a><span data-ttu-id="9376d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="9376d-105">Methods</span></span>  
  
|<span data-ttu-id="9376d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="9376d-106">Method</span></span>|<span data-ttu-id="9376d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="9376d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9376d-108">Метод Евентпипивентделиверед</span><span class="sxs-lookup"><span data-stu-id="9376d-108">EventPipeEventDelivered Method</span></span>](icorprofilercallback10-eventpipeeventdelivered-method.md)|<span data-ttu-id="9376d-109">Уведомляет профилировщик о том, что событие Евентпипе было доставлено в сеанс, Открытый профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="9376d-109">Notifies the profiler that an EventPipe event has been delivered to the session that the profiler has open.</span></span>|
|[<span data-ttu-id="9376d-110">Метод Евентпипепровидеркреатед</span><span class="sxs-lookup"><span data-stu-id="9376d-110">EventPipeProviderCreated Method</span></span>](icorprofilercallback10-eventpipeprovidercreated-method.md)|<span data-ttu-id="9376d-111">Уведомляет профилировщик о том, что создан поставщик Евентпипе, что позволяет профилировщику добавить этот поставщик в сеанс.</span><span class="sxs-lookup"><span data-stu-id="9376d-111">Notifies the profiler that an EventPipe provider has been created, allowing the profiler to add that provider the their session.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9376d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9376d-112">Requirements</span></span>  

<span data-ttu-id="9376d-113">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="9376d-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="9376d-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9376d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="9376d-115">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9376d-115">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9376d-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9376d-116">See also</span></span>

- [<span data-ttu-id="9376d-117">Общие сведения об EventPipe</span><span class="sxs-lookup"><span data-stu-id="9376d-117">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="9376d-118">Хорошо известные Евентпровидерс</span><span class="sxs-lookup"><span data-stu-id="9376d-118">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="9376d-119">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="9376d-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9376d-120">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="9376d-120">ICorProfilerInfo12 Interface</span></span>](ICorProfilerInfo12-interface.md)
- [<span data-ttu-id="9376d-121">ICorProfilerInfo12. Евентпипестартсессион, метод</span><span class="sxs-lookup"><span data-stu-id="9376d-121">ICorProfilerInfo12.EventPipeStartSession method</span></span>](ICorProfilerInfo12-eventpipestartsession-method.md)
- [<span data-ttu-id="9376d-122">ICorProfilerInfo12. Евентпипестопсессион, метод</span><span class="sxs-lookup"><span data-stu-id="9376d-122">ICorProfilerInfo12.EventPipeStopSession method</span></span>](ICorProfilerInfo12-eventpipestopsession-method.md)
