---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback9'
title: Интерфейс ICorProfilerCallback9
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4bfcaf6f8985909ef9142ef4d08535a19facd7e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781653"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="5f61d-103">Интерфейс ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="5f61d-103">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="5f61d-104">[Поддерживается в платформа .NET Framework 4.7.2 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="5f61d-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="5f61d-105">Подкласс [ICorProfilerCallback8](icorprofilercallback8-interface.md) , предоставляющий метод обратного вызова, используемый средой CLR для уведомления профилировщика о том, что динамический метод был собран в мусор и затем выгружен.</span><span class="sxs-lookup"><span data-stu-id="5f61d-105">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f61d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="5f61d-106">Methods</span></span>  
  
|<span data-ttu-id="5f61d-107">Метод</span><span class="sxs-lookup"><span data-stu-id="5f61d-107">Method</span></span>|<span data-ttu-id="5f61d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5f61d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f61d-109">Метод DynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="5f61d-109">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="5f61d-110">Уведомляет профилировщик о том, что динамический метод был собран в мусор и затем выгружен.</span><span class="sxs-lookup"><span data-stu-id="5f61d-110">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f61d-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5f61d-111">Requirements</span></span>  

 <span data-ttu-id="5f61d-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f61d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f61d-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f61d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="5f61d-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f61d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5f61d-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5f61d-115">See also</span></span>

- [<span data-ttu-id="5f61d-116">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5f61d-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5f61d-117">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="5f61d-117">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="5f61d-118">ICorProfilerCallback8. Динамикмесоджиткомпилатионстартед, метод</span><span class="sxs-lookup"><span data-stu-id="5f61d-118">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="5f61d-119">ICorProfilerCallback8. Динамикмесоджиткомпилатионфинишед, метод</span><span class="sxs-lookup"><span data-stu-id="5f61d-119">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
