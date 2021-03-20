---
description: Дополнительные сведения о функции FunctionEnter3
title: Функция FunctionEnter3
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 4726a080157b99c7538fe8a66cf8b26403564ad2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759303"
---
# <a name="functionenter3-function"></a><span data-ttu-id="6a566-103">Функция FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6a566-103">FunctionEnter3 Function</span></span>

<span data-ttu-id="6a566-104">Уведомляет профилировщик о передаче управления в функцию.</span><span class="sxs-lookup"><span data-stu-id="6a566-104">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a566-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6a566-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a566-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a566-106">Parameters</span></span>

<span data-ttu-id="6a566-107">`functionOrRemappedID` окне Идентификатор функции, которой передается элемент управления.</span><span class="sxs-lookup"><span data-stu-id="6a566-107">`functionOrRemappedID` [in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a566-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6a566-108">Remarks</span></span>  

 <span data-ttu-id="6a566-109">`FunctionEnter3`Функция обратного вызова уведомляет профилировщик о вызове функций, но не поддерживает проверку аргументов.</span><span class="sxs-lookup"><span data-stu-id="6a566-109">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="6a566-110">Чтобы зарегистрировать реализацию этой функции, используйте [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6a566-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6a566-111">`FunctionEnter3`Функция является обратным вызовом. ее необходимо реализовать.</span><span class="sxs-lookup"><span data-stu-id="6a566-111">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="6a566-112">Реализация должна использовать `__declspec(naked)` атрибут класса хранения.</span><span class="sxs-lookup"><span data-stu-id="6a566-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6a566-113">Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.</span><span class="sxs-lookup"><span data-stu-id="6a566-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6a566-114">Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).</span><span class="sxs-lookup"><span data-stu-id="6a566-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6a566-115">При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.</span><span class="sxs-lookup"><span data-stu-id="6a566-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a566-116">Требования</span><span class="sxs-lookup"><span data-stu-id="6a566-116">Requirements</span></span>  

 <span data-ttu-id="6a566-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a566-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a566-118">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="6a566-118">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6a566-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a566-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a566-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a566-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a566-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6a566-121">See also</span></span>

- [<span data-ttu-id="6a566-122">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6a566-122">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="6a566-123">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6a566-123">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="6a566-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6a566-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="6a566-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6a566-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="6a566-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6a566-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6a566-127">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6a566-127">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="6a566-128">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6a566-128">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="6a566-129">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="6a566-129">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="6a566-130">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="6a566-130">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="6a566-131">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="6a566-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
