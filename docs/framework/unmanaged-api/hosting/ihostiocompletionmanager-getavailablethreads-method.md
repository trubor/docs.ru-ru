---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: GetAvailableThreads'
title: Метод IHostIoCompletionManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: d50f79716f72b902102a2a97a0bce5dfe645334f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708562"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="914d0-103">Метод IHostIoCompletionManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="914d0-103">IHostIoCompletionManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="914d0-104">Возвращает количество потоков завершения ввода-вывода из общего числа потоков, управляемых узлом, которые в настоящее время не обслуживают запросы.</span><span class="sxs-lookup"><span data-stu-id="914d0-104">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914d0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="914d0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="914d0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="914d0-106">Parameters</span></span>  

 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="914d0-107">заполняет Указатель на число потоков завершения ввода-вывода, управляемых узлом, которые в настоящее время доступны для запросов на обслуживание.</span><span class="sxs-lookup"><span data-stu-id="914d0-107">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="914d0-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="914d0-108">Return Value</span></span>  
  
|<span data-ttu-id="914d0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="914d0-109">HRESULT</span></span>|<span data-ttu-id="914d0-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="914d0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="914d0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="914d0-111">S_OK</span></span>|<span data-ttu-id="914d0-112">`GetAvailableThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="914d0-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="914d0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="914d0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="914d0-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="914d0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="914d0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="914d0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="914d0-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="914d0-116">The call timed out.</span></span>|  
|<span data-ttu-id="914d0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="914d0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="914d0-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="914d0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="914d0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="914d0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="914d0-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="914d0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="914d0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="914d0-121">E_FAIL</span></span>|<span data-ttu-id="914d0-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="914d0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="914d0-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="914d0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="914d0-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="914d0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="914d0-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="914d0-125">E_NOTIMPL</span></span>|<span data-ttu-id="914d0-126">Узел не предоставляет реализацию `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="914d0-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="914d0-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="914d0-127">Remarks</span></span>  

 <span data-ttu-id="914d0-128">Ведущему приложению может потребоваться монопольный контроль над размером пула потоков завершения ввода-вывода по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="914d0-128">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="914d0-129">Таким образом, хосту не требуется реализовывать `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="914d0-129">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="914d0-130">В этом случае узел должен вернуть E_NOTIMPL из этого метода.</span><span class="sxs-lookup"><span data-stu-id="914d0-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914d0-131">Требования</span><span class="sxs-lookup"><span data-stu-id="914d0-131">Requirements</span></span>  

 <span data-ttu-id="914d0-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914d0-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914d0-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="914d0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="914d0-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="914d0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="914d0-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914d0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914d0-136">См. также</span><span class="sxs-lookup"><span data-stu-id="914d0-136">See also</span></span>

- [<span data-ttu-id="914d0-137">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="914d0-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="914d0-138">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="914d0-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
