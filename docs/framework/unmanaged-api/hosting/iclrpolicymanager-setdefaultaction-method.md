---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: SetDefaultAction'
title: Метод ICLRPolicyManager::SetDefaultAction
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
ms.openlocfilehash: cedf29f6217660493b151e06220158e931385d79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637369"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="03b02-103">Метод ICLRPolicyManager::SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="03b02-103">ICLRPolicyManager::SetDefaultAction Method</span></span>

<span data-ttu-id="03b02-104">Указывает действие политики, которое должна выполнять среда CLR при выполнении указанной операции.</span><span class="sxs-lookup"><span data-stu-id="03b02-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b02-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03b02-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03b02-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="03b02-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="03b02-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее действие, для которого необходимо настроить поведение среды CLR.</span><span class="sxs-lookup"><span data-stu-id="03b02-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="03b02-108">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие политики, которое должна предпринять среда CLR при `operation` возникновении.</span><span class="sxs-lookup"><span data-stu-id="03b02-108">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03b02-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="03b02-109">Return Value</span></span>  
  
|<span data-ttu-id="03b02-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03b02-110">HRESULT</span></span>|<span data-ttu-id="03b02-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="03b02-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03b02-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="03b02-112">S_OK</span></span>|<span data-ttu-id="03b02-113">`SetDefaultAction` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="03b02-113">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="03b02-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03b02-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03b02-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="03b02-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03b02-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03b02-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03b02-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="03b02-117">The call timed out.</span></span>|  
|<span data-ttu-id="03b02-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03b02-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03b02-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="03b02-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03b02-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03b02-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03b02-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="03b02-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03b02-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03b02-122">E_FAIL</span></span>|<span data-ttu-id="03b02-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="03b02-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03b02-124">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="03b02-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03b02-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03b02-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03b02-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="03b02-126">E_INVALIDARG</span></span>|<span data-ttu-id="03b02-127">Для `action` задано недопустимое `operation` значение, или для параметра было указано недопустимое `operation` .</span><span class="sxs-lookup"><span data-stu-id="03b02-127">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b02-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="03b02-128">Remarks</span></span>  

 <span data-ttu-id="03b02-129">Не все значения действий политики могут быть указаны в качестве поведения по умолчанию для операций среды CLR.</span><span class="sxs-lookup"><span data-stu-id="03b02-129">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="03b02-130">`SetDefaultAction` обычно может использоваться только для эскалации поведения.</span><span class="sxs-lookup"><span data-stu-id="03b02-130">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="03b02-131">Например, узел может указать, что прерывания потока должны быть преобразованы в грубые прерывания потока, но не могут указывать обратно.</span><span class="sxs-lookup"><span data-stu-id="03b02-131">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="03b02-132">В следующей таблице описаны допустимые `action` значения для каждого возможного `operation` значения.</span><span class="sxs-lookup"><span data-stu-id="03b02-132">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="03b02-133">Значение для `operation`</span><span class="sxs-lookup"><span data-stu-id="03b02-133">Value for `operation`</span></span>|<span data-ttu-id="03b02-134">Допустимые значения для `action`</span><span class="sxs-lookup"><span data-stu-id="03b02-134">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="03b02-135">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="03b02-135">OPR_ThreadAbort</span></span>|<span data-ttu-id="03b02-136">-Еабортсреад</span><span class="sxs-lookup"><span data-stu-id="03b02-136">-   eAbortThread</span></span><br /><span data-ttu-id="03b02-137">-Ерудеабортсреад</span><span class="sxs-lookup"><span data-stu-id="03b02-137">-   eRudeAbortThread</span></span><br /><span data-ttu-id="03b02-138">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-138">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-139">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-139">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-140">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-140">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-141">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-141">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-142">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-142">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-143">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-143">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="03b02-144">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="03b02-144">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="03b02-145">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="03b02-145">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="03b02-146">-Ерудеабортсреад</span><span class="sxs-lookup"><span data-stu-id="03b02-146">-   eRudeAbortThread</span></span><br /><span data-ttu-id="03b02-147">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-147">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-148">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-148">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-149">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-149">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-150">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-150">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-151">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-151">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-152">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-152">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="03b02-153">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="03b02-153">OPR_AppDomainUnload</span></span>|<span data-ttu-id="03b02-154">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-154">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-155">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-155">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-156">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-156">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-157">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-157">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-158">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-158">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-159">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-159">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="03b02-160">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="03b02-160">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="03b02-161">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-161">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-162">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-162">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-163">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-163">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-164">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-164">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-165">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-165">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="03b02-166">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="03b02-166">OPR_ProcessExit</span></span>|<span data-ttu-id="03b02-167">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-167">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-168">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-168">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-169">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-169">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-170">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-170">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="03b02-171">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="03b02-171">OPR_FinalizerRun</span></span>|<span data-ttu-id="03b02-172">-Еноактион</span><span class="sxs-lookup"><span data-stu-id="03b02-172">-   eNoAction</span></span><br /><span data-ttu-id="03b02-173">-Еабортсреад</span><span class="sxs-lookup"><span data-stu-id="03b02-173">-   eAbortThread</span></span><br /><span data-ttu-id="03b02-174">-Ерудеабортсреад</span><span class="sxs-lookup"><span data-stu-id="03b02-174">-   eRudeAbortThread</span></span><br /><span data-ttu-id="03b02-175">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-175">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-176">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="03b02-176">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="03b02-177">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-177">-   eExitProcess</span></span><br /><span data-ttu-id="03b02-178">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-178">-   eFastExitProcess</span></span><br /><span data-ttu-id="03b02-179">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="03b02-179">-   eRudeExitProcess</span></span><br /><span data-ttu-id="03b02-180">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="03b02-180">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03b02-181">Требования</span><span class="sxs-lookup"><span data-stu-id="03b02-181">Requirements</span></span>  

 <span data-ttu-id="03b02-182">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03b02-182">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03b02-183">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="03b02-183">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03b02-184">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03b02-184">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03b02-185">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03b02-185">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b02-186">См. также</span><span class="sxs-lookup"><span data-stu-id="03b02-186">See also</span></span>

- [<span data-ttu-id="03b02-187">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="03b02-187">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="03b02-188">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="03b02-188">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="03b02-189">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="03b02-189">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
