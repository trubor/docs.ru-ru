---
description: 'Дополнительные сведения о методе: IHostTaskManager:: EndThreadAffinity'
title: Метод IHostTaskManager::EndThreadAffinity
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 0bbe42d8e14d20fb5be18fe7ebb266100ae72fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789428"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="98b6b-103">Метод IHostTaskManager::EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="98b6b-103">IHostTaskManager::EndThreadAffinity Method</span></span>

<span data-ttu-id="98b6b-104">Уведомляет узел о выходе управляемого кода за время, в течение которого текущая задача не должна быть перемещена в другой поток операционной системы, после предыдущего вызова [IHostTaskManager:: BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="98b6b-104">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98b6b-105">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="98b6b-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="98b6b-106">Return Value</span></span>  
  
|<span data-ttu-id="98b6b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98b6b-107">HRESULT</span></span>|<span data-ttu-id="98b6b-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="98b6b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98b6b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="98b6b-109">S_OK</span></span>|<span data-ttu-id="98b6b-110">`EndThreadAffinity` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="98b6b-110">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="98b6b-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98b6b-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98b6b-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="98b6b-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98b6b-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98b6b-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98b6b-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="98b6b-114">The call timed out.</span></span>|  
|<span data-ttu-id="98b6b-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98b6b-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98b6b-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="98b6b-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98b6b-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98b6b-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98b6b-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="98b6b-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98b6b-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98b6b-119">E_FAIL</span></span>|<span data-ttu-id="98b6b-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="98b6b-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98b6b-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="98b6b-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98b6b-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98b6b-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98b6b-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="98b6b-123">E_UNEXPECTED</span></span>|<span data-ttu-id="98b6b-124">`EndThreadAffinity` был вызван без ранее соответствующего вызова `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="98b6b-124">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98b6b-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="98b6b-125">Remarks</span></span>  

 <span data-ttu-id="98b6b-126">Среда CLR выполняет соответствующий вызов `BeginThreadAffinity` в текущей задаче перед вызовом метода `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="98b6b-126">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="98b6b-127">В отсутствие такого соответствующего вызова реализация [IHostTaskManager](ihosttaskmanager-interface.md) должна возвращать E_UNEXPECTED и не предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="98b6b-127">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98b6b-128">Требования</span><span class="sxs-lookup"><span data-stu-id="98b6b-128">Requirements</span></span>  

 <span data-ttu-id="98b6b-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98b6b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98b6b-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98b6b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98b6b-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98b6b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98b6b-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98b6b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b6b-133">См. также</span><span class="sxs-lookup"><span data-stu-id="98b6b-133">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="98b6b-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="98b6b-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="98b6b-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="98b6b-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="98b6b-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="98b6b-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="98b6b-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="98b6b-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
