---
description: 'Дополнительные сведения о методе ICLRTask:: Локкшелд'
title: Метод ICLRTask::LocksHeld
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: 5dff0b2a80594e03d61d50c6d9fa52bb12bb42f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799545"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="4e46b-103">Метод ICLRTask::LocksHeld</span><span class="sxs-lookup"><span data-stu-id="4e46b-103">ICLRTask::LocksHeld Method</span></span>

<span data-ttu-id="4e46b-104">Возвращает количество блокировок, которые в настоящее время удерживаются в задаче.</span><span class="sxs-lookup"><span data-stu-id="4e46b-104">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e46b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e46b-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e46b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4e46b-106">Parameters</span></span>  

 `pLockCount`  
 <span data-ttu-id="4e46b-107">заполняет Количество блокировок, удерживаемых для задачи во время вызова метода.</span><span class="sxs-lookup"><span data-stu-id="4e46b-107">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e46b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4e46b-108">Return Value</span></span>  
  
|<span data-ttu-id="4e46b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e46b-109">HRESULT</span></span>|<span data-ttu-id="4e46b-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="4e46b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e46b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e46b-111">S_OK</span></span>|<span data-ttu-id="4e46b-112">`LocksHeld` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="4e46b-112">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="4e46b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4e46b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4e46b-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="4e46b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4e46b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4e46b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4e46b-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="4e46b-116">The call timed out.</span></span>|  
|<span data-ttu-id="4e46b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e46b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4e46b-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="4e46b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4e46b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4e46b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4e46b-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="4e46b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4e46b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4e46b-121">E_FAIL</span></span>|<span data-ttu-id="4e46b-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="4e46b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4e46b-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="4e46b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4e46b-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4e46b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e46b-125">Требования</span><span class="sxs-lookup"><span data-stu-id="4e46b-125">Requirements</span></span>  

 <span data-ttu-id="4e46b-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e46b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e46b-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e46b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e46b-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e46b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e46b-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e46b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e46b-130">См. также</span><span class="sxs-lookup"><span data-stu-id="4e46b-130">See also</span></span>

- [<span data-ttu-id="4e46b-131">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4e46b-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4e46b-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4e46b-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4e46b-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="4e46b-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4e46b-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4e46b-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
