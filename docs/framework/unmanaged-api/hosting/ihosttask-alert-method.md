---
description: 'Дополнительные сведения о методе IHostTask:: Alert'
title: Метод IHostTask::Alert
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 378552db882aada0b6d0f531a871f2deb02132d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784716"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="84241-103">Метод IHostTask::Alert</span><span class="sxs-lookup"><span data-stu-id="84241-103">IHostTask::Alert Method</span></span>

<span data-ttu-id="84241-104">Запрашивает выход узла из задачи, представленной текущим экземпляром [IHostTask](ihosttask-interface.md) , поэтому задачу можно прервать.</span><span class="sxs-lookup"><span data-stu-id="84241-104">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84241-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84241-105">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="84241-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="84241-106">Return Value</span></span>  
  
|<span data-ttu-id="84241-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84241-107">HRESULT</span></span>|<span data-ttu-id="84241-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="84241-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84241-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="84241-109">S_OK</span></span>|<span data-ttu-id="84241-110">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="84241-110">The method returned successfully.</span></span>|  
|<span data-ttu-id="84241-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="84241-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="84241-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="84241-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="84241-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="84241-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="84241-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="84241-114">The call timed out.</span></span>|  
|<span data-ttu-id="84241-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="84241-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="84241-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="84241-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="84241-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="84241-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="84241-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="84241-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="84241-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="84241-119">E_FAIL</span></span>|<span data-ttu-id="84241-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="84241-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="84241-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="84241-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="84241-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="84241-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84241-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="84241-123">Remarks</span></span>  

 <span data-ttu-id="84241-124">Среда CLR вызывает `Alert` метод, когда <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> вызывается из пользовательского кода, или когда объект, <xref:System.AppDomain> связанный с текущим, <xref:System.Threading.Thread> завершает работу.</span><span class="sxs-lookup"><span data-stu-id="84241-124">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="84241-125">Узел должен возвращаться немедленно, так как вызов выполняется асинхронно.</span><span class="sxs-lookup"><span data-stu-id="84241-125">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="84241-126">Если узел не может немедленно предупредить задачу, он должен пробудиться при следующем входе в состояние, в котором она может быть оповещена.</span><span class="sxs-lookup"><span data-stu-id="84241-126">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84241-127">`Alert` затрагивает только те задачи, к которым среда выполнения передала [WAIT_OPTION](wait-option-enumeration.md) значение WAIT_ALERTABLE, в методы, такие как [Join](ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="84241-127">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84241-128">Требования</span><span class="sxs-lookup"><span data-stu-id="84241-128">Requirements</span></span>  

 <span data-ttu-id="84241-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84241-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84241-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84241-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84241-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84241-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84241-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84241-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84241-133">См. также</span><span class="sxs-lookup"><span data-stu-id="84241-133">See also</span></span>

- [<span data-ttu-id="84241-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="84241-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="84241-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="84241-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="84241-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="84241-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="84241-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="84241-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
