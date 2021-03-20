---
description: Дополнительные сведения о функции FunctionTailcall3
title: Функция FunctionTailcall3
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 4a67f218f0815ce6aff6ec4eda3d26ee2bf1fc3c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759460"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="37fc0-103">Функция FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="37fc0-103">FunctionTailcall3 Function</span></span>

<span data-ttu-id="37fc0-104">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="37fc0-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fc0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37fc0-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37fc0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="37fc0-106">Parameters</span></span>

<span data-ttu-id="37fc0-107">`functionOrRemappedID` окне Идентификатор выполняемой в данный момент функции, которая собирается выполнить вызов с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="37fc0-107">`functionOrRemappedID` [in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="37fc0-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="37fc0-108">Remarks</span></span>  

 <span data-ttu-id="37fc0-109">`FunctionTailcall3`Функция обратного вызова уведомляет профилировщик о вызове функций.</span><span class="sxs-lookup"><span data-stu-id="37fc0-109">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="37fc0-110">Чтобы зарегистрировать реализацию этой функции, используйте [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37fc0-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="37fc0-111">`FunctionTailcall3`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="37fc0-111">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="37fc0-112">Реализация должна использовать `__declspec(naked)` атрибут класса хранения.</span><span class="sxs-lookup"><span data-stu-id="37fc0-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="37fc0-113">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="37fc0-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="37fc0-114">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="37fc0-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="37fc0-115">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="37fc0-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="37fc0-116">Реализация `FunctionTailcall3` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="37fc0-116">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="37fc0-117">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="37fc0-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="37fc0-118">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionTailcall3` вернет.</span><span class="sxs-lookup"><span data-stu-id="37fc0-118">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="37fc0-119">`FunctionTailcall3`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="37fc0-119">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fc0-120">Требования</span><span class="sxs-lookup"><span data-stu-id="37fc0-120">Requirements</span></span>  

 <span data-ttu-id="37fc0-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fc0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fc0-122">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="37fc0-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="37fc0-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37fc0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37fc0-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fc0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fc0-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="37fc0-125">See also</span></span>

- [<span data-ttu-id="37fc0-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="37fc0-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="37fc0-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="37fc0-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="37fc0-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="37fc0-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="37fc0-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="37fc0-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="37fc0-130">Функция FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="37fc0-130">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="37fc0-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="37fc0-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="37fc0-132">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="37fc0-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="37fc0-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="37fc0-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="37fc0-134">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="37fc0-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="37fc0-135">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="37fc0-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
