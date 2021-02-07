---
description: 'Дополнительные сведения о методе: ICLRDebugManager:: Ендконнектион'
title: Метод ICLRDebugManager::EndConnection
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 06dc9e20ec02c3e3040090babcc443a2ae59848b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746057"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="45d6f-103">Метод ICLRDebugManager::EndConnection</span><span class="sxs-lookup"><span data-stu-id="45d6f-103">ICLRDebugManager::EndConnection Method</span></span>

<span data-ttu-id="45d6f-104">Удаляет связь между списком задач и идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="45d6f-104">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d6f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45d6f-105">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45d6f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="45d6f-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="45d6f-107">окне Специфический для узла идентификатор соединения и связанный список задач среды CLR.</span><span class="sxs-lookup"><span data-stu-id="45d6f-107">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45d6f-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="45d6f-108">Return Value</span></span>  
  
|<span data-ttu-id="45d6f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45d6f-109">HRESULT</span></span>|<span data-ttu-id="45d6f-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="45d6f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45d6f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="45d6f-111">S_OK</span></span>|<span data-ttu-id="45d6f-112">`EndConnection` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="45d6f-112">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="45d6f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45d6f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45d6f-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="45d6f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45d6f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45d6f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45d6f-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="45d6f-116">The call timed out.</span></span>|  
|<span data-ttu-id="45d6f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45d6f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45d6f-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="45d6f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45d6f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45d6f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45d6f-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="45d6f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45d6f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45d6f-121">E_FAIL</span></span>|<span data-ttu-id="45d6f-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="45d6f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45d6f-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="45d6f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45d6f-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="45d6f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="45d6f-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="45d6f-125">E_INVALIDARG</span></span>|<span data-ttu-id="45d6f-126">[Бегинконнектион](iclrdebugmanager-beginconnection-method.md) никогда не вызывался с помощью `dwConnectionId` , или `dwConnectionId` равен нулю.</span><span class="sxs-lookup"><span data-stu-id="45d6f-126">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45d6f-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="45d6f-127">Remarks</span></span>  

 <span data-ttu-id="45d6f-128">[ICLRDebugManager](iclrdebugmanager-interface.md) предоставляет три метода, `BeginConnection` , [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md)и `EndConnection` , для связывания списков задач с идентификаторами и понятными именами.</span><span class="sxs-lookup"><span data-stu-id="45d6f-128">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45d6f-129">Эти три метода должны вызываться в определенном порядке для каждого набора задач.</span><span class="sxs-lookup"><span data-stu-id="45d6f-129">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="45d6f-130">`BeginConnection` вызывается первым для установления нового соединения.</span><span class="sxs-lookup"><span data-stu-id="45d6f-130">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="45d6f-131">`SetConnectionTasks` вызывается далее для предоставления набора задач, которые должны быть связаны с этим соединением.</span><span class="sxs-lookup"><span data-stu-id="45d6f-131">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="45d6f-132">`EndConnection` вызывается последним, чтобы удалить связь между списком задач и идентификатором и понятным именем. Однако вызовы для различных соединений могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="45d6f-132">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d6f-133">Требования</span><span class="sxs-lookup"><span data-stu-id="45d6f-133">Requirements</span></span>  

 <span data-ttu-id="45d6f-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d6f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d6f-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="45d6f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45d6f-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45d6f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45d6f-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d6f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d6f-138">См. также</span><span class="sxs-lookup"><span data-stu-id="45d6f-138">See also</span></span>

- [<span data-ttu-id="45d6f-139">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="45d6f-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="45d6f-140">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="45d6f-140">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="45d6f-141">Метод BeginConnection</span><span class="sxs-lookup"><span data-stu-id="45d6f-141">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="45d6f-142">Метод SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="45d6f-142">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="45d6f-143">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="45d6f-143">IHostControl Interface</span></span>](ihostcontrol-interface.md)
