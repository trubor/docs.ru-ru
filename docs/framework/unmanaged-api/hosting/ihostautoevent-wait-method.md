---
description: 'Дополнительные сведения о методе: Ихостаутоевент:: wait'
title: Метод IHostAutoEvent::Wait
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 0b75b44075dda46a3d84850cebd6b8f3851b055c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789480"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="a8a6d-103">Метод IHostAutoEvent::Wait</span><span class="sxs-lookup"><span data-stu-id="a8a6d-103">IHostAutoEvent::Wait Method</span></span>

<span data-ttu-id="a8a6d-104">Приводит к тому, что текущий экземпляр [ихостаутоевент](ihostautoevent-interface.md) ожидает его признания или истечения указанного периода времени.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-104">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a6d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8a6d-105">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8a6d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a8a6d-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="a8a6d-107">окне Число миллисекунд, в течение которых текущий `IHostAutoEvent` экземпляр должен ожидать перед возвратом, если ни один из потоков или волокон не получает владение.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-107">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="a8a6d-108">окне Одно из значений [WAIT_OPTION](wait-option-enumeration.md) , определяющее действие, которое должен выполнить узел, если эта операция блокируется.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8a6d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a8a6d-109">Return Value</span></span>  
  
|<span data-ttu-id="a8a6d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8a6d-110">HRESULT</span></span>|<span data-ttu-id="a8a6d-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="a8a6d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8a6d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8a6d-112">S_OK</span></span>|<span data-ttu-id="a8a6d-113">`Wait` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-113">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="a8a6d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a8a6d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a8a6d-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a8a6d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a8a6d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a8a6d-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-117">The call timed out.</span></span>|  
|<span data-ttu-id="a8a6d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a8a6d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a8a6d-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a8a6d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a8a6d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a8a6d-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a8a6d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a8a6d-122">E_FAIL</span></span>|<span data-ttu-id="a8a6d-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a8a6d-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a8a6d-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a8a6d-126">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="a8a6d-126">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="a8a6d-127">Узел обнаружил взаимоблокировку в течение интервала ожидания и выбрал событие, представленное текущим `IHostAutoEvent` экземпляром в качестве жертвы взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="a8a6d-127">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8a6d-128">Требования</span><span class="sxs-lookup"><span data-stu-id="a8a6d-128">Requirements</span></span>  

 <span data-ttu-id="a8a6d-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a6d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a6d-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8a6d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8a6d-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8a6d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8a6d-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a6d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a6d-133">См. также</span><span class="sxs-lookup"><span data-stu-id="a8a6d-133">See also</span></span>

- [<span data-ttu-id="a8a6d-134">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a8a6d-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a8a6d-135">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="a8a6d-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="a8a6d-136">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="a8a6d-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="a8a6d-137">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a8a6d-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
