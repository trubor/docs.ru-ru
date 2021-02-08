---
description: 'Дополнительные сведения о методе: ICLRIoCompletionManager:: OnComplete'
title: Метод ICLRIoCompletionManager::OnComplete
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: d54b189debdfc2959676b53fd3fb51b2c10dce17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789892"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="1c5ca-103">Метод ICLRIoCompletionManager::OnComplete</span><span class="sxs-lookup"><span data-stu-id="1c5ca-103">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="1c5ca-104">Уведомляет среду CLR о состоянии запроса ввода-вывода, выполненного с помощью вызова метода [IHostIoCompletionManager:: BIND](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c5ca-104">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c5ca-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c5ca-105">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c5ca-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c5ca-106">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="1c5ca-107">окне Значение HRESULT, указывающее состояние операции привязки.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-107">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="1c5ca-108">S_OK указывает, что операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-108">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="1c5ca-109">HOST_E_INTERRUPTED указывает, что вызов прерван до завершения.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-109">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="1c5ca-110">E_FAIL указывает, что произошла неизвестная, Неустранимая фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-110">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="1c5ca-111">окне Число байтов, передаваемых во время обработки запроса ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-111">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="1c5ca-112">окне Указатель на `OVERLAPPED` структуру, которая была передана в вызов `IHostIoCompletionManager::Bind` метода.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-112">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c5ca-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1c5ca-113">Return Value</span></span>  
  
|<span data-ttu-id="1c5ca-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c5ca-114">HRESULT</span></span>|<span data-ttu-id="1c5ca-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="1c5ca-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c5ca-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c5ca-116">S_OK</span></span>|<span data-ttu-id="1c5ca-117">`OnComplete` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-117">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="1c5ca-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c5ca-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c5ca-119">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c5ca-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c5ca-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c5ca-121">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-121">The call timed out.</span></span>|  
|<span data-ttu-id="1c5ca-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c5ca-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c5ca-123">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c5ca-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c5ca-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c5ca-125">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c5ca-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c5ca-126">E_FAIL</span></span>|<span data-ttu-id="1c5ca-127">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c5ca-128">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c5ca-129">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c5ca-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c5ca-130">Remarks</span></span>  

 <span data-ttu-id="1c5ca-131">Если узел реализует абстракцию завершения ввода-вывода, среда CLR делает запросы ввода-вывода через узел с помощью методов [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1c5ca-131">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="1c5ca-132">Затем узел вызывает метод, `OnComplete` чтобы уведомить среду выполнения о результатах таких запросов.</span><span class="sxs-lookup"><span data-stu-id="1c5ca-132">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c5ca-133">Требования</span><span class="sxs-lookup"><span data-stu-id="1c5ca-133">Requirements</span></span>  

 <span data-ttu-id="1c5ca-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c5ca-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c5ca-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c5ca-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c5ca-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c5ca-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c5ca-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c5ca-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5ca-138">См. также</span><span class="sxs-lookup"><span data-stu-id="1c5ca-138">See also</span></span>

- [<span data-ttu-id="1c5ca-139">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1c5ca-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1c5ca-140">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="1c5ca-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1c5ca-141">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="1c5ca-141">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
