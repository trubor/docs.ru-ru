---
description: 'Дополнительные сведения о методе: ICLRSyncManager:: Жетрвлокковнернекст'
title: Метод ICLRSyncManager::GetRWLockOwnerNext
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: f49bdd5065ac896147967c0a013347ab39ce1eff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785004"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="3297d-103">Метод ICLRSyncManager::GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="3297d-103">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>

<span data-ttu-id="3297d-104">Возвращает следующий экземпляр [IHostTask](ihosttask-interface.md) , заблокированный для текущей блокировки чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="3297d-104">Gets the next [IHostTask](ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3297d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3297d-105">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3297d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3297d-106">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="3297d-107">окне Итератор, который был создан с помощью вызова [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="3297d-107">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="3297d-108">заполняет Указатель на следующий объект `IHostTask` , ожидающий блокировки, или значение null, если ни одна из задач не ожидает выполнения.</span><span class="sxs-lookup"><span data-stu-id="3297d-108">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3297d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3297d-109">Return Value</span></span>  
  
|<span data-ttu-id="3297d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3297d-110">HRESULT</span></span>|<span data-ttu-id="3297d-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="3297d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3297d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3297d-112">S_OK</span></span>|<span data-ttu-id="3297d-113">`GetRWLockOwnerNext` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="3297d-113">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="3297d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3297d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3297d-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="3297d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3297d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3297d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3297d-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="3297d-117">The call timed out.</span></span>|  
|<span data-ttu-id="3297d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3297d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3297d-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="3297d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3297d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3297d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3297d-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="3297d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3297d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3297d-122">E_FAIL</span></span>|<span data-ttu-id="3297d-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="3297d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3297d-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="3297d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3297d-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3297d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3297d-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="3297d-126">Remarks</span></span>  

 <span data-ttu-id="3297d-127">Если параметр `ppOwnerHostTask` имеет значение null, итерация завершается и узел должен вызвать метод [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3297d-127">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3297d-128">Среда CLR вызывает метод в `AddRef` , `IHostTask` который `ppOwnerHostTask` указывает, чтобы предотвратить выход этой задачи, пока узел удерживает указатель.</span><span class="sxs-lookup"><span data-stu-id="3297d-128">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="3297d-129">Узел должен вызвать `Release` , чтобы уменьшить число ссылок по завершении.</span><span class="sxs-lookup"><span data-stu-id="3297d-129">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3297d-130">Требования</span><span class="sxs-lookup"><span data-stu-id="3297d-130">Requirements</span></span>  

 <span data-ttu-id="3297d-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3297d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3297d-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3297d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3297d-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3297d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3297d-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3297d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3297d-135">См. также</span><span class="sxs-lookup"><span data-stu-id="3297d-135">See also</span></span>

- [<span data-ttu-id="3297d-136">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="3297d-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="3297d-137">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="3297d-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
