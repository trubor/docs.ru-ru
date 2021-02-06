---
description: Дополнительные сведения о функции FunctionIDMapper
title: Функция FunctionIDMapper
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: dca39d9d5269148fda12c50130f35bdeb10cb19d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648653"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="7ea8a-103">Функция FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7ea8a-103">FunctionIDMapper Function</span></span>

<span data-ttu-id="7ea8a-104">Уведомляет профилировщик о том, что заданный идентификатор функции может быть повторно сопоставлен с альтернативным ИДЕНТИФИКАТОРом для использования в обратных вызовах [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)и [FunctionTailcall2](functiontailcall2-function.md) для этой функции.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="7ea8a-105">`FunctionIDMapper` также позволяет профилировщику указать, желает ли он получать обратные вызовы для этой функции.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-105">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ea8a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ea8a-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ea8a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7ea8a-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="7ea8a-108">\[in] идентификатор функции для повторного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-108">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="7ea8a-109">\[out] указатель на значение, которое задает профилировщик `true` , если он хочет получить `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обратные вызовы, и, в противном случае присваивает этому параметру значение `false` .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7ea8a-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7ea8a-110">Return Value</span></span>  

 <span data-ttu-id="7ea8a-111">Профилировщик возвращает значение, которое использует подсистема выполнения в качестве альтернативного идентификатора функции.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="7ea8a-112">Это возвращаемое значение не может быть значением null, если указатель `pbHookFunction` возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="7ea8a-113">В противном случае возвращаемое значение null приведет к непредсказуемым результатам, включая, возможно, остановку процесса.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-113">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ea8a-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ea8a-114">Remarks</span></span>  

 <span data-ttu-id="7ea8a-115">`FunctionIDMapper`Функция является обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-115">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="7ea8a-116">Он реализуется профилировщиком для повторного сопоставления идентификатора функции с другим идентификатором, который более удобен для профилировщика.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-116">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="7ea8a-117">`FunctionIDMapper`Возвращает альтернативный идентификатор, используемый для любой заданной функции.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-117">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="7ea8a-118">Затем подсистема выполнения обрабатывает запрос профилировщика, передавая этот альтернативный идентификатор, помимо традиционного идентификатора функции, обратно в профилировщик в `clientData` параметре `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обработчиков, и, чтобы найти функцию, для которой вызывается обработчик.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-118">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="7ea8a-119">Для указания реализации функции можно использовать метод [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-119">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="7ea8a-120">Метод можно вызвать `ICorProfilerInfo::SetFunctionIDMapper` только один раз, и это рекомендуется сделать в обратном вызове [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-120">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="7ea8a-121">По умолчанию предполагается, что профилировщик, устанавливающий флаг COR_PRF_MONITOR_ENTERLEAVE с помощью [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)и устанавливающий перехватчики через [ICorProfilerInfo:: сетентерлеавефунктионхукс](icorprofilerinfo-setenterleavefunctionhooks-method.md) или [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), должен получить `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обратные вызовы, и для каждой функции.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-121">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="7ea8a-122">Однако профилировщики могут реализовать, `FunctionIDMapper` чтобы выборочно избежать получения этих обратных вызовов для определенных функций, задав `pbHookFunction` для значение `false` .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-122">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="7ea8a-123">Профилировщики должны быть нечувствительными к случаям, когда несколько потоков профилированного приложения вызывают один и тот же метод или функцию одновременно.</span><span class="sxs-lookup"><span data-stu-id="7ea8a-123">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="7ea8a-124">В таких случаях профилировщик может получить несколько `FunctionIDMapper` обратных вызовов для одного и того же `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-124">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="7ea8a-125">Профилировщик должен быть уверенным в том, чтобы возвращать те же значения из этого обратного вызова, когда он вызывается несколько раз с одним и тем же `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="7ea8a-125">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ea8a-126">Требования</span><span class="sxs-lookup"><span data-stu-id="7ea8a-126">Requirements</span></span>  

 <span data-ttu-id="7ea8a-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ea8a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ea8a-128">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="7ea8a-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7ea8a-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ea8a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ea8a-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ea8a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea8a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="7ea8a-131">See also</span></span>

- [<span data-ttu-id="7ea8a-132">Метод SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7ea8a-132">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7ea8a-133">Функция FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7ea8a-133">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="7ea8a-134">Функция FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="7ea8a-134">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="7ea8a-135">Функция FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="7ea8a-135">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="7ea8a-136">Функция FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="7ea8a-136">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="7ea8a-137">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="7ea8a-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
