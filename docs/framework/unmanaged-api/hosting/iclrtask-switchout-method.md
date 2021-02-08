---
description: 'Дополнительные сведения о методе ICLRTask:: Switch.'
title: Метод ICLRTask::SwitchOut
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 6c491c4d9005fb850c5adecd025730f1ea71f513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784942"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="628d8-103">Метод ICLRTask::SwitchOut</span><span class="sxs-lookup"><span data-stu-id="628d8-103">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="628d8-104">Уведомляет среду CLR о том, что задача, представленная текущим экземпляром [ICLRTask](iclrtask-interface.md) , больше не находится в рабочем состоянии.</span><span class="sxs-lookup"><span data-stu-id="628d8-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628d8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="628d8-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="628d8-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="628d8-106">Return Value</span></span>  
  
|<span data-ttu-id="628d8-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="628d8-107">HRESULT</span></span>|<span data-ttu-id="628d8-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="628d8-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="628d8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="628d8-109">S_OK</span></span>|<span data-ttu-id="628d8-110">`SwitchOut` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="628d8-110">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="628d8-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="628d8-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="628d8-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="628d8-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="628d8-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="628d8-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="628d8-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="628d8-114">The call timed out.</span></span>|  
|<span data-ttu-id="628d8-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="628d8-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="628d8-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="628d8-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="628d8-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="628d8-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="628d8-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="628d8-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="628d8-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="628d8-119">E_FAIL</span></span>|<span data-ttu-id="628d8-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="628d8-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="628d8-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="628d8-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="628d8-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="628d8-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="628d8-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="628d8-123">Remarks</span></span>  

 <span data-ttu-id="628d8-124">Вызовы узла `SwitchOut` позволяют информировать среду CLR о том, что она временно прекратила выполнение задачи, `ICLRTask` представленной текущим экземпляром, и перепланирует задачу.</span><span class="sxs-lookup"><span data-stu-id="628d8-124">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="628d8-125">Требования</span><span class="sxs-lookup"><span data-stu-id="628d8-125">Requirements</span></span>  

 <span data-ttu-id="628d8-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="628d8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="628d8-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="628d8-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="628d8-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="628d8-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="628d8-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="628d8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="628d8-130">См. также</span><span class="sxs-lookup"><span data-stu-id="628d8-130">See also</span></span>

- [<span data-ttu-id="628d8-131">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="628d8-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="628d8-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="628d8-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="628d8-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="628d8-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="628d8-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="628d8-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
