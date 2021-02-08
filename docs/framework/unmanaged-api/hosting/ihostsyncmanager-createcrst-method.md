---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: CreateCrst'
title: Метод IHostSyncManager::CreateCrst
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 7d1880f1553d159f62efe65afe8368a60b5bf9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784812"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="7050b-103">Метод IHostSyncManager::CreateCrst</span><span class="sxs-lookup"><span data-stu-id="7050b-103">IHostSyncManager::CreateCrst Method</span></span>

<span data-ttu-id="7050b-104">Создает объект критической секции для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="7050b-104">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7050b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7050b-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7050b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7050b-106">Parameters</span></span>  

 `ppCrst`  
 <span data-ttu-id="7050b-107">заполняет Указатель на адрес экземпляра [IHostCrst](ihostcrst-interface.md) , реализуемого узлом, или значение null, если не удалось создать критический раздел.</span><span class="sxs-lookup"><span data-stu-id="7050b-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7050b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7050b-108">Return Value</span></span>  
  
|<span data-ttu-id="7050b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7050b-109">HRESULT</span></span>|<span data-ttu-id="7050b-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="7050b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7050b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7050b-111">S_OK</span></span>|<span data-ttu-id="7050b-112">`CreateCrst` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7050b-112">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="7050b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7050b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7050b-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7050b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7050b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7050b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7050b-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7050b-116">The call timed out.</span></span>|  
|<span data-ttu-id="7050b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7050b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7050b-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7050b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7050b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7050b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7050b-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7050b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7050b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7050b-121">E_FAIL</span></span>|<span data-ttu-id="7050b-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7050b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7050b-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7050b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7050b-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7050b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7050b-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7050b-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7050b-126">Недостаточно свободной памяти для создания запрошенной критической секции.</span><span class="sxs-lookup"><span data-stu-id="7050b-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7050b-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="7050b-127">Remarks</span></span>  

 <span data-ttu-id="7050b-128">Объекты критических секций обеспечивают синхронизацию, аналогичную той, которая предоставляется объектом Mutex, за исключением того, что критические разделы могут использоваться только потоками одного процесса.</span><span class="sxs-lookup"><span data-stu-id="7050b-128">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="7050b-129">`CreateCrst` отражает функцию Win32 `InitializeCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="7050b-129">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7050b-130">Требования</span><span class="sxs-lookup"><span data-stu-id="7050b-130">Requirements</span></span>  

 <span data-ttu-id="7050b-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7050b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7050b-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7050b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7050b-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7050b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7050b-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7050b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7050b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="7050b-135">See also</span></span>

- [<span data-ttu-id="7050b-136">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="7050b-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7050b-137">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="7050b-137">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="7050b-138">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="7050b-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="7050b-139">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="7050b-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="7050b-140">Мьютексы</span><span class="sxs-lookup"><span data-stu-id="7050b-140">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="7050b-141">Классы Semaphore и SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="7050b-141">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
