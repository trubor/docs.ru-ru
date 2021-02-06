---
description: Дополнительные сведения о функции FunctionIDMapper2
title: Функция FunctionIDMapper2
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 1fd6680ffaa7b28e679dc3eaeb9840981ead5c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648575"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="a07cd-103">Функция FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a07cd-103">FunctionIDMapper2 Function</span></span>

<span data-ttu-id="a07cd-104">Уведомляет профилировщик о том, что заданный идентификатор функции может быть повторно сопоставлен с альтернативным ИДЕНТИФИКАТОРом для использования в ответных вызовах [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), [FunctionTailcall3](functiontailcall3-function.md)или[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)и [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a07cd-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="a07cd-105">`FunctionIDMapper2` также позволяет профилировщику указать, желает ли он получать обратные вызовы для этой функции.</span><span class="sxs-lookup"><span data-stu-id="a07cd-105">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07cd-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a07cd-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a07cd-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a07cd-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="a07cd-108">\[in] идентификатор функции для повторного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="a07cd-108">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="a07cd-109">\[in] указатель на данные, которые используются для однозначного определения между средами выполнения.</span><span class="sxs-lookup"><span data-stu-id="a07cd-109">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="a07cd-110">\[out] указатель на значение, которое задает профилировщик `true` , если он хочет получить `FunctionEnter3` `FunctionLeave3` обратные вызовы,, и, `FunctionTailcall3` или `FunctionEnter3WithInfo` , `FunctionLeave3WithInfo` и, `FunctionTailcall3WithInfo` в противном случае, присваивает этому значению значение `false` .</span><span class="sxs-lookup"><span data-stu-id="a07cd-110">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a07cd-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a07cd-111">Return Value</span></span>  

 <span data-ttu-id="a07cd-112">Профилировщик возвращает значение, которое использует подсистема выполнения в качестве альтернативного идентификатора функции.</span><span class="sxs-lookup"><span data-stu-id="a07cd-112">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="a07cd-113">Это возвращаемое значение не может быть значением null, если указатель `pbHookFunction` возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a07cd-113">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="a07cd-114">В противном случае возвращаемое значение null приводит к непредсказуемым результатам, включая возможное прерывание процесса.</span><span class="sxs-lookup"><span data-stu-id="a07cd-114">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a07cd-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="a07cd-115">Remarks</span></span>  

 <span data-ttu-id="a07cd-116">Этот метод расширяет функцию [FunctionIDMapper](functionidmapper-function.md) с помощью дополнительного параметра, который используется для передачи данных клиента.</span><span class="sxs-lookup"><span data-stu-id="a07cd-116">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="a07cd-117">Эти данные клиента служат для однозначного определения среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a07cd-117">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a07cd-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a07cd-118">Requirements</span></span>  

 <span data-ttu-id="a07cd-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a07cd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a07cd-120">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="a07cd-120">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a07cd-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a07cd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a07cd-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a07cd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07cd-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a07cd-123">See also</span></span>

- [<span data-ttu-id="a07cd-124">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a07cd-124">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a07cd-125">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a07cd-125">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a07cd-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a07cd-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="a07cd-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a07cd-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="a07cd-128">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a07cd-128">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a07cd-129">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a07cd-129">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a07cd-130">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a07cd-130">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a07cd-131">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a07cd-131">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a07cd-132">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="a07cd-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
