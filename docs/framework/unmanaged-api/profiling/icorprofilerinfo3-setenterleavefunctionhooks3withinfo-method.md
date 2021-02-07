---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo'
title: Метод ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 15f6696635172972b09e68beeae13a7d6a8e195a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687016"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="b4d28-103">Метод ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4d28-103">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>

<span data-ttu-id="b4d28-104">Задает реализованные профилировщиком функции, которые будут вызываться для обработчиков [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)и [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) управляемых функций.</span><span class="sxs-lookup"><span data-stu-id="b4d28-104">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d28-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4d28-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d28-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b4d28-106">Parameters</span></span>  

 `pFuncEnter3`  
 <span data-ttu-id="b4d28-107">окне Указатель на реализацию, которая будет использоваться в качестве `FunctionEnter3WithInfo` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="b4d28-107">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="b4d28-108">окне Указатель на реализацию, которая будет использоваться в качестве `FunctionLeave3WithInfo` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="b4d28-108">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="b4d28-109">окне Указатель на реализацию, которая будет использоваться в качестве `FunctionTailcall3WithInfo` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="b4d28-109">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4d28-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4d28-110">Remarks</span></span>  

 <span data-ttu-id="b4d28-111">Обработчики [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)и [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) предоставляют кадры стека и проверку аргументов.</span><span class="sxs-lookup"><span data-stu-id="b4d28-111">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="b4d28-112">Для доступа к этим сведениям `COR_PRF_ENABLE_FUNCTION_ARGS` необходимо `COR_PRF_ENABLE_FUNCTION_RETVAL` задать флаги, и (или) `COR_PRF_ENABLE_FRAME_INFO` .</span><span class="sxs-lookup"><span data-stu-id="b4d28-112">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="b4d28-113">Профилировщик может использовать метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий, а затем использовать `SetEnterLeaveFunctionHooks3WithInfo` метод для регистрации реализации этой функции.</span><span class="sxs-lookup"><span data-stu-id="b4d28-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b4d28-114">В каждый момент времени активным может быть только один набор обратных вызовов, а последняя версия имеет приоритет.</span><span class="sxs-lookup"><span data-stu-id="b4d28-114">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="b4d28-115">Таким образом, если профилировщик вызывает и [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) `SetEnterLeaveFunctionHooks3WithInfo` , и `SetEnterLeaveFunctionHooks3WithInfo` используется.</span><span class="sxs-lookup"><span data-stu-id="b4d28-115">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="b4d28-116">`SetEnterLeaveFunctionHooks3WithInfo`Метод может быть вызван только из обратного вызова [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) профилировщика.</span><span class="sxs-lookup"><span data-stu-id="b4d28-116">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d28-117">Требования</span><span class="sxs-lookup"><span data-stu-id="b4d28-117">Requirements</span></span>  

 <span data-ttu-id="b4d28-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d28-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d28-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4d28-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4d28-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d28-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d28-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d28-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d28-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b4d28-122">See also</span></span>

- [<span data-ttu-id="b4d28-123">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="b4d28-123">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="b4d28-124">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="b4d28-124">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="b4d28-125">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b4d28-125">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="b4d28-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="b4d28-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="b4d28-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4d28-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="b4d28-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4d28-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="b4d28-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4d28-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b4d28-130">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="b4d28-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="b4d28-131">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b4d28-131">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b4d28-132">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b4d28-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b4d28-133">Профилирование</span><span class="sxs-lookup"><span data-stu-id="b4d28-133">Profiling</span></span>](index.md)
