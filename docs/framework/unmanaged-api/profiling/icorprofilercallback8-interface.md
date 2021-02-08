---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback8'
title: Интерфейс ICorProfilerCallback8
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 8dd9b8eea82f38b7598d578bd718743af826070d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781679"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="6d6a6-103">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="6d6a6-103">ICorProfilerCallback8 Interface</span></span>

<span data-ttu-id="6d6a6-104">[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="6d6a6-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="6d6a6-105">Подкласс [ICorProfilerCallback7](icorprofilercallback7-interface.md) , предоставляющий методы обратного вызова, используемые средой CLR для уведомления профилировщика о начале и завершении JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="6d6a6-105">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="6d6a6-106">Методы</span><span class="sxs-lookup"><span data-stu-id="6d6a6-106">Methods</span></span>  
  
|<span data-ttu-id="6d6a6-107">Метод</span><span class="sxs-lookup"><span data-stu-id="6d6a6-107">Method</span></span>|<span data-ttu-id="6d6a6-108">Описание</span><span class="sxs-lookup"><span data-stu-id="6d6a6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d6a6-109">Метод DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="6d6a6-109">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="6d6a6-110">Уведомляет профилировщик о запуске JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="6d6a6-110">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="6d6a6-111">Метод DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="6d6a6-111">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="6d6a6-112">Уведомляет профилировщик о завершении JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="6d6a6-112">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d6a6-113">Требования</span><span class="sxs-lookup"><span data-stu-id="6d6a6-113">Requirements</span></span>  

 <span data-ttu-id="6d6a6-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6a6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6a6-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d6a6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="6d6a6-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6d6a6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="6d6a6-117">See also</span></span>

- [<span data-ttu-id="6d6a6-118">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="6d6a6-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6d6a6-119">Интерфейс ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="6d6a6-119">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
