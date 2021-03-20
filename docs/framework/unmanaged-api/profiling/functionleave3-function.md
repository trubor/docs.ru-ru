---
description: Дополнительные сведения о функции FunctionLeave3
title: Функция FunctionLeave3
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 0409a9969fddbbbcb8fcb5d870acccf1ae3a809b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760110"
---
# <a name="functionleave3-function"></a><span data-ttu-id="e3c1a-103">Функция FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e3c1a-103">FunctionLeave3 Function</span></span>

<span data-ttu-id="e3c1a-104">Уведомляет профилировщик о том, что управление возвращается из функции.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-104">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c1a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3c1a-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c1a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3c1a-106">Parameters</span></span>  

<span data-ttu-id="e3c1a-107">`functionOrRemappedID` окне Идентификатор функции, из которой возвращается элемент управления.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-107">`functionOrRemappedID` [in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e3c1a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3c1a-108">Remarks</span></span>  

 <span data-ttu-id="e3c1a-109">`FunctionLeave3`Функция обратного вызова уведомляет профилировщик о вызове функций, но не поддерживает проверку возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-109">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="e3c1a-110">Чтобы зарегистрировать реализацию этой функции, используйте [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3c1a-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e3c1a-111">`FunctionLeave3`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-111">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="e3c1a-112">Реализация должна использовать `__declspec(naked)` атрибут класса хранения.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="e3c1a-113">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="e3c1a-114">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="e3c1a-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="e3c1a-115">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e3c1a-116">Реализация `FunctionLeave3` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-116">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="e3c1a-117">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e3c1a-118">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave3` вернет.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="e3c1a-119">`FunctionLeave3`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="e3c1a-119">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c1a-120">Требования</span><span class="sxs-lookup"><span data-stu-id="e3c1a-120">Requirements</span></span>  

 <span data-ttu-id="e3c1a-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c1a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c1a-122">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="e3c1a-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e3c1a-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3c1a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3c1a-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c1a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c1a-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e3c1a-125">See also</span></span>

- [<span data-ttu-id="e3c1a-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e3c1a-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="e3c1a-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="e3c1a-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="e3c1a-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e3c1a-128">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="e3c1a-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e3c1a-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="e3c1a-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e3c1a-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="e3c1a-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="e3c1a-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="e3c1a-132">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e3c1a-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="e3c1a-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="e3c1a-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="e3c1a-134">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="e3c1a-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="e3c1a-135">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="e3c1a-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
