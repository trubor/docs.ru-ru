---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: Креатервлокквритеревент'
title: Метод IHostSyncManager::CreateRWLockWriterEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 509f18ff49966e5da3a25e39258d33caf69249a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784760"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="cb3de-103">Метод IHostSyncManager::CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="cb3de-103">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>

<span data-ttu-id="cb3de-104">Создает объект события автоматического сброса для реализации блокировки модуля записи.</span><span class="sxs-lookup"><span data-stu-id="cb3de-104">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3de-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb3de-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb3de-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb3de-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="cb3de-107">окне Файл cookie, связываемый с событием автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="cb3de-107">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="cb3de-108">заполняет Указатель на адрес экземпляра [ихостаутоевент](ihostautoevent-interface.md) или значение null, если не удалось создать объект события.</span><span class="sxs-lookup"><span data-stu-id="cb3de-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb3de-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cb3de-109">Return Value</span></span>  
  
|<span data-ttu-id="cb3de-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb3de-110">HRESULT</span></span>|<span data-ttu-id="cb3de-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="cb3de-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb3de-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb3de-112">S_OK</span></span>|<span data-ttu-id="cb3de-113">`CreateRWLockWriterEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="cb3de-113">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="cb3de-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb3de-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb3de-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cb3de-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb3de-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb3de-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb3de-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cb3de-117">The call timed out.</span></span>|  
|<span data-ttu-id="cb3de-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb3de-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb3de-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cb3de-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb3de-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb3de-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb3de-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cb3de-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb3de-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb3de-122">E_FAIL</span></span>|<span data-ttu-id="cb3de-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cb3de-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb3de-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cb3de-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb3de-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb3de-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb3de-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cb3de-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cb3de-127">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="cb3de-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb3de-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb3de-128">Remarks</span></span>  

 <span data-ttu-id="cb3de-129">Среда CLR вызывает `CreateRWLockWriterEvent` метод, чтобы получить ссылку на `IHostAutoEvent` экземпляр, используемый в реализации блокировки записи.</span><span class="sxs-lookup"><span data-stu-id="cb3de-129">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="cb3de-130">Узел может использовать указанный файл cookie, чтобы определить, какие задачи ожидают блокировки, вызвав методы итерации интерфейса [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cb3de-130">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3de-131">Требования</span><span class="sxs-lookup"><span data-stu-id="cb3de-131">Requirements</span></span>  

 <span data-ttu-id="cb3de-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3de-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3de-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb3de-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb3de-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb3de-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb3de-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3de-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3de-136">См. также</span><span class="sxs-lookup"><span data-stu-id="cb3de-136">See also</span></span>

- [<span data-ttu-id="cb3de-137">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="cb3de-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="cb3de-138">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="cb3de-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="cb3de-139">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="cb3de-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="cb3de-140">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="cb3de-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
