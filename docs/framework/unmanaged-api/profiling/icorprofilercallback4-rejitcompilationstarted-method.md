---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: ReJITCompilationStarted'
title: Метод ICorProfilerCallback4::ReJITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 7656f68ff6b10dcd58e48df212a036a590d0c3b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788713"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="ec800-103">Метод ICorProfilerCallback4::ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="ec800-103">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>

<span data-ttu-id="ec800-104">Уведомляет профилировщик о том, что JIT-компилятор начал перекомпилировать функцию.</span><span class="sxs-lookup"><span data-stu-id="ec800-104">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec800-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec800-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec800-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ec800-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="ec800-107">окне Идентификатор функции, которая была запущена JIT-компилятором для перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="ec800-107">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="ec800-108">окне Идентификатор повторной компиляции новой версии функции.</span><span class="sxs-lookup"><span data-stu-id="ec800-108">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="ec800-109">[входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="ec800-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="ec800-110">Значение `true` не нанесет вред исполняющей среде, но может повлиять на результаты профилирования.</span><span class="sxs-lookup"><span data-stu-id="ec800-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec800-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="ec800-111">Remarks</span></span>  

 <span data-ttu-id="ec800-112">Можно получить несколько `ReJITCompilationStarted` вызовов методов и [режиткомпилатионфинишед](icorprofilercallback4-rejitcompilationfinished-method.md) для каждой из функций, поскольку среда выполнения обрабатывает конструкторы классов.</span><span class="sxs-lookup"><span data-stu-id="ec800-112">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="ec800-113">Например, среда выполнения начинает перекомпилировать метод а, но необходимо запустить конструктор класса для класса B.</span><span class="sxs-lookup"><span data-stu-id="ec800-113">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="ec800-114">Таким образом, среда выполнения перекомпилирует конструктор для класса B и запускает его.</span><span class="sxs-lookup"><span data-stu-id="ec800-114">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="ec800-115">Пока конструктор выполняется, он вызывает метод а, что вызывает повторную компиляцию метода а.</span><span class="sxs-lookup"><span data-stu-id="ec800-115">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="ec800-116">В этом сценарии первая перекомпиляция метода A останавливается.</span><span class="sxs-lookup"><span data-stu-id="ec800-116">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="ec800-117">Однако обе попытки перекомпилировать метод а сообщают о событиях JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="ec800-117">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="ec800-118">Профилировщики должны поддерживать последовательность обратных вызовов JIT-компиляции в случаях, когда два потока одновременно осуществляют обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="ec800-118">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="ec800-119">Например, поток A вызывает метод, `ReJITCompilationStarted` но до того, как поток a вызовет [режиткомпилатионфинишед](icorprofilercallback4-rejitcompilationfinished-method.md), поток B вызывает метод [ICorProfilerCallback:: ексцептионсеарчфунктионентер](icorprofilercallback-exceptionsearchfunctionenter-method.md) с идентификатором функции из `ReJITCompilationStarted` обратного вызова для потока а. Может показаться, что идентификатор функции еще не должен быть допустимым, поскольку профилировщик еще не получил вызов [режиткомпилатионфинишед](icorprofilercallback4-rejitcompilationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ec800-119">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="ec800-120">Однако в этом случае идентификатор функции является допустимым.</span><span class="sxs-lookup"><span data-stu-id="ec800-120">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec800-121">Требования</span><span class="sxs-lookup"><span data-stu-id="ec800-121">Requirements</span></span>  

 <span data-ttu-id="ec800-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec800-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec800-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec800-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec800-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec800-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec800-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec800-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec800-126">См. также</span><span class="sxs-lookup"><span data-stu-id="ec800-126">See also</span></span>

- [<span data-ttu-id="ec800-127">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ec800-127">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ec800-128">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="ec800-128">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="ec800-129">Метод JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="ec800-129">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="ec800-130">Метод ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="ec800-130">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
