---
description: Дополнительные сведения о функции FunctionTailcall2
title: Функция FunctionTailcall2
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: e06c3bde7ad0700de3d7f08b33159032b31eae8a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760071"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="d7fba-103">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="d7fba-103">FunctionTailcall2 Function</span></span>

<span data-ttu-id="d7fba-104">Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail и предоставляет сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="d7fba-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7fba-105">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7fba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7fba-106">Parameters</span></span>

<span data-ttu-id="d7fba-107">`funcId` окне Идентификатор выполняемой в данный момент функции, которая собирается выполнить вызов с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="d7fba-107">`funcId` [in] The identifier of the currently executing function that is about to make a tail call.</span></span>

<span data-ttu-id="d7fba-108">`clientData` окне Идентификатор повторно сопоставленной функции, который ранее был указан с помощью [FunctionIDMapper](functionidmapper-function.md), для выполняемой в данный момент функции, которая собирается выполнить вызов с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="d7fba-108">`clientData` [in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
<span data-ttu-id="d7fba-109">`func` окне `COR_PRF_FRAME_INFO` Значение, указывающее на сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="d7fba-109">`func` [in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

<span data-ttu-id="d7fba-110">Профилировщик должен рассматривать это как непрозрачный маркер, который можно передать обратно в подсистему выполнения метода [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d7fba-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7fba-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7fba-111">Remarks</span></span>  

 <span data-ttu-id="d7fba-112">Целевая функция вызова с префиксом tail будет использовать текущий кадр стека и будет возвращаться непосредственно вызывающему объекту функции, которая выполнила вызов с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="d7fba-112">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="d7fba-113">Это означает, что обратный вызов [FunctionLeave2](functionleave2-function.md) не будет выдаваться для функции, которая является целевым объектом для вызова с префиксом tail.</span><span class="sxs-lookup"><span data-stu-id="d7fba-113">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="d7fba-114">Значение `func` параметра не является допустимым после `FunctionTailcall2` возврата функции, так как оно может измениться или быть уничтожено.</span><span class="sxs-lookup"><span data-stu-id="d7fba-114">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="d7fba-115">`FunctionTailcall2`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="d7fba-115">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="d7fba-116">Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().</span><span class="sxs-lookup"><span data-stu-id="d7fba-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d7fba-117">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="d7fba-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d7fba-118">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="d7fba-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d7fba-119">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="d7fba-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d7fba-120">Реализация `FunctionTailcall2` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="d7fba-120">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d7fba-121">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="d7fba-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d7fba-122">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionTailcall2` вернет.</span><span class="sxs-lookup"><span data-stu-id="d7fba-122">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="d7fba-123">Кроме того, `FunctionTailcall2` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="d7fba-123">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7fba-124">Требования</span><span class="sxs-lookup"><span data-stu-id="d7fba-124">Requirements</span></span>  

 <span data-ttu-id="d7fba-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7fba-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7fba-126">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d7fba-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d7fba-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7fba-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7fba-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7fba-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fba-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d7fba-129">See also</span></span>

- [<span data-ttu-id="d7fba-130">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="d7fba-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d7fba-131">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="d7fba-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="d7fba-132">Метод SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="d7fba-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="d7fba-133">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="d7fba-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
