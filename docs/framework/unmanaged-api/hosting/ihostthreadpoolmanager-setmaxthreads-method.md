---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: SetMaxThreads'
title: Метод IHostThreadPoolManager::SetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 83266b05f639c0aa63e492bca525cbbf09a30775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671247"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="ff174-103">Метод IHostThreadPoolManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="ff174-103">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="ff174-104">Задает максимальное число потоков, которые узел может поддерживать в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="ff174-104">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff174-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff174-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff174-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ff174-106">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="ff174-107">Максимальное количество рабочих потоков в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="ff174-107">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff174-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ff174-108">Return Value</span></span>  
  
|<span data-ttu-id="ff174-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff174-109">HRESULT</span></span>|<span data-ttu-id="ff174-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="ff174-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff174-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff174-111">S_OK</span></span>|<span data-ttu-id="ff174-112">`SetMaxThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ff174-112">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ff174-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff174-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff174-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ff174-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff174-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff174-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff174-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ff174-116">The call timed out.</span></span>|  
|<span data-ttu-id="ff174-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff174-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff174-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ff174-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff174-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff174-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff174-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ff174-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff174-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff174-121">E_FAIL</span></span>|<span data-ttu-id="ff174-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ff174-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ff174-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ff174-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff174-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff174-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ff174-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ff174-125">E_NOTIMPL</span></span>|<span data-ttu-id="ff174-126">Узел не предоставляет реализацию `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="ff174-126">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff174-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff174-127">Remarks</span></span>  

 <span data-ttu-id="ff174-128">Узел не требуется, чтобы разрешить среде CLR настраивать размер пула потоков.</span><span class="sxs-lookup"><span data-stu-id="ff174-128">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="ff174-129">Некоторым узлам может потребоваться монопольный контроль над пулом потоков по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="ff174-129">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="ff174-130">В этом случае узел должен вернуть значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ff174-130">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff174-131">Требования</span><span class="sxs-lookup"><span data-stu-id="ff174-131">Requirements</span></span>  

 <span data-ttu-id="ff174-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff174-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff174-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff174-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff174-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff174-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff174-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff174-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff174-136">См. также</span><span class="sxs-lookup"><span data-stu-id="ff174-136">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="ff174-137">Метод GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="ff174-137">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="ff174-138">Метод SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="ff174-138">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="ff174-139">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="ff174-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
