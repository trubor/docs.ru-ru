---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: CreateRWLockReaderEvent'
title: Метод IHostSyncManager::CreateRWLockReaderEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: be20757924aa45d2a44edab9bf921026aa0247a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784773"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="31d6f-103">Метод IHostSyncManager::CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="31d6f-103">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="31d6f-104">Создает объект события ручного сброса для реализации блокировки чтения.</span><span class="sxs-lookup"><span data-stu-id="31d6f-104">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d6f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="31d6f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d6f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="31d6f-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="31d6f-107">[in] `true` , если `ppEvent` должен быть сигнальным; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="31d6f-107">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="31d6f-108">окне Файл cookie, связываемый с блокировкой чтения.</span><span class="sxs-lookup"><span data-stu-id="31d6f-108">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="31d6f-109">заполняет Указатель на адрес экземпляра [ихостмануалевент](ihostmanualevent-interface.md) или значение null, если не удалось создать объект события.</span><span class="sxs-lookup"><span data-stu-id="31d6f-109">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31d6f-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="31d6f-110">Return Value</span></span>  
  
|<span data-ttu-id="31d6f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31d6f-111">HRESULT</span></span>|<span data-ttu-id="31d6f-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="31d6f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31d6f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="31d6f-113">S_OK</span></span>|<span data-ttu-id="31d6f-114">`CreateRWLockReaderEvent` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="31d6f-114">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="31d6f-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="31d6f-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="31d6f-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="31d6f-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="31d6f-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="31d6f-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="31d6f-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="31d6f-118">The call timed out.</span></span>|  
|<span data-ttu-id="31d6f-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="31d6f-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="31d6f-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="31d6f-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="31d6f-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="31d6f-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="31d6f-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="31d6f-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="31d6f-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="31d6f-123">E_FAIL</span></span>|<span data-ttu-id="31d6f-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="31d6f-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="31d6f-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="31d6f-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="31d6f-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="31d6f-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="31d6f-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="31d6f-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="31d6f-128">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="31d6f-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31d6f-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="31d6f-129">Remarks</span></span>  

 <span data-ttu-id="31d6f-130">Вызовы CLR `CreateRWLockReaderEvent` для получения ссылки на `IHostManualEvent` экземпляр, используемый в его реализации блокировки чтения.</span><span class="sxs-lookup"><span data-stu-id="31d6f-130">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="31d6f-131">Узел может использовать файл cookie для определения задач, ожидающих блокировки чтения, путем запроса к интерфейсу [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="31d6f-131">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d6f-132">Требования</span><span class="sxs-lookup"><span data-stu-id="31d6f-132">Requirements</span></span>  

 <span data-ttu-id="31d6f-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d6f-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d6f-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31d6f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31d6f-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31d6f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31d6f-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d6f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d6f-137">См. также</span><span class="sxs-lookup"><span data-stu-id="31d6f-137">See also</span></span>

- [<span data-ttu-id="31d6f-138">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="31d6f-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="31d6f-139">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="31d6f-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="31d6f-140">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="31d6f-140">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="31d6f-141">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="31d6f-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
