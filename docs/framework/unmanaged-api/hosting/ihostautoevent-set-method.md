---
description: 'Дополнительные сведения о методе: Ихостаутоевент:: Set'
title: Метод IHostAutoEvent::Set
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: e4ba63b5250a383431e410cd6e552f8344fedf5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708922"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="f37cb-103">Метод IHostAutoEvent::Set</span><span class="sxs-lookup"><span data-stu-id="f37cb-103">IHostAutoEvent::Set Method</span></span>

<span data-ttu-id="f37cb-104">Устанавливает для текущего экземпляра [ихостаутоевент](ihostautoevent-interface.md) сигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="f37cb-104">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f37cb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f37cb-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f37cb-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f37cb-106">Return Value</span></span>  
  
|<span data-ttu-id="f37cb-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f37cb-107">HRESULT</span></span>|<span data-ttu-id="f37cb-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="f37cb-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f37cb-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f37cb-109">S_OK</span></span>|<span data-ttu-id="f37cb-110">`Set` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="f37cb-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="f37cb-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f37cb-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f37cb-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="f37cb-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f37cb-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f37cb-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f37cb-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="f37cb-114">The call timed out.</span></span>|  
|<span data-ttu-id="f37cb-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f37cb-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f37cb-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="f37cb-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f37cb-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f37cb-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f37cb-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="f37cb-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f37cb-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f37cb-119">E_FAIL</span></span>|<span data-ttu-id="f37cb-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="f37cb-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f37cb-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="f37cb-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f37cb-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f37cb-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f37cb-123">Требования</span><span class="sxs-lookup"><span data-stu-id="f37cb-123">Requirements</span></span>  

 <span data-ttu-id="f37cb-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f37cb-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f37cb-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f37cb-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f37cb-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f37cb-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f37cb-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f37cb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f37cb-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f37cb-128">See also</span></span>

- [<span data-ttu-id="f37cb-129">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="f37cb-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f37cb-130">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="f37cb-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="f37cb-131">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="f37cb-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="f37cb-132">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f37cb-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
