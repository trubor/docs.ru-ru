---
description: 'Дополнительные сведения о методе: IHostTaskManager:: Свитчтотаск'
title: Метод IHostTaskManager::SwitchToTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
ms.openlocfilehash: 6333dcdf7e1bbe6bde575f53f4743a1300c770f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789363"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="28b79-103">Метод IHostTaskManager::SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="28b79-103">IHostTaskManager::SwitchToTask Method</span></span>

<span data-ttu-id="28b79-104">Уведомляет узел о том, что необходимо отключить текущую задачу.</span><span class="sxs-lookup"><span data-stu-id="28b79-104">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b79-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28b79-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28b79-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="28b79-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="28b79-107">окне Одно из значений перечисления [WAIT_OPTION](wait-option-enumeration.md) , указывающее действие, которое должен выполнить узел, если запрошенная операция блокируется.</span><span class="sxs-lookup"><span data-stu-id="28b79-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28b79-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="28b79-108">Return Value</span></span>  
  
|<span data-ttu-id="28b79-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28b79-109">HRESULT</span></span>|<span data-ttu-id="28b79-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="28b79-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28b79-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28b79-111">S_OK</span></span>|<span data-ttu-id="28b79-112">`SwitchToTask` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="28b79-112">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="28b79-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28b79-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28b79-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="28b79-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28b79-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28b79-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28b79-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="28b79-116">The call timed out.</span></span>|  
|<span data-ttu-id="28b79-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28b79-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28b79-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="28b79-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28b79-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28b79-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28b79-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="28b79-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28b79-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28b79-121">E_FAIL</span></span>|<span data-ttu-id="28b79-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="28b79-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28b79-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="28b79-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28b79-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28b79-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28b79-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="28b79-125">Remarks</span></span>  

 <span data-ttu-id="28b79-126">Узел может переключиться на другую задачу по мере необходимости или необходимости.</span><span class="sxs-lookup"><span data-stu-id="28b79-126">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28b79-127">`SwitchToTask` не указывает, к какой задаче узел должен переключиться; Он указывает только задачу, с которой она должна переключаться.</span><span class="sxs-lookup"><span data-stu-id="28b79-127">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28b79-128">Требования</span><span class="sxs-lookup"><span data-stu-id="28b79-128">Requirements</span></span>  

 <span data-ttu-id="28b79-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b79-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b79-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="28b79-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28b79-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28b79-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28b79-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28b79-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b79-133">См. также</span><span class="sxs-lookup"><span data-stu-id="28b79-133">See also</span></span>

- [<span data-ttu-id="28b79-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="28b79-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="28b79-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="28b79-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="28b79-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="28b79-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="28b79-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="28b79-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
