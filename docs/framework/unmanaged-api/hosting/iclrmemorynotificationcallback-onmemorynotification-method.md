---
description: 'Дополнительные сведения о методе: ICLRMemoryNotificationCallback:: OnMemoryNotification'
title: Метод ICLRMemoryNotificationCallback::OnMemoryNotification
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: 92041c433fa82bb63afda7968eb8c6e1fa72acb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789919"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="876ec-103">Метод ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="876ec-103">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>

<span data-ttu-id="876ec-104">Уведомляет среду CLR о загрузке памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="876ec-104">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="876ec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="876ec-105">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="876ec-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="876ec-106">Parameters</span></span>  

 `eMemoryAvailable`  
 <span data-ttu-id="876ec-107">окне Одно из значений [емеморяваилабле](ememoryavailable-enumeration.md) , указывающее на нехватку памяти в данный момент на компьютере.</span><span class="sxs-lookup"><span data-stu-id="876ec-107">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="876ec-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="876ec-108">Return Value</span></span>  
  
|<span data-ttu-id="876ec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="876ec-109">HRESULT</span></span>|<span data-ttu-id="876ec-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="876ec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="876ec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="876ec-111">S_OK</span></span>|<span data-ttu-id="876ec-112">`OnMemoryNotification` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="876ec-112">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="876ec-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="876ec-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="876ec-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="876ec-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="876ec-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="876ec-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="876ec-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="876ec-116">The call timed out.</span></span>|  
|<span data-ttu-id="876ec-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="876ec-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="876ec-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="876ec-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="876ec-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="876ec-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="876ec-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="876ec-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="876ec-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="876ec-121">E_FAIL</span></span>|<span data-ttu-id="876ec-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="876ec-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="876ec-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="876ec-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="876ec-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="876ec-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="876ec-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="876ec-125">Remarks</span></span>  

 <span data-ttu-id="876ec-126">Среда CLR регистрирует обратный вызов с `OnMemoryNotification` помощью вызова метода [IHostMemoryManager:: RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="876ec-126">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="876ec-127">Среда выполнения использует сведения, возвращаемые при обратном вызове, чтобы освободить дополнительную память, когда узел сообщает, что ресурсы памяти имеют низкий уровень.</span><span class="sxs-lookup"><span data-stu-id="876ec-127">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="876ec-128">Вызовы `OnMemoryNotification` никогда не блокируются.</span><span class="sxs-lookup"><span data-stu-id="876ec-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="876ec-129">Они всегда возвращают немедленно.</span><span class="sxs-lookup"><span data-stu-id="876ec-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="876ec-130">Требования</span><span class="sxs-lookup"><span data-stu-id="876ec-130">Requirements</span></span>  

 <span data-ttu-id="876ec-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="876ec-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="876ec-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="876ec-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="876ec-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="876ec-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="876ec-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="876ec-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876ec-135">См. также</span><span class="sxs-lookup"><span data-stu-id="876ec-135">See also</span></span>

- [<span data-ttu-id="876ec-136">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="876ec-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="876ec-137">Метод RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="876ec-137">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="876ec-138">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="876ec-138">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
