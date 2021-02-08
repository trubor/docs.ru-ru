---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: Креатемануалевент'
title: Метод IHostSyncManager::CreateManualEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 300d6cbf9555eb331a470767cdfb2745da300bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784799"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="37aad-103">Метод IHostSyncManager::CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="37aad-103">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="37aad-104">Создает объект события ручного сброса.</span><span class="sxs-lookup"><span data-stu-id="37aad-104">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37aad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37aad-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37aad-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="37aad-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="37aad-107">[in] `true` , если объект получает сигнал; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="37aad-107">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="37aad-108">заполняет Указатель на адрес экземпляра [ихостмануалевент](ihostmanualevent-interface.md) или значение null, если не удалось создать событие.</span><span class="sxs-lookup"><span data-stu-id="37aad-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37aad-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="37aad-109">Return Value</span></span>  
  
|<span data-ttu-id="37aad-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37aad-110">HRESULT</span></span>|<span data-ttu-id="37aad-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="37aad-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37aad-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="37aad-112">S_OK</span></span>|<span data-ttu-id="37aad-113">`CreateManualEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="37aad-113">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="37aad-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37aad-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37aad-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="37aad-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37aad-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37aad-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37aad-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="37aad-117">The call timed out.</span></span>|  
|<span data-ttu-id="37aad-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37aad-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37aad-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="37aad-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37aad-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37aad-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37aad-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="37aad-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37aad-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37aad-122">E_FAIL</span></span>|<span data-ttu-id="37aad-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="37aad-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37aad-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="37aad-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37aad-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37aad-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37aad-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="37aad-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="37aad-127">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="37aad-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37aad-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="37aad-128">Remarks</span></span>  

 <span data-ttu-id="37aad-129">`CreateManualEvent` создает `IHostManualEvent` объект события ручного сброса, для которого требуется вызов метода [ихостмануалевент:: Reset](ihostmanualevent-reset-method.md) , чтобы установить несигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="37aad-129">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="37aad-130">`CreateManualEvent` отражает функцию Win32 `CreateEvent` со значением, `true` указанным для `bManualReset` параметра.</span><span class="sxs-lookup"><span data-stu-id="37aad-130">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37aad-131">Требования</span><span class="sxs-lookup"><span data-stu-id="37aad-131">Requirements</span></span>  

 <span data-ttu-id="37aad-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37aad-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37aad-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37aad-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37aad-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37aad-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37aad-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37aad-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37aad-136">См. также</span><span class="sxs-lookup"><span data-stu-id="37aad-136">See also</span></span>

- [<span data-ttu-id="37aad-137">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="37aad-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="37aad-138">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="37aad-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="37aad-139">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="37aad-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
