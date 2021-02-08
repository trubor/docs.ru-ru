---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: Рекуестрежит'
title: Метод ICorProfilerInfo4::RequestReJIT
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 2da65c2db5722f689f1a8588169ea099aff71be6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799022"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="c14ba-103">Метод ICorProfilerInfo4::RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="c14ba-103">ICorProfilerInfo4::RequestReJIT Method</span></span>

<span data-ttu-id="c14ba-104">Запрашивает перекомпиляцию JIT всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="c14ba-104">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c14ba-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c14ba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c14ba-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="c14ba-107">[in] Число функций для перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="c14ba-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="c14ba-108">[in] Указывает часть `moduleId` пар (`module`, `methodDef`), которые идентифицируют перекомпилируемые функции.</span><span class="sxs-lookup"><span data-stu-id="c14ba-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="c14ba-109">[in] Указывает часть `methodId` пар (`module`, `methodDef`), которые идентифицируют перекомпилируемые функции.</span><span class="sxs-lookup"><span data-stu-id="c14ba-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c14ba-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c14ba-110">Return Value</span></span>  

 <span data-ttu-id="c14ba-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="c14ba-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c14ba-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c14ba-112">HRESULT</span></span>|<span data-ttu-id="c14ba-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="c14ba-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c14ba-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c14ba-114">S_OK</span></span>|<span data-ttu-id="c14ba-115">Была предпринята попытка пометить все методы для перекомпиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="c14ba-115">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="c14ba-116">Профилировщик должен реализовать метод [ICorProfilerCallback4:: режитеррор](icorprofilercallback4-rejiterror-method.md) , чтобы определить, какие методы были успешно отмечены для повторной компиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="c14ba-116">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="c14ba-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="c14ba-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="c14ba-118">Чтобы этот вызов поддерживался, профилировщик должен реализовать интерфейс [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c14ba-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="c14ba-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="c14ba-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="c14ba-120">Перекомпиляция JIT не была включена.</span><span class="sxs-lookup"><span data-stu-id="c14ba-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="c14ba-121">Необходимо включить повторную компиляцию JIT-компилятора во время инициализации с помощью метода [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , чтобы установить `COR_PRF_ENABLE_REJIT` флаг.</span><span class="sxs-lookup"><span data-stu-id="c14ba-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="c14ba-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c14ba-122">E_INVALIDARG</span></span>|<span data-ttu-id="c14ba-123">Параметр `cFunctions` имеет значение 0, либо один из параметров `moduleIds` и `methodIds` имеет значение `NULL`.</span><span class="sxs-lookup"><span data-stu-id="c14ba-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="c14ba-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c14ba-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c14ba-125">Среде CLR не удалось выполнить запрос, поскольку не хватило памяти.</span><span class="sxs-lookup"><span data-stu-id="c14ba-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c14ba-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="c14ba-126">Remarks</span></span>  

 <span data-ttu-id="c14ba-127">Вызовите `RequestReJIT`, чтобы среда выполнения перекомпилировала указанный набор функций.</span><span class="sxs-lookup"><span data-stu-id="c14ba-127">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="c14ba-128">Затем профилировщик кода может использовать интерфейс [икорпрофилерфунктионконтрол](icorprofilerfunctioncontrol-interface.md) для настройки кода, формируемого при повторной компиляции функций.</span><span class="sxs-lookup"><span data-stu-id="c14ba-128">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="c14ba-129">Это не влияет на функции, выполняющиеся в текущий момент; только на будущие вызовы функций.</span><span class="sxs-lookup"><span data-stu-id="c14ba-129">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="c14ba-130">Если любая из указанных функций уже подверглась перекомпиляции JIT ранее, то запрос перекомпиляции эквивалентен восстановлению исходного состояния и перекомпиляции этой функции.</span><span class="sxs-lookup"><span data-stu-id="c14ba-130">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="c14ba-131">Для сохранения возможности восстановления исходного состояния, когда JIT-компилятор компилирует исходную версию функции, он рассматривает только исходные версии вызывающих ее объектов для встраиваемых решений.</span><span class="sxs-lookup"><span data-stu-id="c14ba-131">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="c14ba-132">Когда JIT-компилятор перекомпилирует функцию, он рассматривает текущие версии (перекомпилированные или исходные) ее  вызывающих объектов для встраивания.</span><span class="sxs-lookup"><span data-stu-id="c14ba-132">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="c14ba-133">Профилировщик обычно вызывает `RequestReJIT` в ответ на ввод пользователя, запрашивающего инструментирование профилировщиком одного или нескольких методов.</span><span class="sxs-lookup"><span data-stu-id="c14ba-133">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="c14ba-134">Обычно `RequestReJIT` приостанавливает среду выполнения для выполнения некоторых операций и потенциально может инициировать сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="c14ba-134">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="c14ba-135">Таким образом, профилировщик должен вызывать `RequestReJIT` из потока, созданного им ранее, а не из потока, созданного средой CLR, который в текущий момент выполняет обратный вызов профилировщика.</span><span class="sxs-lookup"><span data-stu-id="c14ba-135">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c14ba-136">Требования</span><span class="sxs-lookup"><span data-stu-id="c14ba-136">Requirements</span></span>  

 <span data-ttu-id="c14ba-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14ba-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c14ba-138">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c14ba-138">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c14ba-139">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c14ba-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c14ba-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c14ba-140">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14ba-141">См. также</span><span class="sxs-lookup"><span data-stu-id="c14ba-141">See also</span></span>

- [<span data-ttu-id="c14ba-142">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="c14ba-142">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="c14ba-143">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c14ba-143">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c14ba-144">Профилирование</span><span class="sxs-lookup"><span data-stu-id="c14ba-144">Profiling</span></span>](index.md)
