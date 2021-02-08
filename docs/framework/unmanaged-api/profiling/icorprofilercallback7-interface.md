---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback7'
title: Интерфейс ICorProfilerCallback7
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: 3db402db221fca4487939f9817b20ec0c5207fc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781744"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="29156-103">Интерфейс ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="29156-103">ICorProfilerCallback7 Interface</span></span>

<span data-ttu-id="29156-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="29156-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="29156-105">Подкласс [ICorProfilerCallback6](icorprofilercallback6-interface.md) , который предоставляет метод обратного вызова, используемый средой CLR для уведомления профилировщика, что обновляется поток символов, связанный с модулем в памяти.</span><span class="sxs-lookup"><span data-stu-id="29156-105">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29156-106">Методы</span><span class="sxs-lookup"><span data-stu-id="29156-106">Methods</span></span>  
  
|<span data-ttu-id="29156-107">Метод</span><span class="sxs-lookup"><span data-stu-id="29156-107">Method</span></span>|<span data-ttu-id="29156-108">Описание</span><span class="sxs-lookup"><span data-stu-id="29156-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29156-109">Метод ModuleInMemorySymbolsUpdated</span><span class="sxs-lookup"><span data-stu-id="29156-109">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="29156-110">Уведомляет профилировщик об обновлении потока символов, связанного с модулем в памяти.</span><span class="sxs-lookup"><span data-stu-id="29156-110">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29156-111">Требования</span><span class="sxs-lookup"><span data-stu-id="29156-111">Requirements</span></span>  

 <span data-ttu-id="29156-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29156-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29156-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29156-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29156-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29156-114">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29156-115">См. также</span><span class="sxs-lookup"><span data-stu-id="29156-115">See also</span></span>

- [<span data-ttu-id="29156-116">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="29156-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
