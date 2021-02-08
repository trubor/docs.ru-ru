---
description: 'Дополнительные сведения о методе: ICLRHostBindingPolicyManager:: EvaluatePolicy'
title: Метод ICLRHostBindingPolicyManager::EvaluatePolicy
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: e92126a8c12d03ee21e4867754b1a418ef11d463
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789974"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="0a240-103">Метод ICLRHostBindingPolicyManager::EvaluatePolicy</span><span class="sxs-lookup"><span data-stu-id="0a240-103">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>

<span data-ttu-id="0a240-104">Оценивает политику привязки от имени узла.</span><span class="sxs-lookup"><span data-stu-id="0a240-104">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a240-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a240-105">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a240-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0a240-106">Parameters</span></span>  

 `pwzReferenceIdentity`  
 <span data-ttu-id="0a240-107">окне Ссылка на сборку перед вычислением политики.</span><span class="sxs-lookup"><span data-stu-id="0a240-107">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="0a240-108">окне Указатель на буфер, содержащий данные политики.</span><span class="sxs-lookup"><span data-stu-id="0a240-108">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="0a240-109">окне Размер `pbApplicationPolicy` буфера.</span><span class="sxs-lookup"><span data-stu-id="0a240-109">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="0a240-110">заполняет Ссылка на сборку после вычисления новых данных политики.</span><span class="sxs-lookup"><span data-stu-id="0a240-110">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="0a240-111">[вход, выход] Указатель на размер буфера ссылки идентификации сборки после вычисления новых данных политики.</span><span class="sxs-lookup"><span data-stu-id="0a240-111">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="0a240-112">заполняет Указатель на логическое или сочетание значений [EBindPolicyLevels](ebindpolicylevels-enumeration.md) , указывающих, какие политики были применены.</span><span class="sxs-lookup"><span data-stu-id="0a240-112">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a240-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0a240-113">Return Value</span></span>  
  
|<span data-ttu-id="0a240-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a240-114">HRESULT</span></span>|<span data-ttu-id="0a240-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="0a240-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a240-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a240-116">S_OK</span></span>|<span data-ttu-id="0a240-117">Оценка успешно завершена.</span><span class="sxs-lookup"><span data-stu-id="0a240-117">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="0a240-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a240-118">E_INVALIDARG</span></span>|<span data-ttu-id="0a240-119">Либо `pwzReferenceIdentity` `pbApplicationPolicy` является пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="0a240-119">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="0a240-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="0a240-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="0a240-121">`cbAppPolicySize` слишком мал.</span><span class="sxs-lookup"><span data-stu-id="0a240-121">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="0a240-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a240-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a240-123">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0a240-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a240-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a240-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a240-125">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="0a240-125">The call timed out.</span></span>|  
|<span data-ttu-id="0a240-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a240-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a240-127">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="0a240-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a240-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a240-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a240-129">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="0a240-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a240-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a240-130">E_FAIL</span></span>|<span data-ttu-id="0a240-131">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0a240-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a240-132">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0a240-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a240-133">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a240-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a240-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a240-134">Remarks</span></span>  

 <span data-ttu-id="0a240-135">`EvaluatePolicy`Метод позволяет основному приложению влиять на политику привязки, чтобы обеспечить соответствие требованиям к версии сборки, относящейся к конкретному узлу.</span><span class="sxs-lookup"><span data-stu-id="0a240-135">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="0a240-136">Сам модуль политики остается внутри среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0a240-136">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a240-137">Требования</span><span class="sxs-lookup"><span data-stu-id="0a240-137">Requirements</span></span>  

 <span data-ttu-id="0a240-138">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a240-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a240-139">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a240-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a240-140">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a240-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a240-141">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a240-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a240-142">См. также</span><span class="sxs-lookup"><span data-stu-id="0a240-142">See also</span></span>

- [<span data-ttu-id="0a240-143">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0a240-143">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
