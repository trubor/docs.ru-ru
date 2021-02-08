---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback6'
title: Интерфейс ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 12eaafff8bd9ab8d4d58eac8f2d62415531bc898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781757"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="95d12-103">Интерфейс ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="95d12-103">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="95d12-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="95d12-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="95d12-105">Подкласс [ICorProfilerCallback5](icorprofilercallback5-interface.md) , предоставляющий метод обратного вызова, который среда CLR использует для уведомления профилировщика о загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="95d12-105">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95d12-106">Методы</span><span class="sxs-lookup"><span data-stu-id="95d12-106">Methods</span></span>  
  
|<span data-ttu-id="95d12-107">Метод</span><span class="sxs-lookup"><span data-stu-id="95d12-107">Method</span></span>|<span data-ttu-id="95d12-108">Описание</span><span class="sxs-lookup"><span data-stu-id="95d12-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95d12-109">Метод GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="95d12-109">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="95d12-110">Уведомляет профилировщика о том, что сборка находится на очень ранней стадии загрузки, когда среда CLR выполняет обход замыкания ссылки на сборку.</span><span class="sxs-lookup"><span data-stu-id="95d12-110">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d12-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="95d12-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d12-112">Требования</span><span class="sxs-lookup"><span data-stu-id="95d12-112">Requirements</span></span>  

 <span data-ttu-id="95d12-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d12-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95d12-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95d12-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95d12-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d12-116">См. также</span><span class="sxs-lookup"><span data-stu-id="95d12-116">See also</span></span>

- [<span data-ttu-id="95d12-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="95d12-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
