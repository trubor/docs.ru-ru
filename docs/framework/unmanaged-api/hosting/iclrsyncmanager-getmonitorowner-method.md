---
description: 'Дополнительные сведения о методе: ICLRSyncManager:: GetMonitorOwner'
title: Метод ICLRSyncManager::GetMonitorOwner
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: 67fb966c415009236cabef5e6b4d27cbb90d50ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785033"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="d5bfc-103">Метод ICLRSyncManager::GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="d5bfc-103">ICLRSyncManager::GetMonitorOwner Method</span></span>

<span data-ttu-id="d5bfc-104">Возвращает экземпляр [IHostTask](ihosttask-interface.md) , которому принадлежит монитор, идентифицируемый указанным файлом cookie.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-104">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5bfc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5bfc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5bfc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d5bfc-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="d5bfc-107">окне Файл cookie, связанный с монитором.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-107">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="d5bfc-108">заполняет Указатель на объект `IHostTask` , который в данный момент владеет монитором, или значение null, если ни одна задача не владеет.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-108">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5bfc-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d5bfc-109">Return Value</span></span>  
  
|<span data-ttu-id="d5bfc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5bfc-110">HRESULT</span></span>|<span data-ttu-id="d5bfc-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="d5bfc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5bfc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5bfc-112">S_OK</span></span>|<span data-ttu-id="d5bfc-113">`GetMonitorOwner` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-113">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="d5bfc-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5bfc-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5bfc-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5bfc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5bfc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5bfc-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-117">The call timed out.</span></span>|  
|<span data-ttu-id="d5bfc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5bfc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5bfc-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5bfc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5bfc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5bfc-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5bfc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5bfc-122">E_FAIL</span></span>|<span data-ttu-id="d5bfc-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5bfc-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5bfc-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5bfc-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5bfc-126">Remarks</span></span>  

 <span data-ttu-id="d5bfc-127">Узел обычно вызывается `GetMonitorOwner` как часть механизма обнаружения взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-127">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="d5bfc-128">Файл cookie связывается с монитором при его создании с помощью вызова [метод ihostsyncmanager:: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="d5bfc-128">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5bfc-129">Вызов для освобождения события, лежащего в основе монитора, может блокироваться, но не будет взаимоблокировками, если вызов этого метода в настоящее время действует на файл cookie, связанный с этим монитором.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-129">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="d5bfc-130">Другие задачи также могут блокироваться при попытке получить этот монитор.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-130">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="d5bfc-131">`GetMonitorOwner` всегда возвращает значение немедленно и может вызываться в любое время после вызова `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="d5bfc-131">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="d5bfc-132">Узлу не нужно ждать, пока задача ожидает события.</span><span class="sxs-lookup"><span data-stu-id="d5bfc-132">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5bfc-133">Требования</span><span class="sxs-lookup"><span data-stu-id="d5bfc-133">Requirements</span></span>  

 <span data-ttu-id="d5bfc-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5bfc-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5bfc-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5bfc-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5bfc-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5bfc-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5bfc-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5bfc-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5bfc-138">См. также</span><span class="sxs-lookup"><span data-stu-id="d5bfc-138">See also</span></span>

- [<span data-ttu-id="d5bfc-139">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d5bfc-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d5bfc-140">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d5bfc-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
