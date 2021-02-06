---
description: 'Дополнительные сведения о методе ICLRTask:: Reset'
title: Метод ICLRTask::Reset
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: d30738b98003e0543c1a2a31c7471b15811efe5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636992"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="84683-103">Метод ICLRTask::Reset</span><span class="sxs-lookup"><span data-stu-id="84683-103">ICLRTask::Reset Method</span></span>

<span data-ttu-id="84683-104">Информирует среду CLR о том, что узел завершил задачу, и позволяет среде CLR повторно использовать текущий экземпляр [ICLRTask](iclrtask-interface.md) для представления другой задачи.</span><span class="sxs-lookup"><span data-stu-id="84683-104">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84683-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84683-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84683-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="84683-106">Parameters</span></span>  

 `fFull`  
 <span data-ttu-id="84683-107">[in] `true` , если среда выполнения должна сбрасывать все статические значения, связанные с потоками, в дополнение к сведениям о безопасности и национальной настройке, связанным с текущим `ICLRTask` экземпляром; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="84683-107">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="84683-108">Если значение равно `true` , среда выполнения сбрасывает данные, сохраненные с помощью <xref:System.Threading.Thread.AllocateDataSlot%2A> или <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .</span><span class="sxs-lookup"><span data-stu-id="84683-108">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84683-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="84683-109">Return Value</span></span>  
  
|<span data-ttu-id="84683-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84683-110">HRESULT</span></span>|<span data-ttu-id="84683-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="84683-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84683-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="84683-112">S_OK</span></span>|<span data-ttu-id="84683-113">`Reset` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="84683-113">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="84683-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84683-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84683-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="84683-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="84683-116">успешность</span><span class="sxs-lookup"><span data-stu-id="84683-116">successfully</span></span>|  
|<span data-ttu-id="84683-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84683-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84683-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="84683-118">The call timed out.</span></span>|  
|<span data-ttu-id="84683-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84683-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84683-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="84683-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84683-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84683-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84683-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="84683-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84683-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84683-123">E_FAIL</span></span>|<span data-ttu-id="84683-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="84683-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84683-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="84683-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84683-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="84683-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84683-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="84683-127">Remarks</span></span>  

 <span data-ttu-id="84683-128">Среда CLR может перезапустить ранее созданные `ICLRTask` экземпляры, чтобы избежать лишних затрат на создание новых экземпляров каждый раз, когда требуется новая задача.</span><span class="sxs-lookup"><span data-stu-id="84683-128">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="84683-129">Узел включает эту функцию, вызывая `ICLRTask::Reset` вместо [ICLRTask:: ExitTask](iclrtask-exittask-method.md) после завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="84683-129">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="84683-130">В следующем списке приведено краткое описание обычного жизненного цикла `ICLRTask` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="84683-130">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="84683-131">Среда выполнения создает новый `ICLRTask` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="84683-131">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="84683-132">Среда выполнения вызывает [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) , чтобы получить ссылку на текущую задачу узла.</span><span class="sxs-lookup"><span data-stu-id="84683-132">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="84683-133">Среда выполнения вызывает метод [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) , чтобы связать новый экземпляр с задачей хоста.</span><span class="sxs-lookup"><span data-stu-id="84683-133">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="84683-134">Задача выполняется и завершается.</span><span class="sxs-lookup"><span data-stu-id="84683-134">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="84683-135">Узел уничтожает задачу путем вызова `ICLRTask::ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="84683-135">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="84683-136">`Reset` изменяет этот сценарий двумя способами.</span><span class="sxs-lookup"><span data-stu-id="84683-136">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="84683-137">На шаге 5, приведенном выше, вызывается вызов узла `Reset` для сброса задачи до чистого состояния, а затем отделяет `ICLRTask` экземпляр от связанного экземпляра [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="84683-137">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="84683-138">При необходимости узел также может кэшировать `IHostTask` экземпляр для повторного использования.</span><span class="sxs-lookup"><span data-stu-id="84683-138">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="84683-139">На шаге 1 выше среда выполнения извлекает `ICLRTask` из кэша, а не создает новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="84683-139">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="84683-140">Этот подход хорошо работает, когда узел также имеет пул рабочих задач с многократным использованием.</span><span class="sxs-lookup"><span data-stu-id="84683-140">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="84683-141">Когда узел уничтожает один из его `IHostTask` экземпляров, он уничтожает соответствующий `ICLRTask` вызовом `ExitTask` .</span><span class="sxs-lookup"><span data-stu-id="84683-141">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84683-142">Требования</span><span class="sxs-lookup"><span data-stu-id="84683-142">Requirements</span></span>  

 <span data-ttu-id="84683-143">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84683-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84683-144">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84683-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84683-145">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84683-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84683-146">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84683-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84683-147">См. также</span><span class="sxs-lookup"><span data-stu-id="84683-147">See also</span></span>

- [<span data-ttu-id="84683-148">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="84683-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="84683-149">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="84683-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="84683-150">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="84683-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="84683-151">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="84683-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
