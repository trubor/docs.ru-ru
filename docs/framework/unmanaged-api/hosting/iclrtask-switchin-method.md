---
description: 'См. Дополнительные сведения о методе ICLRTask:: Switched.'
title: Метод ICLRTask::SwitchIn
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: 0bbcd2b9594a8ce465a1dcd7b5ae3f8a0799826d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636836"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="556ba-103">Метод ICLRTask::SwitchIn</span><span class="sxs-lookup"><span data-stu-id="556ba-103">ICLRTask::SwitchIn Method</span></span>

<span data-ttu-id="556ba-104">Уведомляет среду CLR о том, что задача, которую представляет текущий экземпляр [ICLRTask](iclrtask-interface.md) , теперь находится в рабочем состоянии.</span><span class="sxs-lookup"><span data-stu-id="556ba-104">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="556ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="556ba-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="556ba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="556ba-106">Parameters</span></span>  

 `threadHandle`  
 <span data-ttu-id="556ba-107">окне Маркер физического потока, в котором выполняются задачи, представленные текущим `ICLRTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="556ba-107">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="556ba-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="556ba-108">Return Value</span></span>  
  
|<span data-ttu-id="556ba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="556ba-109">HRESULT</span></span>|<span data-ttu-id="556ba-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="556ba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="556ba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="556ba-111">S_OK</span></span>|<span data-ttu-id="556ba-112">`SwitchIn` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="556ba-112">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="556ba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="556ba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="556ba-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="556ba-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="556ba-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="556ba-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="556ba-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="556ba-116">The call timed out.</span></span>|  
|<span data-ttu-id="556ba-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="556ba-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="556ba-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="556ba-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="556ba-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="556ba-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="556ba-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="556ba-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="556ba-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="556ba-121">E_FAIL</span></span>|<span data-ttu-id="556ba-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="556ba-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="556ba-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="556ba-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="556ba-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="556ba-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="556ba-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="556ba-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="556ba-126">`SwitchIn` был вызван без предыдущего вызова [метода Switch](iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="556ba-126">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="556ba-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="556ba-127">Remarks</span></span>  

 <span data-ttu-id="556ba-128">`threadHandle`Параметр представляет собой обработчик для потока операционной системы, в котором запланирована задача, представленная текущим `ICLRTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="556ba-128">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="556ba-129">Если в этом потоке возникло олицетворение, то перед переключением в задаче необходимо вызвать метод [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) .</span><span class="sxs-lookup"><span data-stu-id="556ba-129">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="556ba-130">Вызов метода `SwitchIn` без предыдущего вызова `SwitchOut` завершается ошибкой со значением HRESULT, равным HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="556ba-130">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="556ba-131">Требования</span><span class="sxs-lookup"><span data-stu-id="556ba-131">Requirements</span></span>  

 <span data-ttu-id="556ba-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="556ba-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="556ba-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="556ba-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="556ba-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="556ba-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="556ba-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="556ba-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556ba-136">См. также</span><span class="sxs-lookup"><span data-stu-id="556ba-136">See also</span></span>

- [<span data-ttu-id="556ba-137">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="556ba-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="556ba-138">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="556ba-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="556ba-139">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="556ba-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="556ba-140">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="556ba-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
