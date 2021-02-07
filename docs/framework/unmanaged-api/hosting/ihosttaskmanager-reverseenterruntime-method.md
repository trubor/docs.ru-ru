---
description: 'Дополнительные сведения о методе: IHostTaskManager:: Реверсинтеррунтиме'
title: Метод IHostTaskManager::ReverseEnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 1c2d2d7d60bd110999591ed5e94c86d680560d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707552"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="42701-103">Метод IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="42701-103">IHostTaskManager::ReverseEnterRuntime Method</span></span>

<span data-ttu-id="42701-104">Уведомляет узел о том, что в среде CLR выполняется вызов из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="42701-104">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42701-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="42701-105">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="42701-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="42701-106">Return Value</span></span>  
  
|<span data-ttu-id="42701-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42701-107">HRESULT</span></span>|<span data-ttu-id="42701-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="42701-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42701-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="42701-109">S_OK</span></span>|<span data-ttu-id="42701-110">`ReverseEnterRuntime` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="42701-110">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="42701-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42701-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42701-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="42701-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42701-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42701-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42701-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="42701-114">The call timed out.</span></span>|  
|<span data-ttu-id="42701-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42701-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42701-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="42701-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42701-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42701-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42701-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="42701-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42701-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42701-119">E_FAIL</span></span>|<span data-ttu-id="42701-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="42701-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42701-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="42701-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42701-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42701-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42701-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42701-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="42701-124">Недостаточно памяти для завершения запрошенного выделения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="42701-124">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42701-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="42701-125">Remarks</span></span>  

 <span data-ttu-id="42701-126">Если вызов среды CLR выполняется из последовательности, порожденной в управляемом коде, каждый вызов `ReverseEnterRuntime` соответствует вызову [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="42701-126">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42701-127">Вызовы могут исходить из неуправляемого кода без вложения.</span><span class="sxs-lookup"><span data-stu-id="42701-127">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="42701-128">В этом случае нет вызова [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [леаверунтиме](ihosttaskmanager-leaveruntime-method.md)или `ReverseLeaveRuntime` , а число вызовов не `ReverseEnterRuntime` равно числу вызовов `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="42701-128">In this case, there is no call to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42701-129">Требования</span><span class="sxs-lookup"><span data-stu-id="42701-129">Requirements</span></span>  

 <span data-ttu-id="42701-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42701-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42701-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="42701-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42701-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42701-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42701-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42701-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42701-134">См. также</span><span class="sxs-lookup"><span data-stu-id="42701-134">See also</span></span>

- [<span data-ttu-id="42701-135">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="42701-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="42701-136">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="42701-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="42701-137">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="42701-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="42701-138">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="42701-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
