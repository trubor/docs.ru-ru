---
description: 'Дополнительные сведения о методе: ICLRSyncManager::D Елетервлокковнеритератор'
title: Метод ICLRSyncManager::DeleteRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: 7968f326f1ad92fe6e3a0f91749fb7e462e81c04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789779"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="cce66-103">Метод ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="cce66-103">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="cce66-104">Запрашивает уничтожение итератора, созданного с помощью вызова метода [ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md), в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="cce66-104">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce66-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cce66-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cce66-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cce66-106">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="cce66-107">окне Итератор, который был создан с помощью вызова `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="cce66-107">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cce66-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cce66-108">Return Value</span></span>  
  
|<span data-ttu-id="cce66-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cce66-109">HRESULT</span></span>|<span data-ttu-id="cce66-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="cce66-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cce66-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cce66-111">S_OK</span></span>|<span data-ttu-id="cce66-112">`DeleteRWLockOwnerIterator` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="cce66-112">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="cce66-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cce66-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cce66-114">Среда CLR не была загружена в процесс или находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cce66-114">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="cce66-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cce66-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cce66-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cce66-116">The call timed out.</span></span>|  
|<span data-ttu-id="cce66-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cce66-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cce66-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cce66-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cce66-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cce66-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cce66-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cce66-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cce66-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cce66-121">E_FAIL</span></span>|<span data-ttu-id="cce66-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cce66-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cce66-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cce66-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cce66-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cce66-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cce66-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="cce66-125">Remarks</span></span>  

 <span data-ttu-id="cce66-126">Узел может вызвать этот метод и `CreateRWLockOwnerIterator` убедиться, что его реализация потоков остается синхронизированной.</span><span class="sxs-lookup"><span data-stu-id="cce66-126">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce66-127">Требования</span><span class="sxs-lookup"><span data-stu-id="cce66-127">Requirements</span></span>  

 <span data-ttu-id="cce66-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cce66-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce66-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cce66-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cce66-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cce66-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cce66-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce66-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce66-132">См. также</span><span class="sxs-lookup"><span data-stu-id="cce66-132">See also</span></span>

- [<span data-ttu-id="cce66-133">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="cce66-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="cce66-134">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="cce66-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
