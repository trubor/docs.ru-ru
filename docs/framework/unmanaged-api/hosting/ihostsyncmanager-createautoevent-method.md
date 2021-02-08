---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: Креатеаутоевент'
title: Метод IHostSyncManager::CreateAutoEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: 69767f1e01ead93c874eecf01c3167a5dc0e4b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784851"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="c1a78-103">Метод IHostSyncManager::CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="c1a78-103">IHostSyncManager::CreateAutoEvent Method</span></span>

<span data-ttu-id="c1a78-104">Создает объект события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="c1a78-104">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c1a78-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a78-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c1a78-106">Parameters</span></span>  

 `ppEvent`  
 <span data-ttu-id="c1a78-107">заполняет Указатель на адрес экземпляра [ихостаутоевент](ihostautoevent-interface.md) , реализуемого узлом, или значение null, если не удалось создать объект события.</span><span class="sxs-lookup"><span data-stu-id="c1a78-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1a78-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c1a78-108">Return Value</span></span>  
  
|<span data-ttu-id="c1a78-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1a78-109">HRESULT</span></span>|<span data-ttu-id="c1a78-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="c1a78-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1a78-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1a78-111">S_OK</span></span>|<span data-ttu-id="c1a78-112">`CreateAutoEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="c1a78-112">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c1a78-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1a78-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1a78-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="c1a78-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1a78-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1a78-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1a78-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="c1a78-116">The call timed out.</span></span>|  
|<span data-ttu-id="c1a78-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1a78-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1a78-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="c1a78-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1a78-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1a78-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1a78-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="c1a78-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1a78-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1a78-121">E_FAIL</span></span>|<span data-ttu-id="c1a78-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="c1a78-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1a78-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="c1a78-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1a78-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1a78-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1a78-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c1a78-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c1a78-126">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="c1a78-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a78-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="c1a78-127">Remarks</span></span>  

 <span data-ttu-id="c1a78-128">`CreateAutoEvent` Создает объект автоматического события, состояние которого автоматически меняется на несигнальное после освобождения ожидающего потока.</span><span class="sxs-lookup"><span data-stu-id="c1a78-128">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="c1a78-129">Этот метод отражает функцию Win32 `CreateEvent` со значением, `false` указанным для `bManualReset` параметра</span><span class="sxs-lookup"><span data-stu-id="c1a78-129">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a78-130">Требования</span><span class="sxs-lookup"><span data-stu-id="c1a78-130">Requirements</span></span>  

 <span data-ttu-id="c1a78-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a78-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a78-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c1a78-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1a78-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1a78-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1a78-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a78-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a78-135">См. также</span><span class="sxs-lookup"><span data-stu-id="c1a78-135">See also</span></span>

- [<span data-ttu-id="c1a78-136">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c1a78-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c1a78-137">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="c1a78-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="c1a78-138">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="c1a78-138">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="c1a78-139">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c1a78-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
