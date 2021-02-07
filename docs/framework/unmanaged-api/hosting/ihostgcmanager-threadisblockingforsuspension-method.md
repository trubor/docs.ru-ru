---
description: 'Дополнительные сведения о методе: IHostGCManager:: Среадисблоккингфорсуспенсион'
title: Метод IHostGCManager::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 9cb07b80fa9aad1ac289bc5a3abb5a4760f2bfc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708645"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="8873b-103">Метод IHostGCManager::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="8873b-103">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="8873b-104">Уведомляет узел о том, что поток, из которого был сделан вызов метода, собирается блокироваться для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8873b-104">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8873b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8873b-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8873b-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8873b-106">Return Value</span></span>  
  
|<span data-ttu-id="8873b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8873b-107">HRESULT</span></span>|<span data-ttu-id="8873b-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="8873b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8873b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8873b-109">S_OK</span></span>|<span data-ttu-id="8873b-110">`ThreadIsBlockingForSuspension` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="8873b-110">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="8873b-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8873b-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8873b-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8873b-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8873b-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8873b-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8873b-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="8873b-114">The call timed out.</span></span>|  
|<span data-ttu-id="8873b-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8873b-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8873b-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="8873b-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8873b-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8873b-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8873b-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="8873b-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8873b-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8873b-119">E_FAIL</span></span>|<span data-ttu-id="8873b-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="8873b-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8873b-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8873b-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8873b-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8873b-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8873b-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="8873b-123">Remarks</span></span>  

 <span data-ttu-id="8873b-124">Среда CLR обычно вызывает `ThreadIsBlockForSuspension` метод в процессе подготовки к сборке мусора, чтобы дать узлу возможность перепланировать поток для неуправляемых задач.</span><span class="sxs-lookup"><span data-stu-id="8873b-124">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8873b-125">Узел может перепланировать задачи только после вызова `ThreadIsBlockingForSuspension` .</span><span class="sxs-lookup"><span data-stu-id="8873b-125">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="8873b-126">После того как среда выполнения вызовет [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), узел не должен перепланировать задачу.</span><span class="sxs-lookup"><span data-stu-id="8873b-126">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8873b-127">Требования</span><span class="sxs-lookup"><span data-stu-id="8873b-127">Requirements</span></span>  

 <span data-ttu-id="8873b-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8873b-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8873b-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8873b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8873b-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8873b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8873b-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8873b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8873b-132">См. также</span><span class="sxs-lookup"><span data-stu-id="8873b-132">See also</span></span>

- [<span data-ttu-id="8873b-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="8873b-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8873b-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="8873b-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8873b-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="8873b-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8873b-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="8873b-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8873b-137">Интерфейс IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="8873b-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
