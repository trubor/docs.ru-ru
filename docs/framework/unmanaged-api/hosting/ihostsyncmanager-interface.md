---
description: 'Дополнительные сведения о: интерфейс метод ihostsyncmanager'
title: Интерфейс IHostSyncManager
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: c3bd2928315567605d320c772de8ff824ad3cd09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784734"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="72397-103">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="72397-103">IHostSyncManager Interface</span></span>

<span data-ttu-id="72397-104">Предоставляет методы, позволяющие среде CLR создавать примитивы синхронизации путем вызова узла вместо использования функций синхронизации Win32.</span><span class="sxs-lookup"><span data-stu-id="72397-104">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72397-105">Методы</span><span class="sxs-lookup"><span data-stu-id="72397-105">Methods</span></span>  
  
|<span data-ttu-id="72397-106">Метод</span><span class="sxs-lookup"><span data-stu-id="72397-106">Method</span></span>|<span data-ttu-id="72397-107">Описание</span><span class="sxs-lookup"><span data-stu-id="72397-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72397-108">Метод CreateAutoEvent</span><span class="sxs-lookup"><span data-stu-id="72397-108">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="72397-109">Создает объект события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="72397-109">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="72397-110">Метод CreateCrst</span><span class="sxs-lookup"><span data-stu-id="72397-110">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="72397-111">Создает объект критической секции для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="72397-111">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="72397-112">Метод CreateCrstWithSpinCount</span><span class="sxs-lookup"><span data-stu-id="72397-112">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="72397-113">Создает объект критической секции с количеством счетчиков для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="72397-113">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="72397-114">Метод CreateManualEvent</span><span class="sxs-lookup"><span data-stu-id="72397-114">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="72397-115">Создает объект события ручного сброса.</span><span class="sxs-lookup"><span data-stu-id="72397-115">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="72397-116">Метод CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="72397-116">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="72397-117">Создает Отслеживаемый объект события автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="72397-117">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="72397-118">Метод CreateRWLockReaderEvent</span><span class="sxs-lookup"><span data-stu-id="72397-118">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="72397-119">Создает объект события ручного сброса для реализации блокировки чтения.</span><span class="sxs-lookup"><span data-stu-id="72397-119">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="72397-120">Метод CreateRWLockWriterEvent</span><span class="sxs-lookup"><span data-stu-id="72397-120">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="72397-121">Создает объект события автоматического сброса для реализации блокировки модуля записи.</span><span class="sxs-lookup"><span data-stu-id="72397-121">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="72397-122">Метод CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="72397-122">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="72397-123">Создает объект [IHostSemaphore](ihostsemaphore-interface.md) для среды CLR, который будет использоваться в качестве семафора для событий ожидания.</span><span class="sxs-lookup"><span data-stu-id="72397-123">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="72397-124">Метод SetCLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="72397-124">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="72397-125">Задает экземпляр [ICLRSyncManager](iclrsyncmanager-interface.md) , связываемый с текущим `IHostSyncManager` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="72397-125">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72397-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="72397-126">Remarks</span></span>  

 <span data-ttu-id="72397-127">Среда CLR обнаруживает реализацию узла `IHostSyncManager` , вызывая метод [IHostControl:: жесостманажер](ihostcontrol-gethostmanager-method.md) с `IID` IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="72397-127">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72397-128">Требования</span><span class="sxs-lookup"><span data-stu-id="72397-128">Requirements</span></span>  

 <span data-ttu-id="72397-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72397-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72397-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72397-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72397-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72397-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72397-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72397-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72397-133">См. также</span><span class="sxs-lookup"><span data-stu-id="72397-133">See also</span></span>

- [<span data-ttu-id="72397-134">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="72397-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="72397-135">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="72397-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
