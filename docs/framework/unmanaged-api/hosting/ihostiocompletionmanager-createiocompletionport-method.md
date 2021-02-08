---
description: 'Дополнительные сведения о методе: IHostIoCompletionManager:: CreateIoCompletionPort'
title: Метод IHostIoCompletionManager::CreateIoCompletionPort
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: da4cd595e84c341eb15837ff97f4ba23cac23210
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789441"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="7fef3-103">Метод IHostIoCompletionManager::CreateIoCompletionPort</span><span class="sxs-lookup"><span data-stu-id="7fef3-103">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="7fef3-104">Запрашивает создание узлом нового порта завершения ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="7fef3-104">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fef3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7fef3-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fef3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7fef3-106">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="7fef3-107">заполняет Указатель на обработчик для вновь созданного порта завершения ввода-вывода или 0 (нуль), если не удалось создать порт.</span><span class="sxs-lookup"><span data-stu-id="7fef3-107">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fef3-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7fef3-108">Return Value</span></span>  
  
|<span data-ttu-id="7fef3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fef3-109">HRESULT</span></span>|<span data-ttu-id="7fef3-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="7fef3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fef3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fef3-111">S_OK</span></span>|<span data-ttu-id="7fef3-112">`CreateIoCompletionPort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7fef3-112">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="7fef3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fef3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fef3-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7fef3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fef3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fef3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fef3-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7fef3-116">The call timed out.</span></span>|  
|<span data-ttu-id="7fef3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fef3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fef3-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7fef3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fef3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fef3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fef3-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7fef3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fef3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fef3-121">E_FAIL</span></span>|<span data-ttu-id="7fef3-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7fef3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fef3-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7fef3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fef3-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fef3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7fef3-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7fef3-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7fef3-126">Недостаточно памяти для выделения запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="7fef3-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fef3-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="7fef3-127">Remarks</span></span>  

 <span data-ttu-id="7fef3-128">Среда CLR вызывает `CreateIoCompletionPort` метод, чтобы запросить создание узлом нового порта завершения ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="7fef3-128">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="7fef3-129">Он привязывает операции ввода-вывода к этому порту с помощью вызова метода [IHostIoCompletionManager:: BIND](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7fef3-129">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="7fef3-130">Узел сообщает среде CLR о состоянии, вызывая [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="7fef3-130">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fef3-131">Требования</span><span class="sxs-lookup"><span data-stu-id="7fef3-131">Requirements</span></span>  

 <span data-ttu-id="7fef3-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fef3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fef3-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fef3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fef3-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fef3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fef3-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fef3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fef3-136">См. также</span><span class="sxs-lookup"><span data-stu-id="7fef3-136">See also</span></span>

- [<span data-ttu-id="7fef3-137">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="7fef3-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7fef3-138">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="7fef3-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
