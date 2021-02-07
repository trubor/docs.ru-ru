---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2::D Остаккснапшот'
title: Метод ICorProfilerInfo2::DoStackSnapshot
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: e30e11dfe04da1e7a5adfef004036507b724963d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753254"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="cd82d-103">Метод ICorProfilerInfo2::DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="cd82d-103">ICorProfilerInfo2::DoStackSnapshot Method</span></span>

<span data-ttu-id="cd82d-104">Просматривает управляемые кадры в стеке для указанного потока и отправляет сведения профилировщику через обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="cd82d-104">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd82d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd82d-105">Syntax</span></span>  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd82d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd82d-106">Parameters</span></span>  

 `thread`  
 <span data-ttu-id="cd82d-107">окне Идентификатор целевого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-107">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="cd82d-108">При передаче значения NULL в `thread` получается моментальный снимок текущего потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-108">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="cd82d-109">Если `ThreadID` передается другой поток, среда CLR приостанавливает этот поток, выполняет моментальный снимок и возобновляет работу.</span><span class="sxs-lookup"><span data-stu-id="cd82d-109">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="cd82d-110">окне Указатель на реализацию метода [стаккснапшоткаллбакк](stacksnapshotcallback-function.md) , который ВЫЗЫВАЕТся средой CLR для предоставления профилировщику сведений о каждом управляемом кадре и каждом запуске неуправляемых фреймов.</span><span class="sxs-lookup"><span data-stu-id="cd82d-110">[in] A pointer to the implementation of the [StackSnapshotCallback](stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="cd82d-111">`StackSnapshotCallback`Метод реализуется модулем записи профилировщика.</span><span class="sxs-lookup"><span data-stu-id="cd82d-111">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="cd82d-112">окне Значение перечисления [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) , которое указывает объем данных, которые необходимо передать обратно для каждого кадра `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="cd82d-112">[in] A value of the [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="cd82d-113">окне Указатель на клиентские данные, которые передаются непосредственно в `StackSnapshotCallback` функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="cd82d-113">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="cd82d-114">окне Указатель на `CONTEXT` структуру Win32, которая используется для заполнения прохода стека.</span><span class="sxs-lookup"><span data-stu-id="cd82d-114">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="cd82d-115">Структура Win32 `CONTEXT` содержит значения регистров ЦП и представляет состояние ЦП в определенный момент времени.</span><span class="sxs-lookup"><span data-stu-id="cd82d-115">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="cd82d-116">Начальное значение помогает среде CLR определить, где следует начать анализ стека, если вершина стека является неуправляемым вспомогательным кодом. в противном случае начальное значение игнорируется.</span><span class="sxs-lookup"><span data-stu-id="cd82d-116">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="cd82d-117">Для асинхронного прохода необходимо указать начальное значение.</span><span class="sxs-lookup"><span data-stu-id="cd82d-117">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="cd82d-118">При выполнении синхронного анализа начальное значение не требуется.</span><span class="sxs-lookup"><span data-stu-id="cd82d-118">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="cd82d-119">`context`Параметр допустим только в том случае, если в параметре был передан флаг COR_PRF_SNAPSHOT_CONTEXT `infoFlags` .</span><span class="sxs-lookup"><span data-stu-id="cd82d-119">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cd82d-120">окне Размер `CONTEXT` структуры, на которую ссылается `context` параметр.</span><span class="sxs-lookup"><span data-stu-id="cd82d-120">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd82d-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd82d-121">Remarks</span></span>  

 <span data-ttu-id="cd82d-122">При передаче значения NULL для `thread` получается моментальный снимок текущего потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-122">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="cd82d-123">Моментальные снимки могут создаваться для других потоков, только если целевой поток приостановлен в данный момент времени.</span><span class="sxs-lookup"><span data-stu-id="cd82d-123">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="cd82d-124">Когда профилировщик хочет пройти по стеку, он вызывает `DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="cd82d-124">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="cd82d-125">Перед возвратом из этого вызова среда CLR вызывает `StackSnapshotCallback` несколько раз, один раз для каждого управляемого кадра (или для запуска неуправляемых фреймов) в стеке.</span><span class="sxs-lookup"><span data-stu-id="cd82d-125">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="cd82d-126">При обнаружении неуправляемых кадров их необходимо проанализировать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="cd82d-126">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="cd82d-127">Порядок, в котором выполняется продвижение стека, — это обратная процедура, с которой кадры помещаются в стек: первый кадр (последний отправленный), основной кадр (с первой передачей) последним.</span><span class="sxs-lookup"><span data-stu-id="cd82d-127">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="cd82d-128">Дополнительные сведения о программировании профилировщика для прохода по управляемым стекам см. в статьях анализ [стека профилировщика в платформа .NET Framework 2,0: основы и больше](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="cd82d-128">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="cd82d-129">Анализ стека может быть синхронным или асинхронным, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="cd82d-129">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="cd82d-130">Синхронный анализ стека</span><span class="sxs-lookup"><span data-stu-id="cd82d-130">Synchronous Stack Walk</span></span>  

 <span data-ttu-id="cd82d-131">Синхронный анализ стека включает в себя проход стека текущего потока в ответ на обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="cd82d-131">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="cd82d-132">Для этого не требуется заполнение или приостановка.</span><span class="sxs-lookup"><span data-stu-id="cd82d-132">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="cd82d-133">Синхронный вызов выполняется, когда в ответ на CLR, вызывающий один из методов [ICorProfilerCallback](icorprofilercallback-interface.md) (или [ICorProfilerCallback2](icorprofilercallback2-interface.md)) профилировщика, вызывается `DoStackSnapshot` для прохода по стеку текущего потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-133">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](icorprofilercallback-interface.md) (or [ICorProfilerCallback2](icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="cd82d-134">Это полезно, если нужно увидеть, как выглядит стек на уведомлении, например, с помощью [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd82d-134">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="cd82d-135">Вы просто вызываете в `DoStackSnapshot` `ICorProfilerCallback` методе, передавая NULL в `context` `thread` параметрах и.</span><span class="sxs-lookup"><span data-stu-id="cd82d-135">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="cd82d-136">Асинхронный анализ стека</span><span class="sxs-lookup"><span data-stu-id="cd82d-136">Asynchronous Stack Walk</span></span>  

 <span data-ttu-id="cd82d-137">Асинхронный проход стека включает в себя проход стека другого потока или проход стека текущего потока, а не в ответ на обратный вызов, но путем захвата указателя инструкций текущего потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-137">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="cd82d-138">Асинхронный проход требует начального значения, если вершина стека является неуправляемым кодом, который не является частью вызова неуправляемого кода (PInvoke) или вызовов COM, но вспомогательный код в самой среде CLR.</span><span class="sxs-lookup"><span data-stu-id="cd82d-138">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="cd82d-139">Например, код, выполняющий JIT-компиляцию или сборку мусора, является вспомогательным кодом.</span><span class="sxs-lookup"><span data-stu-id="cd82d-139">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="cd82d-140">Вы получаете начальное значение, напрямую приостанавливая целевой поток и проследуя его стек, пока не найдете самый верхний управляемый фрейм.</span><span class="sxs-lookup"><span data-stu-id="cd82d-140">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="cd82d-141">После приостановки целевого потока получите текущий контекст регистров целевого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-141">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="cd82d-142">Затем определите, указывает ли контекст регистра на неуправляемый код, вызвав [ICorProfilerInfo:: GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — если он возвращает значение `FunctionID` , равное нулю, кадр является неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="cd82d-142">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="cd82d-143">Теперь пройдите по стеку, пока не дойдете до первого управляемого фрейма, а затем вычислите контекст начального значения в зависимости от контекста регистров для этого кадра.</span><span class="sxs-lookup"><span data-stu-id="cd82d-143">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="cd82d-144">Вызовите его `DoStackSnapshot` с контекстом начального значения, чтобы начать асинхронный обход стека.</span><span class="sxs-lookup"><span data-stu-id="cd82d-144">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="cd82d-145">Если не указать начальное значение, `DoStackSnapshot` может пропускать управляемые фреймы в верхней части стека и, следовательно, выдаст вам неполную проверку стека.</span><span class="sxs-lookup"><span data-stu-id="cd82d-145">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="cd82d-146">Если указать начальное значение, оно должно указывать на JIT-скомпилированный или созданный генератором образов машинный код (Ngen.exe); в противном случае `DoStackSnapshot` возвращает код ошибки CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span><span class="sxs-lookup"><span data-stu-id="cd82d-146">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="cd82d-147">Асинхронные проверки стека могут привести к взаимоблокировкам или нарушениям доступа, если не следовать приведенным ниже рекомендациям.</span><span class="sxs-lookup"><span data-stu-id="cd82d-147">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
- <span data-ttu-id="cd82d-148">При прямой приостановке потоков Помните, что только поток, который никогда не выполнял управляемый код, может приостановить другой поток.</span><span class="sxs-lookup"><span data-stu-id="cd82d-148">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
- <span data-ttu-id="cd82d-149">Всегда заблокируйте в обратном вызове [ICorProfilerCallback:: ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) , пока не завершится проверка стека этого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-149">Always block in your [ICorProfilerCallback::ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
- <span data-ttu-id="cd82d-150">Не держите блокировку во время вызова профилировщика в функцию CLR, которая может активировать сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="cd82d-150">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="cd82d-151">Это значит, что блокировка не удерживается, если владеющий поток может выполнить вызов, который активирует сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="cd82d-151">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="cd82d-152">Кроме того, существует риск взаимоблокировки при вызове `DoStackSnapshot` из потока, созданного профилировщиком, чтобы можно было проанализировать стек отдельного целевого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-152">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="cd82d-153">В первый раз, когда созданный поток вводит определенные `ICorProfilerInfo*` методы (включая `DoStackSnapshot` ), среда CLR выполнит для этого потока инициализацию, зависящую от среды CLR, для каждого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-153">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="cd82d-154">Если профилировщик приостановил целевой поток, стек которого вы пытаетесь проанализировать, и если этот целевой поток был владельцем блокировки, необходимой для выполнения этой инициализации для каждого потока, произойдет взаимоблокировка.</span><span class="sxs-lookup"><span data-stu-id="cd82d-154">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="cd82d-155">Чтобы избежать этой взаимоблокировки, сделайте начальный вызов `DoStackSnapshot` из потока, созданного профилировщиком, для прохода по отдельному целевому потоку, но сначала не приостанавливаете целевой поток.</span><span class="sxs-lookup"><span data-stu-id="cd82d-155">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="cd82d-156">Этот начальный вызов гарантирует, что инициализация для каждого потока может завершиться без взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="cd82d-156">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="cd82d-157">Если `DoStackSnapshot` в случае успешности и сообщает по крайней мере один кадр, после этой точки он будет защищен для этого потока, созданного профилировщиком, для приостановки любого целевого потока и вызова `DoStackSnapshot` для прохода стека этого целевого потока.</span><span class="sxs-lookup"><span data-stu-id="cd82d-157">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd82d-158">Требования</span><span class="sxs-lookup"><span data-stu-id="cd82d-158">Requirements</span></span>  

 <span data-ttu-id="cd82d-159">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd82d-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd82d-160">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd82d-160">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd82d-161">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd82d-161">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd82d-162">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd82d-162">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd82d-163">См. также</span><span class="sxs-lookup"><span data-stu-id="cd82d-163">See also</span></span>

- [<span data-ttu-id="cd82d-164">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="cd82d-164">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cd82d-165">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="cd82d-165">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
