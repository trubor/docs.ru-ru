---
description: 'Дополнительные сведения о методе: ICLRDebugManager:: Бегинконнектион'
title: Метод ICLRDebugManager::BeginConnection
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 9b4ee64ad96bddfd5d7d650b657c6691b27d8c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746143"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="737ca-103">Метод ICLRDebugManager::BeginConnection</span><span class="sxs-lookup"><span data-stu-id="737ca-103">ICLRDebugManager::BeginConnection Method</span></span>

<span data-ttu-id="737ca-104">Устанавливает новое соединение между узлом и отладчиком, чтобы связать список задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="737ca-104">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="737ca-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="737ca-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="737ca-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="737ca-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="737ca-107">окне Идентификатор, связываемый со списком задач среды CLR.</span><span class="sxs-lookup"><span data-stu-id="737ca-107">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="737ca-108">окне Понятное имя, связываемое со списком задач среды CLR.</span><span class="sxs-lookup"><span data-stu-id="737ca-108">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="737ca-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="737ca-109">Return Value</span></span>  
  
|<span data-ttu-id="737ca-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="737ca-110">HRESULT</span></span>|<span data-ttu-id="737ca-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="737ca-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="737ca-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="737ca-112">S_OK</span></span>|<span data-ttu-id="737ca-113">`BeginConnection` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="737ca-113">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="737ca-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="737ca-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="737ca-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="737ca-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="737ca-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="737ca-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="737ca-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="737ca-117">The call timed out.</span></span>|  
|<span data-ttu-id="737ca-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="737ca-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="737ca-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="737ca-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="737ca-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="737ca-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="737ca-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="737ca-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="737ca-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="737ca-122">E_FAIL</span></span>|<span data-ttu-id="737ca-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="737ca-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="737ca-124">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="737ca-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="737ca-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="737ca-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="737ca-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="737ca-126">E_INVALIDARG</span></span>|<span data-ttu-id="737ca-127">`dwConnectionId` был равен нулю или `BeginConnection` уже был вызван с помощью этого `dwConnectionId` значения или `szConnectionName` был равен null.</span><span class="sxs-lookup"><span data-stu-id="737ca-127">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="737ca-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="737ca-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="737ca-129">Не удалось выделить достаточно памяти для размещения списка задач, связанных с этим соединением.</span><span class="sxs-lookup"><span data-stu-id="737ca-129">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="737ca-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="737ca-130">Remarks</span></span>  

 <span data-ttu-id="737ca-131">[ICLRDebugManager](iclrdebugmanager-interface.md) предоставляет три метода, `BeginConnection` , [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)и [ендконнектион](iclrdebugmanager-endconnection-method.md)для связывания списков задач с идентификаторами и понятными именами.</span><span class="sxs-lookup"><span data-stu-id="737ca-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="737ca-132">Эти три метода должны вызываться в определенном порядке для каждого набора задач.</span><span class="sxs-lookup"><span data-stu-id="737ca-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="737ca-133">`BeginConnection` вызывается первым для установления нового соединения.</span><span class="sxs-lookup"><span data-stu-id="737ca-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="737ca-134">`SetConnectionTasks` вызывается далее для предоставления набора задач, которые должны быть связаны с этим соединением.</span><span class="sxs-lookup"><span data-stu-id="737ca-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="737ca-135">`EndConnection` вызывается последним, чтобы удалить связь между списком задач и идентификатором и понятным именем. Однако вызовы для различных соединений могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="737ca-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="737ca-136">Требования</span><span class="sxs-lookup"><span data-stu-id="737ca-136">Requirements</span></span>  

 <span data-ttu-id="737ca-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="737ca-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="737ca-138">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="737ca-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="737ca-139">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="737ca-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="737ca-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="737ca-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737ca-141">См. также</span><span class="sxs-lookup"><span data-stu-id="737ca-141">See also</span></span>

- [<span data-ttu-id="737ca-142">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="737ca-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="737ca-143">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="737ca-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="737ca-144">Метод EndConnection</span><span class="sxs-lookup"><span data-stu-id="737ca-144">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="737ca-145">Метод SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="737ca-145">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="737ca-146">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="737ca-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
