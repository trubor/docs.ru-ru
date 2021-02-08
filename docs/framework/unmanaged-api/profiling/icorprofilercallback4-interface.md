---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback4'
title: Интерфейс ICorProfilerCallback4
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 882f234cb94ccd65203b42ed213aab6355250af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788752"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="ab155-103">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="ab155-103">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="ab155-104">Предоставляет методы обратного вызова, используемые средой CLR для передачи информации в профилировщик.</span><span class="sxs-lookup"><span data-stu-id="ab155-104">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab155-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ab155-105">Methods</span></span>  
  
|<span data-ttu-id="ab155-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ab155-106">Method</span></span>|<span data-ttu-id="ab155-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ab155-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab155-108">Метод GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="ab155-108">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="ab155-109">Позволяет профилировщику кода устанавливать альтернативные флаги создания кода для нового текста перекомпилированного метода.</span><span class="sxs-lookup"><span data-stu-id="ab155-109">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="ab155-110">Метод MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="ab155-110">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="ab155-111">Сообщает о новом макете объектов в куче в результате сборки мусора для сжатия.</span><span class="sxs-lookup"><span data-stu-id="ab155-111">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="ab155-112">Метод ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="ab155-112">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="ab155-113">Уведомляет профилировщик о том, что JIT-компилятор завершил повторную компиляцию функции.</span><span class="sxs-lookup"><span data-stu-id="ab155-113">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="ab155-114">Метод ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="ab155-114">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="ab155-115">Уведомляет профилировщик о том, что JIT-компилятор начал перекомпилировать функцию.</span><span class="sxs-lookup"><span data-stu-id="ab155-115">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="ab155-116">Метод ReJITError</span><span class="sxs-lookup"><span data-stu-id="ab155-116">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="ab155-117">Сообщает об ошибке, возникшей при обработке запроса на перекомпиляцию.</span><span class="sxs-lookup"><span data-stu-id="ab155-117">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="ab155-118">Метод SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="ab155-118">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="ab155-119">Предоставляет информацию о структуре объектов в куче в результате сборки мусора без сжатия.</span><span class="sxs-lookup"><span data-stu-id="ab155-119">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab155-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ab155-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab155-121">Требования</span><span class="sxs-lookup"><span data-stu-id="ab155-121">Requirements</span></span>  

 <span data-ttu-id="ab155-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab155-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab155-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab155-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab155-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab155-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab155-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab155-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab155-126">См. также</span><span class="sxs-lookup"><span data-stu-id="ab155-126">See also</span></span>

- [<span data-ttu-id="ab155-127">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="ab155-127">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="ab155-128">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ab155-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ab155-129">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ab155-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
