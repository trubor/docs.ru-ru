---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: RevertToSelf'
title: Метод IHostSecurityManager::RevertToSelf
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: f3488653bcb498c7521de0e368b33bc444967f21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671507"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="cb985-103">Метод IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="cb985-103">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="cb985-104">Завершает олицетворение текущего удостоверения пользователя и возвращает исходный маркер потока.</span><span class="sxs-lookup"><span data-stu-id="cb985-104">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb985-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb985-105">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cb985-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cb985-106">Return Value</span></span>  
  
|<span data-ttu-id="cb985-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb985-107">HRESULT</span></span>|<span data-ttu-id="cb985-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="cb985-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb985-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb985-109">S_OK</span></span>|<span data-ttu-id="cb985-110">`RevertToSelf` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="cb985-110">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="cb985-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb985-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb985-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cb985-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb985-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb985-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb985-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cb985-114">The call timed out.</span></span>|  
|<span data-ttu-id="cb985-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb985-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb985-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cb985-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb985-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb985-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb985-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cb985-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb985-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb985-119">E_FAIL</span></span>|<span data-ttu-id="cb985-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cb985-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb985-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cb985-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb985-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb985-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb985-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb985-123">Remarks</span></span>  

 <span data-ttu-id="cb985-124">`RevertToSelf` метод вызывается для возврата к исходному маркеру потока после предыдущего вызова метода [имперсонателогжедонусер](ihostsecuritymanager-impersonateloggedonuser-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cb985-124">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb985-125">Требования</span><span class="sxs-lookup"><span data-stu-id="cb985-125">Requirements</span></span>  

 <span data-ttu-id="cb985-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb985-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb985-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb985-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb985-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb985-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb985-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb985-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb985-130">См. также</span><span class="sxs-lookup"><span data-stu-id="cb985-130">See also</span></span>

- [<span data-ttu-id="cb985-131">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="cb985-131">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="cb985-132">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="cb985-132">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="cb985-133">Метод ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="cb985-133">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
