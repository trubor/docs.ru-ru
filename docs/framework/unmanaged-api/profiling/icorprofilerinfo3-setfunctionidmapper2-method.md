---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: SetFunctionIDMapper2'
title: Метод ICorProfilerInfo3::SetFunctionIDMapper2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 4847d3bd7b8bf6142da0f32c3558016b2c758087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686990"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="e4f89-103">Метод ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="e4f89-103">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>

<span data-ttu-id="e4f89-104">Задает реализуемую профилировщиком функцию, которая будет вызвана для сопоставления значений `FunctionID` с альтернативными значениями, передаваемыми обработчикам входа и выхода для функции профилировщика.</span><span class="sxs-lookup"><span data-stu-id="e4f89-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="e4f89-105">Этот метод расширяет метод [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) с дополнительным параметром данных, который профилировщики могут использовать для устранения неоднозначности между средами выполнения.</span><span class="sxs-lookup"><span data-stu-id="e4f89-105">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f89-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4f89-106">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f89-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e4f89-107">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="e4f89-108">окне Указатель на реализацию [FunctionIDMapper2](functionidmapper2-function.md) , которая будет вызываться для соответствия `FunctionID` значений их альтернативным значениям.</span><span class="sxs-lookup"><span data-stu-id="e4f89-108">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="e4f89-109">окне Указатель, который передается в каждый вызов функции [FunctionIDMapper2](functionidmapper2-function.md) , выполненной текущей средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="e4f89-109">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="e4f89-110">Профилировщик может использовать эти сведения для устранения неоднозначности между средами выполнения.</span><span class="sxs-lookup"><span data-stu-id="e4f89-110">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f89-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e4f89-111">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4f89-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e4f89-112">Remarks</span></span>  

 <span data-ttu-id="e4f89-113">Альтернативы значениям FunctionID будут переданы обработчикам входа и выхода функций профилировщика ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)и [FunctionTailcall3](functiontailcall3-function.md); или [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)и [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)), которые указаны в методе [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) или [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e4f89-113">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="e4f89-114">`FunctionIDMapper2`Метод можно задать только один раз. рекомендуется задать его в обратном вызове метода [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e4f89-114">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f89-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e4f89-115">Requirements</span></span>  

 <span data-ttu-id="e4f89-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f89-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f89-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4f89-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4f89-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4f89-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f89-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f89-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e4f89-120">See also</span></span>

- [<span data-ttu-id="e4f89-121">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="e4f89-121">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="e4f89-122">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="e4f89-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e4f89-123">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e4f89-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e4f89-124">Профилирование</span><span class="sxs-lookup"><span data-stu-id="e4f89-124">Profiling</span></span>](index.md)
