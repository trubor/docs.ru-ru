---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: Имперсонателогжедонусер'
title: Метод IHostSecurityManager::ImpersonateLoggedOnUser
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: 7b77e0a163551a48629898b1311fc19ba815aaf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671598"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="facc5-103">Метод IHostSecurityManager::ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="facc5-103">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>

<span data-ttu-id="facc5-104">Запрашивает выполнение кода с использованием учетных данных удостоверения текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="facc5-104">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facc5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="facc5-105">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="facc5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="facc5-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="facc5-107">окне Маркер, представляющий учетные данные пользователя, для которого необходимо выполнить олицетворение.</span><span class="sxs-lookup"><span data-stu-id="facc5-107">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="facc5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="facc5-108">Return Value</span></span>  
  
|<span data-ttu-id="facc5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="facc5-109">HRESULT</span></span>|<span data-ttu-id="facc5-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="facc5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="facc5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="facc5-111">S_OK</span></span>|<span data-ttu-id="facc5-112">`ImpersonateLoggedOnUser` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="facc5-112">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="facc5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="facc5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="facc5-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="facc5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="facc5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="facc5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="facc5-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="facc5-116">The call timed out.</span></span>|  
|<span data-ttu-id="facc5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="facc5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="facc5-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="facc5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="facc5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="facc5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="facc5-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="facc5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="facc5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="facc5-121">E_FAIL</span></span>|<span data-ttu-id="facc5-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="facc5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="facc5-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="facc5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="facc5-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="facc5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="facc5-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="facc5-125">Remarks</span></span>  

 <span data-ttu-id="facc5-126">Вызов `LogonUser` или связанная функция Win32 для получения маркера учетных данных удостоверения текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="facc5-126">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="facc5-127">`HANDLE`Тип не совместим с COM, то есть его размер зависит от операционной системы и требует настраиваемого маршалирования.</span><span class="sxs-lookup"><span data-stu-id="facc5-127">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="facc5-128">Таким же маркер предназначен только для использования внутри процесса между средой CLR и узлом.</span><span class="sxs-lookup"><span data-stu-id="facc5-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facc5-129">Требования</span><span class="sxs-lookup"><span data-stu-id="facc5-129">Requirements</span></span>  

 <span data-ttu-id="facc5-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facc5-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facc5-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="facc5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="facc5-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="facc5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="facc5-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facc5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facc5-134">См. также</span><span class="sxs-lookup"><span data-stu-id="facc5-134">See also</span></span>

- [<span data-ttu-id="facc5-135">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="facc5-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="facc5-136">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="facc5-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="facc5-137">Метод RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="facc5-137">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)
