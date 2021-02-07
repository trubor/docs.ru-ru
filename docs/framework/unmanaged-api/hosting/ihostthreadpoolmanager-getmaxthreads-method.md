---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: GetMaxThreads'
title: Метод IHostThreadPoolManager::GetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
ms.openlocfilehash: e8cae2aa29a50ef58a5b87deba9e275a441d43ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728388"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="5cdde-103">Метод IHostThreadPoolManager::GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5cdde-103">IHostThreadPoolManager::GetMaxThreads Method</span></span>

<span data-ttu-id="5cdde-104">Возвращает максимальное число потоков, которые обслуживается одновременно в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="5cdde-104">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cdde-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cdde-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cdde-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5cdde-106">Parameters</span></span>  

 `pdwMaxWorkerThreads`  
 <span data-ttu-id="5cdde-107">заполняет Указатель на максимальное число потоков, поддерживаемых узлом в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="5cdde-107">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cdde-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5cdde-108">Return Value</span></span>  
  
|<span data-ttu-id="5cdde-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cdde-109">HRESULT</span></span>|<span data-ttu-id="5cdde-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="5cdde-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cdde-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cdde-111">S_OK</span></span>|<span data-ttu-id="5cdde-112">`GetMaxThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="5cdde-112">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5cdde-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5cdde-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5cdde-114">Общеязыковая среда выполнения (CLR не загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5cdde-114">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5cdde-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5cdde-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5cdde-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="5cdde-116">The call timed out.</span></span>|  
|<span data-ttu-id="5cdde-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5cdde-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5cdde-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="5cdde-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5cdde-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5cdde-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5cdde-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="5cdde-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5cdde-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5cdde-121">E_FAIL</span></span>|<span data-ttu-id="5cdde-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="5cdde-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5cdde-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5cdde-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5cdde-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5cdde-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5cdde-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5cdde-125">E_NOTIMPL</span></span>|<span data-ttu-id="5cdde-126">Узел не предоставляет реализацию `GetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="5cdde-126">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cdde-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="5cdde-127">Remarks</span></span>  

 <span data-ttu-id="5cdde-128">Вызовы CLR `GetMaxThreads` для определения общего числа потоков в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="5cdde-128">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="5cdde-129">Метод [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) возвращает число потоков, которые в данный момент не обрабатывают рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="5cdde-129">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="5cdde-130">Все запросы выше возвращенного значения `pdwMaxWorkerThreads` параметра остаются в очереди до тех пор, пока потоки не станут доступными.</span><span class="sxs-lookup"><span data-stu-id="5cdde-130">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="5cdde-131">Если узел не предоставляет реализацию `GetMaxThreads` , он должен возвращать значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5cdde-131">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cdde-132">Требования</span><span class="sxs-lookup"><span data-stu-id="5cdde-132">Requirements</span></span>  

 <span data-ttu-id="5cdde-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdde-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdde-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5cdde-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5cdde-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cdde-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cdde-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdde-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdde-137">См. также</span><span class="sxs-lookup"><span data-stu-id="5cdde-137">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5cdde-138">Метод GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="5cdde-138">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="5cdde-139">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5cdde-139">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="5cdde-140">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="5cdde-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
