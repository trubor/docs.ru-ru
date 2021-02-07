---
description: 'Дополнительные сведения: Отладка интерфейсов'
title: Интерфейсы отладки
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717970"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="e5a2c-103">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e5a2c-103">Debugging Interfaces</span></span>

<span data-ttu-id="e5a2c-104">В этом разделе описываются неуправляемые интерфейсы отладки, управляющие отладкой программы, выполняемой в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-104">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5a2c-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="e5a2c-105">In This Section</span></span>  

 <span data-ttu-id="e5a2c-106">[Интерфейс Иклрдатаенуммеморирегионс](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-106">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-107">Предоставляет метод, выполняющий перечисление областей памяти, заданной вызовами.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-107">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="e5a2c-108">[Интерфейс Иклрдатаенуммеморирегионскаллбакк](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-108">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-109">Предоставляет метод обратного вызова для метода `EnumMemoryRegions`, сообщающий отладчику результат попытки перечисления заданной области памяти.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-109">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="e5a2c-110">[Интерфейс ICLRDataTarget](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-110">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-111">Предоставляет методы для взаимодействия с целевым процессом среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-111">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="e5a2c-112">[Интерфейс ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-112">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-113">Подкласс `ICLRDataTarget`, используемый уровнем служб доступа к данным с целью управления областями виртуальной памяти в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-113">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="e5a2c-114">[Интерфейс метод iclrdatatarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-114">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-115">Подкласс [ICLRDataTarget2](iclrdatatarget2-interface.md) , предоставляющий доступ к сведениям об исключениях.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-115">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="e5a2c-116">[Интерфейс ICLRDebugging](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-116">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-117">Предоставляет методы, обрабатывающие загрузку и выгрузку модулей для отладки.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-117">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="e5a2c-118">[Интерфейс Иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-118">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-119">Включает метод [метода ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) , который получает интерфейс обратного вызова поставщика библиотеки, который позволяет находить и загружать библиотеки отладки, относящиеся к конкретной версии среды CLR, по запросу.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-119">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="e5a2c-120">[Интерфейс Иклрметадаталокатор](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-120">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-121">Интерфейс, используемый уровнем служб доступа к данным для определения местонахождения метаданных сборок в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-121">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="e5a2c-122">[Интерфейс ICorDebug](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-122">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-123">Предоставляет методы, позволяющие разработчикам отлаживать приложения в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-123">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="e5a2c-124">[Интерфейс ICorDebugAppDomain](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-124">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-125">Предоставляет методы для отладки доменов приложения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-125">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="e5a2c-126">[Интерфейс ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-126">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-127">Предоставляет методы для работы с массивами, указателями, указателями функций и типами ByRef.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-127">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="e5a2c-128">Этот интерфейс является расширением интерфейса `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-128">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="e5a2c-129">[Интерфейс ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-129">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-130">Предоставляет методы для работы с типами среда выполнения Windows в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-130">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="e5a2c-131">Этот интерфейс является расширением интерфейса `ICorDebugAppDomain` и `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-131">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="e5a2c-132">[Интерфейс ICorDebugAppDomain4](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-132">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-133">Логически расширяет интерфейс [ICorDebugAppDomain](icordebugappdomain-interface.md) для получения управляемого объекта из вызываемой оболочки COM.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-133">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="e5a2c-134">[Интерфейс Икордебугаппдомаиненум](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-134">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-135">Предоставляет метод, возвращающий заданное число значений `ICorDebugAppDomain`, начиная со следующего расположения в перечислении.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-135">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="e5a2c-136">[Интерфейс ICorDebugArrayValue](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-136">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-137">Подкласс интерфейса `ICorDebugHeapValue`, представляющий одномерный или многомерный массив.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-137">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="e5a2c-138">[Интерфейс ICorDebugAssembly](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-138">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-139">Представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-139">Represents an assembly.</span></span>  
  
 <span data-ttu-id="e5a2c-140">[Интерфейс ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-140">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-141">Представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-141">Represents an assembly.</span></span> <span data-ttu-id="e5a2c-142">Этот интерфейс является расширением интерфейса `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-142">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="e5a2c-143">[Интерфейс ICorDebugAssembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-143">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-144">Логически расширяет интерфейс [ICorDebugAssembly](icordebugassembly-interface.md) , чтобы обеспечить поддержку для сборок контейнеров и содержащихся в них сборок.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-144">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="e5a2c-145">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-145">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-146">[Интерфейс ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-146">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-147">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-147">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-148">[Интерфейс Икордебугблоккингобжектенум](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-148">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-149">Предоставляет перечислитель для списка структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-149">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="e5a2c-150">[Интерфейс Икордебугбоксвалуе](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-150">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-151">Подкласс интерфейса `ICorDebugHeapValue`, представляющий упакованное значение объектов класса.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-151">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="e5a2c-152">[Интерфейс Икордебугбреакпоинт](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-152">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-153">Представляет точку останова в функции или контрольную точку для значения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-153">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="e5a2c-154">[Интерфейс ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-154">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-155">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-155">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-156">[Интерфейс ICorDebugChain](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-156">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-157">Представляет сегмент физического или логического стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-157">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="e5a2c-158">[Интерфейс Икордебугчаиненум](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-158">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-159">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-159">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-160">[Интерфейс ICorDebugClass](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-160">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-161">Представляет тип, который может быть базовым или сложным (иными словами, пользовательским).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-161">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e5a2c-162">Если тип универсальный, `ICorDebugClass` представляет универсальный тип, у которого отсутствуют экземпляры.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-162">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="e5a2c-163">[Интерфейс ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-163">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-164">Представляет универсальный класс или класс параметром метода типа <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-164">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="e5a2c-165">Этот интерфейс расширяет интерфейс `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-165">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="e5a2c-166">[Интерфейс ICorDebugCode](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-166">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-167">Представляет сегмент кода на языке MSIL или сегмент машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-167">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="e5a2c-168">[Интерфейс ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-168">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-169">Предоставляет методы, расширяющие возможности интерфейса `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-169">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="e5a2c-170">[Интерфейс ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-170">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-171">Предоставляет метод, расширяющий интерфейс [ICorDebugCode](icordebugcode-interface1.md) и [ICorDebugCode2](icordebugcode2-interface.md) для предоставления сведений об управляемом возвращаемом значении.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-171">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="e5a2c-172">[Интерфейс ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-172">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-173">Предоставляет метод, позволяющий отладчику перечислить локальные переменные и аргументы в функции.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-173">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="e5a2c-174">[Интерфейс Икордебугкодинум](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-174">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-175">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-175">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-176">[Интерфейс Икордебугкомобжектвалуе](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-176">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-177">Предоставляет методы для получения кэшированных объектов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-177">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="e5a2c-178">[Интерфейс Икордебугконтекст](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-178">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-179">Представляет объект контекста.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-179">Represents a context object.</span></span> <span data-ttu-id="e5a2c-180">Этот интерфейс еще не реализован.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-180">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="e5a2c-181">[Интерфейс ICorDebugController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-181">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-182">Представляет область (<xref:System.Diagnostics.Process> или <xref:System.AppDomain>), в которой можно осуществлять управление контекстом выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-182">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="e5a2c-183">[Интерфейс ICorDebugDataTarget](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-183">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-184">Предоставляет интерфейс обратного вызова, обеспечивающий доступ к конкретному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-184">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="e5a2c-185">[Интерфейс метод icordebugdatatarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-185">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-186">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-186">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="e5a2c-187">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-187">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-188">[Интерфейс ICorDebugDataTarget3](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-188">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-189">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) , чтобы предоставить сведения о загруженных модулях.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-189">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="e5a2c-190">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-190">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-191">[Интерфейс ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-191">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-192">Определяет базовый интерфейс, из которого возникают все события отладки `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-192">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="e5a2c-193">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-193">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-194">[Интерфейс Икордебужедитандконтинуирроринфо](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-194">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-195">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-195">Obsolete.</span></span> <span data-ttu-id="e5a2c-196">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-196">Do not use this interface.</span></span>  
  
 <span data-ttu-id="e5a2c-197">[Интерфейс метод icordebugeditandcontinuesnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-197">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-198">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-198">Obsolete.</span></span> <span data-ttu-id="e5a2c-199">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-199">Do not use this interface.</span></span>  
  
 <span data-ttu-id="e5a2c-200">[Интерфейс ICorDebugEnum](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-200">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-201">Служит абстрактным базовым интерфейсом для перечислителей отладки.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-201">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="e5a2c-202">[Интерфейс ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-202">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-203">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-203">Obsolete.</span></span> <span data-ttu-id="e5a2c-204">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-204">Do not use this interface.</span></span>  
  
 <span data-ttu-id="e5a2c-205">[Интерфейс ICorDebugEval](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-205">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-206">Предоставляет методы, позволяющие отладчику выполнять код в контексте отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-206">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="e5a2c-207">[Интерфейс ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-207">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-208">Расширяет интерфейс `ICorDebugEval` для предоставления поддержки универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-208">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="e5a2c-209">[Интерфейс Икордебужексцептиондебужевент](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-209">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-210">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий исключения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-210">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="e5a2c-211">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-211">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-212">[Интерфейс ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-212">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-213">Предоставляет перечислитель для сведений стека вызовов, встроенных в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-213">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="e5a2c-214">[Интерфейс ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-214">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-215">Расширяет интерфейс [ICorDebugObjectValue](icordebugobjectvalue-interface.md) для предоставления сведений о трассировке стека из управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-215">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="e5a2c-216">[Интерфейс ICorDebugFrame](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-216">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-217">Представляет кадр текущего стека.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-217">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="e5a2c-218">[Интерфейс ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-218">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-219">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-219">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-220">[Интерфейс ICorDebugFunction](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-220">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-221">Представляет управляемую функцию или метод.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-221">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="e5a2c-222">[Интерфейс ICorDebugFunction2](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-222">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-223">Локально расширяет интерфейс `ICorDebugFunction` для предоставления поддержки отладки в пошаговом режиме "Только мой код".</span><span class="sxs-lookup"><span data-stu-id="e5a2c-223">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="e5a2c-224">[Интерфейс ICorDebugFunction3](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-224">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-225">Логически расширяет интерфейс [ICorDebugFunction](icordebugfunction-interface1.md) , чтобы предоставить доступ к коду из запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-225">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="e5a2c-226">[Интерфейс ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-226">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-227">Расширяет интерфейс `ICorDebugBreakpoint` для поддержки точек останова в функциях.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-227">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="e5a2c-228">[Интерфейс ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-228">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-229">Предоставляет перечислитель для объектов, для которых будет выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-229">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="e5a2c-230">[Интерфейс ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-230">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-231">Подкласс интерфейса `ICorDebugValue`, применяемый ко всем значениям.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-231">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="e5a2c-232">Этот интерфейс предоставляет для значения методы Get и Set.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-232">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="e5a2c-233">[Интерфейс ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-233">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-234">Предоставляет перечислитель для объекта, сопоставляющего идентификаторы GUID и соответствующие объекты `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-234">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="e5a2c-235">[Интерфейс ICorDebugHandleValue](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-235">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-236">Подкласс интерфейса `ICorDebugReferenceValue`, представляющий значение ссылки, для которого отладчик создал дескриптор сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-236">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="e5a2c-237">[Интерфейс Икордебугхеапенум](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-237">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-238">Предоставляет перечислитель для объектов в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-238">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="e5a2c-239">[Интерфейс Икордебугхеапсегментенум](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-239">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-240">Предоставляет перечислитель для областей памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-240">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="e5a2c-241">[Интерфейс ICorDebugHeapValue](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-241">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-242">Подкласс интерфейса `ICorDebugValue`, представляющий объект, подобранный сборщиком мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-242">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="e5a2c-243">[Интерфейс ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-243">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-244">Расширение интерфейса `ICorDebugHeapValue`, предоставляющее поддержку дескрипторов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-244">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="e5a2c-245">[Интерфейс ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-245">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-246">Предоставляет свойства блокировки монитора объектов.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-246">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="e5a2c-247">[Интерфейс Икордебугилкоде](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-247">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-248">Представляет сегмент кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-248">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="e5a2c-249">[Интерфейс ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-249">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-250">Логически расширяет интерфейс [икордебугилкоде](icordebugilcode-interface.md) , чтобы предоставить методы, которые возвращают маркер для сигнатуры локальной переменной функции и сопоставляют смещенные промежуточные языки (IL) профилировщика с исходными смещениями Il метода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-250">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="e5a2c-251">[Интерфейс ICorDebugILFrame](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-251">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-252">Предоставляет кадр стека кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-252">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="e5a2c-253">[Интерфейс ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-253">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-254">Логическое расширение интерфейса `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-254">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="e5a2c-255">[Интерфейс ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-255">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-256">Предоставляет метод, инкапсулирующий возвращаемое значение функции.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-256">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="e5a2c-257">[Интерфейс ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-257">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-258">Предоставляет методы, обеспечивающие доступ к локальным переменным и коду в кадре стека кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-258">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="e5a2c-259">Параметр показывает, имеет ли отладчик доступ к переменным и коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-259">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="e5a2c-260">[Интерфейс ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-260">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-261">Представляет сведения отладочного символа для поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-261">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="e5a2c-262">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-262">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-263">[Интерфейс ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-263">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-264">Задает типы кадров для отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-264">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="e5a2c-265">[Интерфейс ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-265">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-266">Предоставляет сведения о внутренних кадрах, включая адрес стека и расположение по отношению к объектам [ICorDebugFrame](icordebugframe-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-266">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="e5a2c-267">[Интерфейс Икордебуглоадедмодуле](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-267">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-268">Предоставляет сведения о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-268">Provides information about a loaded module.</span></span> <span data-ttu-id="e5a2c-269">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-269">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-270">[Интерфейс ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-270">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-271">Предоставляет методы для обработки обратных вызовов отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-271">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="e5a2c-272">[Интерфейс ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-272">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-273">Предоставляет методы для поддержки обработки исключений отладчика и управляемых помощников по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-273">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="e5a2c-274">Интерфейс `ICorDebugManagedCallback2` является логическим расширением интерфейса `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-274">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="e5a2c-275">[Интерфейс ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-275">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-276">Предоставляет метод обратного вызова, указывающий, что создано включенное пользовательское уведомление отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-276">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="e5a2c-277">[Интерфейс ICorDebugMDA](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-277">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-278">Представляет сообщение управляемого помощника по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-278">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="e5a2c-279">[Интерфейс Икордебугмеморибуффер](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-279">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-280">Представляет буфер в памяти.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-280">Represents an in-memory buffer.</span></span> <span data-ttu-id="e5a2c-281">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-281">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-282">[Интерфейс Икордебугмержедассемблирекорд](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-282">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-283">Предоставляет сведения о сборке после слияния.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-283">Provides information about a merged assembly.</span></span> <span data-ttu-id="e5a2c-284">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-284">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-285">[Интерфейс Икордебугметадаталокатор](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-285">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-286">Предоставляет сведения о метаданных для отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-286">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="e5a2c-287">[Интерфейс ICorDebugModule](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-287">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-288">Представляет модуль среды CLR, который является либо исполняемым файлом, либо библиотекой динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-288">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="e5a2c-289">[Интерфейс ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-289">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-290">Служит логическим расширением интерфейса `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-290">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="e5a2c-291">[Интерфейс метод icordebugmodule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-291">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-292">Создает средство чтения символов для динамического модуля.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-292">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="e5a2c-293">[Интерфейс Икордебугмодулебреакпоинт](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-293">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-294">Расширяет интерфейс `ICorDebugBreakpoint` для предоставления доступа к указанным модулям.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-294">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="e5a2c-295">[Интерфейс Икордебугмодуледебужевент](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-295">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-296">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий уровня модуля.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-296">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="e5a2c-297">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-297">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-298">[Интерфейс Икордебугмодулинум](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-298">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-299">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-299">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-300">[Интерфейс Икордебугмутабледататаржет](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-300">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-301">Расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) для поддержки целевых объектов данных.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-301">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="e5a2c-302">[Интерфейс ICorDebugNativeFrame](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-302">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-303">Специализированная реализация интерфейса `ICorDebugFrame`, используемая для кадров машинного кода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-303">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="e5a2c-304">[Интерфейс ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-304">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-305">Предоставляет методы, проверяющие для кадров наличие взаимоотношений типа "дочерний-родительский".</span><span class="sxs-lookup"><span data-stu-id="e5a2c-305">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="e5a2c-306">[Интерфейс Икордебугобжектенум](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-306">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-307">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов объектов по их относительным виртуальным адресам (RVA).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-307">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="e5a2c-308">[Интерфейс ICorDebugObjectValue](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-308">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-309">Подкласс `ICorDebugValue`, представляющий значение, содержащее объект.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-309">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="e5a2c-310">[Интерфейс ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-310">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-311">Расширяет интерфейс `ICorDebugObjectValue` для поддержки наследования и переопределений.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-311">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="e5a2c-312">[Интерфейс ICorDebugProcess](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-312">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-313">Представляет процесс, выполняющий управляемый код.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-313">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="e5a2c-314">[Интерфейс ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-314">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-315">Логическое расширение интерфейса `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-315">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="e5a2c-316">[Интерфейс ICorDebugProcess3](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-316">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-317">Управляет пользовательскими уведомлениями отладчика.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-317">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="e5a2c-318">[Интерфейс ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-318">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-319">Обеспечивает поддержку управления выполнением в процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-319">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="e5a2c-320">[Интерфейс метод ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-320">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-321">Расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) для поддержки доступа к управляемой куче, предоставляет сведения о сборке мусора управляемых объектов и определяет, загружает ли отладчик изображения из локального кэша образов в машинном код.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-321">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="e5a2c-322">[Интерфейс ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-322">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-323">Логически расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) , позволяя выполнять такие функции, как декодирование управляемых событий отладки, которые кодируются в событиях отладки машинного кода и разбиении виртуального модуля.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-323">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="e5a2c-324">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-324">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-325">[Интерфейс ICorDebugProcess7](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-325">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-326">Предоставляет метод, который настраивает отладчик для обработки обновлений находящихся в памяти метаданных в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-326">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="e5a2c-327">[Интерфейс ICorDebugProcess8](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-327">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-328">Логически расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) , чтобы включать или отключать определенные типы обратных вызовов исключений [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-328">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="e5a2c-329">[Интерфейс Икордебугпроцессенум](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-329">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-330">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-330">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-331">[Интерфейс ICorDebugReferenceValue](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-331">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-332">Подкласс интерфейса `ICorDebugValue`, поддерживающего ссылочные типы.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-332">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="e5a2c-333">[Интерфейс ICorDebugRegisterSet](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-333">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-334">Представляет набор регистров, доступных для компьютера, на котором в данный момент выполняется код.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-334">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="e5a2c-335">[Интерфейс ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-335">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-336">Расширяет возможности интерфейса `ICorDebugRegisterSet` для аппаратных платформ, количество регистров которых превышает 64.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-336">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="e5a2c-337">[Интерфейс метод icordebugremote](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-337">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-338">Позволяет запускать или подключать управляемый отладчик к удаленному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-338">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="e5a2c-339">[Интерфейс ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-339">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-340">Предоставляет методы, позволяющие отлаживать приложения на основе Silverlight в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-340">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="e5a2c-341">[Интерфейс Икордебугрунтимеунвиндаблефраме](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-341">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-342">Предоставляет поддержку для неуправляемых методов, которым требуется среда CLR для раскручивания кадра.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-342">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="e5a2c-343">[Интерфейс Икордебугстакквалк](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-343">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-344">Обеспечивает методы для получения управляемых методов или кадров в стеке потока.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-344">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="e5a2c-345">[Интерфейс Икордебугстатикфиелдсимбол](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-345">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-346">Представляет сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-346">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="e5a2c-347">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-347">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-348">[Интерфейс ICorDebugStepper](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-348">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-349">Представляет предпринимаемый отладчиком шаг при выполнении кода, служащий идентификатором на промежутке между подачей команды и ее завершением, а также предоставляет возможность отмены шага.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-349">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="e5a2c-350">[Интерфейс ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-350">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-351">Предоставляет поддержку отладки "Только мой код".</span><span class="sxs-lookup"><span data-stu-id="e5a2c-351">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="e5a2c-352">[Интерфейс Икордебугстепперенум](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-352">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-353">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-353">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-354">[Интерфейс ICorDebugStringValue](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-354">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-355">Подкласс `ICorDebugHeapValue`, применяемый к строковым значениям.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-355">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="e5a2c-356">[Интерфейс метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-356">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-357">Предоставляет методы, которые могут использоваться для получения сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-357">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="e5a2c-358">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-358">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-359">[Интерфейс ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-359">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-360">Логически расширяет интерфейс [метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md) для получения дополнительных сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-360">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="e5a2c-361">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-361">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-362">[Интерфейс ICorDebugThread](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-362">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-363">Представляет поток в процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-363">Represents a thread in a process.</span></span> <span data-ttu-id="e5a2c-364">Время существования экземпляра `ICorDebugThread` равно времени существования потока, который он представляет.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-364">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="e5a2c-365">[Интерфейс ICorDebugThread2](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-365">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-366">Служит логическим расширением интерфейса `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-366">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="e5a2c-367">[Интерфейс ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-367">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-368">Предоставляет точку входа для [икордебугстакквалк](icordebugstackwalk-interface.md) и соответствующих интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-368">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="e5a2c-369">[Интерфейс ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-369">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-370">Предоставляет сведения о блокировке потока.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-370">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="e5a2c-371">[Интерфейс Икордебугсреаденум](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-371">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="e5a2c-372">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-372">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-373">[Интерфейс ICorDebugType](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-373">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-374">Представляет тип, который может быть базовым или сложным (иными словами, пользовательским).</span><span class="sxs-lookup"><span data-stu-id="e5a2c-374">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e5a2c-375">Если тип универсален, интерфейс `ICorDebugType` представляет универсальный тип с экземплярами.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-375">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="e5a2c-376">[Интерфейс ICorDebugType2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-376">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-377">Расширяет интерфейс [ICorDebugType](icordebugtype-interface.md) для получения идентификатора типа базового типа или сложного (определяемого пользователем) типа.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-377">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="e5a2c-378">[Интерфейс ICorDebugTypeEnum](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-378">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-379">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-379">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-380">[Интерфейс Икордебугунманажедкаллбакк](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-380">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-381">Предоставляет уведомление о событиях машинного кода, которые не связаны непосредственно со средой CLR.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-381">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="e5a2c-382">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-382">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-383">Представляет значение для записи или чтения в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-383">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="e5a2c-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-385">Расширяет интерфейс `ICorDebugValue` для предоставления поддержки интерфейса `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-385">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="e5a2c-386">[Интерфейс ICorDebugValue3](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-386">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-387">Расширяет интерфейсы "ICorDebugValue" и "ICorDebugValue2", чтобы обеспечить поддержку массивов, размер которых превышает 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-387">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="e5a2c-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-389">Расширяет интерфейс `ICorDebugBreakpoint` для обеспечения доступа к указанным значениям.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-389">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="e5a2c-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-391">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-391">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="e5a2c-392">[Интерфейс ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-392">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-393">Представляет локальную переменную или аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-393">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="e5a2c-394">[Интерфейс ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-394">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-395">Предоставляет перечислитель для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-395">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="e5a2c-396">[Интерфейс ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-396">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-397">Извлекает сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-397">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="e5a2c-398">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-398">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-399">[Интерфейс ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-399">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-400">Предоставляет методы, помогающие очистить стек.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-400">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="e5a2c-401">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-401">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="e5a2c-402">[Интерфейс ICorPublish](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-402">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-403">Служит универсальным интерфейсом для процессов публикации.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-403">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="e5a2c-404">[Интерфейс ICorPublishAppDomain](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-404">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-405">Представляет и предоставляет информацию о домене приложения.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-405">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="e5a2c-406">[Интерфейс ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-406">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-407">Предоставляет методы, выполняющие перебор коллекции объектов `ICorPublishAppDomain`, существующих в процессе в данный момент.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-407">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="e5a2c-408">[Интерфейс ICorPublishEnum](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-408">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-409">Служит абстрактной базой для перечислителей публикации.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-409">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="e5a2c-410">[Интерфейс ICorPublishProcess](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-410">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-411">Предоставляет методы, позволяющие получить доступ к сведениям о процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-411">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="e5a2c-412">[Интерфейс ICorPublishProcessEnum](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-412">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-413">Предоставляет методы, выполняющие перебор коллекции объектов `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-413">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="e5a2c-414">[Интерфейс ИсосдаЦинтерфаце](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-414">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-415">Предоставляет вспомогательные методы для доступа к данным из `SOS` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-415">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="e5a2c-416">[Интерфейс Иксклрдатамесоддефинитион](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-416">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-417">Предоставляет методы для запроса сведений об определении метода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-417">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="e5a2c-418">[Интерфейс Иксклрдатамесодинстанце](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-418">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-419">Предоставляет методы для запроса сведений об экземпляре метода.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-419">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="e5a2c-420">[Интерфейс Иксклрдатамодуле](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-420">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-421">Предоставляет методы для запроса сведений о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-421">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="e5a2c-422">[Интерфейс Иксклрдатапроцесс](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-422">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="e5a2c-423">Предоставляет методы для запроса сведений о процессе.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-423">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="e5a2c-424">См. также</span><span class="sxs-lookup"><span data-stu-id="e5a2c-424">Related Sections</span></span>  

 <span data-ttu-id="e5a2c-425">[Коклассы отладки](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-425">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="e5a2c-426">[Отладка глобальных статических функций](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-426">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="e5a2c-427">[Перечисления отладки](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-427">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="e5a2c-428">[Структуры отладки](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="e5a2c-428">[Debugging Structures](debugging-structures.md)</span></span>\
