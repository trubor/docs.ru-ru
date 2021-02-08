---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: Сетактиононфаилуре'
title: Метод ICLRPolicyManager::SetActionOnFailure
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 67d3ca5d7924caf0a768b4de53b4b24f1c72fa27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789805"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="ca4df-103">Метод ICLRPolicyManager::SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="ca4df-103">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="ca4df-104">Указывает действие политики, которое должна выполнять среда CLR при возникновении указанного сбоя.</span><span class="sxs-lookup"><span data-stu-id="ca4df-104">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4df-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca4df-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca4df-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca4df-106">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="ca4df-107">окне Одно из значений [еклрфаилуре](eclrfailure-enumeration.md) , указывающее тип сбоя, для которого необходимо выполнить действие.</span><span class="sxs-lookup"><span data-stu-id="ca4df-107">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="ca4df-108">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие, выполняемое в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="ca4df-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="ca4df-109">Список поддерживаемых значений см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="ca4df-109">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca4df-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ca4df-110">Return Value</span></span>  
  
|<span data-ttu-id="ca4df-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca4df-111">HRESULT</span></span>|<span data-ttu-id="ca4df-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="ca4df-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca4df-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca4df-113">S_OK</span></span>|<span data-ttu-id="ca4df-114">`SetActionOnFailure` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ca4df-114">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="ca4df-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca4df-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca4df-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ca4df-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca4df-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca4df-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca4df-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ca4df-118">The call timed out.</span></span>|  
|<span data-ttu-id="ca4df-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca4df-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca4df-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ca4df-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca4df-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca4df-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca4df-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ca4df-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca4df-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca4df-123">E_FAIL</span></span>|<span data-ttu-id="ca4df-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ca4df-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca4df-125">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ca4df-125">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca4df-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca4df-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca4df-127">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ca4df-127">E_INVALIDARG</span></span>|<span data-ttu-id="ca4df-128">Действие политики не может быть задано для указанной операции, или для операции указано недопустимое действие политики.</span><span class="sxs-lookup"><span data-stu-id="ca4df-128">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca4df-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca4df-129">Remarks</span></span>  

 <span data-ttu-id="ca4df-130">По умолчанию среда CLR создает исключение, когда не удается выделить ресурс, например память.</span><span class="sxs-lookup"><span data-stu-id="ca4df-130">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="ca4df-131">`SetActionOnFailure` позволяет узлу переопределить это поведение, указав действие политики для выполнения при сбое.</span><span class="sxs-lookup"><span data-stu-id="ca4df-131">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="ca4df-132">В следующей таблице показаны поддерживаемые сочетания значений [еклрфаилуре](eclrfailure-enumeration.md) и [еполициактион](epolicyaction-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ca4df-132">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="ca4df-133">(Префикс FAIL_ опущен из значений [еклрфаилуре](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="ca4df-133">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="ca4df-134">нонкритикалресаурце</span><span class="sxs-lookup"><span data-stu-id="ca4df-134">NonCriticalResource</span></span>|<span data-ttu-id="ca4df-135">критикалресаурце</span><span class="sxs-lookup"><span data-stu-id="ca4df-135">CriticalResource</span></span>|<span data-ttu-id="ca4df-136">фаталрунтиме</span><span class="sxs-lookup"><span data-stu-id="ca4df-136">FatalRuntime</span></span>|<span data-ttu-id="ca4df-137">орфанедлокк</span><span class="sxs-lookup"><span data-stu-id="ca4df-137">OrphanedLock</span></span>|<span data-ttu-id="ca4df-138">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="ca4df-138">StackOverflow</span></span>|<span data-ttu-id="ca4df-139">AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="ca4df-139">AccessViolation</span></span>|<span data-ttu-id="ca4df-140">кодеконтракт</span><span class="sxs-lookup"><span data-stu-id="ca4df-140">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="ca4df-141">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-141">X</span></span>|<span data-ttu-id="ca4df-142">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-142">X</span></span>||||<span data-ttu-id="ca4df-143">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-143">N/A</span></span>||  
|<span data-ttu-id="ca4df-144">есровексцептион</span><span class="sxs-lookup"><span data-stu-id="ca4df-144">eThrowException</span></span>|<span data-ttu-id="ca4df-145">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-145">X</span></span>|<span data-ttu-id="ca4df-146">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-146">X</span></span>||||<span data-ttu-id="ca4df-147">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-147">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="ca4df-148">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-148">X</span></span>|<span data-ttu-id="ca4df-149">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-149">X</span></span>||||<span data-ttu-id="ca4df-150">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-150">N/A</span></span>|<span data-ttu-id="ca4df-151">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-151">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="ca4df-152">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-152">X</span></span>|<span data-ttu-id="ca4df-153">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-153">X</span></span>||||<span data-ttu-id="ca4df-154">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-154">N/A</span></span>|<span data-ttu-id="ca4df-155">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-155">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="ca4df-156">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-156">X</span></span>|<span data-ttu-id="ca4df-157">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-157">X</span></span>||<span data-ttu-id="ca4df-158">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-158">X</span></span>||<span data-ttu-id="ca4df-159">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-159">N/A</span></span>|<span data-ttu-id="ca4df-160">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-160">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="ca4df-161">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-161">X</span></span>|<span data-ttu-id="ca4df-162">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-162">X</span></span>||<span data-ttu-id="ca4df-163">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-163">X</span></span>|<span data-ttu-id="ca4df-164">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-164">X</span></span>|<span data-ttu-id="ca4df-165">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-165">N/A</span></span>|<span data-ttu-id="ca4df-166">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-166">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="ca4df-167">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-167">X</span></span>|<span data-ttu-id="ca4df-168">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-168">X</span></span>||<span data-ttu-id="ca4df-169">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-169">X</span></span>|<span data-ttu-id="ca4df-170">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-170">X</span></span>|<span data-ttu-id="ca4df-171">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-171">N/A</span></span>|<span data-ttu-id="ca4df-172">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-172">X</span></span>|  
|<span data-ttu-id="ca4df-173">ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="ca4df-173">eFastExitProcess</span></span>|<span data-ttu-id="ca4df-174">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-174">X</span></span>|<span data-ttu-id="ca4df-175">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-175">X</span></span>||<span data-ttu-id="ca4df-176">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-176">X</span></span>|<span data-ttu-id="ca4df-177">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-177">X</span></span>|<span data-ttu-id="ca4df-178">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-178">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="ca4df-179">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-179">X</span></span>|<span data-ttu-id="ca4df-180">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-180">X</span></span>|<span data-ttu-id="ca4df-181">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-181">X</span></span>|<span data-ttu-id="ca4df-182">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-182">X</span></span>|<span data-ttu-id="ca4df-183">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-183">X</span></span>|<span data-ttu-id="ca4df-184">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-184">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="ca4df-185">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-185">X</span></span>|<span data-ttu-id="ca4df-186">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-186">X</span></span>|<span data-ttu-id="ca4df-187">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-187">X</span></span>|<span data-ttu-id="ca4df-188">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-188">X</span></span>|<span data-ttu-id="ca4df-189">X</span><span class="sxs-lookup"><span data-stu-id="ca4df-189">X</span></span>|<span data-ttu-id="ca4df-190">н/д</span><span class="sxs-lookup"><span data-stu-id="ca4df-190">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="ca4df-191">Требования</span><span class="sxs-lookup"><span data-stu-id="ca4df-191">Requirements</span></span>  

 <span data-ttu-id="ca4df-192">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4df-192">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4df-193">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca4df-193">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca4df-194">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca4df-194">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca4df-195">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4df-195">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4df-196">См. также</span><span class="sxs-lookup"><span data-stu-id="ca4df-196">See also</span></span>

- [<span data-ttu-id="ca4df-197">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="ca4df-197">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="ca4df-198">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="ca4df-198">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ca4df-199">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="ca4df-199">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ca4df-200">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ca4df-200">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
