---
description: Дополнительные сведения о функции FunctionEnter
title: Функция FunctionEnter
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 0f5c9f0dde405aaadf50a7da476bbae664ef8ef7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759382"
---
# <a name="functionenter-function"></a><span data-ttu-id="15dc3-103">Функция FunctionEnter</span><span class="sxs-lookup"><span data-stu-id="15dc3-103">FunctionEnter Function</span></span>

<span data-ttu-id="15dc3-104">Уведомляет профилировщик о передаче управления в функцию.</span><span class="sxs-lookup"><span data-stu-id="15dc3-104">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15dc3-105">`FunctionEnter`Функция является устаревшей в платформа .NET Framework версии 2,0, и ее использование приведет к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="15dc3-105">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="15dc3-106">Вместо этого используйте функцию [FunctionEnter2](functionenter2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="15dc3-106">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15dc3-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="15dc3-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15dc3-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="15dc3-108">Parameters</span></span>

<span data-ttu-id="15dc3-109">`funcID` окне Идентификатор функции, которой передается элемент управления.</span><span class="sxs-lookup"><span data-stu-id="15dc3-109">`funcID` [in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="15dc3-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="15dc3-110">Remarks</span></span>  

 <span data-ttu-id="15dc3-111">`FunctionEnter`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="15dc3-111">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="15dc3-112">Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().</span><span class="sxs-lookup"><span data-stu-id="15dc3-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="15dc3-113">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="15dc3-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="15dc3-114">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="15dc3-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="15dc3-115">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="15dc3-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="15dc3-116">Реализация `FunctionEnter` не должна блокироваться, так как она приведет к задержке сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="15dc3-116">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="15dc3-117">Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="15dc3-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="15dc3-118">Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter` вернет.</span><span class="sxs-lookup"><span data-stu-id="15dc3-118">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="15dc3-119">Кроме того, `FunctionEnter` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="15dc3-119">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15dc3-120">Требования</span><span class="sxs-lookup"><span data-stu-id="15dc3-120">Requirements</span></span>  

 <span data-ttu-id="15dc3-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15dc3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15dc3-122">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="15dc3-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="15dc3-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15dc3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15dc3-124">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="15dc3-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15dc3-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="15dc3-125">See also</span></span>

- [<span data-ttu-id="15dc3-126">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="15dc3-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="15dc3-127">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="15dc3-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="15dc3-128">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="15dc3-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="15dc3-129">Метод SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="15dc3-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="15dc3-130">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="15dc3-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
