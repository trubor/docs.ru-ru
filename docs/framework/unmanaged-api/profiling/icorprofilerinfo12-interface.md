---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo12'
title: Интерфейс ICorProfilerInfo12
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805731"
---
# <a name="icorprofilerinfo12-interface"></a><span data-ttu-id="98575-103">Интерфейс ICorProfilerInfo12</span><span class="sxs-lookup"><span data-stu-id="98575-103">ICorProfilerInfo12 Interface</span></span>

 <span data-ttu-id="98575-104">Подкласс [ICorProfilerInfo11](icorprofilerinfo11-interface.md) , предоставляющий методы для создания евентпипе сеансов, событий и поставщиков.</span><span class="sxs-lookup"><span data-stu-id="98575-104">A subclass of [ICorProfilerInfo11](icorprofilerinfo11-interface.md) that provides methods to create EventPipe sessions, events, and providers.</span></span>
  
## <a name="methods"></a><span data-ttu-id="98575-105">Методы</span><span class="sxs-lookup"><span data-stu-id="98575-105">Methods</span></span>  
  
|<span data-ttu-id="98575-106">Метод</span><span class="sxs-lookup"><span data-stu-id="98575-106">Method</span></span>|<span data-ttu-id="98575-107">Описание</span><span class="sxs-lookup"><span data-stu-id="98575-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98575-108">Метод Евентпипестартсессион</span><span class="sxs-lookup"><span data-stu-id="98575-108">EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)|<span data-ttu-id="98575-109">Запускает сеанс Евентпипе профилировщика.</span><span class="sxs-lookup"><span data-stu-id="98575-109">Starts a profiler EventPipe session.</span></span>|
|[<span data-ttu-id="98575-110">Метод Евентпипеаддпровидертосессион</span><span class="sxs-lookup"><span data-stu-id="98575-110">EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|<span data-ttu-id="98575-111">Добавляет поставщик в существующий сеанс Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="98575-111">Adds a provider to an existing EventPipe session.</span></span>|
|[<span data-ttu-id="98575-112">Метод Евентпипестопсессион</span><span class="sxs-lookup"><span data-stu-id="98575-112">EventPipeStopSession Method</span></span>](icorprofilerinfo12-eventpipestopsession-method.md)|<span data-ttu-id="98575-113">Останавливает сеанс Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="98575-113">Stops an EventPipe session.</span></span>|
|[<span data-ttu-id="98575-114">Метод Евентпипекреатепровидер</span><span class="sxs-lookup"><span data-stu-id="98575-114">EventPipeCreateProvider Method</span></span>](icorprofilerinfo12-eventpipecreateprovider-method.md)|<span data-ttu-id="98575-115">Создает поставщик Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="98575-115">Creates an EventPipe provider.</span></span>|  
|[<span data-ttu-id="98575-116">Метод Евентпипежетпровидеринфо</span><span class="sxs-lookup"><span data-stu-id="98575-116">EventPipeGetProviderInfo Method</span></span>](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|<span data-ttu-id="98575-117">Возвращает имя поставщика Евентпипе из его идентификатора.</span><span class="sxs-lookup"><span data-stu-id="98575-117">Gets the name of an EventPipe provider from its ID.</span></span>|
|[<span data-ttu-id="98575-118">Метод Евентпипедефинивент</span><span class="sxs-lookup"><span data-stu-id="98575-118">EventPipeDefineEvent Method</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)|<span data-ttu-id="98575-119">Определяет событие для существующего поставщика Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="98575-119">Defines an event on an existing EventPipe provider.</span></span>|  
|[<span data-ttu-id="98575-120">Метод Евентпипевритивент</span><span class="sxs-lookup"><span data-stu-id="98575-120">EventPipeWriteEvent Method</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)|<span data-ttu-id="98575-121">Записывает событие Евентпипе.</span><span class="sxs-lookup"><span data-stu-id="98575-121">Writes an EventPipe event.</span></span>|
  
## <a name="requirements"></a><span data-ttu-id="98575-122">Требования</span><span class="sxs-lookup"><span data-stu-id="98575-122">Requirements</span></span>  

<span data-ttu-id="98575-123">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="98575-123">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="98575-124">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98575-124">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="98575-125">**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98575-125">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="98575-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="98575-126">See also</span></span>

- [<span data-ttu-id="98575-127">Общие сведения об EventPipe</span><span class="sxs-lookup"><span data-stu-id="98575-127">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="98575-128">Хорошо известные Евентпровидерс</span><span class="sxs-lookup"><span data-stu-id="98575-128">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="98575-129">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="98575-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="98575-130">Интерфейс ICorProfilerCallback10</span><span class="sxs-lookup"><span data-stu-id="98575-130">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
