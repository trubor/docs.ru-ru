---
description: 'Дополнительные сведения о методе: ICLRHostBindingPolicyManager:: ModifyApplicationPolicy'
title: Метод ICLRHostBindingPolicyManager::ModifyApplicationPolicy
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: 3f7d992f4b7d24233da175814f991106bb97a937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789935"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="36e24-103">Метод ICLRHostBindingPolicyManager::ModifyApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="36e24-103">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>

<span data-ttu-id="36e24-104">Изменяет политику привязки для указанной сборки и создает новую версию политики.</span><span class="sxs-lookup"><span data-stu-id="36e24-104">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e24-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36e24-105">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36e24-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="36e24-106">Parameters</span></span>  

 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="36e24-107">окне Идентификатор сборки, которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="36e24-107">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="36e24-108">окне Новое удостоверение измененной сборки.</span><span class="sxs-lookup"><span data-stu-id="36e24-108">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="36e24-109">окне Указатель на буфер, содержащий данные политики привязки для изменяемой сборки.</span><span class="sxs-lookup"><span data-stu-id="36e24-109">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="36e24-110">окне Размер заменяемой политики привязки.</span><span class="sxs-lookup"><span data-stu-id="36e24-110">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="36e24-111">окне Логическое или сочетание значений [ехостбиндингполицимодифифлагс](ehostbindingpolicymodifyflags-enumeration.md) , указывающее на контроль перенаправления.</span><span class="sxs-lookup"><span data-stu-id="36e24-111">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="36e24-112">заполняет Указатель на буфер, содержащий новые данные политики привязки.</span><span class="sxs-lookup"><span data-stu-id="36e24-112">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="36e24-113">[вход, выход] Указатель на размер нового буфера политики привязки.</span><span class="sxs-lookup"><span data-stu-id="36e24-113">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36e24-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="36e24-114">Return Value</span></span>  
  
|<span data-ttu-id="36e24-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36e24-115">HRESULT</span></span>|<span data-ttu-id="36e24-116">Описание:</span><span class="sxs-lookup"><span data-stu-id="36e24-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36e24-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="36e24-117">S_OK</span></span>|<span data-ttu-id="36e24-118">Политика успешно изменена.</span><span class="sxs-lookup"><span data-stu-id="36e24-118">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="36e24-119">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="36e24-119">E_INVALIDARG</span></span>|<span data-ttu-id="36e24-120">`pwzSourceAssemblyIdentity` или `pwzTargetAssemblyIdentity` является пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="36e24-120">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="36e24-121">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="36e24-121">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="36e24-122">`pbNewApplicationPolicy` слишком мал.</span><span class="sxs-lookup"><span data-stu-id="36e24-122">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="36e24-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36e24-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36e24-124">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="36e24-124">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36e24-125">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36e24-125">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36e24-126">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="36e24-126">The call timed out.</span></span>|  
|<span data-ttu-id="36e24-127">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36e24-127">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36e24-128">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="36e24-128">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36e24-129">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36e24-129">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36e24-130">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="36e24-130">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36e24-131">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36e24-131">E_FAIL</span></span>|<span data-ttu-id="36e24-132">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="36e24-132">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36e24-133">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="36e24-133">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36e24-134">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36e24-134">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e24-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="36e24-135">Remarks</span></span>  

 <span data-ttu-id="36e24-136">`ModifyApplicationPolicy`Метод можно вызвать дважды.</span><span class="sxs-lookup"><span data-stu-id="36e24-136">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="36e24-137">Первый вызов должен предоставить значение NULL для `pbNewApplicationPolicy` параметра.</span><span class="sxs-lookup"><span data-stu-id="36e24-137">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="36e24-138">Этот вызов возвратит с требуемым значением для `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="36e24-138">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="36e24-139">Второй вызов должен предоставить это значение для `pcbNewAppPolicySize` и указать буфер этого размера для `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="36e24-139">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36e24-140">Требования</span><span class="sxs-lookup"><span data-stu-id="36e24-140">Requirements</span></span>  

 <span data-ttu-id="36e24-141">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36e24-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36e24-142">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="36e24-142">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36e24-143">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36e24-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36e24-144">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36e24-144">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e24-145">См. также</span><span class="sxs-lookup"><span data-stu-id="36e24-145">See also</span></span>

- [<span data-ttu-id="36e24-146">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="36e24-146">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
