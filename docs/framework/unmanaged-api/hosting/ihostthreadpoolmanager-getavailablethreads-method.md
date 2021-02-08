---
description: 'Дополнительные сведения о методе: IHostThreadPoolManager:: GetAvailableThreads'
title: Метод IHostThreadPoolManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 95ecaa5757442bb384d303c1f8dafa342bd62f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789338"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="8ad7c-103">Метод IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="8ad7c-103">IHostThreadPoolManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="8ad7c-104">Возвращает число потоков в пуле потоков, которые в данный момент не обрабатывают рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-104">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad7c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8ad7c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad7c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8ad7c-106">Parameters</span></span>  

 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="8ad7c-107">заполняет Указатель на число потоков в пуле потоков, которые в данный момент не обрабатывают рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-107">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ad7c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8ad7c-108">Return Value</span></span>  
  
|<span data-ttu-id="8ad7c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ad7c-109">HRESULT</span></span>|<span data-ttu-id="8ad7c-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="8ad7c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ad7c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ad7c-111">S_OK</span></span>|<span data-ttu-id="8ad7c-112">`GetAvailableThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="8ad7c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ad7c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ad7c-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ad7c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ad7c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ad7c-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-116">The call timed out.</span></span>|  
|<span data-ttu-id="8ad7c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ad7c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ad7c-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ad7c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ad7c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ad7c-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ad7c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ad7c-121">E_FAIL</span></span>|<span data-ttu-id="8ad7c-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ad7c-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ad7c-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ad7c-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8ad7c-125">E_NOTIMPL</span></span>|<span data-ttu-id="8ad7c-126">Узел не предоставляет реализацию `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="8ad7c-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ad7c-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="8ad7c-127">Remarks</span></span>  

 <span data-ttu-id="8ad7c-128">Если узел не предоставляет реализацию `GetAvailableThreads` , он должен возвращать значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8ad7c-128">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad7c-129">Требования</span><span class="sxs-lookup"><span data-stu-id="8ad7c-129">Requirements</span></span>  

 <span data-ttu-id="8ad7c-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad7c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad7c-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ad7c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ad7c-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ad7c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ad7c-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad7c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad7c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="8ad7c-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8ad7c-135">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="8ad7c-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
