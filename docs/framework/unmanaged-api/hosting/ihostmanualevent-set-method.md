---
description: 'Дополнительные сведения о методе: Ихостмануалевент:: Set'
title: Метод IHostManualEvent::Set
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: e2de1fde2f8c0f512733ecde43d5240a94f84264
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707934"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="1d1a2-103">Метод IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="1d1a2-103">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="1d1a2-104">Устанавливает для текущего экземпляра [ихостмануалевент](ihostmanualevent-interface.md) сигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-104">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d1a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1d1a2-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1d1a2-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1d1a2-106">Return Value</span></span>  
  
|<span data-ttu-id="1d1a2-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d1a2-107">HRESULT</span></span>|<span data-ttu-id="1d1a2-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="1d1a2-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d1a2-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d1a2-109">S_OK</span></span>|<span data-ttu-id="1d1a2-110">`Set` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="1d1a2-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d1a2-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d1a2-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d1a2-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d1a2-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d1a2-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-114">The call timed out.</span></span>|  
|<span data-ttu-id="1d1a2-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d1a2-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d1a2-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d1a2-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d1a2-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d1a2-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d1a2-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d1a2-119">E_FAIL</span></span>|<span data-ttu-id="1d1a2-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d1a2-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d1a2-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d1a2-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d1a2-123">Требования</span><span class="sxs-lookup"><span data-stu-id="1d1a2-123">Requirements</span></span>  

 <span data-ttu-id="1d1a2-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d1a2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d1a2-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1d1a2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d1a2-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d1a2-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d1a2-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d1a2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1a2-128">См. также</span><span class="sxs-lookup"><span data-stu-id="1d1a2-128">See also</span></span>

- [<span data-ttu-id="1d1a2-129">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="1d1a2-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1d1a2-130">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="1d1a2-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="1d1a2-131">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="1d1a2-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="1d1a2-132">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="1d1a2-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="1d1a2-133">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="1d1a2-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
