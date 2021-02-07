---
description: 'Дополнительные сведения о методе: Ихостмануалевент:: wait'
title: Метод IHostManualEvent::Wait
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: f9e681e5075f1de34dc45ed2b2485a0e1269cb11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707873"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="ecc62-103">Метод IHostManualEvent::Wait</span><span class="sxs-lookup"><span data-stu-id="ecc62-103">IHostManualEvent::Wait Method</span></span>

<span data-ttu-id="ecc62-104">Заставляет текущий экземпляр [ихостмануалевент](ihostmanualevent-interface.md) ожидать его признания или истечения указанного времени.</span><span class="sxs-lookup"><span data-stu-id="ecc62-104">Causes the current [IHostManualEvent](ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc62-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ecc62-105">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc62-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ecc62-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="ecc62-107">окне Число миллисекунд ожидания перед возвратом, если текущий `IHostManualEvent` экземпляр не принадлежит.</span><span class="sxs-lookup"><span data-stu-id="ecc62-107">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="ecc62-108">окне Одно из значений [WAIT_OPTION](wait-option-enumeration.md) , указывающее действие, которое должен выполнить узел, если эта операция блокируется.</span><span class="sxs-lookup"><span data-stu-id="ecc62-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecc62-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ecc62-109">Return Value</span></span>  
  
|<span data-ttu-id="ecc62-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecc62-110">HRESULT</span></span>|<span data-ttu-id="ecc62-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="ecc62-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecc62-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecc62-112">S_OK</span></span>|<span data-ttu-id="ecc62-113">`Wait` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ecc62-113">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="ecc62-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecc62-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecc62-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ecc62-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecc62-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecc62-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecc62-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ecc62-117">The call timed out.</span></span>|  
|<span data-ttu-id="ecc62-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecc62-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecc62-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ecc62-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecc62-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecc62-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecc62-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ecc62-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecc62-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecc62-122">E_FAIL</span></span>|<span data-ttu-id="ecc62-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ecc62-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecc62-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ecc62-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecc62-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecc62-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecc62-126">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="ecc62-126">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="ecc62-127">Узел обнаружил взаимоблокировку в течение интервала ожидания и выбрал текущий экземпляр в `IHostManualEvent` качестве жертвы взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="ecc62-127">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecc62-128">Требования</span><span class="sxs-lookup"><span data-stu-id="ecc62-128">Requirements</span></span>  

 <span data-ttu-id="ecc62-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc62-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc62-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecc62-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecc62-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecc62-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc62-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc62-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc62-133">См. также</span><span class="sxs-lookup"><span data-stu-id="ecc62-133">See also</span></span>

- [<span data-ttu-id="ecc62-134">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="ecc62-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="ecc62-135">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="ecc62-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="ecc62-136">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="ecc62-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="ecc62-137">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="ecc62-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="ecc62-138">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="ecc62-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
