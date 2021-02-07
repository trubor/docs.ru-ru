---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Житкачедфунктионсеарчфинишед'
title: Метод ICorProfilerCallback::JITCachedFunctionSearchFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: b5025a7d33800047bb6244b82308ba2ab158cea7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705854"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="f3db7-103">Метод ICorProfilerCallback::JITCachedFunctionSearchFinished</span><span class="sxs-lookup"><span data-stu-id="f3db7-103">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>

<span data-ttu-id="f3db7-104">Уведомляет профилировщик о завершении поиска для функции, которая была скомпилирована ранее с помощью генератора образов в машинном кодах (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="f3db7-104">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3db7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3db7-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3db7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f3db7-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="f3db7-107">\[in] идентификатор функции, для которой был выполнен поиск.</span><span class="sxs-lookup"><span data-stu-id="f3db7-107">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="f3db7-108">\[в] значение перечисления [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , указывающее результат поиска.</span><span class="sxs-lookup"><span data-stu-id="f3db7-108">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3db7-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3db7-109">Remarks</span></span>  

 <span data-ttu-id="f3db7-110">В платформа .NET Framework версии 2,0 функции [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) и `JITCachedFunctionSearchFinished` обратные вызовы не будут выполняться для всех функций в обычных образах Ngen.</span><span class="sxs-lookup"><span data-stu-id="f3db7-110">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="f3db7-111">Только образы NGen, оптимизированные для профилировщика, будут создавать обратные вызовы для всех функций в образе.</span><span class="sxs-lookup"><span data-stu-id="f3db7-111">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="f3db7-112">Однако из-за дополнительных издержек профилировщик должен запросить оптимизированные профилировщиком генераторы NGen только в том случае, если планируется использовать эти обратные вызовы для принудительной компиляции функции JIT (JIT).</span><span class="sxs-lookup"><span data-stu-id="f3db7-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="f3db7-113">В противном случае профилировщик должен использовать отложенную стратегию для сбора сведений о функции.</span><span class="sxs-lookup"><span data-stu-id="f3db7-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3db7-114">Требования</span><span class="sxs-lookup"><span data-stu-id="f3db7-114">Requirements</span></span>  

 <span data-ttu-id="f3db7-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3db7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3db7-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3db7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3db7-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3db7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3db7-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3db7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3db7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f3db7-119">See also</span></span>

- [<span data-ttu-id="f3db7-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="f3db7-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
