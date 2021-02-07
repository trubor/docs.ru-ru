---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: Сетактиононтимеаут'
title: Метод ICLRPolicyManager::SetActionOnTimeout
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: d682acd49bdc4fa0f8c58a1300e2215816fe2718
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689031"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="fce1f-103">Метод ICLRPolicyManager::SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="fce1f-103">ICLRPolicyManager::SetActionOnTimeout Method</span></span>

<span data-ttu-id="fce1f-104">Указывает действие политики, которое должна выполнять среда CLR при истечении времени ожидания указанной операции.</span><span class="sxs-lookup"><span data-stu-id="fce1f-104">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce1f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fce1f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fce1f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fce1f-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="fce1f-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее операцию, для которой необходимо указать действие времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="fce1f-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="fce1f-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="fce1f-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="fce1f-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="fce1f-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="fce1f-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="fce1f-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="fce1f-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fce1f-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="fce1f-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fce1f-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="fce1f-113">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие политики, выполняемое при истечении времени ожидания операции.</span><span class="sxs-lookup"><span data-stu-id="fce1f-113">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fce1f-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fce1f-114">Return Value</span></span>  
  
|<span data-ttu-id="fce1f-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fce1f-115">HRESULT</span></span>|<span data-ttu-id="fce1f-116">Описание:</span><span class="sxs-lookup"><span data-stu-id="fce1f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fce1f-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="fce1f-117">S_OK</span></span>|<span data-ttu-id="fce1f-118">`SetActionOnTimeout` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="fce1f-118">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="fce1f-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fce1f-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fce1f-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="fce1f-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fce1f-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fce1f-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fce1f-122">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="fce1f-122">The call timed out.</span></span>|  
|<span data-ttu-id="fce1f-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce1f-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fce1f-124">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="fce1f-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fce1f-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fce1f-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fce1f-126">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="fce1f-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fce1f-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fce1f-127">E_FAIL</span></span>|<span data-ttu-id="fce1f-128">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="fce1f-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fce1f-129">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="fce1f-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fce1f-130">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fce1f-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fce1f-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fce1f-131">E_INVALIDARG</span></span>|<span data-ttu-id="fce1f-132">Не удается задать время ожидания для указанного `operation` или указано недопустимое значение для `operation` .</span><span class="sxs-lookup"><span data-stu-id="fce1f-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fce1f-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="fce1f-133">Remarks</span></span>  

 <span data-ttu-id="fce1f-134">Значение времени ожидания может быть либо временем ожидания по умолчанию, установленным средой CLR, либо значением, заданным узлом при вызове метода [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fce1f-134">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="fce1f-135">Не все значения действий политики могут быть указаны в качестве поведения времени ожидания для операций среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fce1f-135">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="fce1f-136">`SetActionOnTimeout` обычно используется только для эскалации поведения.</span><span class="sxs-lookup"><span data-stu-id="fce1f-136">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="fce1f-137">Например, узел может указать, что прерывания потока должны быть преобразованы в грубые прерывания потока, но не могут указывать обратно.</span><span class="sxs-lookup"><span data-stu-id="fce1f-137">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="fce1f-138">В следующей таблице описаны допустимые `action` значения для допустимых `operation` значений.</span><span class="sxs-lookup"><span data-stu-id="fce1f-138">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="fce1f-139">Значение для `operation`</span><span class="sxs-lookup"><span data-stu-id="fce1f-139">Value for `operation`</span></span>|<span data-ttu-id="fce1f-140">Допустимые значения для `action`</span><span class="sxs-lookup"><span data-stu-id="fce1f-140">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="fce1f-141">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fce1f-141">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="fce1f-142">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="fce1f-142">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="fce1f-143">-Ерудеабортсреад</span><span class="sxs-lookup"><span data-stu-id="fce1f-143">-   eRudeAbortThread</span></span><br /><span data-ttu-id="fce1f-144">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="fce1f-144">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fce1f-145">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="fce1f-145">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fce1f-146">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-146">-   eExitProcess</span></span><br /><span data-ttu-id="fce1f-147">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-147">-   eFastExitProcess</span></span><br /><span data-ttu-id="fce1f-148">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-148">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fce1f-149">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="fce1f-149">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fce1f-150">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="fce1f-150">OPR_AppDomainUnload</span></span>|<span data-ttu-id="fce1f-151">-Еунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="fce1f-151">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="fce1f-152">-Ерудеунлоадаппдомаин</span><span class="sxs-lookup"><span data-stu-id="fce1f-152">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="fce1f-153">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-153">-   eExitProcess</span></span><br /><span data-ttu-id="fce1f-154">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-154">-   eFastExitProcess</span></span><br /><span data-ttu-id="fce1f-155">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-155">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fce1f-156">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="fce1f-156">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="fce1f-157">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="fce1f-157">OPR_ProcessExit</span></span>|<span data-ttu-id="fce1f-158">-Икситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-158">-   eExitProcess</span></span><br /><span data-ttu-id="fce1f-159">-Ефастекситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-159">-   eFastExitProcess</span></span><br /><span data-ttu-id="fce1f-160">-Ерудикситпроцесс</span><span class="sxs-lookup"><span data-stu-id="fce1f-160">-   eRudeExitProcess</span></span><br /><span data-ttu-id="fce1f-161">-Едисаблерунтиме</span><span class="sxs-lookup"><span data-stu-id="fce1f-161">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fce1f-162">Требования</span><span class="sxs-lookup"><span data-stu-id="fce1f-162">Requirements</span></span>  

 <span data-ttu-id="fce1f-163">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fce1f-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fce1f-164">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fce1f-164">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fce1f-165">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fce1f-165">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fce1f-166">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fce1f-166">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce1f-167">См. также</span><span class="sxs-lookup"><span data-stu-id="fce1f-167">See also</span></span>

- [<span data-ttu-id="fce1f-168">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="fce1f-168">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="fce1f-169">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="fce1f-169">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="fce1f-170">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="fce1f-170">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="fce1f-171">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="fce1f-171">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
