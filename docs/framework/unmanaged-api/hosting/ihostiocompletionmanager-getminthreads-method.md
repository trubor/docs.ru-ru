---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: GetMinThreads'
title: Метод IHostIoCompletionManager::GetMinThreads
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: 73b8d8cbff3777fe6aa956f282d3da5d4ac1b5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708524"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="b0f94-103">Метод IHostIoCompletionManager::GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="b0f94-103">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="b0f94-104">Возвращает минимальное число потоков, которые предоставляет узел для обработки запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="b0f94-104">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f94-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0f94-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0f94-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0f94-106">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="b0f94-107">заполняет Указатель на минимальное количество потоков, предоставляемых узлом для обработки запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="b0f94-107">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0f94-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b0f94-108">Return Value</span></span>  
  
|<span data-ttu-id="b0f94-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0f94-109">HRESULT</span></span>|<span data-ttu-id="b0f94-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="b0f94-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0f94-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0f94-111">S_OK</span></span>|<span data-ttu-id="b0f94-112">`GetMinThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b0f94-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b0f94-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b0f94-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b0f94-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b0f94-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b0f94-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b0f94-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b0f94-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b0f94-116">The call timed out.</span></span>|  
|<span data-ttu-id="b0f94-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0f94-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b0f94-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b0f94-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b0f94-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b0f94-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b0f94-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b0f94-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b0f94-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0f94-121">E_FAIL</span></span>|<span data-ttu-id="b0f94-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b0f94-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b0f94-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b0f94-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b0f94-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b0f94-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b0f94-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b0f94-125">E_NOTIMPL</span></span>|<span data-ttu-id="b0f94-126">Узел не предоставляет реализацию `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="b0f94-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0f94-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0f94-127">Remarks</span></span>  

 <span data-ttu-id="b0f94-128">Узлу может потребоваться эксклюзивный контроль над числом потоков, выделенных для запросов на обслуживание операций ввода-вывода, по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="b0f94-128">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b0f94-129">По этой причине узел не является обязательным для реализации `GetMinThreads` .</span><span class="sxs-lookup"><span data-stu-id="b0f94-129">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="b0f94-130">В этом случае узел должен вернуть E_NOTIMPL из этого метода.</span><span class="sxs-lookup"><span data-stu-id="b0f94-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0f94-131">Требования</span><span class="sxs-lookup"><span data-stu-id="b0f94-131">Requirements</span></span>  

 <span data-ttu-id="b0f94-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0f94-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0f94-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0f94-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0f94-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0f94-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0f94-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0f94-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f94-136">См. также</span><span class="sxs-lookup"><span data-stu-id="b0f94-136">See also</span></span>

- [<span data-ttu-id="b0f94-137">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b0f94-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b0f94-138">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="b0f94-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
