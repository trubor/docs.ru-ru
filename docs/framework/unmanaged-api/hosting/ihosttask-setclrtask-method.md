---
description: 'Дополнительные сведения о методе IHostTask:: SetCLRTask'
title: Метод IHostTask::SetCLRTask
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: 381b7827f043b6ef1d4a6698f5eb103233c9af55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784682"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="eccf7-103">Метод IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="eccf7-103">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="eccf7-104">Связывает `ICLRTask` экземпляр с текущим экземпляром [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eccf7-104">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eccf7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eccf7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eccf7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eccf7-106">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="eccf7-107">окне Указатель интерфейса на экземпляр, `ICLRTask` который должен быть связан с текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="eccf7-107">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eccf7-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eccf7-108">Return Value</span></span>  
  
|<span data-ttu-id="eccf7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eccf7-109">HRESULT</span></span>|<span data-ttu-id="eccf7-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="eccf7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eccf7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eccf7-111">S_OK</span></span>|<span data-ttu-id="eccf7-112">`SetCLRTask` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="eccf7-112">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="eccf7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eccf7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eccf7-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="eccf7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eccf7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eccf7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eccf7-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="eccf7-116">The call timed out.</span></span>|  
|<span data-ttu-id="eccf7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eccf7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eccf7-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="eccf7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eccf7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eccf7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eccf7-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="eccf7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eccf7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eccf7-121">E_FAIL</span></span>|<span data-ttu-id="eccf7-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="eccf7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eccf7-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="eccf7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eccf7-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eccf7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eccf7-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="eccf7-125">Remarks</span></span>  

 <span data-ttu-id="eccf7-126">Среда CLR вызывает метод `SetCLRTask` , чтобы связать `ICLRTask` экземпляр с текущим `IHostTask` экземпляром, который был создан с помощью вызова [IHostTaskManager:: CreateTask](ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="eccf7-126">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eccf7-127">Требования</span><span class="sxs-lookup"><span data-stu-id="eccf7-127">Requirements</span></span>  

 <span data-ttu-id="eccf7-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eccf7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eccf7-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eccf7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eccf7-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eccf7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eccf7-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eccf7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccf7-132">См. также</span><span class="sxs-lookup"><span data-stu-id="eccf7-132">See also</span></span>

- [<span data-ttu-id="eccf7-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="eccf7-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eccf7-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="eccf7-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eccf7-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="eccf7-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eccf7-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="eccf7-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
