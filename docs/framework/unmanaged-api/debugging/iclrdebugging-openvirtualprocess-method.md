---
description: 'Дополнительные сведения о методе: ICLRDebugging:: OpenVirtualProcess'
title: Метод ICLRDebugging::OpenVirtualProcess
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: f9f195e1202a26a13b09cace74328c3937a9fcf1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723300"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="8e378-103">Метод ICLRDebugging::OpenVirtualProcess</span><span class="sxs-lookup"><span data-stu-id="8e378-103">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="8e378-104">Возвращает интерфейс ICorDebugProcess, соответствующий загруженному в процесс модулю среды CLR.</span><span class="sxs-lookup"><span data-stu-id="8e378-104">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e378-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e378-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e378-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e378-106">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="8e378-107">окне Базовый адрес модуля в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="8e378-107">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="8e378-108">COR_E_NOT_CLR будет возвращен, если указанный модуль не является модулем CLR.</span><span class="sxs-lookup"><span data-stu-id="8e378-108">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="8e378-109">окне Абстракция целевого объекта данных, позволяющая управляемому отладчику проверять состояние процесса.</span><span class="sxs-lookup"><span data-stu-id="8e378-109">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="8e378-110">В отладчике должен быть реализован интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8e378-110">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="8e378-111">Необходимо реализовать интерфейс [иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md) для поддержки сценариев, в которых отлаживаемая среда CLR не установлена локально на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8e378-111">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="8e378-112">окне Интерфейс обратного вызова поставщика библиотеки, позволяющий находить и загружать библиотеки отладки для конкретных версий по запросу.</span><span class="sxs-lookup"><span data-stu-id="8e378-112">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="8e378-113">Этот параметр является обязательным только в том случае `ppProcess` , если значение параметра или `pFlags` не равно `null` .</span><span class="sxs-lookup"><span data-stu-id="8e378-113">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="8e378-114">окне Самая высокая версия среды CLR, которую отладчик может отлаживать.</span><span class="sxs-lookup"><span data-stu-id="8e378-114">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="8e378-115">Необходимо указать основной, дополнительный номер версии и версию сборки из последней версии среды CLR, которую поддерживает этот отладчик, и установить номер редакции 65535 для размещения будущих выпусков среды CLR на месте.</span><span class="sxs-lookup"><span data-stu-id="8e378-115">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="8e378-116">окне ИДЕНТИФИКАТОР получаемого интерфейса ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="8e378-116">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="8e378-117">В настоящее время допустимыми значениями являются IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 и IID_CORDEBUGPROCESS.</span><span class="sxs-lookup"><span data-stu-id="8e378-117">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="8e378-118">заполняет Указатель на COM-интерфейс, идентифицируемый `riidProcess` .</span><span class="sxs-lookup"><span data-stu-id="8e378-118">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="8e378-119">[вход, выход] Версия среды CLR.</span><span class="sxs-lookup"><span data-stu-id="8e378-119">[in, out] The version of the CLR.</span></span> <span data-ttu-id="8e378-120">Во входных данных это значение может быть равно `null` .</span><span class="sxs-lookup"><span data-stu-id="8e378-120">On input, this value can be `null`.</span></span> <span data-ttu-id="8e378-121">Он также может указывать на структуру [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) . в этом случае `wStructVersion` поле структуры должно быть инициализировано равным 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="8e378-121">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="8e378-122">В выходных данных возвращаемая `CLR_DEBUGGING_VERSION` структура будет заполнена сведениями о версии для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="8e378-122">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="8e378-123">заполняет Информационные флаги для указанной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="8e378-123">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="8e378-124">Описание флагов см. в [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) разделе.</span><span class="sxs-lookup"><span data-stu-id="8e378-124">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e378-125">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8e378-125">Return Value</span></span>  

 <span data-ttu-id="8e378-126">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="8e378-126">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8e378-127">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e378-127">HRESULT</span></span>|<span data-ttu-id="8e378-128">Описание:</span><span class="sxs-lookup"><span data-stu-id="8e378-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e378-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e378-129">S_OK</span></span>|<span data-ttu-id="8e378-130">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="8e378-130">The method completed successfully.</span></span>|  
|<span data-ttu-id="8e378-131">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8e378-131">E_POINTER</span></span>|<span data-ttu-id="8e378-132">Параметр `pDataTarget` равен `null`.</span><span class="sxs-lookup"><span data-stu-id="8e378-132">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="8e378-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="8e378-133">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="8e378-134">Обратный вызов [иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md) возвращает ошибку или не предоставляет допустимый маркер.</span><span class="sxs-lookup"><span data-stu-id="8e378-134">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="8e378-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="8e378-135">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="8e378-136">`pDataTarget` не реализует необходимые интерфейсы целевого объекта данных для этой версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="8e378-136">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="8e378-137">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="8e378-137">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="8e378-138">Указанный модуль не является модулем CLR.</span><span class="sxs-lookup"><span data-stu-id="8e378-138">The indicated module is not a CLR module.</span></span> <span data-ttu-id="8e378-139">Это значение HRESULT также возвращается, если модуль среды CLR не удается обнаружить из-за повреждения памяти, модуль недоступен или версия среды CLR позже версии оболочки совместимости.</span><span class="sxs-lookup"><span data-stu-id="8e378-139">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="8e378-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="8e378-140">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="8e378-141">Эта версия среды выполнения не поддерживает эту модель отладки.</span><span class="sxs-lookup"><span data-stu-id="8e378-141">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="8e378-142">В настоящее время модель отладки не поддерживается версиями CLR до платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8e378-142">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="8e378-143">`pwszVersion`После этой ошибки параметру OUTPUT по-прежнему присваивается правильное значение.</span><span class="sxs-lookup"><span data-stu-id="8e378-143">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="8e378-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="8e378-144">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="8e378-145">Версия CLR больше версии, которую этот отладчик заявляет для поддержки.</span><span class="sxs-lookup"><span data-stu-id="8e378-145">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="8e378-146">`pwszVersion`После этой ошибки параметру OUTPUT по-прежнему присваивается правильное значение.</span><span class="sxs-lookup"><span data-stu-id="8e378-146">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="8e378-147">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="8e378-147">E_NO_INTERFACE</span></span>|<span data-ttu-id="8e378-148">`riidProcess`Интерфейс недоступен.</span><span class="sxs-lookup"><span data-stu-id="8e378-148">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="8e378-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="8e378-149">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="8e378-150">`CLR_DEBUGGING_VERSION`Структура не имеет известного значения для `wStructVersion` .</span><span class="sxs-lookup"><span data-stu-id="8e378-150">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="8e378-151">Единственным допустимым значением в данный момент является 0.</span><span class="sxs-lookup"><span data-stu-id="8e378-151">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8e378-152">Исключения</span><span class="sxs-lookup"><span data-stu-id="8e378-152">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e378-153">Remarks</span><span class="sxs-lookup"><span data-stu-id="8e378-153">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e378-154">Требования</span><span class="sxs-lookup"><span data-stu-id="8e378-154">Requirements</span></span>  

 <span data-ttu-id="8e378-155">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e378-155">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e378-156">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e378-156">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e378-157">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e378-157">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e378-158">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e378-158">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e378-159">См. также</span><span class="sxs-lookup"><span data-stu-id="8e378-159">See also</span></span>

- [<span data-ttu-id="8e378-160">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8e378-160">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8e378-161">Отладка</span><span class="sxs-lookup"><span data-stu-id="8e378-161">Debugging</span></span>](index.md)
