---
description: 'Дополнительные сведения о методе: IHostGCManager:: SuspensionStarting'
title: Метод IHostGCManager::SuspensionStarting
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
ms.openlocfilehash: 3a57d47fea735ab004fd0db293bed1ba4d3314e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708649"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="f4075-103">Метод IHostGCManager::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="f4075-103">IHostGCManager::SuspensionStarting Method</span></span>

<span data-ttu-id="f4075-104">Уведомляет основное приложение о том, что среда CLR приостанавливает выполнение задач, для выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f4075-104">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4075-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4075-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f4075-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f4075-106">Return Value</span></span>  
  
|<span data-ttu-id="f4075-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4075-107">HRESULT</span></span>|<span data-ttu-id="f4075-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="f4075-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4075-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4075-109">S_OK</span></span>|<span data-ttu-id="f4075-110">`SuspensionStarting` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="f4075-110">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="f4075-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4075-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4075-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="f4075-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4075-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4075-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4075-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="f4075-114">The call timed out.</span></span>|  
|<span data-ttu-id="f4075-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4075-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4075-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="f4075-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4075-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4075-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4075-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="f4075-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4075-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4075-119">E_FAIL</span></span>|<span data-ttu-id="f4075-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="f4075-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4075-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="f4075-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4075-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f4075-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4075-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4075-123">Remarks</span></span>  

 <span data-ttu-id="f4075-124">Вызовы CLR `SuspensionStarting` для информирования узла о сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="f4075-124">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f4075-125">Не Перепланируйте эту задачу.</span><span class="sxs-lookup"><span data-stu-id="f4075-125">Do not reschedule this task.</span></span> <span data-ttu-id="f4075-126">Узел должен перепланировать задачу при вызове [среадисблоккингфорсуспенсион](ihostgcmanager-threadisblockingforsuspension-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f4075-126">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4075-127">Требования</span><span class="sxs-lookup"><span data-stu-id="f4075-127">Requirements</span></span>  

 <span data-ttu-id="f4075-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4075-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4075-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4075-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4075-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4075-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4075-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4075-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4075-132">См. также</span><span class="sxs-lookup"><span data-stu-id="f4075-132">See also</span></span>

- [<span data-ttu-id="f4075-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f4075-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f4075-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f4075-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f4075-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="f4075-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f4075-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f4075-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f4075-137">Интерфейс IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="f4075-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
