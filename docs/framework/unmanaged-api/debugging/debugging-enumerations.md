---
description: 'Дополнительные сведения: Отладка перечислений'
title: Перечисления отладки
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 4a1d2fc9061fec7f5384418e4893c357f5d340ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801427"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="6e863-103">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="6e863-103">Debugging Enumerations</span></span>

<span data-ttu-id="6e863-104">В этом разделе описываются неуправляемые перечисления, которые использует API отладки.</span><span class="sxs-lookup"><span data-stu-id="6e863-104">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e863-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="6e863-105">In This Section</span></span>  

 [<span data-ttu-id="6e863-106">Перечисление CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6e863-106">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="6e863-107">Предоставляет значения, используемые методом [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-107">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="6e863-108">Перечисление CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="6e863-108">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="6e863-109">Указывает, к каким областям памяти должен быть вызван вызов метода [иклрдатаенуммеморирегионс:: енуммеморирегионс](iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-109">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="6e863-110">Перечисление COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="6e863-110">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="6e863-111">Идентифицирует тип процесса для перечисления.</span><span class="sxs-lookup"><span data-stu-id="6e863-111">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="6e863-112">Перечисление CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="6e863-112">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="6e863-113">Указывает возможные причины блокировки потока на данном объекте.</span><span class="sxs-lookup"><span data-stu-id="6e863-113">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="6e863-114">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="6e863-114">CorDebugChainReason</span></span>  
 <span data-ttu-id="6e863-115">Указывает причину или причины запуска цепочки вызовов.</span><span class="sxs-lookup"><span data-stu-id="6e863-115">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="6e863-116">Перечисление CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="6e863-116">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="6e863-117">Описывает, каким образом экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="6e863-117">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="6e863-118">Перечисление CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="6e863-118">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="6e863-119">Описывает, почему экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="6e863-119">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="6e863-120">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="6e863-120">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="6e863-121">Предоставляет дополнительные параметры отладки, которые можно использовать при вызове метода [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-121">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="6e863-122">Перечисление CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="6e863-122">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="6e863-123">Указывает тип события, сведения о котором декодированы методом [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-123">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="6e863-124">Перечисление CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="6e863-124">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="6e863-125">Предоставляет дополнительную информацию о событиях отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="6e863-125">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="6e863-126">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="6e863-126">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="6e863-127">Указывает тип обратного вызова, сделанный из события [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-127">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="6e863-128">Перечисление CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6e863-128">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="6e863-129">Предоставляет дополнительные сведения об исключении.</span><span class="sxs-lookup"><span data-stu-id="6e863-129">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="6e863-130">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="6e863-130">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="6e863-131">Указывает событие, о котором сообщает обратный вызов во время фазы перемотки.</span><span class="sxs-lookup"><span data-stu-id="6e863-131">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="6e863-132">Перечисление CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="6e863-132">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="6e863-133">Указывает, где выполняется сборщик мусора: на рабочей станции или на сервере.</span><span class="sxs-lookup"><span data-stu-id="6e863-133">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="6e863-134">Перечисление CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="6e863-134">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="6e863-135">Указывает на создание области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="6e863-135">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="6e863-136">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="6e863-136">CorDebugHandleType</span></span>  
 <span data-ttu-id="6e863-137">Указывает тип обработки.</span><span class="sxs-lookup"><span data-stu-id="6e863-137">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="6e863-138">Перечисление CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="6e863-138">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="6e863-139">Указывает, соответствует ли определенный диапазон машинных инструкций специальной области кода.</span><span class="sxs-lookup"><span data-stu-id="6e863-139">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="6e863-140">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="6e863-140">CorDebugIntercept</span></span>  
 <span data-ttu-id="6e863-141">Указывает типы кода, который может быть пошагово выполнен.</span><span class="sxs-lookup"><span data-stu-id="6e863-141">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="6e863-142">Перечисление CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="6e863-142">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="6e863-143">Указывает либо версию платформы .NET Framework, либо версию платформы .NET Framework, в которой был представлен интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6e863-143">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="6e863-144">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="6e863-144">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="6e863-145">Указывает тип кадра стека.</span><span class="sxs-lookup"><span data-stu-id="6e863-145">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="6e863-146">Перечисление CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="6e863-146">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="6e863-147">Содержит значения, которые влияют на поведение управляемого JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="6e863-147">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="6e863-148">Перечисление CorDebugJITCompilerFlagsDeprecated</span><span class="sxs-lookup"><span data-stu-id="6e863-148">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="6e863-149">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="6e863-149">Obsolete.</span></span> <span data-ttu-id="6e863-150">`CORDEBUG_JIT_DEFAULT`Вместо этого используйте член перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="6e863-150">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="6e863-151">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="6e863-151">CorDebugMappingResult</span></span>  
 <span data-ttu-id="6e863-152">Предоставляет сведения о том, как было получено значение указателя инструкций.</span><span class="sxs-lookup"><span data-stu-id="6e863-152">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="6e863-153">Перечисление CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="6e863-153">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="6e863-154">Указывает состояние потока, по которому был вызван помощник по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6e863-154">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="6e863-155">Перечисление CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="6e863-155">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="6e863-156">Предоставляет значение, который определяет, загружает ли отладчик образы в машинном коде (NGen) из кэша образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="6e863-156">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="6e863-157">Перечисление CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="6e863-157">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="6e863-158">Предоставляет значения целевой платформы, используемые методом [ICorDebugDataTarget::](icordebugdatatarget-getplatform-method.md) WebMethod.</span><span class="sxs-lookup"><span data-stu-id="6e863-158">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="6e863-159">Перечисление CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="6e863-159">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="6e863-160">Описывает формат данных в массиве байтов, который содержит информацию о событии отладки собственного исключения.</span><span class="sxs-lookup"><span data-stu-id="6e863-160">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="6e863-161">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="6e863-161">CorDebugRegister</span></span>  
 <span data-ttu-id="6e863-162">Указывает регистры, связанные с данной архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="6e863-162">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="6e863-163">Перечисление CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="6e863-163">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="6e863-164">Указывает происхождение контекста: взят из активного (или листового) кадра в стеке или был вычислен в результате освобождения другого кадра.</span><span class="sxs-lookup"><span data-stu-id="6e863-164">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="6e863-165">Перечисление CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="6e863-165">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="6e863-166">Описывает объем кэшированных данных, которые должны быть отброшены на основе изменений, внесенных в процесс.</span><span class="sxs-lookup"><span data-stu-id="6e863-166">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="6e863-167">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="6e863-167">CorDebugStepReason</span></span>  
 <span data-ttu-id="6e863-168">Указывает результат отдельного шага.</span><span class="sxs-lookup"><span data-stu-id="6e863-168">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="6e863-169">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="6e863-169">CorDebugThreadState</span></span>  
 <span data-ttu-id="6e863-170">Указывает состояние потока для отладки.</span><span class="sxs-lookup"><span data-stu-id="6e863-170">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="6e863-171">\>кордебугунмаппедстоп</span><span class="sxs-lookup"><span data-stu-id="6e863-171">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="6e863-172">Указывает тип несопоставимого кода, который может привести к прерыванию выполнения кода пошаговым средством.</span><span class="sxs-lookup"><span data-stu-id="6e863-172">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="6e863-173">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="6e863-173">CorDebugUserState</span></span>  
 <span data-ttu-id="6e863-174">Указывает состояние пользователя потока.</span><span class="sxs-lookup"><span data-stu-id="6e863-174">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="6e863-175">Перечисление CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="6e863-175">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="6e863-176">Идентифицирует источник объекта, в котором должна быть выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="6e863-176">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="6e863-177">Перечисление ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="6e863-177">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="6e863-178">Предоставляет значения, которые указывают, может ли отладчик получить доступ к локальным переменным или коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="6e863-178">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="6e863-179">Перечисление LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="6e863-179">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="6e863-180">Указывает уровень важности описательного сообщения, записанного в журнале событий при регистрации события управляемым потоком.</span><span class="sxs-lookup"><span data-stu-id="6e863-180">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="6e863-181">Перечисление LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="6e863-181">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="6e863-182">Указывает операцию, выполненную на переключателе отладки и трассировки.</span><span class="sxs-lookup"><span data-stu-id="6e863-182">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="6e863-183">Перечисление VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="6e863-183">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="6e863-184">Указывает тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="6e863-184">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="6e863-185">Перечисление WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="6e863-185">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="6e863-186">Предоставляет значения, указывающие, будут ли видны в отладчике обновления копии метаданных в памяти.</span><span class="sxs-lookup"><span data-stu-id="6e863-186">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="6e863-187">[Перечисление клрдатасаурцетипе](clrdatasourcetype-enumeration.md) Предоставляет значения, используемые структурой CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="6e863-187">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6e863-188">См. также</span><span class="sxs-lookup"><span data-stu-id="6e863-188">Related Sections</span></span>  

 [<span data-ttu-id="6e863-189">Компонентные классы отладки</span><span class="sxs-lookup"><span data-stu-id="6e863-189">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="6e863-190">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6e863-190">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="6e863-191">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="6e863-191">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="6e863-192">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="6e863-192">Debugging Structures</span></span>](debugging-structures.md)
