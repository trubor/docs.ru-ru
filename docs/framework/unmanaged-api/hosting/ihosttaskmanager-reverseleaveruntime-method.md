---
description: 'Дополнительные сведения о методе: IHostTaskManager:: ReverseLeaveRuntime'
title: Метод IHostTaskManager::ReverseLeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: 2fed157f6ea05243270b957cacdb00ba5a47a88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680871"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="160d8-103">Метод IHostTaskManager::ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="160d8-103">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="160d8-104">Уведомляет узел, что элемент управления выходит из среды CLR и вводит неуправляемую функцию, которая, в свою очередь, вызывается из управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="160d8-104">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="160d8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="160d8-105">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="160d8-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="160d8-106">Return Value</span></span>  
  
|<span data-ttu-id="160d8-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="160d8-107">HRESULT</span></span>|<span data-ttu-id="160d8-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="160d8-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="160d8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="160d8-109">S_OK</span></span>|<span data-ttu-id="160d8-110">`ReverseLeaveRuntime` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="160d8-110">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="160d8-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="160d8-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="160d8-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="160d8-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="160d8-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="160d8-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="160d8-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="160d8-114">The call timed out.</span></span>|  
|<span data-ttu-id="160d8-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="160d8-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="160d8-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="160d8-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="160d8-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="160d8-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="160d8-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="160d8-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="160d8-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="160d8-119">E_FAIL</span></span>|<span data-ttu-id="160d8-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="160d8-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="160d8-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="160d8-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="160d8-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="160d8-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="160d8-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="160d8-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="160d8-124">Недостаточно памяти для завершения запрошенного выделения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="160d8-124">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="160d8-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="160d8-125">Remarks</span></span>  

 <span data-ttu-id="160d8-126">Вызовы CLR `ReverseLeaveRuntime` для информирования основного приложения о том, что выполняемая в данный момент задача возвращает управление неуправляемой функции, которая, в свою очередь, вызывается из управляемого кода через вызов платформы.</span><span class="sxs-lookup"><span data-stu-id="160d8-126">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="160d8-127">Каждый вызов `ReverseLeaveRuntime` соответствует соответствующему вызову [реверсинтеррунтиме](ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="160d8-127">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="160d8-128">Требования</span><span class="sxs-lookup"><span data-stu-id="160d8-128">Requirements</span></span>  

 <span data-ttu-id="160d8-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="160d8-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="160d8-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="160d8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="160d8-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="160d8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="160d8-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="160d8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160d8-133">См. также</span><span class="sxs-lookup"><span data-stu-id="160d8-133">See also</span></span>

- [<span data-ttu-id="160d8-134">Метод CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="160d8-134">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="160d8-135">Метод EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="160d8-135">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="160d8-136">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="160d8-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="160d8-137">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="160d8-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="160d8-138">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="160d8-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="160d8-139">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="160d8-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="160d8-140">Метод LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="160d8-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="160d8-141">[Подробный обзор вызова неуправляемого кода](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="160d8-141">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
