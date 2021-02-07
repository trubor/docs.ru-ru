---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: SetMaxThreads'
title: Метод IHostIoCompletionManager::SetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 6b36523b0b0d6cefba383d324eb23debefd7c41b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708285"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="1f1c6-103">Метод IHostIoCompletionManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="1f1c6-103">IHostIoCompletionManager::SetMaxThreads Method</span></span>

<span data-ttu-id="1f1c6-104">Задает максимальное число потоков, которое узел запрашивает для обслуживания запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-104">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1c6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f1c6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f1c6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1f1c6-106">Parameters</span></span>  

 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="1f1c6-107">окне Максимальное число потоков, которое можно выделить для запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-107">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f1c6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1f1c6-108">Return Value</span></span>  
  
|<span data-ttu-id="1f1c6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f1c6-109">HRESULT</span></span>|<span data-ttu-id="1f1c6-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="1f1c6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f1c6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f1c6-111">S_OK</span></span>|<span data-ttu-id="1f1c6-112">`SetMaxThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-112">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1f1c6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f1c6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f1c6-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f1c6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f1c6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f1c6-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-116">The call timed out.</span></span>|  
|<span data-ttu-id="1f1c6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f1c6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f1c6-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f1c6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f1c6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f1c6-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f1c6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f1c6-121">E_FAIL</span></span>|<span data-ttu-id="1f1c6-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f1c6-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f1c6-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f1c6-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1f1c6-125">E_NOTIMPL</span></span>|<span data-ttu-id="1f1c6-126">Узел не предоставляет реализацию `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="1f1c6-126">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f1c6-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f1c6-127">Remarks</span></span>  

 <span data-ttu-id="1f1c6-128">`SetMaxThreads` предоставляет среде CLR возможность задать максимальное число потоков, доступных для запросов на обслуживание на портах ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-128">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="1f1c6-129">Узлу может потребоваться эксклюзивный контроль над размером пула потоков по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-129">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1f1c6-130">По этой причине узел не является обязательным для реализации `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="1f1c6-130">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="1f1c6-131">В этом случае узел должен возвращать E_NOTIMPL из этого метода.</span><span class="sxs-lookup"><span data-stu-id="1f1c6-131">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f1c6-132">Требования</span><span class="sxs-lookup"><span data-stu-id="1f1c6-132">Requirements</span></span>  

 <span data-ttu-id="1f1c6-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f1c6-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f1c6-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f1c6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f1c6-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f1c6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f1c6-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f1c6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1c6-137">См. также</span><span class="sxs-lookup"><span data-stu-id="1f1c6-137">See also</span></span>

- [<span data-ttu-id="1f1c6-138">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1f1c6-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1f1c6-139">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1f1c6-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
