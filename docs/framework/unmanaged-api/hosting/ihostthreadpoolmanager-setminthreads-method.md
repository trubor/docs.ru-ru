---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: SetMinThreads'
title: Метод IHostThreadPoolManager::SetMinThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: 00d6bd8212ee95318bbe546da80ca34bff7d1324
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753761"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="2700c-103">Метод IHostThreadPoolManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="2700c-103">IHostThreadPoolManager::SetMinThreads Method</span></span>

<span data-ttu-id="2700c-104">Задает минимальное число бездействующих потоков, которые должны поддерживаться узлом в ожидаемых запросах.</span><span class="sxs-lookup"><span data-stu-id="2700c-104">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2700c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2700c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2700c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2700c-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="2700c-107">окне Новое минимальное число потоков, которое должен поддерживать узел.</span><span class="sxs-lookup"><span data-stu-id="2700c-107">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2700c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2700c-108">Return Value</span></span>  
  
|<span data-ttu-id="2700c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2700c-109">HRESULT</span></span>|<span data-ttu-id="2700c-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="2700c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2700c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2700c-111">S_OK</span></span>|<span data-ttu-id="2700c-112">`SetMinThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="2700c-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2700c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2700c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2700c-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="2700c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2700c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2700c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2700c-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="2700c-116">The call timed out.</span></span>|  
|<span data-ttu-id="2700c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2700c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2700c-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="2700c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2700c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2700c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2700c-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="2700c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2700c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2700c-121">E_FAIL</span></span>|<span data-ttu-id="2700c-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="2700c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2700c-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="2700c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2700c-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2700c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2700c-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2700c-125">E_NOTIMPL</span></span>|<span data-ttu-id="2700c-126">Узел не предоставляет реализацию `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="2700c-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2700c-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="2700c-127">Remarks</span></span>  

 <span data-ttu-id="2700c-128">Узлу не требуется предоставлять реализацию `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="2700c-128">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="2700c-129">В этом случае он должен возвращать значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2700c-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2700c-130">Требования</span><span class="sxs-lookup"><span data-stu-id="2700c-130">Requirements</span></span>  

 <span data-ttu-id="2700c-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2700c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2700c-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2700c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2700c-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2700c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2700c-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2700c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2700c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="2700c-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="2700c-136">Метод GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="2700c-136">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="2700c-137">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="2700c-137">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="2700c-138">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="2700c-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
