---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: CreateMonitorEvent'
title: Метод IHostSyncManager::CreateMonitorEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: b48d0417e614cf04c3ab150f0bdda73408b7a273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784786"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="d599a-103">Метод IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="d599a-103">IHostSyncManager::CreateMonitorEvent Method</span></span>

<span data-ttu-id="d599a-104">Создает Отслеживаемый объект события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="d599a-104">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d599a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d599a-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d599a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d599a-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="d599a-107">окне Файл cookie, связываемый с объектом события.</span><span class="sxs-lookup"><span data-stu-id="d599a-107">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="d599a-108">заполняет Указатель на адрес экземпляра [ихостаутоевент](ihostautoevent-interface.md) или значение null, если не удалось создать объект события.</span><span class="sxs-lookup"><span data-stu-id="d599a-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d599a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d599a-109">Return Value</span></span>  
  
|<span data-ttu-id="d599a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d599a-110">HRESULT</span></span>|<span data-ttu-id="d599a-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="d599a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d599a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d599a-112">S_OK</span></span>|<span data-ttu-id="d599a-113">`CreateMonitorEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d599a-113">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="d599a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d599a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d599a-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d599a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d599a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d599a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d599a-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d599a-117">The call timed out.</span></span>|  
|<span data-ttu-id="d599a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d599a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d599a-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d599a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d599a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d599a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d599a-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d599a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d599a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d599a-122">E_FAIL</span></span>|<span data-ttu-id="d599a-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d599a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d599a-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d599a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d599a-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d599a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d599a-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d599a-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d599a-127">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="d599a-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d599a-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="d599a-128">Remarks</span></span>  

 <span data-ttu-id="d599a-129">`CreateMonitorEvent` Возвращает объект `IHostAutoEvent` , используемый средой CLR в реализации управляемого <xref:System.Threading.Monitor?displayProperty=nameWithType> типа.</span><span class="sxs-lookup"><span data-stu-id="d599a-129">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="d599a-130">Этот метод отражает функцию Win32 `CreateEvent` со значением, `false` указанным для `bManualReset` параметра.</span><span class="sxs-lookup"><span data-stu-id="d599a-130">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="d599a-131">Узел может использовать файл cookie, чтобы определить, какая задача ожидает монитор, вызвав метод [ICLRSyncManager:: GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d599a-131">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d599a-132">Требования</span><span class="sxs-lookup"><span data-stu-id="d599a-132">Requirements</span></span>  

 <span data-ttu-id="d599a-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d599a-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d599a-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d599a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d599a-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d599a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d599a-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d599a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d599a-137">См. также</span><span class="sxs-lookup"><span data-stu-id="d599a-137">See also</span></span>

- [<span data-ttu-id="d599a-138">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d599a-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d599a-139">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="d599a-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d599a-140">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d599a-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
