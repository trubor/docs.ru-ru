---
description: 'Дополнительные сведения о методе: Икорпрофилерфунктионконтрол:: SetCodegenFlags'
title: Метод ICorProfilerFunctionControl::SetCodegenFlags
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 61fa8be0993a06a3b2d352af408ac47b7b30e385
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781627"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="d9e7a-103">Метод ICorProfilerFunctionControl::SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="d9e7a-103">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>

<span data-ttu-id="d9e7a-104">Задает один или несколько флагов из перечисления [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) для управления созданием кода для перекомпилированной функции JIT.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-104">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e7a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9e7a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e7a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9e7a-106">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="d9e7a-107">окне Один или несколько флагов из перечисления [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d9e7a-107">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9e7a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9e7a-108">Remarks</span></span>  

 <span data-ttu-id="d9e7a-109">Профилировщик получает экземпляр этого интерфейса через обратный вызов [ICorProfilerCallback4:: жетрежитпараметерс](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9e7a-109">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="d9e7a-110">`SetCodegenFlags` позволяет профилировщику управлять созданием кода для повторно скомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-110">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="d9e7a-111">Как и в случае с другими параметрами повторной компиляции JIT, флаги создания кода применяются ко всем экземплярам функции.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-111">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="d9e7a-112">JIT-компилятор рассматривает эти флаги компиляции вместе с другими флагами, заданными другими источниками, при компиляции функции.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-112">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="d9e7a-113">Другие источники включают отладчик, глобальные флаги, заданные профилировщиком при запуске, с помощью метода [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (со значениями `COR_PRF_DISABLE_INLINING` и `COR_PRF_DISABLE_OPTIMIZATIONS` ) и обратного вызова [ICorProfilerCallback:: житинлининг](icorprofilercallback-jitinlining-method.md) профилировщика.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-113">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="d9e7a-114">JIT-компилятор обеспечивает приоритет к источнику, который запрашивает наименьший уровень оптимизации.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-114">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="d9e7a-115">Например, если профилировщик указывает при `COR_PRF_DISABLE_INLINING` запуске, но не указан `COR_PRF_CODEGEN_DISABLE_INLINING` в обратном вызове [Икорпрофилерфунктионконтрол:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) , встраивание по-прежнему отключено.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-115">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="d9e7a-116">Аналогично, если профилировщик не указывает `COR_PRF_CODEGEN_DISABLE_INLINING` в `SetCodegenFlags` , а затем отключает встраивание с помощью обратного вызова [ICorProfilerCallback:: житинлининг](icorprofilercallback-jitinlining-method.md) , встраивание отключено.</span><span class="sxs-lookup"><span data-stu-id="d9e7a-116">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e7a-117">Требования</span><span class="sxs-lookup"><span data-stu-id="d9e7a-117">Requirements</span></span>  

 <span data-ttu-id="d9e7a-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e7a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e7a-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9e7a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9e7a-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9e7a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9e7a-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e7a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e7a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="d9e7a-122">See also</span></span>

- [<span data-ttu-id="d9e7a-123">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="d9e7a-123">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
