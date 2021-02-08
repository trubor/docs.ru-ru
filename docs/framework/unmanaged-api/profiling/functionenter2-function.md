---
description: Дополнительные сведения о функции FunctionEnter2
title: Функция FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 8b8061b213d02efd845e214c1177db4e5351869b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788986"
---
# <a name="functionenter2-function"></a><span data-ttu-id="837bd-103">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="837bd-103">FunctionEnter2 Function</span></span>

<span data-ttu-id="837bd-104">Уведомляет профилировщик о передаче управления в функцию и предоставляет сведения о кадре стека и аргументах функции.</span><span class="sxs-lookup"><span data-stu-id="837bd-104">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="837bd-105">Эта функция заменяет функцию [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="837bd-105">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837bd-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="837bd-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="837bd-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="837bd-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="837bd-108">\[in] идентификатор функции, для которой передается элемент управления.</span><span class="sxs-lookup"><span data-stu-id="837bd-108">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="837bd-109">\[in] идентификатор повторно сопоставленной функции, который профилировщик ранее указал с помощью функции [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="837bd-109">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="837bd-110">\[в] `COR_PRF_FRAME_INFO` значение, указывающее на сведения о кадре стека.</span><span class="sxs-lookup"><span data-stu-id="837bd-110">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="837bd-111">Профилировщик должен рассматривать это как непрозрачный маркер, который можно передать обратно в подсистему выполнения метода [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="837bd-111">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="837bd-112">\[in] указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , указывающую расположения в памяти аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="837bd-112">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="837bd-113">Чтобы получить доступ к сведениям об аргументах, `COR_PRF_ENABLE_FUNCTION_ARGS` необходимо установить флаг.</span><span class="sxs-lookup"><span data-stu-id="837bd-113">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="837bd-114">Профилировщик может использовать метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.</span><span class="sxs-lookup"><span data-stu-id="837bd-114">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="837bd-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="837bd-115">Remarks</span></span>  

 <span data-ttu-id="837bd-116">Значения `func` `argumentInfo` параметров и недопустимы после `FunctionEnter2` возврата функции, так как значения могут измениться или быть уничтожены.</span><span class="sxs-lookup"><span data-stu-id="837bd-116">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="837bd-117">`FunctionEnter2`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="837bd-117">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="837bd-118">Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().</span><span class="sxs-lookup"><span data-stu-id="837bd-118">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="837bd-119">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="837bd-119">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="837bd-120">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="837bd-120">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="837bd-121">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="837bd-121">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="837bd-122">Реализация `FunctionEnter2` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="837bd-122">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="837bd-123">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="837bd-123">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="837bd-124">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter2` вернет.</span><span class="sxs-lookup"><span data-stu-id="837bd-124">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="837bd-125">Кроме того, `FunctionEnter2` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="837bd-125">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837bd-126">Требования</span><span class="sxs-lookup"><span data-stu-id="837bd-126">Requirements</span></span>  

 <span data-ttu-id="837bd-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="837bd-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837bd-128">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="837bd-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="837bd-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="837bd-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="837bd-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837bd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837bd-131">См. также</span><span class="sxs-lookup"><span data-stu-id="837bd-131">See also</span></span>

- [<span data-ttu-id="837bd-132">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="837bd-132">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="837bd-133">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="837bd-133">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="837bd-134">Метод SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="837bd-134">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="837bd-135">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="837bd-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
