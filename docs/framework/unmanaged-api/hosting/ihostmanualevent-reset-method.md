---
description: 'Дополнительные сведения о методе: Ихостмануалевент:: Reset'
title: Метод IHostManualEvent::Reset
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 84debb8b37c2cdfdbf294bff6736b081424f9e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708077"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="d0b0c-103">Метод IHostManualEvent::Reset</span><span class="sxs-lookup"><span data-stu-id="d0b0c-103">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="d0b0c-104">Сбрасывает текущий экземпляр [ихостмануалевент](ihostmanualevent-interface.md) в несигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-104">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b0c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d0b0c-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d0b0c-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d0b0c-106">Return Value</span></span>  
  
|<span data-ttu-id="d0b0c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0b0c-107">HRESULT</span></span>|<span data-ttu-id="d0b0c-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="d0b0c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0b0c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0b0c-109">S_OK</span></span>|<span data-ttu-id="d0b0c-110">`Reset` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-110">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="d0b0c-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0b0c-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0b0c-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0b0c-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0b0c-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0b0c-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-114">The call timed out.</span></span>|  
|<span data-ttu-id="d0b0c-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0b0c-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0b0c-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0b0c-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0b0c-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0b0c-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0b0c-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0b0c-119">E_FAIL</span></span>|<span data-ttu-id="d0b0c-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0b0c-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0b0c-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0b0c-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0b0c-123">Требования</span><span class="sxs-lookup"><span data-stu-id="d0b0c-123">Requirements</span></span>  

 <span data-ttu-id="d0b0c-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b0c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b0c-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0b0c-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0b0c-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0b0c-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0b0c-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b0c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b0c-128">См. также</span><span class="sxs-lookup"><span data-stu-id="d0b0c-128">See also</span></span>

- [<span data-ttu-id="d0b0c-129">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d0b0c-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d0b0c-130">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="d0b0c-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d0b0c-131">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="d0b0c-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d0b0c-132">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="d0b0c-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="d0b0c-133">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d0b0c-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
