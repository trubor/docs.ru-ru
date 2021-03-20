---
description: 'Дополнительные сведения о методе: Иклрпрофилинг:: AttachProfiler'
title: Метод ICLRProfiling::AttachProfiler
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
ms.openlocfilehash: 00ae5ca76462d8800a77c2869ef73703a4f1d980
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760773"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="98fa3-103">Метод ICLRProfiling::AttachProfiler</span><span class="sxs-lookup"><span data-stu-id="98fa3-103">ICLRProfiling::AttachProfiler Method</span></span>

<span data-ttu-id="98fa3-104">Подключает указанный профилировщик к указанному процессу.</span><span class="sxs-lookup"><span data-stu-id="98fa3-104">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98fa3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98fa3-105">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="98fa3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="98fa3-106">Parameters</span></span>

<span data-ttu-id="98fa3-107">`dwProfileeProcessID` окне Идентификатор процесса, к которому должен быть присоединен профилировщик.</span><span class="sxs-lookup"><span data-stu-id="98fa3-107">`dwProfileeProcessID` [in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="98fa3-108">На 64-разрядном компьютере разрядность профилируемого процесса должна соответствовать разрядности инициирующего процесса, вызывающего метод `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-108">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="98fa3-109">Если учетная запись пользователя, в которой вызывается метод `AttachProfiler`, имеет права администратора, целевым процессом может быть любой процесс в системе.</span><span class="sxs-lookup"><span data-stu-id="98fa3-109">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="98fa3-110">В противном случае целевой процесс должен принадлежать той же учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="98fa3-110">Otherwise, the target process must be owned by the same user account.</span></span>

<span data-ttu-id="98fa3-111">`dwMillisecondsMax` окне Длительность выполнения (в миллисекундах) `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="98fa3-111">`dwMillisecondsMax` [in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="98fa3-112">Инициирующий процесс должен передавать интервал времени, которого заведомо будет достаточно, чтобы конкретный профилировщик завершил свою инициализацию.</span><span class="sxs-lookup"><span data-stu-id="98fa3-112">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
<span data-ttu-id="98fa3-113">`pClsidProfiler` окне Указатель на идентификатор CLSID загружаемого профилировщика.</span><span class="sxs-lookup"><span data-stu-id="98fa3-113">`pClsidProfiler` [in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="98fa3-114">Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-114">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

<span data-ttu-id="98fa3-115">`wszProfilerPath` окне Полный путь к загружаемому файлу DLL профилировщика.</span><span class="sxs-lookup"><span data-stu-id="98fa3-115">`wszProfilerPath` [in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="98fa3-116">Эта строка должна содержать не более 260 символов, включая символ конца строки null.</span><span class="sxs-lookup"><span data-stu-id="98fa3-116">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="98fa3-117">Если в параметре `wszProfilerPath` задана пустая строка или значение null, среда CLR будет пытаться найти местоположение DLL-файла профилировщика путем поиска в реестре CLSID, на который указывает параметр `pClsidProfiler`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-117">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

<span data-ttu-id="98fa3-118">`pvClientData` окне Указатель на данные, передаваемые профилировщику методом [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98fa3-118">`pvClientData` [in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="98fa3-119">Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-119">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="98fa3-120">Если параметр `pvClientData` имеет значение null, параметр `cbClientData` должен иметь значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="98fa3-120">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

<span data-ttu-id="98fa3-121">`cbClientData` окне Размер (в байтах) данных, на которые `pvClientData` указывает.</span><span class="sxs-lookup"><span data-stu-id="98fa3-121">`cbClientData` [in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="98fa3-122">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="98fa3-122">Return Value</span></span>  

 <span data-ttu-id="98fa3-123">Этот метод возвращает следующие значения HRESULT.</span><span class="sxs-lookup"><span data-stu-id="98fa3-123">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="98fa3-124">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98fa3-124">HRESULT</span></span>|<span data-ttu-id="98fa3-125">Описание:</span><span class="sxs-lookup"><span data-stu-id="98fa3-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98fa3-126">S_OK</span><span class="sxs-lookup"><span data-stu-id="98fa3-126">S_OK</span></span>|<span data-ttu-id="98fa3-127">Указанный профилировщик успешно подключен к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="98fa3-127">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="98fa3-128">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="98fa3-128">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="98fa3-129">Уже существует активный профилировщик или профилировщик, подключенный к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="98fa3-129">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="98fa3-130">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="98fa3-130">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="98fa3-131">Указанный профилировщик не поддерживает подключение.</span><span class="sxs-lookup"><span data-stu-id="98fa3-131">The specified profiler does not support attachment.</span></span> <span data-ttu-id="98fa3-132">Инициирующий процесс может попытаться подключить другой профилировщик.</span><span class="sxs-lookup"><span data-stu-id="98fa3-132">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="98fa3-133">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="98fa3-133">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="98fa3-134">Не удалось запросить подключение профилировщика, так как версия целевого процесса несовместима с текущим процессом, вызывающим метод `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-134">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="98fa3-135">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="98fa3-135">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="98fa3-136">Пользователь инициирующего процесса не имеет доступа к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="98fa3-136">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="98fa3-137">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="98fa3-137">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="98fa3-138">Пользователь инициирующего процесса не имеет привилегий, необходимых для подключения профилировщика к указанному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="98fa3-138">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="98fa3-139">В журнале событий приложений могут содержаться дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="98fa3-139">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="98fa3-140">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="98fa3-140">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="98fa3-141">Произошла ошибка при взаимодействии с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="98fa3-141">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="98fa3-142">Обычно это происходит при завершении работы целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="98fa3-142">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="98fa3-143">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="98fa3-143">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="98fa3-144">Целевой процесс не существует, или в нем не запущена среда CLR, которая поддерживает подключение.</span><span class="sxs-lookup"><span data-stu-id="98fa3-144">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="98fa3-145">Это может указывать, что среда CLR была выгружена после вызова метода перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="98fa3-145">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="98fa3-146">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="98fa3-146">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="98fa3-147">Время ожидания истекло, а загрузка профилировщика не началась.</span><span class="sxs-lookup"><span data-stu-id="98fa3-147">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="98fa3-148">Можно повторить операцию подключения.</span><span class="sxs-lookup"><span data-stu-id="98fa3-148">You can retry the attach operation.</span></span> <span data-ttu-id="98fa3-149">Время ожидания истекает, когда метод завершения в целевом процессе выполняется дольше, чем задано в значении времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="98fa3-149">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="98fa3-150">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="98fa3-150">E_INVALIDARG</span></span>|<span data-ttu-id="98fa3-151">Как минимум один из следующих параметров имеет недопустимое значение.</span><span class="sxs-lookup"><span data-stu-id="98fa3-151">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="98fa3-152">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98fa3-152">E_FAIL</span></span>|<span data-ttu-id="98fa3-153">Произошел другой, не указанный сбой.</span><span class="sxs-lookup"><span data-stu-id="98fa3-153">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="98fa3-154">Другие коды ошибок</span><span class="sxs-lookup"><span data-stu-id="98fa3-154">Other error codes</span></span>|<span data-ttu-id="98fa3-155">Если метод [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) профилировщика ВОЗВРАЩАЕТ значение HRESULT, которое указывает на сбой, `AttachProfiler` ВОЗВРАЩАЕТ то же значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="98fa3-155">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="98fa3-156">В этом случае E_NOTIMPL преобразуется в CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="98fa3-156">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98fa3-157">Remarks</span><span class="sxs-lookup"><span data-stu-id="98fa3-157">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="98fa3-158">Управление памятью</span><span class="sxs-lookup"><span data-stu-id="98fa3-158">Memory Management</span></span>  

 <span data-ttu-id="98fa3-159">В соответствии с соглашениями COM объект, вызывающий метод `AttachProfiler` (например, код триггера, созданный разработчиком профилировщика), отвечает за выделение и освобождение памяти для данных, на которые указывает параметр `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="98fa3-159">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="98fa3-160">Когда среда CLR выполняет вызов `AttachProfiler`, создается копия памяти, на которую указывает `pvClientData`, которая затем передается в целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="98fa3-160">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="98fa3-161">Когда среда CLR в целевом процессе получает собственную копию блока `pvClientData`, она передает этот блок в профилировщик с помощью метода `InitializeForAttach`, а затем освобождает свою копию блока `pvClientData` в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="98fa3-161">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98fa3-162">Требования</span><span class="sxs-lookup"><span data-stu-id="98fa3-162">Requirements</span></span>  

 <span data-ttu-id="98fa3-163">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98fa3-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98fa3-164">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98fa3-164">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98fa3-165">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98fa3-165">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98fa3-166">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98fa3-166">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fa3-167">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="98fa3-167">See also</span></span>

- [<span data-ttu-id="98fa3-168">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="98fa3-168">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="98fa3-169">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="98fa3-169">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="98fa3-170">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="98fa3-170">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="98fa3-171">Профилирование</span><span class="sxs-lookup"><span data-stu-id="98fa3-171">Profiling</span></span>](index.md)
