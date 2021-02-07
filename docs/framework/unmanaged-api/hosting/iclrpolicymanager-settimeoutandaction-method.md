---
description: 'Дополнительные сведения о методе: ICLRPolicyManager:: SetTimeoutAndAction'
title: Метод ICLRPolicyManager::SetTimeoutAndAction
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: c91d43cce381bef804b30e9e1dcb50574ddcd1b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716579"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="0ca53-103">Метод ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="0ca53-103">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>

<span data-ttu-id="0ca53-104">Задает значение времени ожидания для указанной операции и указывает действие политики, которое должна выполнять среда CLR при выполнении операции.</span><span class="sxs-lookup"><span data-stu-id="0ca53-104">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca53-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ca53-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ca53-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ca53-106">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="0ca53-107">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее операцию, для которой необходимо задать время ожидания и политику `action` .</span><span class="sxs-lookup"><span data-stu-id="0ca53-107">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="0ca53-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="0ca53-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="0ca53-109">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="0ca53-109">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="0ca53-110">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="0ca53-110">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="0ca53-111">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="0ca53-111">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="0ca53-112">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="0ca53-112">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="0ca53-113">окне Новое значение времени ожидания в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="0ca53-113">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="0ca53-114">Значение бесконечности приводит к тому, что `operation` время ожидания никогда не истекает.</span><span class="sxs-lookup"><span data-stu-id="0ca53-114">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="0ca53-115">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие политики, ВЫПОЛНЯЕМое средой CLR при `operation` возникновении.</span><span class="sxs-lookup"><span data-stu-id="0ca53-115">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ca53-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ca53-116">Return Value</span></span>  
  
|<span data-ttu-id="0ca53-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ca53-117">HRESULT</span></span>|<span data-ttu-id="0ca53-118">Описание:</span><span class="sxs-lookup"><span data-stu-id="0ca53-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ca53-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ca53-119">S_OK</span></span>|<span data-ttu-id="0ca53-120">`SetTimeoutAndAction` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="0ca53-120">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="0ca53-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ca53-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ca53-122">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0ca53-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ca53-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ca53-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ca53-124">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="0ca53-124">The call timed out.</span></span>|  
|<span data-ttu-id="0ca53-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ca53-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ca53-126">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="0ca53-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ca53-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ca53-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ca53-128">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="0ca53-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ca53-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ca53-129">E_FAIL</span></span>|<span data-ttu-id="0ca53-130">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0ca53-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ca53-131">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0ca53-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ca53-132">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ca53-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ca53-133">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0ca53-133">E_INVALIDARG</span></span>|<span data-ttu-id="0ca53-134">Не удается задать время ожидания для указанного `operation` или указано недопустимое значение для `action` .</span><span class="sxs-lookup"><span data-stu-id="0ca53-134">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca53-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="0ca53-135">Remarks</span></span>  

 <span data-ttu-id="0ca53-136">`SetTimeoutAndAction` Инкапсулирует возможности методов [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) и [ICLRPolicyManager:: сетактиононтимеаут](iclrpolicymanager-setactionontimeout-method.md) , и их можно вызывать вместо последовательных вызовов этих двух методов.</span><span class="sxs-lookup"><span data-stu-id="0ca53-136">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0ca53-137">Не все значения действий политики могут быть указаны в качестве поведения времени ожидания для операций среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0ca53-137">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="0ca53-138">Допустимые значения см. в подразделах "Примечания" для этих двух методов.</span><span class="sxs-lookup"><span data-stu-id="0ca53-138">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca53-139">Требования</span><span class="sxs-lookup"><span data-stu-id="0ca53-139">Requirements</span></span>  

 <span data-ttu-id="0ca53-140">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca53-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca53-141">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ca53-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ca53-142">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ca53-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca53-143">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca53-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca53-144">См. также</span><span class="sxs-lookup"><span data-stu-id="0ca53-144">See also</span></span>

- [<span data-ttu-id="0ca53-145">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="0ca53-145">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="0ca53-146">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="0ca53-146">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="0ca53-147">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0ca53-147">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="0ca53-148">Метод SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="0ca53-148">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="0ca53-149">ICLRPolicyManager:: SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="0ca53-149">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
