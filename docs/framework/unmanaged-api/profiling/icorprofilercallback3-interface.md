---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback3'
title: Интерфейс ICorProfilerCallback3
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 70fba8768fef5da411b566d918308989a3f6e863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788804"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="0c7d6-103">Интерфейс ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="0c7d6-103">ICorProfilerCallback3 Interface</span></span>

<span data-ttu-id="0c7d6-104">Предоставляет методы обратного вызова, используемые средой CLR для передачи сведений о состоянии подключения и отсоединения профилировщику.</span><span class="sxs-lookup"><span data-stu-id="0c7d6-104">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c7d6-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0c7d6-105">Methods</span></span>  
  
|<span data-ttu-id="0c7d6-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0c7d6-106">Method</span></span>|<span data-ttu-id="0c7d6-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0c7d6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c7d6-108">Метод InitializeForAttach</span><span class="sxs-lookup"><span data-stu-id="0c7d6-108">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="0c7d6-109">Вызывается средой CLR, чтобы предоставить профилировщику возможность инициализировать свое состояние после операции присоединения.</span><span class="sxs-lookup"><span data-stu-id="0c7d6-109">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="0c7d6-110">Метод ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="0c7d6-110">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="0c7d6-111">Вызывается средой CLR для указания на то, что профилировщик теперь может вызывать методы перехвата.</span><span class="sxs-lookup"><span data-stu-id="0c7d6-111">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="0c7d6-112">Метод ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="0c7d6-112">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="0c7d6-113">Уведомляет профилировщик о том, что среда CLR намерена выгрузить библиотеку DLL профилировщика.</span><span class="sxs-lookup"><span data-stu-id="0c7d6-113">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7d6-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c7d6-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c7d6-115">Требования</span><span class="sxs-lookup"><span data-stu-id="0c7d6-115">Requirements</span></span>  

 <span data-ttu-id="0c7d6-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c7d6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c7d6-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c7d6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c7d6-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c7d6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c7d6-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7d6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7d6-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0c7d6-120">See also</span></span>

- [<span data-ttu-id="0c7d6-121">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0c7d6-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0c7d6-122">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0c7d6-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0c7d6-123">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="0c7d6-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="0c7d6-124">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="0c7d6-124">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
