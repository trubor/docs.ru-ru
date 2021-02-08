---
description: 'Дополнительные сведения о методе ICLRTask:: Иелдтаск'
title: Метод ICLRTask::YieldTask
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: b72b31b0a1c10a2b0b1e2ad379b140ff33419fa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784929"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="d219b-103">Метод ICLRTask::YieldTask</span><span class="sxs-lookup"><span data-stu-id="d219b-103">ICLRTask::YieldTask Method</span></span>

<span data-ttu-id="d219b-104">Запрашивает, что среда CLR должна отложить задачу, представляемую текущим экземпляром [ICLRTask](iclrtask-interface.md) , и сделать процессор доступным для других задач.</span><span class="sxs-lookup"><span data-stu-id="d219b-104">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d219b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d219b-105">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d219b-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d219b-106">Return Value</span></span>  
  
|<span data-ttu-id="d219b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d219b-107">HRESULT</span></span>|<span data-ttu-id="d219b-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="d219b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d219b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="d219b-109">S_OK</span></span>|<span data-ttu-id="d219b-110">`YieldTask` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d219b-110">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="d219b-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d219b-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d219b-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d219b-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d219b-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d219b-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d219b-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d219b-114">The call timed out.</span></span>|  
|<span data-ttu-id="d219b-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d219b-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d219b-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d219b-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d219b-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d219b-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d219b-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d219b-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d219b-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d219b-119">E_FAIL</span></span>|<span data-ttu-id="d219b-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d219b-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d219b-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d219b-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d219b-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d219b-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d219b-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="d219b-123">Remarks</span></span>  

 <span data-ttu-id="d219b-124">Вызовы узла `YieldTask` для запроса ресурсов процессора для других задач или процессов.</span><span class="sxs-lookup"><span data-stu-id="d219b-124">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="d219b-125">Этот метод в основном предназначен для того, чтобы долго выполняемый код выдать время ЦП.</span><span class="sxs-lookup"><span data-stu-id="d219b-125">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="d219b-126">Среда выполнения пытается разместить задачу, которая представляет текущий `ICLRTask` экземпляр, в состоянии, в котором оно может подавать время обработки, но не гарантирует успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="d219b-126">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d219b-127">Требования</span><span class="sxs-lookup"><span data-stu-id="d219b-127">Requirements</span></span>  

 <span data-ttu-id="d219b-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d219b-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d219b-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d219b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d219b-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d219b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d219b-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d219b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d219b-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d219b-132">See also</span></span>

- [<span data-ttu-id="d219b-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d219b-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d219b-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d219b-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d219b-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="d219b-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d219b-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d219b-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
