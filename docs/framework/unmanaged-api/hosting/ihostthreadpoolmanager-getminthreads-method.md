---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: GetMinThreads'
title: Метод IHostThreadPoolManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: 2ebb828f9bc6230b4b0237aa1494f428a1834139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728400"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="50148-103">Метод IHostThreadPoolManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="50148-103">IHostThreadPoolManager::GetMinThreads Method</span></span>

<span data-ttu-id="50148-104">Возвращает минимальное количество бездействующих потоков, которые обслуживающий узел хранит в пуле потоков в ожидаемых запросах.</span><span class="sxs-lookup"><span data-stu-id="50148-104">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50148-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50148-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50148-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="50148-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="50148-107">заполняет Указатель на минимальное число бездействующих рабочих потоков, которое в настоящее время поддерживает узел.</span><span class="sxs-lookup"><span data-stu-id="50148-107">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50148-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="50148-108">Return Value</span></span>  
  
|<span data-ttu-id="50148-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50148-109">HRESULT</span></span>|<span data-ttu-id="50148-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="50148-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50148-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="50148-111">S_OK</span></span>|<span data-ttu-id="50148-112">`GetMinThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="50148-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="50148-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50148-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50148-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="50148-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50148-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50148-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50148-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="50148-116">The call timed out.</span></span>|  
|<span data-ttu-id="50148-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50148-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50148-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="50148-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50148-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50148-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50148-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="50148-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50148-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50148-121">E_FAIL</span></span>|<span data-ttu-id="50148-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="50148-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50148-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="50148-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50148-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50148-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50148-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="50148-125">E_NOTIMPL</span></span>|<span data-ttu-id="50148-126">Узел не предоставляет реализацию `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="50148-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50148-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="50148-127">Remarks</span></span>  

 <span data-ttu-id="50148-128">Узлу не требуется предоставлять реализацию `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="50148-128">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="50148-129">В этом случае он должен возвращать значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="50148-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50148-130">Требования</span><span class="sxs-lookup"><span data-stu-id="50148-130">Requirements</span></span>  

 <span data-ttu-id="50148-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50148-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50148-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50148-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50148-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50148-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50148-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50148-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50148-135">См. также</span><span class="sxs-lookup"><span data-stu-id="50148-135">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="50148-136">Метод GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="50148-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="50148-137">Метод SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="50148-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="50148-138">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="50148-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
