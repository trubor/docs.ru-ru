---
description: 'Дополнительные сведения о методе: IHostGCManager:: SuspensionEnding'
title: Метод IHostGCManager::SuspensionEnding
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 43ec3db76e6e6448719f9c40ef2476da4e2ccf9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708627"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="036a1-103">Метод IHostGCManager::SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="036a1-103">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="036a1-104">Уведомляет основное приложение о том, что среда CLR возобновляет выполнение задач в потоках, которые были приостановлены для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="036a1-104">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="036a1-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="036a1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="036a1-106">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="036a1-107">окне Поколение сборки мусора, которое только что завершается, из которого происходит возобновление работы потока.</span><span class="sxs-lookup"><span data-stu-id="036a1-107">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="036a1-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="036a1-108">Return Value</span></span>  
  
|<span data-ttu-id="036a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="036a1-109">HRESULT</span></span>|<span data-ttu-id="036a1-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="036a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="036a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="036a1-111">S_OK</span></span>|<span data-ttu-id="036a1-112">`SuspensionEnding` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="036a1-112">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="036a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="036a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="036a1-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="036a1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="036a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="036a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="036a1-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="036a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="036a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="036a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="036a1-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="036a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="036a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="036a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="036a1-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="036a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="036a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="036a1-121">E_FAIL</span></span>|<span data-ttu-id="036a1-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="036a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="036a1-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="036a1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="036a1-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="036a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="036a1-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="036a1-125">Remarks</span></span>  

 <span data-ttu-id="036a1-126">Среда CLR вызывает `SuspensionEnding` после выполнения сборки мусора, чтобы уведомить узел о том, что поток возобновляет выполнение.</span><span class="sxs-lookup"><span data-stu-id="036a1-126">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="036a1-127">Не Перепланируйте поток, из которого был сделан вызов метода.</span><span class="sxs-lookup"><span data-stu-id="036a1-127">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036a1-128">Требования</span><span class="sxs-lookup"><span data-stu-id="036a1-128">Requirements</span></span>  

 <span data-ttu-id="036a1-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036a1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036a1-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="036a1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="036a1-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="036a1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="036a1-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036a1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036a1-133">См. также</span><span class="sxs-lookup"><span data-stu-id="036a1-133">See also</span></span>

- [<span data-ttu-id="036a1-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="036a1-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="036a1-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="036a1-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="036a1-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="036a1-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="036a1-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="036a1-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="036a1-138">Интерфейс IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="036a1-138">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
