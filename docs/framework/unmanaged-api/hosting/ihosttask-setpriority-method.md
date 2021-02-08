---
description: 'Дополнительные сведения о методе IHostTask:: SetPriority'
title: Метод IHostTask::SetPriority
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
ms.openlocfilehash: c3e8fee954e5cbea2d084141a4b2d22d2fa5e95b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784643"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="d5060-103">Метод IHostTask::SetPriority</span><span class="sxs-lookup"><span data-stu-id="d5060-103">IHostTask::SetPriority Method</span></span>

<span data-ttu-id="d5060-104">Запрашивает у узла настройку уровня приоритета потока для задачи, представленной текущим экземпляром [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5060-104">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5060-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5060-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5060-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d5060-106">Parameters</span></span>  

 `newPriority`  
 <span data-ttu-id="d5060-107">окне Целое число, представляющее запрошенное значение приоритета потока для задачи, представленной текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="d5060-107">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5060-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d5060-108">Return Value</span></span>  
  
|<span data-ttu-id="d5060-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5060-109">HRESULT</span></span>|<span data-ttu-id="d5060-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="d5060-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5060-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5060-111">S_OK</span></span>|<span data-ttu-id="d5060-112">`SetPriority` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d5060-112">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d5060-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5060-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5060-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d5060-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5060-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5060-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5060-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d5060-116">The call timed out.</span></span>|  
|<span data-ttu-id="d5060-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5060-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5060-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d5060-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5060-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5060-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5060-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d5060-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5060-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5060-121">E_FAIL</span></span>|<span data-ttu-id="d5060-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d5060-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5060-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d5060-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5060-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5060-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5060-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5060-125">Remarks</span></span>  

 <span data-ttu-id="d5060-126">Потокам предоставляется время обработки с помощью системы циклического перебора, частично основанной на уровне приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="d5060-126">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="d5060-127">`SetPriority` позволяет среде CLR устанавливать этот уровень приоритета потока для текущей задачи.</span><span class="sxs-lookup"><span data-stu-id="d5060-127">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="d5060-128">`newPriority`Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="d5060-128">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="d5060-129">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d5060-129">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="d5060-130">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d5060-130">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="d5060-131">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="d5060-131">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="d5060-132">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="d5060-132">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="d5060-133">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="d5060-133">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="d5060-134">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d5060-134">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="d5060-135">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="d5060-135">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="d5060-136">Среда CLR вызывает, `SetPriority` когда значение изменяется <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> с помощью пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="d5060-136">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="d5060-137">Узел может определять собственные алгоритмы для назначения приоритета потоков и может без необходимости пропускать этот запрос.</span><span class="sxs-lookup"><span data-stu-id="d5060-137">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5060-138">`SetPriority` не сообщает, был ли изменен уровень приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="d5060-138">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="d5060-139">Вызовите метод [IHostTask:: предшествовал](ihosttask-getpriority-method.md) , чтобы определить значение уровня приоритета потока задачи.</span><span class="sxs-lookup"><span data-stu-id="d5060-139">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="d5060-140">Значения уровня приоритета потока определяются функцией Win32 `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="d5060-140">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="d5060-141">Дополнительные сведения о приоритете потоков см. в документации по платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="d5060-141">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5060-142">Требования</span><span class="sxs-lookup"><span data-stu-id="d5060-142">Requirements</span></span>  

 <span data-ttu-id="d5060-143">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5060-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5060-144">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5060-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5060-145">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5060-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5060-146">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5060-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5060-147">См. также</span><span class="sxs-lookup"><span data-stu-id="d5060-147">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="d5060-148">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d5060-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d5060-149">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d5060-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d5060-150">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="d5060-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d5060-151">Метод GetPriority</span><span class="sxs-lookup"><span data-stu-id="d5060-151">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="d5060-152">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d5060-152">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
