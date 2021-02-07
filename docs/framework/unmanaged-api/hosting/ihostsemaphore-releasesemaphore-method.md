---
description: 'Дополнительные сведения о методе: IHostSemaphore:: ReleaseSemaphore'
title: Метод IHostSemaphore::ReleaseSemaphore
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
ms.openlocfilehash: 368dc5ebe3017e03c0d6e8c57d0f122bc48d439f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707451"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="d2bcd-103">Метод IHostSemaphore::ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="d2bcd-103">IHostSemaphore::ReleaseSemaphore Method</span></span>

<span data-ttu-id="d2bcd-104">Увеличивает количество текущего экземпляра [IHostSemaphore](ihostsemaphore-interface.md) на указанный объем.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-104">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2bcd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2bcd-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2bcd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2bcd-106">Parameters</span></span>  

 `lReleaseCount`  
 <span data-ttu-id="d2bcd-107">окне Величина, на которую увеличивается количество текущего `IHostSemaphore` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-107">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="d2bcd-108">Это значение должно быть больше нуля.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-108">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="d2bcd-109">заполняет Указатель на предыдущее число или значение null, если для вызывающего объекта не требуется предыдущее число.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-109">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2bcd-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d2bcd-110">Return Value</span></span>  
  
|<span data-ttu-id="d2bcd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2bcd-111">HRESULT</span></span>|<span data-ttu-id="d2bcd-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="d2bcd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2bcd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2bcd-113">S_OK</span></span>|<span data-ttu-id="d2bcd-114">`ReleaseSemaphore` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-114">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="d2bcd-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2bcd-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2bcd-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2bcd-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2bcd-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2bcd-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-118">The call timed out.</span></span>|  
|<span data-ttu-id="d2bcd-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2bcd-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2bcd-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2bcd-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2bcd-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2bcd-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2bcd-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2bcd-123">E_FAIL</span></span>|<span data-ttu-id="d2bcd-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2bcd-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2bcd-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2bcd-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2bcd-127">Remarks</span></span>  

 <span data-ttu-id="d2bcd-128">Среда CLR обычно вызывает `ReleaseSemaphore` для уведомления узла о завершении работы с ресурсом, передавая значение 1 для `lReleaseCount` параметра.</span><span class="sxs-lookup"><span data-stu-id="d2bcd-128">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2bcd-129">Требования</span><span class="sxs-lookup"><span data-stu-id="d2bcd-129">Requirements</span></span>  

 <span data-ttu-id="d2bcd-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2bcd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2bcd-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2bcd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2bcd-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2bcd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2bcd-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2bcd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2bcd-134">См. также</span><span class="sxs-lookup"><span data-stu-id="d2bcd-134">See also</span></span>

- [<span data-ttu-id="d2bcd-135">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d2bcd-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d2bcd-136">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="d2bcd-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d2bcd-137">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="d2bcd-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d2bcd-138">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="d2bcd-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="d2bcd-139">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d2bcd-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
