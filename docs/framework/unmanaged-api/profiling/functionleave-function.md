---
description: Дополнительные сведения о функции FunctionLeave
title: Функция FunctionLeave
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 619c1ecd92d2cc53512687d542becb3a2636b8af
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759499"
---
# <a name="functionleave-function"></a><span data-ttu-id="6e450-103">Функция FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="6e450-103">FunctionLeave Function</span></span>

<span data-ttu-id="6e450-104">Уведомляет профилировщик о том, что функция собирается вернуть вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="6e450-104">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e450-105">`FunctionLeave`Функция является устаревшей в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="6e450-105">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="6e450-106">Он будет продолжать работать, но будет приводить к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="6e450-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="6e450-107">Вместо этого используйте функцию [FunctionLeave2](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="6e450-107">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e450-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6e450-108">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e450-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="6e450-109">Parameters</span></span>

<span data-ttu-id="6e450-110">`funcID` окне Идентификатор возвращаемой функции.</span><span class="sxs-lookup"><span data-stu-id="6e450-110">`funcID` [in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e450-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="6e450-111">Remarks</span></span>  

 <span data-ttu-id="6e450-112">`FunctionLeave`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="6e450-112">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="6e450-113">Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().</span><span class="sxs-lookup"><span data-stu-id="6e450-113">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="6e450-114">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="6e450-114">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6e450-115">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="6e450-115">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6e450-116">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="6e450-116">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6e450-117">Реализация `FunctionLeave` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6e450-117">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="6e450-118">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6e450-118">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6e450-119">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave` вернет.</span><span class="sxs-lookup"><span data-stu-id="6e450-119">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="6e450-120">Кроме того, `FunctionLeave` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="6e450-120">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e450-121">Требования</span><span class="sxs-lookup"><span data-stu-id="6e450-121">Requirements</span></span>  

 <span data-ttu-id="6e450-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e450-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e450-123">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6e450-123">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6e450-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e450-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e450-125">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="6e450-125">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e450-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6e450-126">See also</span></span>

- [<span data-ttu-id="6e450-127">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="6e450-127">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="6e450-128">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="6e450-128">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="6e450-129">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="6e450-129">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="6e450-130">Метод SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="6e450-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="6e450-131">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="6e450-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
