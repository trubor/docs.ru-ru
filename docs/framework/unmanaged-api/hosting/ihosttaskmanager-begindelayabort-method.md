---
description: 'Дополнительные сведения о методе: IHostTaskManager:: BeginDelayAbort'
title: Метод IHostTaskManager::BeginDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f991690af4f7e634c8d845bdbd09f690b4ea3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784617"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="f47fa-103">Метод IHostTaskManager::BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="f47fa-103">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="f47fa-104">Уведомляет узел о том, что управляемый код вводит точку, в которой не нужно прерывать текущую задачу.</span><span class="sxs-lookup"><span data-stu-id="f47fa-104">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f47fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f47fa-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f47fa-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f47fa-106">Return Value</span></span>  
  
|<span data-ttu-id="f47fa-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f47fa-107">HRESULT</span></span>|<span data-ttu-id="f47fa-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="f47fa-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f47fa-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f47fa-109">S_OK</span></span>|<span data-ttu-id="f47fa-110">`BeginDelayAbort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="f47fa-110">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f47fa-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f47fa-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f47fa-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="f47fa-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f47fa-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f47fa-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f47fa-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="f47fa-114">The call timed out.</span></span>|  
|<span data-ttu-id="f47fa-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f47fa-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f47fa-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="f47fa-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f47fa-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f47fa-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f47fa-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="f47fa-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f47fa-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f47fa-119">E_FAIL</span></span>|<span data-ttu-id="f47fa-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="f47fa-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f47fa-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="f47fa-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f47fa-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f47fa-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f47fa-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="f47fa-123">E_UNEXPECTED</span></span>|<span data-ttu-id="f47fa-124">`BeginDelayAbort` уже вызван, но соответствующий вызов [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) еще не получен.</span><span class="sxs-lookup"><span data-stu-id="f47fa-124">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f47fa-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="f47fa-125">Remarks</span></span>  

 <span data-ttu-id="f47fa-126">Узел не должен прерывать текущую задачу до `EndDelayAbort` вызова метода.</span><span class="sxs-lookup"><span data-stu-id="f47fa-126">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="f47fa-127">Если другой вызов выполняется `BeginDelayAbort` без промежуточного вызова `EndDelayAbort` , узел должен возвращать E_UNEXPECTED из `BeginDelayAbort` и не должен предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="f47fa-127">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f47fa-128">Требования</span><span class="sxs-lookup"><span data-stu-id="f47fa-128">Requirements</span></span>  

 <span data-ttu-id="f47fa-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f47fa-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47fa-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f47fa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f47fa-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f47fa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f47fa-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f47fa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47fa-133">См. также</span><span class="sxs-lookup"><span data-stu-id="f47fa-133">See also</span></span>

- [<span data-ttu-id="f47fa-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f47fa-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f47fa-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f47fa-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f47fa-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f47fa-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
