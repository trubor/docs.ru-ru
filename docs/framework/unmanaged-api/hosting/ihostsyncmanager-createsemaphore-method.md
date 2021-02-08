---
description: 'Дополнительные сведения о методе: метод ihostsyncmanager:: Createsemaphore-'
title: Метод IHostSyncManager::CreateSemaphore
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 5a03ef7532e2ac8357ec015b40cc54942f5420e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784747"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="0ddfb-103">Метод IHostSyncManager::CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="0ddfb-103">IHostSyncManager::CreateSemaphore Method</span></span>

<span data-ttu-id="0ddfb-104">Создает объект [IHostSemaphore](ihostsemaphore-interface.md) для общеязыковой среды выполнения (CLR) для использования в качестве семафора для событий ожидания.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-104">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddfb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ddfb-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ddfb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ddfb-106">Parameters</span></span>  

 `dwInitial`  
 <span data-ttu-id="0ddfb-107">окне Начальное число для `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="0ddfb-107">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="0ddfb-108">окне Максимальное число для `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="0ddfb-108">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="0ddfb-109">заполняет Указатель на адрес `IHostSemaphore` экземпляра или значение null, если не удалось создать семафор.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-109">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ddfb-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ddfb-110">Return Value</span></span>  
  
|<span data-ttu-id="0ddfb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ddfb-111">HRESULT</span></span>|<span data-ttu-id="0ddfb-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="0ddfb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ddfb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ddfb-113">S_OK</span></span>|<span data-ttu-id="0ddfb-114">`CreateSemaphore` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-114">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="0ddfb-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ddfb-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ddfb-116">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ddfb-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ddfb-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ddfb-118">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-118">The call timed out.</span></span>|  
|<span data-ttu-id="0ddfb-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ddfb-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ddfb-120">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ddfb-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ddfb-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ddfb-122">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ddfb-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ddfb-123">E_FAIL</span></span>|<span data-ttu-id="0ddfb-124">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ddfb-125">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ddfb-126">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ddfb-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0ddfb-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0ddfb-128">Недостаточно свободной памяти для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ddfb-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="0ddfb-129">Remarks</span></span>  

 <span data-ttu-id="0ddfb-130">`CreateSemaphore` отражает функцию Win32 с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-130">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="0ddfb-131">`dwInitial`Параметры и `dwMax` используют ту же семантику для счетчика семафора `lInitialCount` , что и Win32 и `lMaximumCount` параметры соответственно.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-131">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="0ddfb-132">`dwInitial` значение должно находиться в диапазоне от 0 до `dwMax` включительно.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-132">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="0ddfb-133">`dwMax` должно быть больше нуля.</span><span class="sxs-lookup"><span data-stu-id="0ddfb-133">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ddfb-134">Требования</span><span class="sxs-lookup"><span data-stu-id="0ddfb-134">Requirements</span></span>  

 <span data-ttu-id="0ddfb-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ddfb-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ddfb-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ddfb-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ddfb-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ddfb-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ddfb-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ddfb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddfb-139">См. также</span><span class="sxs-lookup"><span data-stu-id="0ddfb-139">See also</span></span>

- [<span data-ttu-id="0ddfb-140">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="0ddfb-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0ddfb-141">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="0ddfb-141">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="0ddfb-142">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="0ddfb-142">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
