---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: SetFunctionIDMapper'
title: Метод ICorProfilerInfo::SetFunctionIDMapper
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: c03c225db3b4126c3ac46ef6e5d36a5f72e529f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647223"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="e510b-103">Метод ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="e510b-103">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>

<span data-ttu-id="e510b-104">Задает реализуемую профилировщиком функцию, которая будет вызвана для сопоставления значений `FunctionID` с альтернативными значениями, передаваемыми обработчикам входа и выхода для функции профилировщика.</span><span class="sxs-lookup"><span data-stu-id="e510b-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e510b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e510b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e510b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e510b-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="e510b-107">окне Указатель на реализацию [FunctionIDMapper](functionidmapper-function.md) , которая будет вызываться для отображения `FunctionID` значений их альтернативных значений.</span><span class="sxs-lookup"><span data-stu-id="e510b-107">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e510b-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e510b-108">Remarks</span></span>  

 <span data-ttu-id="e510b-109">Альтернативные варианты `FunctionID` значений будут переданы обработчикам входа и выхода функций профилировщика ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)и [FunctionTailcall2](functiontailcall2-function.md)), заданным методом [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e510b-109">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="e510b-110">Параметр `FunctionIDMapper` можно задать только один раз, и его рекомендуется задать в обратном вызове [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e510b-110">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e510b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e510b-111">Requirements</span></span>  

 <span data-ttu-id="e510b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e510b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e510b-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e510b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e510b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e510b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e510b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e510b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e510b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e510b-116">See also</span></span>

- [<span data-ttu-id="e510b-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e510b-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
