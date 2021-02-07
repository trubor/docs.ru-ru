---
description: 'Дополнительные сведения о методе: IHostCrst:: Сетспинкаунт'
title: Метод IHostCrst::SetSpinCount
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: f04281d2649f210e64fc4c0585eb7d52be3e8ec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721233"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="1ae4a-103">Метод IHostCrst::SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="1ae4a-103">IHostCrst::SetSpinCount Method</span></span>

<span data-ttu-id="1ae4a-104">Задает счетчик прокрутки для текущего экземпляра [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1ae4a-104">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae4a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ae4a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ae4a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ae4a-106">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="1ae4a-107">окне Новое количество прокруток для текущего `IHostCrst` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-107">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ae4a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1ae4a-108">Return Value</span></span>  
  
|<span data-ttu-id="1ae4a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ae4a-109">HRESULT</span></span>|<span data-ttu-id="1ae4a-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="1ae4a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ae4a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ae4a-111">S_OK</span></span>|<span data-ttu-id="1ae4a-112">`SetSpinCount` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-112">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="1ae4a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ae4a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ae4a-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ae4a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ae4a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ae4a-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-116">The call timed out.</span></span>|  
|<span data-ttu-id="1ae4a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ae4a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ae4a-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ae4a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ae4a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ae4a-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ae4a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ae4a-121">E_FAIL</span></span>|<span data-ttu-id="1ae4a-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ae4a-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ae4a-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ae4a-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ae4a-125">Remarks</span></span>  

 <span data-ttu-id="1ae4a-126">В многопроцессорных системах, если критическая секция, представленная текущим `IHostCrst` экземпляром, недоступна, вызывающий поток вращает `dwSpinCount` время до вызова [IHostSemaphore:: wait](ihostsemaphore-wait-method.md) для семафора, связанного с критическим разделом.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-126">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="1ae4a-127">Если критическая секция будет свободна во время операции Spin, вызывающий поток не будет выполнять операцию ожидания.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-127">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="1ae4a-128">Использование аналогично `dwSpinCount` использованию параметра с тем же именем в `InitializeCriticalSectionAndSpinCount` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="1ae4a-128">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae4a-129">Требования</span><span class="sxs-lookup"><span data-stu-id="1ae4a-129">Requirements</span></span>  

 <span data-ttu-id="1ae4a-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae4a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae4a-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ae4a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ae4a-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ae4a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ae4a-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae4a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae4a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="1ae4a-134">See also</span></span>

- [<span data-ttu-id="1ae4a-135">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="1ae4a-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1ae4a-136">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="1ae4a-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="1ae4a-137">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="1ae4a-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
