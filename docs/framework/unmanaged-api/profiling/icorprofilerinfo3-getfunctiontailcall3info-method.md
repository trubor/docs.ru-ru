---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetFunctionTailcall3Info'
title: Метод ICorProfilerInfo3::GetFunctionTailcall3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: a8976a11cf7a2c556afa62a559e3a294d81b9a1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646807"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="0a7f9-103">Метод ICorProfilerInfo3::GetFunctionTailcall3Info</span><span class="sxs-lookup"><span data-stu-id="0a7f9-103">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>

<span data-ttu-id="0a7f9-104">Предоставляет кадр стека функции, о которой сообщается профилировщику функцией [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0a7f9-104">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="0a7f9-105">Этот метод может быть вызван только во время обратного вызова `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-105">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a7f9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a7f9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a7f9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0a7f9-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="0a7f9-108">окне Возвращаемое значение `FunctionID` функции.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-108">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="0a7f9-109">[in] Непрозрачный дескриптор, представляющий сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-109">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0a7f9-110">Профилировщик должен предоставить `eltInfo` профилировщику тот же, который был передан `FunctionTailcall3WithInfo` функцией.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-110">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="0a7f9-111">[out] Непрозрачный дескриптор, представляющий универсальные сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-111">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="0a7f9-112">Этот дескриптор допустим только во время обратного вызова `FunctionTailcall3WithInfo`, в котором профилировщик вызывал метод `GetFunctionTailcall3Info`.</span><span class="sxs-lookup"><span data-stu-id="0a7f9-112">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a7f9-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a7f9-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a7f9-114">Требования</span><span class="sxs-lookup"><span data-stu-id="0a7f9-114">Requirements</span></span>  

 <span data-ttu-id="0a7f9-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a7f9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a7f9-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a7f9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a7f9-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a7f9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a7f9-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a7f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7f9-119">См. также</span><span class="sxs-lookup"><span data-stu-id="0a7f9-119">See also</span></span>

- [<span data-ttu-id="0a7f9-120">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a7f9-120">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="0a7f9-121">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a7f9-121">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="0a7f9-122">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a7f9-122">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0a7f9-123">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="0a7f9-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0a7f9-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0a7f9-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0a7f9-125">Профилирование</span><span class="sxs-lookup"><span data-stu-id="0a7f9-125">Profiling</span></span>](index.md)
