---
description: Дополнительные сведения о перечислении CorDebugInterfaceVersion
title: Перечисление CorDebugInterfaceVersion
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: 35b8fd6eae2b7999d7669632506cfea43dffbd45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801648"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="79ffd-103">Перечисление CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="79ffd-103">CorDebugInterfaceVersion Enumeration</span></span>

<span data-ttu-id="79ffd-104">Указывает интерфейс, версию платформы .NET Framework или версию платформы .NET Framework, в которой был представлен интерфейс.</span><span class="sxs-lookup"><span data-stu-id="79ffd-104">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ffd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79ffd-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="79ffd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="79ffd-106">Members</span></span>  

 <span data-ttu-id="79ffd-107">В следующей таблице каждое значение перечисления сопоставляется с соответствующим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="79ffd-107">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="79ffd-108">Кроме того, в таблице указана первая версия платформы .NET Framework, в которой поддерживался интерфейс.</span><span class="sxs-lookup"><span data-stu-id="79ffd-108">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="79ffd-109">Член</span><span class="sxs-lookup"><span data-stu-id="79ffd-109">Member</span></span>|<span data-ttu-id="79ffd-110">Что определяет</span><span class="sxs-lookup"><span data-stu-id="79ffd-110">Specifies</span></span>|<span data-ttu-id="79ffd-111">Версия платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="79ffd-111">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="79ffd-112">Недопустимая версия платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79ffd-112">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="79ffd-113">Версия платформы .NET Framework (включая все пакеты обновления) — 1.0.</span><span class="sxs-lookup"><span data-stu-id="79ffd-113">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="79ffd-114">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-114">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="79ffd-115">Версия платформы .NET Framework (включая все пакеты обновления) — 1.1.</span><span class="sxs-lookup"><span data-stu-id="79ffd-115">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="79ffd-116">1,1</span><span class="sxs-lookup"><span data-stu-id="79ffd-116">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="79ffd-117">Версия платформы .NET Framework (включая все пакеты обновления) — 2.0.</span><span class="sxs-lookup"><span data-stu-id="79ffd-117">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="79ffd-118">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-118">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="79ffd-119">Версия платформы .NET Framework (включая все пакеты обновления) — 4.</span><span class="sxs-lookup"><span data-stu-id="79ffd-119">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="79ffd-120">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-120">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="79ffd-121">Версия платформы .NET Framework (включая все пакеты обновления) — 4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-121">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="79ffd-122">4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-122">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="79ffd-123">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="79ffd-123">ICorDebugManagedCallback</span></span>](icordebugmanagedcallback-interface.md)|<span data-ttu-id="79ffd-124">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-124">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="79ffd-125">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="79ffd-125">ICorDebugUnmanagedCallback</span></span>](icordebugunmanagedcallback-interface.md)|<span data-ttu-id="79ffd-126">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-126">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="79ffd-127">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="79ffd-127">ICorDebug</span></span>](icordebug-interface.md)|<span data-ttu-id="79ffd-128">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-128">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="79ffd-129">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="79ffd-129">ICorDebugController</span></span>](icordebugcontroller-interface.md)|<span data-ttu-id="79ffd-130">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-130">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="79ffd-131">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="79ffd-131">ICorDebugAppDomain</span></span>](icordebugappdomain-interface.md)|<span data-ttu-id="79ffd-132">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-132">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="79ffd-133">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="79ffd-133">ICorDebugAssembly</span></span>](icordebugassembly-interface.md)|<span data-ttu-id="79ffd-134">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-134">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="79ffd-135">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="79ffd-135">ICorDebugProcess</span></span>](icordebugprocess-interface.md)|<span data-ttu-id="79ffd-136">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-136">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="79ffd-137">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="79ffd-137">ICorDebugBreakpoint</span></span>](icordebugbreakpoint-interface.md)|<span data-ttu-id="79ffd-138">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-138">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="79ffd-139">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="79ffd-139">ICorDebugFunctionBreakpoint</span></span>](icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="79ffd-140">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-140">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="79ffd-141">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="79ffd-141">ICorDebugModuleBreakpoint</span></span>](icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="79ffd-142">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-142">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="79ffd-143">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="79ffd-143">ICorDebugValueBreakpoint</span></span>](icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="79ffd-144">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-144">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="79ffd-145">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="79ffd-145">ICorDebugStepper</span></span>](icordebugstepper-interface.md)|<span data-ttu-id="79ffd-146">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-146">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="79ffd-147">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="79ffd-147">ICorDebugRegisterSet</span></span>](icordebugregisterset-interface.md)|<span data-ttu-id="79ffd-148">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-148">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="79ffd-149">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="79ffd-149">ICorDebugThread</span></span>](icordebugthread-interface.md)|<span data-ttu-id="79ffd-150">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-150">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="79ffd-151">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="79ffd-151">ICorDebugChain</span></span>](icordebugchain-interface.md)|<span data-ttu-id="79ffd-152">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-152">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="79ffd-153">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="79ffd-153">ICorDebugFrame</span></span>](icordebugframe-interface.md)|<span data-ttu-id="79ffd-154">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-154">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="79ffd-155">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="79ffd-155">ICorDebugILFrame</span></span>](icordebugilframe-interface.md)|<span data-ttu-id="79ffd-156">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-156">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="79ffd-157">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="79ffd-157">ICorDebugNativeFrame</span></span>](icordebugnativeframe-interface.md)|<span data-ttu-id="79ffd-158">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-158">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="79ffd-159">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="79ffd-159">ICorDebugModule</span></span>](icordebugmodule-interface.md)|<span data-ttu-id="79ffd-160">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-160">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="79ffd-161">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="79ffd-161">ICorDebugFunction</span></span>](icordebugfunction-interface1.md)|<span data-ttu-id="79ffd-162">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-162">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="79ffd-163">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="79ffd-163">ICorDebugCode</span></span>](icordebugcode-interface1.md)|<span data-ttu-id="79ffd-164">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-164">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="79ffd-165">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="79ffd-165">ICorDebugClass</span></span>](icordebugclass-interface.md)|<span data-ttu-id="79ffd-166">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-166">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="79ffd-167">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="79ffd-167">ICorDebugEval</span></span>](icordebugeval-interface.md)|<span data-ttu-id="79ffd-168">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-168">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="79ffd-169">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-169">ICorDebugValue</span></span>](icordebugvalue-interface.md)|<span data-ttu-id="79ffd-170">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-170">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="79ffd-171">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-171">ICorDebugGenericValue</span></span>](icordebuggenericvalue-interface.md)|<span data-ttu-id="79ffd-172">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-172">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="79ffd-173">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-173">ICorDebugReferenceValue</span></span>](icordebugreferencevalue-interface.md)|<span data-ttu-id="79ffd-174">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-174">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="79ffd-175">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-175">ICorDebugHeapValue</span></span>](icordebugheapvalue-interface.md)|<span data-ttu-id="79ffd-176">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-176">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="79ffd-177">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-177">ICorDebugObjectValue</span></span>](icordebugobjectvalue-interface.md)|<span data-ttu-id="79ffd-178">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-178">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="79ffd-179">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-179">ICorDebugBoxValue</span></span>](icordebugboxvalue-interface.md)|<span data-ttu-id="79ffd-180">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-180">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="79ffd-181">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-181">ICorDebugStringValue</span></span>](icordebugstringvalue-interface.md)|<span data-ttu-id="79ffd-182">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-182">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="79ffd-183">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-183">ICorDebugArrayValue</span></span>](icordebugarrayvalue-interface.md)|<span data-ttu-id="79ffd-184">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-184">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="79ffd-185">ICorDebugContext</span><span class="sxs-lookup"><span data-stu-id="79ffd-185">ICorDebugContext</span></span>](icordebugcontext-interface.md)|<span data-ttu-id="79ffd-186">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-186">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="79ffd-187">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-187">ICorDebugEnum</span></span>](icordebugenum-interface1.md)|<span data-ttu-id="79ffd-188">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-188">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="79ffd-189">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-189">ICorDebugObjectEnum</span></span>](icordebugobjectenum-interface.md)|<span data-ttu-id="79ffd-190">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-190">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="79ffd-191">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-191">ICorDebugBreakpointEnum</span></span>](icordebugbreakpointenum-interface.md)|<span data-ttu-id="79ffd-192">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-192">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="79ffd-193">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-193">ICorDebugStepperEnum</span></span>](icordebugstepperenum-interface.md)|<span data-ttu-id="79ffd-194">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-194">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="79ffd-195">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-195">ICorDebugProcessEnum</span></span>](icordebugprocessenum-interface.md)|<span data-ttu-id="79ffd-196">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-196">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="79ffd-197">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-197">ICorDebugThreadEnum</span></span>](icordebugthreadenum-interface1.md)|<span data-ttu-id="79ffd-198">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-198">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="79ffd-199">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-199">ICorDebugFrameEnum</span></span>](icordebugframeenum-interface.md)|<span data-ttu-id="79ffd-200">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-200">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="79ffd-201">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-201">ICorDebugChainEnum</span></span>](icordebugchainenum-interface.md)|<span data-ttu-id="79ffd-202">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-202">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="79ffd-203">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-203">ICorDebugModuleEnum</span></span>](icordebugmoduleenum-interface.md)|<span data-ttu-id="79ffd-204">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-204">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="79ffd-205">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-205">ICorDebugValueEnum</span></span>](icordebugvalueenum-interface.md)|<span data-ttu-id="79ffd-206">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-206">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="79ffd-207">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-207">ICorDebugCodeEnum</span></span>](icordebugcodeenum-interface.md)|<span data-ttu-id="79ffd-208">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-208">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="79ffd-209">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-209">ICorDebugTypeEnum</span></span>](icordebugtypeenum-interface.md)|<span data-ttu-id="79ffd-210">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-210">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="79ffd-211">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-211">ICorDebugErrorInfoEnum</span></span>](icordebugerrorinfoenum-interface.md)|<span data-ttu-id="79ffd-212">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-212">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="79ffd-213">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-213">ICorDebugAppDomainEnum</span></span>](icordebugappdomainenum-interface.md)|<span data-ttu-id="79ffd-214">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-214">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="79ffd-215">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-215">ICorDebugAssemblyEnum</span></span>](icordebugassemblyenum-interface.md)|<span data-ttu-id="79ffd-216">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-216">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="79ffd-217">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="79ffd-217">ICorDebugEditAndContinueErrorInfo</span></span>](icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="79ffd-218">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-218">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="79ffd-219">Метод icordebugeditandcontinuesnapshot</span><span class="sxs-lookup"><span data-stu-id="79ffd-219">ICorDebugEditAndContinueSnapshot</span></span>](icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="79ffd-220">1.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-220">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="79ffd-221">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="79ffd-221">ICorDebugManagedCallback2</span></span>](icordebugmanagedcallback2-interface.md)|<span data-ttu-id="79ffd-222">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-222">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="79ffd-223">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="79ffd-223">ICorDebugAppDomain2</span></span>](icordebugappdomain2-interface.md)|<span data-ttu-id="79ffd-224">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-224">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="79ffd-225">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="79ffd-225">ICorDebugProcess2</span></span>](icordebugprocess2-interface1.md)|<span data-ttu-id="79ffd-226">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-226">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="79ffd-227">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="79ffd-227">ICorDebugStepper2</span></span>](icordebugstepper2-interface1.md)|<span data-ttu-id="79ffd-228">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-228">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="79ffd-229">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="79ffd-229">ICorDebugRegisterSet2</span></span>](icordebugregisterset2-interface.md)|<span data-ttu-id="79ffd-230">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-230">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="79ffd-231">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="79ffd-231">ICorDebugThread2</span></span>](icordebugthread2-interface.md)|<span data-ttu-id="79ffd-232">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-232">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="79ffd-233">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="79ffd-233">ICorDebugILFrame2</span></span>](icordebugilframe2-interface.md)|<span data-ttu-id="79ffd-234">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-234">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="79ffd-235">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="79ffd-235">ICorDebugModule2</span></span>](icordebugmodule2-interface.md)|<span data-ttu-id="79ffd-236">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-236">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="79ffd-237">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="79ffd-237">ICorDebugFunction2</span></span>](icordebugfunction2-interface.md)|<span data-ttu-id="79ffd-238">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-238">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="79ffd-239">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="79ffd-239">ICorDebugCode2</span></span>](icordebugcode2-interface.md)|<span data-ttu-id="79ffd-240">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-240">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="79ffd-241">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="79ffd-241">"ICorDebugClass2"</span></span>|<span data-ttu-id="79ffd-242">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-242">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="79ffd-243">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="79ffd-243">"ICorDebugValue2"</span></span>|<span data-ttu-id="79ffd-244">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-244">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="79ffd-245">"ICorDebugEval2".</span><span class="sxs-lookup"><span data-stu-id="79ffd-245">The "ICorDebugEval2".</span></span>|<span data-ttu-id="79ffd-246">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-246">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="79ffd-247">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="79ffd-247">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="79ffd-248">2.0</span><span class="sxs-lookup"><span data-stu-id="79ffd-248">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="79ffd-249">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="79ffd-249">ICorDebugThread3</span></span>](icordebugthread3-interface.md)|<span data-ttu-id="79ffd-250">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-250">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="79ffd-251">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="79ffd-251">ICorDebugThread4</span></span>](icordebugthread4-interface.md)|<span data-ttu-id="79ffd-252">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-252">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="79ffd-253">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="79ffd-253">ICorDebugStackWalk</span></span>](icordebugstackwalk-interface.md)|<span data-ttu-id="79ffd-254">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-254">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="79ffd-255">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="79ffd-255">ICorDebugNativeFrame2</span></span>](icordebugnativeframe2-interface.md)|<span data-ttu-id="79ffd-256">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-256">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="79ffd-257">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="79ffd-257">ICorDebugInternalFrame2</span></span>](icordebuginternalframe2-interface.md)|<span data-ttu-id="79ffd-258">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-258">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="79ffd-259">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="79ffd-259">ICorDebugRuntimeUnwindableFrame</span></span>](icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="79ffd-260">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-260">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="79ffd-261">Интерфейс ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="79ffd-261">ICorDebugHeapValue3 Interface</span></span>](icordebugheapvalue3-interface.md)|<span data-ttu-id="79ffd-262">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-262">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="79ffd-263">Интерфейс ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="79ffd-263">ICorDebugBlockingObjectEnum Interface</span></span>](icordebugblockingobjectenum-interface.md)|<span data-ttu-id="79ffd-264">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-264">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="79ffd-265">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="79ffd-265">ICorDebugValue3</span></span>](icordebugvalue3-interface.md)|<span data-ttu-id="79ffd-266">4</span><span class="sxs-lookup"><span data-stu-id="79ffd-266">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="79ffd-267">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="79ffd-267">ICorDebugComObjectValue</span></span>](icordebugcomobjectvalue-interface.md)|<span data-ttu-id="79ffd-268">4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-268">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="79ffd-269">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="79ffd-269">ICorDebugAppDomain3</span></span>](icordebugappdomain3-interface.md)|<span data-ttu-id="79ffd-270">4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-270">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="79ffd-271">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="79ffd-271">ICorDebugCode3</span></span>](icordebugcode3-interface.md)|<span data-ttu-id="79ffd-272">4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-272">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="79ffd-273">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="79ffd-273">ICorDebugILFrame3</span></span>](icordebugilframe3-interface.md)|<span data-ttu-id="79ffd-274">4.5.</span><span class="sxs-lookup"><span data-stu-id="79ffd-274">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="79ffd-275">Версия платформы .NET Framework (включая все пакеты обновления) — самая последняя.</span><span class="sxs-lookup"><span data-stu-id="79ffd-275">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="79ffd-276">Remarks</span><span class="sxs-lookup"><span data-stu-id="79ffd-276">Remarks</span></span>  

 <span data-ttu-id="79ffd-277">Отладчик может использовать `CorDebugInterfaceVersion` перечисление в функции [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) для указания самой высокой версии платформа .NET Framework, поддерживаемой отладчиком.</span><span class="sxs-lookup"><span data-stu-id="79ffd-277">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="79ffd-278">Имена интерфейсов</span><span class="sxs-lookup"><span data-stu-id="79ffd-278">Interface Names</span></span>  

 <span data-ttu-id="79ffd-279">Число в конце каждого имени интерфейсов в API отладки (например, "3" в `ICorDebugThread3`) обозначает версию интерфейса, а не платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79ffd-279">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="79ffd-280">Все имена интерфейсов в API отладки, кроме интерфейсов, появившихся в платформе .NET Framework версии 1, включают номера версий.</span><span class="sxs-lookup"><span data-stu-id="79ffd-280">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="79ffd-281">Любые совпадения между номерами версий интерфейсов и номерами версий платформы .NET Framework являются случайными.</span><span class="sxs-lookup"><span data-stu-id="79ffd-281">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="79ffd-282">Интерфейсы, представленные в платформе .NET Framework версии 1.0, не включают цифры, потому что все они имеют версию 1.</span><span class="sxs-lookup"><span data-stu-id="79ffd-282">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="79ffd-283">Платформа .NET Framework версии 1.1 использует интерфейсы версии 1.0 и не вводит никаких новых интерфейсов отладки.</span><span class="sxs-lookup"><span data-stu-id="79ffd-283">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="79ffd-284">Четырнадцать интерфейсов отладки, представленных в платформе .NET Framework версии 2.0, являются логическими расширениями версии 1, а их названия содержат число "2".</span><span class="sxs-lookup"><span data-stu-id="79ffd-284">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="79ffd-285">Платформы .NET Framework версий 3.0 и 3.5 используют существующие интерфейсы платформы .NET Framework версии 2.0 и не вводят никаких новых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="79ffd-285">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="79ffd-286">В платформа .NET Framework 4 введены разные версии интерфейса.</span><span class="sxs-lookup"><span data-stu-id="79ffd-286">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="79ffd-287">Например, и `ICorDebugThread3`, и `ICorDebugThread4` отображаются как третья и четвертая версии интерфейса `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="79ffd-287">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="79ffd-288">В платформа .NET Framework 4 также введена первая версия `ICorDebugStackWalk` интерфейса и вторая версия `ICorDebugNativeFrame` интерфейса ( `ICorDebugNativeFrame2` ).</span><span class="sxs-lookup"><span data-stu-id="79ffd-288">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79ffd-289">Требования</span><span class="sxs-lookup"><span data-stu-id="79ffd-289">Requirements</span></span>  

 <span data-ttu-id="79ffd-290">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79ffd-290">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79ffd-291">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79ffd-291">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79ffd-292">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79ffd-292">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79ffd-293">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79ffd-293">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ffd-294">См. также</span><span class="sxs-lookup"><span data-stu-id="79ffd-294">See also</span></span>

- [<span data-ttu-id="79ffd-295">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="79ffd-295">Debugging Enumerations</span></span>](debugging-enumerations.md)
