---
description: 'Дополнительные сведения о методе ICLRTask:: Abort'
title: Метод ICLRTask::Abort
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: ddb761ac50d7401180355236aa8fdc22cca1c580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785015"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="35821-103">Метод ICLRTask::Abort</span><span class="sxs-lookup"><span data-stu-id="35821-103">ICLRTask::Abort Method</span></span>

<span data-ttu-id="35821-104">Запрашивает прекращение средой CLR задачи, которую представляет текущий экземпляр [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="35821-104">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35821-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35821-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35821-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="35821-106">Return Value</span></span>  
  
|<span data-ttu-id="35821-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35821-107">HRESULT</span></span>|<span data-ttu-id="35821-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="35821-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35821-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="35821-109">S_OK</span></span>|<span data-ttu-id="35821-110">`Abort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="35821-110">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="35821-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35821-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35821-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="35821-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35821-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35821-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35821-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="35821-114">The call timed out.</span></span>|  
|<span data-ttu-id="35821-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35821-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35821-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="35821-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35821-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35821-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35821-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="35821-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35821-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35821-119">E_FAIL</span></span>|<span data-ttu-id="35821-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="35821-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35821-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="35821-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35821-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="35821-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35821-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="35821-123">Remarks</span></span>  

 <span data-ttu-id="35821-124">Среда CLR вызывает исключение <xref:System.Threading.ThreadAbortException> при вызове узла `Abort` .</span><span class="sxs-lookup"><span data-stu-id="35821-124">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="35821-125">Он возвращает сразу после инициализации сведений об исключении, не дожидаясь выполнения пользовательского кода, например методов завершения или механизмов обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="35821-125">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="35821-126">Вызовы, `Abort` таким путем, быстро возвращают.</span><span class="sxs-lookup"><span data-stu-id="35821-126">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35821-127">Требования</span><span class="sxs-lookup"><span data-stu-id="35821-127">Requirements</span></span>  

 <span data-ttu-id="35821-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35821-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35821-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="35821-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35821-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35821-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35821-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35821-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35821-132">См. также</span><span class="sxs-lookup"><span data-stu-id="35821-132">See also</span></span>

- [<span data-ttu-id="35821-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="35821-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="35821-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="35821-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="35821-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="35821-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="35821-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="35821-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
