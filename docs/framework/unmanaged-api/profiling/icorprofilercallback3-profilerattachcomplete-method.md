---
description: 'Дополнительные сведения о методе: ICorProfilerCallback3::P Рофилераттачкомплете'
title: Метод ICorProfilerCallback3::ProfilerAttachComplete
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: dcd8ab9fed402593fc955050b0d3be6f8a46730a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788791"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="5091d-103">Метод ICorProfilerCallback3::ProfilerAttachComplete</span><span class="sxs-lookup"><span data-stu-id="5091d-103">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>

<span data-ttu-id="5091d-104">Вызывается средой CLR для указания на то, что профилировщик теперь может вызывать методы перехвата [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) и [ICorProfilerInfo3:: EnumModules](icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5091d-104">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5091d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5091d-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5091d-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="5091d-106">Remarks</span></span>  

 <span data-ttu-id="5091d-107">`ProfilerAttachComplete`Обратный вызов выдается после вызова метода [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5091d-107">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="5091d-108">Он указывает следующее.</span><span class="sxs-lookup"><span data-stu-id="5091d-108">It indicates the following:</span></span>  
  
- <span data-ttu-id="5091d-109">Обратные вызовы, которые были запрошены профилировщиком в `InitializeForAttach`, были активированы.</span><span class="sxs-lookup"><span data-stu-id="5091d-109">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="5091d-110">Профилировщик теперь может выполнять захват в связанных идентификаторах, не заботясь об отсутствующих уведомлениях.</span><span class="sxs-lookup"><span data-stu-id="5091d-110">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="5091d-111">Среда CLR игнорирует возвращаемое значение из этого обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="5091d-111">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5091d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="5091d-112">Requirements</span></span>  

 <span data-ttu-id="5091d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5091d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5091d-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5091d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5091d-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5091d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5091d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5091d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5091d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5091d-117">See also</span></span>

- [<span data-ttu-id="5091d-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5091d-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5091d-119">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="5091d-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5091d-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5091d-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5091d-121">Профилирование</span><span class="sxs-lookup"><span data-stu-id="5091d-121">Profiling</span></span>](index.md)
