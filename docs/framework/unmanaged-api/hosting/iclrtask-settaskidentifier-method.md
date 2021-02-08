---
description: 'Дополнительные сведения о методе ICLRTask:: SetTaskIdentifier'
title: Метод ICLRTask::SetTaskIdentifier
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e746d8ec96d16f7761dd49ac814ddbed073c2686
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784955"
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="b736b-103">Метод ICLRTask::SetTaskIdentifier</span><span class="sxs-lookup"><span data-stu-id="b736b-103">ICLRTask::SetTaskIdentifier Method</span></span>

<span data-ttu-id="b736b-104">Инструктирует среду CLR, чтобы связать указанное значение идентификатора с задачей, представленной текущим экземпляром [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b736b-104">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b736b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b736b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b736b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b736b-106">Parameters</span></span>  

 `Asked`  
 <span data-ttu-id="b736b-107">окне Уникальный идентификатор среды CLR, связываемый с задачей, представленной текущим `ICLRTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="b736b-107">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b736b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b736b-108">Return Value</span></span>  
  
|<span data-ttu-id="b736b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b736b-109">HRESULT</span></span>|<span data-ttu-id="b736b-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="b736b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b736b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b736b-111">S_OK</span></span>|<span data-ttu-id="b736b-112">`SetTaskIdentifier` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b736b-112">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="b736b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b736b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b736b-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b736b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b736b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b736b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b736b-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b736b-116">The call timed out.</span></span>|  
|<span data-ttu-id="b736b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b736b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b736b-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b736b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b736b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b736b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b736b-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b736b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b736b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b736b-121">E_FAIL</span></span>|<span data-ttu-id="b736b-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b736b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b736b-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b736b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b736b-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b736b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b736b-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="b736b-125">Remarks</span></span>  

 <span data-ttu-id="b736b-126">Узел может связать идентификатор с задачей, чтобы упростить интеграцию среды CLR и узла в среде отладки.</span><span class="sxs-lookup"><span data-stu-id="b736b-126">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="b736b-127">Идентификатор не имеет смысла для CLR.</span><span class="sxs-lookup"><span data-stu-id="b736b-127">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="b736b-128">Среда CLR передает ее в приложение отладчика.</span><span class="sxs-lookup"><span data-stu-id="b736b-128">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="b736b-129">Отладчик может использовать этот идентификатор для связывания стека вызовов CLR с стеком вызовов узла и включения соответствующей информации трассировки при просмотре в пользовательском интерфейсе отладчика.</span><span class="sxs-lookup"><span data-stu-id="b736b-129">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b736b-130">Требования</span><span class="sxs-lookup"><span data-stu-id="b736b-130">Requirements</span></span>  

 <span data-ttu-id="b736b-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b736b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b736b-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b736b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b736b-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b736b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b736b-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b736b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b736b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="b736b-135">See also</span></span>

- [<span data-ttu-id="b736b-136">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b736b-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b736b-137">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b736b-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b736b-138">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="b736b-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b736b-139">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b736b-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
