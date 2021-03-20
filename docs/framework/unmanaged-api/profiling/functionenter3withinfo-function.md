---
description: Дополнительные сведения о функции FunctionEnter3WithInfo
title: Функция FunctionEnter3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 9bcebba724f7ebb405bb3d404f028e3ebca3e0d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759316"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="60e7c-103">Функция FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="60e7c-103">FunctionEnter3WithInfo Function</span></span>

<span data-ttu-id="60e7c-104">Уведомляет профилировщик о передаче управления в функцию и предоставляет маркер, который может быть передан [методу ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) для получения кадра стека и аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="60e7c-104">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e7c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60e7c-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60e7c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60e7c-106">Parameters</span></span>

<span data-ttu-id="60e7c-107">`functionIDOrClientID` окне Идентификатор функции, которой передается элемент управления.</span><span class="sxs-lookup"><span data-stu-id="60e7c-107">`functionIDOrClientID` [in] The identifier of the function to which control is passed.</span></span>

<span data-ttu-id="60e7c-108">`eltInfo` окне Непрозрачный маркер, представляющий сведения об заданном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="60e7c-108">`eltInfo` [in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="60e7c-109">Этот маркер действителен только во время обратного вызова, к которому он передается.</span><span class="sxs-lookup"><span data-stu-id="60e7c-109">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="60e7c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="60e7c-110">Remarks</span></span>  

 <span data-ttu-id="60e7c-111">`FunctionEnter3WithInfo`Метод обратного вызова уведомляет профилировщик о вызове функций и позволяет профилировщику использовать [метод ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) для проверки значений аргументов.</span><span class="sxs-lookup"><span data-stu-id="60e7c-111">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="60e7c-112">Чтобы получить доступ к сведениям об аргументах, необходимо `COR_PRF_ENABLE_FUNCTION_ARGS` установить флаг.</span><span class="sxs-lookup"><span data-stu-id="60e7c-112">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="60e7c-113">Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий, а затем использовать [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) для регистрации реализации этой функции.</span><span class="sxs-lookup"><span data-stu-id="60e7c-113">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="60e7c-114">`FunctionEnter3WithInfo`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="60e7c-114">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="60e7c-115">Реализация должна использовать `__declspec(naked)` атрибут класса хранения.</span><span class="sxs-lookup"><span data-stu-id="60e7c-115">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="60e7c-116">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="60e7c-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="60e7c-117">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="60e7c-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="60e7c-118">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="60e7c-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="60e7c-119">Реализация `FunctionEnter3WithInfo` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="60e7c-119">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="60e7c-120">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="60e7c-120">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="60e7c-121">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter3WithInfo` вернет.</span><span class="sxs-lookup"><span data-stu-id="60e7c-121">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="60e7c-122">`FunctionEnter3WithInfo`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="60e7c-122">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60e7c-123">Требования</span><span class="sxs-lookup"><span data-stu-id="60e7c-123">Requirements</span></span>  

 <span data-ttu-id="60e7c-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60e7c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60e7c-125">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="60e7c-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="60e7c-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60e7c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60e7c-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60e7c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e7c-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="60e7c-128">See also</span></span>

- [<span data-ttu-id="60e7c-129">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="60e7c-129">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="60e7c-130">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="60e7c-130">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="60e7c-131">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="60e7c-131">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="60e7c-132">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="60e7c-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
