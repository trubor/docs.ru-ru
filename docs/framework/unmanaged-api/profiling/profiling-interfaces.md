---
description: 'Дополнительные сведения: интерфейсы профилирования'
title: Профилирующие интерфейсы
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: d35931c0caad93116d7ea26d29020d84e48ebc29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798931"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="729a7-103">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="729a7-103">Profiling Interfaces</span></span>

<span data-ttu-id="729a7-104">В этом разделе описываются неуправляемые интерфейсы, позволяющие профилировать программу, выполняемую в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="729a7-104">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="729a7-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="729a7-105">In This Section</span></span>  

 [<span data-ttu-id="729a7-106">Интерфейс ICLRProfiling</span><span class="sxs-lookup"><span data-stu-id="729a7-106">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="729a7-107">Предоставляет метод [AttachProfiler](iclrprofiling-attachprofiler-method.md) , который позволяет профилировщику присоединяться к выполняющемуся процессу.</span><span class="sxs-lookup"><span data-stu-id="729a7-107">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="729a7-108">Интерфейс ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="729a7-108">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="729a7-109">Позволяет профилировщику сообщать о CLR ссылок на сборки, которые профилировщик будет добавлять в обратный вызов [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="729a7-109">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="729a7-110">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="729a7-110">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="729a7-111">Предоставляет методы, используемые средой CLR для уведомления профилировщика кода при событиях, на которые подписан профилировщик.</span><span class="sxs-lookup"><span data-stu-id="729a7-111">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="729a7-112">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="729a7-112">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="729a7-113">Расширяет интерфейс `ICorProfilerCallback` обратными вызовами, поддерживаемыми платформой .NET Framework 2.0 и более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="729a7-113">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="729a7-114">Интерфейс ICorProfilerCallback3</span><span class="sxs-lookup"><span data-stu-id="729a7-114">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="729a7-115">Предоставляет методы обратного вызова, используемые средой CLR для передачи сведений о подключенном и отключенном состоянии профилировщику.</span><span class="sxs-lookup"><span data-stu-id="729a7-115">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="729a7-116">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="729a7-116">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="729a7-117">Предоставляет методы обратного вызова, используемые средой CLR для передачи сведений профилировщику.</span><span class="sxs-lookup"><span data-stu-id="729a7-117">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="729a7-118">Интерфейс ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="729a7-118">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="729a7-119">Предоставляет метод, идентифицирующий транзитивное замыкание объектов, на которые ссылаются корни сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="729a7-119">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="729a7-120">Интерфейс ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="729a7-120">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="729a7-121">Предоставляет метод обратного вызова, который используется средой CLR для уведомления профилировщика о загрузке сборки.</span><span class="sxs-lookup"><span data-stu-id="729a7-121">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="729a7-122">Интерфейс ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="729a7-122">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="729a7-123">Предоставляет метод обратного вызова, используемый средой CLR для уведомления профилировщика о том, что поток символов, связанный с модулем в памяти, обновлен.</span><span class="sxs-lookup"><span data-stu-id="729a7-123">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="729a7-124">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="729a7-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="729a7-125">Предоставляет методы обратного вызова, используемые средой CLR для уведомления профилировщика о начале и завершении JIT-компиляции динамического метода.</span><span class="sxs-lookup"><span data-stu-id="729a7-125">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="729a7-126">Интерфейс ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="729a7-126">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="729a7-127">Предоставляет метод обратного вызова, используемый средой CLR для уведомления профилировщика о том, что динамический метод уничтожается сборщиком мусора и затем выгружается.</span><span class="sxs-lookup"><span data-stu-id="729a7-127">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="729a7-128">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="729a7-128">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="729a7-129">Предоставляет методы, позволяющие профилировщику кода взаимодействовать со средой выполнения CLR и контролировать порядок генерирования кода JIT-компилятором при повторной компиляции указанного метода.</span><span class="sxs-lookup"><span data-stu-id="729a7-129">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="729a7-130">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="729a7-130">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="729a7-131">Предоставляет методы для последовательного перебора коллекции функций в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="729a7-131">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="729a7-132">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="729a7-132">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="729a7-133">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий и для запроса сведений.</span><span class="sxs-lookup"><span data-stu-id="729a7-133">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="729a7-134">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="729a7-134">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="729a7-135">Расширяет интерфейс `ICorProfilerInfo` методами, поддерживаемыми платформой .NET Framework 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="729a7-135">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="729a7-136">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="729a7-136">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="729a7-137">Расширяет `ICorProfilerInfo2` интерфейс с помощью методов, поддерживаемых в платформа .NET Framework 4 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="729a7-137">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="729a7-138">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="729a7-138">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="729a7-139">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий и для запроса сведений.</span><span class="sxs-lookup"><span data-stu-id="729a7-139">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="729a7-140">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="729a7-140">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="729a7-141">Предоставляет методы, которые используются профилировщиками кода для взаимодействия со средой CLR с целью управления отслеживанием событий.</span><span class="sxs-lookup"><span data-stu-id="729a7-141">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="729a7-142">Интерфейс ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="729a7-142">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="729a7-143">Предоставляет перечислитель для всех методов, принадлежащих заданному модулю NGen и встроенных в тело данного метода.</span><span class="sxs-lookup"><span data-stu-id="729a7-143">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="729a7-144">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="729a7-144">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="729a7-145">Предоставляет метод для применения новых заданных метаданных к модулю и предоставляет доступ к потоку символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="729a7-145">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="729a7-146">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="729a7-146">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="729a7-147">Предоставляет методы для последовательного перебора коллекции модулей, загруженных приложением или профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="729a7-147">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="729a7-148">Интерфейс ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="729a7-148">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="729a7-149">Предоставляет методы для последовательного прохода по коллекции замороженных объектов, созданных [Ngen.exe (генератор образов в машинном код)](../../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="729a7-149">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="729a7-150">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="729a7-150">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="729a7-151">Предоставляет методы для последовательного перебора коллекции потоков в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="729a7-151">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="729a7-152">Интерфейс IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="729a7-152">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="729a7-153">Предоставляет метод [выделения](imethodmalloc-alloc-method.md) для выделения памяти для нового текста функции MSIL.</span><span class="sxs-lookup"><span data-stu-id="729a7-153">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="729a7-154">См. также</span><span class="sxs-lookup"><span data-stu-id="729a7-154">Related Sections</span></span>  

 [<span data-ttu-id="729a7-155">Общие сведения о профилировании</span><span class="sxs-lookup"><span data-stu-id="729a7-155">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="729a7-156">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="729a7-156">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="729a7-157">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="729a7-157">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="729a7-158">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="729a7-158">Profiling Structures</span></span>](profiling-structures.md)
