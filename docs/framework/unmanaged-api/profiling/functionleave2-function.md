---
description: Дополнительные сведения о функции FunctionLeave2
title: Функция FunctionLeave2
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: a9a97b84c70fd50044e8340b6f59fdbefe1d1a60
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760149"
---
# <a name="functionleave2-function"></a><span data-ttu-id="319b8-103">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="319b8-103">FunctionLeave2 Function</span></span>

<span data-ttu-id="319b8-104">Уведомляет профилировщик о том, что функция собирается вернуться к вызывающему объекту, и предоставляет сведения о кадре стека и возвращаемом значении функции.</span><span class="sxs-lookup"><span data-stu-id="319b8-104">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="319b8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="319b8-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="319b8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="319b8-106">Parameters</span></span>

<span data-ttu-id="319b8-107">`funcId` окне Идентификатор возвращаемой функции.</span><span class="sxs-lookup"><span data-stu-id="319b8-107">`funcId` [in] The identifier of the function that is returning.</span></span>

<span data-ttu-id="319b8-108">`clientData` окне Идентификатор повторно сопоставленной функции, который профилировщик ранее указал с помощью функции [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="319b8-108">`clientData` [in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

<span data-ttu-id="319b8-109">`func` окне `COR_PRF_FRAME_INFO` Значение, указывающее на сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="319b8-109">`func` [in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

<span data-ttu-id="319b8-110">Профилировщик должен рассматривать это как непрозрачный маркер, который можно передать обратно в подсистему выполнения метода [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="319b8-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
<span data-ttu-id="319b8-111">`retvalRange` окне Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , указывающую расположение в памяти возвращаемого значения функции.</span><span class="sxs-lookup"><span data-stu-id="319b8-111">`retvalRange` [in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

<span data-ttu-id="319b8-112">Чтобы получить доступ к сведениям о возвращаемом значении, `COR_PRF_ENABLE_FUNCTION_RETVAL` необходимо установить флаг.</span><span class="sxs-lookup"><span data-stu-id="319b8-112">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="319b8-113">Профилировщик может использовать метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.</span><span class="sxs-lookup"><span data-stu-id="319b8-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="319b8-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="319b8-114">Remarks</span></span>  

 <span data-ttu-id="319b8-115">Значения `func` `retvalRange` параметров и недопустимы после `FunctionLeave2` возврата функции, так как значения могут измениться или быть уничтожены.</span><span class="sxs-lookup"><span data-stu-id="319b8-115">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="319b8-116">`FunctionLeave2`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="319b8-116">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="319b8-117">Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().</span><span class="sxs-lookup"><span data-stu-id="319b8-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="319b8-118">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="319b8-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="319b8-119">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="319b8-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="319b8-120">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="319b8-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="319b8-121">Реализация `FunctionLeave2` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="319b8-121">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="319b8-122">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="319b8-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="319b8-123">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave2` вернет.</span><span class="sxs-lookup"><span data-stu-id="319b8-123">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="319b8-124">Кроме того, `FunctionLeave2` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="319b8-124">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="319b8-125">Требования</span><span class="sxs-lookup"><span data-stu-id="319b8-125">Requirements</span></span>  

 <span data-ttu-id="319b8-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="319b8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="319b8-127">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="319b8-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="319b8-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="319b8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="319b8-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="319b8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319b8-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="319b8-130">See also</span></span>

- [<span data-ttu-id="319b8-131">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="319b8-131">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="319b8-132">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="319b8-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="319b8-133">Метод SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="319b8-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="319b8-134">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="319b8-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
