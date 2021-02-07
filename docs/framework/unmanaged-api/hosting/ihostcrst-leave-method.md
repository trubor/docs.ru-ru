---
description: 'Дополнительные сведения о методе: IHostCrst:: Leave'
title: Метод IHostCrst::Leave
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: b00e62c7b2683ab6024a7c9b8de4645ceb59fb02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708844"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="8f116-103">Метод IHostCrst::Leave</span><span class="sxs-lookup"><span data-stu-id="8f116-103">IHostCrst::Leave Method</span></span>

<span data-ttu-id="8f116-104">Оставляет критический раздел, представленный текущим экземпляром [IHostCrst](ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8f116-104">Leaves the critical section that is represented by the current instance of [IHostCrst](ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f116-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f116-105">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8f116-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8f116-106">Return Value</span></span>  
  
|<span data-ttu-id="8f116-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f116-107">HRESULT</span></span>|<span data-ttu-id="8f116-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="8f116-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f116-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f116-109">S_OK</span></span>|<span data-ttu-id="8f116-110">`Leave` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="8f116-110">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="8f116-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f116-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f116-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8f116-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f116-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f116-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f116-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="8f116-114">The call timed out.</span></span>|  
|<span data-ttu-id="8f116-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f116-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f116-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="8f116-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f116-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f116-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f116-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="8f116-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f116-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f116-119">E_FAIL</span></span>|<span data-ttu-id="8f116-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="8f116-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f116-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8f116-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f116-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f116-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f116-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f116-123">Remarks</span></span>  

 <span data-ttu-id="8f116-124">`Leave` позволяет среде CLR напрямую взаимодействовать с реализацией потоковой реализации узла вместо использования соответствующей `LeaveCriticalSection` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="8f116-124">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="8f116-125">Поток, который принимает владение критической секцией, представленной текущим `IHostCrst` экземпляром, должен вызывать `Leave` один раз для каждого входа в критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="8f116-125">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f116-126">Требования</span><span class="sxs-lookup"><span data-stu-id="8f116-126">Requirements</span></span>  

 <span data-ttu-id="8f116-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f116-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f116-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f116-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f116-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f116-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f116-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f116-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f116-131">См. также</span><span class="sxs-lookup"><span data-stu-id="8f116-131">See also</span></span>

- [<span data-ttu-id="8f116-132">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="8f116-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8f116-133">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="8f116-133">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="8f116-134">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="8f116-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
