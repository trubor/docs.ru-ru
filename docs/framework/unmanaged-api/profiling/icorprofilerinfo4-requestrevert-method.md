---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: Рекуестреверт'
title: Метод ICorProfilerInfo4::RequestRevert
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: 24a6a86f32bb9657e62a4433edcb5835e16b9754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737308"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="e475a-103">Метод ICorProfilerInfo4::RequestRevert</span><span class="sxs-lookup"><span data-stu-id="e475a-103">ICorProfilerInfo4::RequestRevert Method</span></span>

<span data-ttu-id="e475a-104">Восстанавливает исходные версии всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="e475a-104">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e475a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e475a-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e475a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e475a-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="e475a-107">[in] Число функций для восстановления.</span><span class="sxs-lookup"><span data-stu-id="e475a-107">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="e475a-108">[in] Указывает часть `moduleId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.</span><span class="sxs-lookup"><span data-stu-id="e475a-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="e475a-109">[in] Указывает часть `methodId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.</span><span class="sxs-lookup"><span data-stu-id="e475a-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="e475a-110">[out] Массив значений HRESULT, перечисленных в разделе «Значения HRESULT для состояния» далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="e475a-110">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="e475a-111">Каждое значение HRESULT указывает успех или сбой попытки восстановления исходного состояния каждой функции, указанной в параллельных массивах `moduleIds` и `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="e475a-111">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e475a-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e475a-112">Return Value</span></span>  

 <span data-ttu-id="e475a-113">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="e475a-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e475a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e475a-114">HRESULT</span></span>|<span data-ttu-id="e475a-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="e475a-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e475a-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e475a-116">S_OK</span></span>|<span data-ttu-id="e475a-117">Была предпринята попытка восстановления исходного состояния всех запросов; однако необходимо проверить массив возвращенных состояний, чтобы определить, какие функции были успешно восстановлены.</span><span class="sxs-lookup"><span data-stu-id="e475a-117">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="e475a-118">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="e475a-118">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="e475a-119">Чтобы этот вызов поддерживался, профилировщик должен реализовать интерфейс [ICorProfilerCallback4](icorprofilercallback4-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e475a-119">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="e475a-120">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="e475a-120">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="e475a-121">Перекомпиляция JIT не была включена.</span><span class="sxs-lookup"><span data-stu-id="e475a-121">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="e475a-122">Необходимо включить повторную компиляцию JIT-компилятора во время инициализации с помощью метода [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , чтобы установить `COR_PRF_ENABLE_REJIT` флаг.</span><span class="sxs-lookup"><span data-stu-id="e475a-122">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="e475a-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e475a-123">E_INVALIDARG</span></span>|<span data-ttu-id="e475a-124">Параметр `cFunctions` имеет значение 0, либо один из параметров `moduleIds` и `methodIds` имеет значение `NULL`.</span><span class="sxs-lookup"><span data-stu-id="e475a-124">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="e475a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e475a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e475a-126">Среде CLR не удалось выполнить запрос, поскольку не хватило памяти.</span><span class="sxs-lookup"><span data-stu-id="e475a-126">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="e475a-127">Значения HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="e475a-127">Status HRESULTS</span></span>  
  
|<span data-ttu-id="e475a-128">Массив значений HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="e475a-128">Status array HRESULT</span></span>|<span data-ttu-id="e475a-129">Описание:</span><span class="sxs-lookup"><span data-stu-id="e475a-129">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="e475a-130">S_OK</span><span class="sxs-lookup"><span data-stu-id="e475a-130">S_OK</span></span>|<span data-ttu-id="e475a-131">Соответствующая функция была успешно возвращена.</span><span class="sxs-lookup"><span data-stu-id="e475a-131">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="e475a-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e475a-132">E_INVALIDARG</span></span>|<span data-ttu-id="e475a-133">Значение параметра `moduleID` или параметра `methodDef` — `NULL`.</span><span class="sxs-lookup"><span data-stu-id="e475a-133">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="e475a-134">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="e475a-134">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="e475a-135">Модуль еще не полностью загружен или находится в процессе выгрузки.</span><span class="sxs-lookup"><span data-stu-id="e475a-135">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="e475a-136">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="e475a-136">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="e475a-137">Указанный модуль был создан динамически (например, с помощью `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="e475a-137">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="e475a-138">Поэтому он не поддерживается данным методом.</span><span class="sxs-lookup"><span data-stu-id="e475a-138">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="e475a-139">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="e475a-139">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="e475a-140">Среде CLR не удалось восстановить исходное состояние указанной функции, так как не найден соответствующий активный запрос перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="e475a-140">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="e475a-141">Либо эта перекомпиляция никогда не запрашивалась, либо функция уже была восстановлена.</span><span class="sxs-lookup"><span data-stu-id="e475a-141">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="e475a-142">Другое</span><span class="sxs-lookup"><span data-stu-id="e475a-142">Other</span></span>|<span data-ttu-id="e475a-143">Операционная система возвратила сбой за пределами среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e475a-143">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="e475a-144">Например, в случае сбоя системного вызова изменения защиты доступа к странице памяти будет отображаться ошибка операционной системы.</span><span class="sxs-lookup"><span data-stu-id="e475a-144">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e475a-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="e475a-145">Remarks</span></span>  

 <span data-ttu-id="e475a-146">При следующем вызове любой из восстановленных функций будет запускаться исходная версия этой функции.</span><span class="sxs-lookup"><span data-stu-id="e475a-146">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="e475a-147">Если функция уже выполняется, то будет завершено выполнение запущенной версии.</span><span class="sxs-lookup"><span data-stu-id="e475a-147">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e475a-148">Требования</span><span class="sxs-lookup"><span data-stu-id="e475a-148">Requirements</span></span>  

 <span data-ttu-id="e475a-149">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e475a-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e475a-150">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e475a-150">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e475a-151">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e475a-151">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e475a-152">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e475a-152">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e475a-153">См. также</span><span class="sxs-lookup"><span data-stu-id="e475a-153">See also</span></span>

- [<span data-ttu-id="e475a-154">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="e475a-154">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e475a-155">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e475a-155">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e475a-156">Профилирование</span><span class="sxs-lookup"><span data-stu-id="e475a-156">Profiling</span></span>](index.md)
