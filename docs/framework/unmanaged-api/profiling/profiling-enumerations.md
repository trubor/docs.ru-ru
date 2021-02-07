---
description: 'Дополнительные сведения: Профилирование перечислений'
title: Перечисления профилирования
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: f202e70dd27654dd39740851549477d4a6bf77a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736756"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="5a4af-103">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="5a4af-103">Profiling Enumerations</span></span>

<span data-ttu-id="5a4af-104">В этом разделе описываются неуправляемые перечисления, которые использует API профилирования.</span><span class="sxs-lookup"><span data-stu-id="5a4af-104">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a4af-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="5a4af-105">In This Section</span></span>  

 [<span data-ttu-id="5a4af-106">Перечисление COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5a4af-106">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="5a4af-107">Указывает тип предложения исключения, код которого был только что введен или удален.</span><span class="sxs-lookup"><span data-stu-id="5a4af-107">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="5a4af-108">Перечисление COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5a4af-108">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="5a4af-109">Определяет флаги создания кода, которые можно задать с помощью метода [икорпрофилерфунктионконтрол:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4af-109">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="5a4af-110">Перечисление COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5a4af-110">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="5a4af-111">Описывает метод завершения для объекта.</span><span class="sxs-lookup"><span data-stu-id="5a4af-111">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="5a4af-112">Перечисление COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="5a4af-112">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="5a4af-113">Идентифицирует создание сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="5a4af-113">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="5a4af-114">Перечисление COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="5a4af-114">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="5a4af-115">Указывает причину возникновения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="5a4af-115">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="5a4af-116">Перечисление COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5a4af-116">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="5a4af-117">Указывает свойства корня сборщика мусора.</span><span class="sxs-lookup"><span data-stu-id="5a4af-117">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="5a4af-118">Перечисление COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="5a4af-118">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="5a4af-119">Указывает тип корня сборщика мусора, предоставляемый обратным вызовом [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4af-119">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="5a4af-120">Перечисление COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="5a4af-120">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="5a4af-121">Предоставляет флаги в дополнение к тем, которые находятся в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) , которые профилировщик может указать в методе [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) при загрузке.</span><span class="sxs-lookup"><span data-stu-id="5a4af-121">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="5a4af-122">Перечисление COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="5a4af-122">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="5a4af-123">Указывает результат кэшированной функции поиска.</span><span class="sxs-lookup"><span data-stu-id="5a4af-123">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="5a4af-124">Перечисление COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="5a4af-124">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="5a4af-125">Содержит постоянные значения, которые указывают специальные идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="5a4af-125">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="5a4af-126">Перечисление COR_PRF_MODULE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5a4af-126">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="5a4af-127">Указывает свойства модуля.</span><span class="sxs-lookup"><span data-stu-id="5a4af-127">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="5a4af-128">Перечисление COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="5a4af-128">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="5a4af-129">Содержит значения, используемые для указания поведения, возможностей или событий, на которые желает подписаться профилировщик.</span><span class="sxs-lookup"><span data-stu-id="5a4af-129">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="5a4af-130">Перечисление COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="5a4af-130">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="5a4af-131">Содержит значения, которые указывают версию среды CLR.</span><span class="sxs-lookup"><span data-stu-id="5a4af-131">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="5a4af-132">Перечисление COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="5a4af-132">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="5a4af-133">Указывает количество данных для обратной передачи со снимком стека в каждом вызове функции профилировщика `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="5a4af-133">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="5a4af-134">Перечисление COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="5a4af-134">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="5a4af-135">Указывает, является ли поле статическим и, если да, относящееся к этому полю статическое качество.</span><span class="sxs-lookup"><span data-stu-id="5a4af-135">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="5a4af-136">Перечисление COR_PRF_SUSPEND_REASON</span><span class="sxs-lookup"><span data-stu-id="5a4af-136">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="5a4af-137">Указывает причину приостановки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5a4af-137">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="5a4af-138">Перечисление COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="5a4af-138">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="5a4af-139">Указывает причину перехода из управляемого в неуправляемый код или наоборот.</span><span class="sxs-lookup"><span data-stu-id="5a4af-139">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a4af-140">См. также</span><span class="sxs-lookup"><span data-stu-id="5a4af-140">Related Sections</span></span>  

 [<span data-ttu-id="5a4af-141">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="5a4af-141">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="5a4af-142">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5a4af-142">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="5a4af-143">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="5a4af-143">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="5a4af-144">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="5a4af-144">Profiling Structures</span></span>](profiling-structures.md)
