---
description: 'Дополнительные сведения о методе: ICLRDebugManager:: SetConnectionTasks'
title: Метод ICLRDebugManager::SetConnectionTasks
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 851b3f54cc5599781596314dfb70296a3d86491a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728747"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="53276-103">Метод ICLRDebugManager::SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="53276-103">ICLRDebugManager::SetConnectionTasks Method</span></span>

<span data-ttu-id="53276-104">Связывает список экземпляров [ICLRTask](iclrtask-interface.md) с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="53276-104">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53276-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53276-105">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53276-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="53276-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="53276-107">окне Специфический для узла идентификатор соединения, с которым связывается `ppCLRTask` массив.</span><span class="sxs-lookup"><span data-stu-id="53276-107">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="53276-108">окне Число членов `ppCLRTask` .</span><span class="sxs-lookup"><span data-stu-id="53276-108">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="53276-109">Это число должно быть больше нуля.</span><span class="sxs-lookup"><span data-stu-id="53276-109">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="53276-110">окне Массив `ICLRTask` указателей, связываемый с соединением, определенным `id` .</span><span class="sxs-lookup"><span data-stu-id="53276-110">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="53276-111">Этот массив должен содержать по крайней мере один элемент.</span><span class="sxs-lookup"><span data-stu-id="53276-111">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53276-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53276-112">Return Value</span></span>  
  
|<span data-ttu-id="53276-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53276-113">HRESULT</span></span>|<span data-ttu-id="53276-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="53276-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53276-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="53276-115">S_OK</span></span>|<span data-ttu-id="53276-116">`SetConnectionTasks` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="53276-116">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="53276-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53276-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53276-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="53276-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53276-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53276-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53276-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="53276-120">The call timed out.</span></span>|  
|<span data-ttu-id="53276-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53276-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53276-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="53276-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53276-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53276-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53276-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="53276-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53276-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53276-125">E_FAIL</span></span>|<span data-ttu-id="53276-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="53276-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53276-127">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="53276-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53276-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53276-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="53276-129">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="53276-129">E_INVALIDARG</span></span>|<span data-ttu-id="53276-130">[Бегинконнектион](iclrdebugmanager-beginconnection-method.md) не вызывался с использованием этого значения `id` , или `dwCount` или `id` равно нулю, либо один из элементов `ppCLRTask` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="53276-130">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53276-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="53276-131">Remarks</span></span>  

 <span data-ttu-id="53276-132">[ICLRDebugManager](iclrdebugmanager-interface.md) предоставляет три метода, `BeginConnection` , `SetConnectionTasks` и [ендконнектион](iclrdebugmanager-endconnection-method.md)для связывания списков задач с идентификаторами и понятными именами.</span><span class="sxs-lookup"><span data-stu-id="53276-132">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="53276-133">Эти три метода должны вызываться в определенном порядке для каждого набора задач.</span><span class="sxs-lookup"><span data-stu-id="53276-133">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="53276-134">`BeginConnection` вызывается первым для установления нового соединения.</span><span class="sxs-lookup"><span data-stu-id="53276-134">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="53276-135">`SetConnectionTasks` вызывается далее для предоставления набора задач, которые должны быть связаны с этим соединением.</span><span class="sxs-lookup"><span data-stu-id="53276-135">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="53276-136">`EndConnection` вызывается последним, чтобы удалить связь между списком задач и идентификатором и понятным именем. Однако вызовы для различных соединений могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="53276-136">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53276-137">Требования</span><span class="sxs-lookup"><span data-stu-id="53276-137">Requirements</span></span>  

 <span data-ttu-id="53276-138">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53276-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53276-139">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53276-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53276-140">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53276-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53276-141">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53276-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53276-142">См. также</span><span class="sxs-lookup"><span data-stu-id="53276-142">See also</span></span>

- [<span data-ttu-id="53276-143">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="53276-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="53276-144">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="53276-144">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="53276-145">Метод BeginConnection</span><span class="sxs-lookup"><span data-stu-id="53276-145">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="53276-146">Метод EndConnection</span><span class="sxs-lookup"><span data-stu-id="53276-146">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="53276-147">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="53276-147">IHostControl Interface</span></span>](ihostcontrol-interface.md)
