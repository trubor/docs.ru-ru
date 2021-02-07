---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Сетентерлеавефунктионхукс'
title: Метод ICorProfilerInfo::SetEnterLeaveFunctionHooks
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45c161a76f3ae568da6a83a2c45acb214a327ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687211"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="51b51-103">Метод ICorProfilerInfo::SetEnterLeaveFunctionHooks</span><span class="sxs-lookup"><span data-stu-id="51b51-103">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>

<span data-ttu-id="51b51-104">Задает реализованные профилировщиком функции, которые должны вызываться для обработчиков "Ввод", "Leave" и "таилкалл" управляемых функций.</span><span class="sxs-lookup"><span data-stu-id="51b51-104">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b51-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="51b51-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51b51-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="51b51-106">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="51b51-107">окне Указатель на реализацию, которая будет использоваться в качестве обратного вызова [FunctionEnter](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="51b51-107">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="51b51-108">окне Указатель на реализацию, которая будет использоваться в качестве обратного вызова [FunctionLeave](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="51b51-108">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="51b51-109">окне Указатель на реализацию, которая будет использоваться в качестве обратного вызова [функтионтаилкалл](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="51b51-109">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b51-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="51b51-110">Remarks</span></span>  

 <span data-ttu-id="51b51-111">В платформа .NET Framework версии 1,0 каждый указатель функции может иметь значение null, чтобы отключить соответствующий обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="51b51-111">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="51b51-112">Одновременно может быть активным только один набор обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="51b51-112">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="51b51-113">Таким образом, если профилировщик вызывает `SetEnterLeaveFunctionHooks` и [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), то `SetEnterLeaveFunctionHooks2` имеет приоритет.</span><span class="sxs-lookup"><span data-stu-id="51b51-113">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="51b51-114">`SetEnterLeaveFunctionHooks`Метод может быть вызван только из обратного вызова [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) профилировщика.</span><span class="sxs-lookup"><span data-stu-id="51b51-114">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b51-115">Требования</span><span class="sxs-lookup"><span data-stu-id="51b51-115">Requirements</span></span>  

 <span data-ttu-id="51b51-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b51-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b51-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51b51-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51b51-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b51-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b51-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b51-119">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b51-120">См. также</span><span class="sxs-lookup"><span data-stu-id="51b51-120">See also</span></span>

- [<span data-ttu-id="51b51-121">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="51b51-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
