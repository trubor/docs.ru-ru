---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: SetMinThreads'
title: Метод IHostIoCompletionManager::SetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: aade5ebb9e318d51296e52e7cf1c31c6ea9e4f6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708246"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="e8f15-103">Метод IHostIoCompletionManager::SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="e8f15-103">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="e8f15-104">Задает минимальное число потоков, которое узел должен выделить при завершении ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e8f15-104">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f15-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8f15-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8f15-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8f15-106">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="e8f15-107">окне Минимальное число потоков завершения ввода-вывода, которые должен создать узел.</span><span class="sxs-lookup"><span data-stu-id="e8f15-107">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8f15-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e8f15-108">Return Value</span></span>  
  
|<span data-ttu-id="e8f15-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8f15-109">HRESULT</span></span>|<span data-ttu-id="e8f15-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="e8f15-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8f15-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8f15-111">S_OK</span></span>|<span data-ttu-id="e8f15-112">`SetMinThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e8f15-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e8f15-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8f15-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8f15-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e8f15-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8f15-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8f15-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8f15-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="e8f15-116">The call timed out.</span></span>|  
|<span data-ttu-id="e8f15-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8f15-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8f15-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="e8f15-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8f15-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8f15-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8f15-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="e8f15-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8f15-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8f15-121">E_FAIL</span></span>|<span data-ttu-id="e8f15-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e8f15-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8f15-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e8f15-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8f15-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8f15-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8f15-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e8f15-125">E_NOTIMPL</span></span>|<span data-ttu-id="e8f15-126">Узел не предоставляет реализацию `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="e8f15-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f15-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8f15-127">Remarks</span></span>  

 <span data-ttu-id="e8f15-128">Узлу может потребоваться эксклюзивный контроль над количеством потоков, которые могут быть выделены для обработки запросов ввода-вывода, по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="e8f15-128">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="e8f15-129">По этой причине узел не является обязательным для реализации `SetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="e8f15-129">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="e8f15-130">В этом случае узел должен вернуть E_NOTIMPL из этого метода.</span><span class="sxs-lookup"><span data-stu-id="e8f15-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8f15-131">Требования</span><span class="sxs-lookup"><span data-stu-id="e8f15-131">Requirements</span></span>  

 <span data-ttu-id="e8f15-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f15-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f15-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8f15-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8f15-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8f15-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8f15-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f15-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f15-136">См. также</span><span class="sxs-lookup"><span data-stu-id="e8f15-136">See also</span></span>

- [<span data-ttu-id="e8f15-137">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e8f15-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e8f15-138">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e8f15-138">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="e8f15-139">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="e8f15-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
