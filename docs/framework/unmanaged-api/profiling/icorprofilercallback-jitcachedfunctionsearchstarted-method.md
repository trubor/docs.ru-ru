---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: JITCachedFunctionSearchStarted'
title: Метод ICorProfilerCallback::JITCachedFunctionSearchStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 1faaf8fbc1e0fee9ce76850cfedcd4e8cf934371
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705776"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="c3281-103">Метод ICorProfilerCallback::JITCachedFunctionSearchStarted</span><span class="sxs-lookup"><span data-stu-id="c3281-103">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>

<span data-ttu-id="c3281-104">Уведомляет профилировщик о начале поиска для функции, которая была скомпилирована ранее с помощью генератора образов в машинном кодах (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="c3281-104">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3281-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3281-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3281-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c3281-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c3281-107">\[in] идентификатор функции, для которой выполняется поиск.</span><span class="sxs-lookup"><span data-stu-id="c3281-107">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="c3281-108">\[out], `true` если подсистема выполнения должна использовать кэшированную версию функции (если она доступна); в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="c3281-108">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="c3281-109">Если значение равно `false` , подсистема выполнения JIT-компилирует функцию вместо использования версии, которая не является JIT-скомпилированной.</span><span class="sxs-lookup"><span data-stu-id="c3281-109">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3281-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3281-110">Remarks</span></span>  

 <span data-ttu-id="c3281-111">В платформа .NET Framework версии 2,0 `JITCachedFunctionSearchStarted` обратные вызовы [методов и ICorProfilerCallback:: житкачедфунктионсеарчфинишед](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) не будут выполняться для всех функций в обычных образах Ngen.</span><span class="sxs-lookup"><span data-stu-id="c3281-111">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="c3281-112">Только образы NGen, оптимизированные для профиля, будут создавать обратные вызовы для всех функций в образе.</span><span class="sxs-lookup"><span data-stu-id="c3281-112">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="c3281-113">Однако из-за дополнительных издержек профилировщик должен запросить оптимизированные профилировщиком генераторы NGen только в том случае, если планируется использовать эти обратные вызовы для принудительной компиляции функции JIT (JIT).</span><span class="sxs-lookup"><span data-stu-id="c3281-113">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="c3281-114">В противном случае профилировщик должен использовать отложенную стратегию для сбора сведений о функции.</span><span class="sxs-lookup"><span data-stu-id="c3281-114">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="c3281-115">Профилировщики должны поддерживать случаи, когда несколько потоков профилированного приложения одновременно вызывают один и тот же метод.</span><span class="sxs-lookup"><span data-stu-id="c3281-115">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="c3281-116">Например, поток а вызывает `JITCachedFunctionSearchStarted` и профилировщик отвечает, устанавливая для *пбусекачедфунктион* значение false для принудительной JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="c3281-116">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction* to FALSE to force JIT compilation.</span></span> <span data-ttu-id="c3281-117">Затем поток а вызывает метод [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) и [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3281-117">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="c3281-118">Теперь потоки B вызывают `JITCachedFunctionSearchStarted` одну и ту же функцию.</span><span class="sxs-lookup"><span data-stu-id="c3281-118">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="c3281-119">Несмотря на то, что профилировщик установил свою цель для JIT-компиляции функции, профилировщик получает второй обратный вызов, так как поток B отправляет обратный вызов до того, как профилировщик ответил на вызов потока A `JITCachedFunctionSearchStarted` .</span><span class="sxs-lookup"><span data-stu-id="c3281-119">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="c3281-120">Порядок, в котором потоки выполняют вызовы, зависит от того, как запланированы потоки.</span><span class="sxs-lookup"><span data-stu-id="c3281-120">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="c3281-121">Когда профилировщик получает дублирующиеся обратные вызовы, он должен задать значение, на которое ссылается, `pbUseCachedFunction` на то же значение для всех повторяющихся обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="c3281-121">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="c3281-122">То есть, когда `JITCachedFunctionSearchStarted` вызывается несколько раз с одним и тем же `functionId` значением, профилировщик должен каждый раз реагировать на эти же значения.</span><span class="sxs-lookup"><span data-stu-id="c3281-122">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3281-123">Требования</span><span class="sxs-lookup"><span data-stu-id="c3281-123">Requirements</span></span>  

 <span data-ttu-id="c3281-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3281-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3281-125">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3281-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3281-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3281-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3281-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3281-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3281-128">См. также</span><span class="sxs-lookup"><span data-stu-id="c3281-128">See also</span></span>

- [<span data-ttu-id="c3281-129">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c3281-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
