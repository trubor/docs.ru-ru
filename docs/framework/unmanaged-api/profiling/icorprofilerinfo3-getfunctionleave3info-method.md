---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetFunctionLeave3Info'
title: Метод ICorProfilerInfo3::GetFunctionLeave3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: 3031190a3603bedb3f58e7a86747542831c72291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646801"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="b981e-103">Метод ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="b981e-103">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>

<span data-ttu-id="b981e-104">Предоставляет кадр стека и возвращаемое значение функции, о которой сообщается профилировщику функцией [функции FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b981e-104">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="b981e-105">Этот метод может быть вызван только во время обратного вызова `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="b981e-105">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b981e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b981e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b981e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="b981e-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="b981e-108">окне Возвращаемое значение `FunctionID` функции.</span><span class="sxs-lookup"><span data-stu-id="b981e-108">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b981e-109">[in] Непрозрачный дескриптор, представляющий сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="b981e-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b981e-110">Профилировщик должен предоставлять те же `eltInfo` данные, что и профилировщик, с помощью функции [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b981e-110">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b981e-111">[out] Непрозрачный дескриптор, представляющий универсальные сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="b981e-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b981e-112">Этот дескриптор допустим только во время обратного вызова `FunctionLeave3WithInfo`, в котором профилировщик вызывал метод `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="b981e-112">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="b981e-113">заполняет Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , которая содержит значение, возвращаемое функцией.</span><span class="sxs-lookup"><span data-stu-id="b981e-113">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="b981e-114">Чтобы получить доступ к сведениям о возвращаемом значении, `COR_PRF_ENABLE_FUNCTION_RETVAL` необходимо установить флаг.</span><span class="sxs-lookup"><span data-stu-id="b981e-114">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="b981e-115">Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.</span><span class="sxs-lookup"><span data-stu-id="b981e-115">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b981e-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="b981e-116">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b981e-117">Требования</span><span class="sxs-lookup"><span data-stu-id="b981e-117">Requirements</span></span>  

 <span data-ttu-id="b981e-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b981e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b981e-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b981e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b981e-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b981e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b981e-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b981e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b981e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b981e-122">See also</span></span>

- [<span data-ttu-id="b981e-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b981e-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="b981e-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b981e-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="b981e-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b981e-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b981e-126">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b981e-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b981e-127">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b981e-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b981e-128">Профилирование</span><span class="sxs-lookup"><span data-stu-id="b981e-128">Profiling</span></span>](index.md)
