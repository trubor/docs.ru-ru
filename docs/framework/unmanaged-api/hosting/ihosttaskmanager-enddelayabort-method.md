---
description: 'Дополнительные сведения о методе: IHostTaskManager:: EndDelayAbort'
title: Метод IHostTaskManager::EndDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: e0d1c4231d381baf2ff92d187d33714f1c6f3003
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784565"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="20c17-103">Метод IHostTaskManager::EndDelayAbort</span><span class="sxs-lookup"><span data-stu-id="20c17-103">IHostTaskManager::EndDelayAbort Method</span></span>

<span data-ttu-id="20c17-104">Уведомляет узел о выходе управляемого кода за время, в течение которого текущая задача не должна прерываться, после предыдущего вызова [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="20c17-104">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c17-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20c17-105">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="20c17-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="20c17-106">Return Value</span></span>  
  
|<span data-ttu-id="20c17-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20c17-107">HRESULT</span></span>|<span data-ttu-id="20c17-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="20c17-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20c17-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="20c17-109">S_OK</span></span>|<span data-ttu-id="20c17-110">`EndDelayAbort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="20c17-110">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="20c17-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20c17-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20c17-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="20c17-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20c17-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20c17-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20c17-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="20c17-114">The call timed out.</span></span>|  
|<span data-ttu-id="20c17-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20c17-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20c17-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="20c17-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20c17-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20c17-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20c17-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="20c17-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20c17-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20c17-119">E_FAIL</span></span>|<span data-ttu-id="20c17-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="20c17-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20c17-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="20c17-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20c17-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20c17-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="20c17-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="20c17-123">E_UNEXPECTED</span></span>|<span data-ttu-id="20c17-124">`EndDelayAbort` был вызван без соответствующего вызова `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="20c17-124">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20c17-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="20c17-125">Remarks</span></span>  

 <span data-ttu-id="20c17-126">Среда CLR выполняет соответствующий вызов `BeginDelayAbort` в текущей задаче перед вызовом метода `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="20c17-126">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="20c17-127">В отсутствие такого соответствующего вызова реализация [IHostTaskManager](ihosttaskmanager-interface.md) должна возвращать E_UNEXPECTED из `EndDelayAbort` и не должна предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="20c17-127">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c17-128">Требования</span><span class="sxs-lookup"><span data-stu-id="20c17-128">Requirements</span></span>  

 <span data-ttu-id="20c17-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20c17-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c17-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20c17-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20c17-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20c17-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20c17-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c17-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c17-133">См. также</span><span class="sxs-lookup"><span data-stu-id="20c17-133">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="20c17-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="20c17-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="20c17-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="20c17-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="20c17-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="20c17-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="20c17-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="20c17-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
