---
description: 'Дополнительные сведения о методе: IHostTaskManager:: Sleep'
title: Метод IHostTaskManager::Sleep
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: fedb87c6bd4558a2aa6158299551327cb2271d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789376"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="40ca3-103">Метод IHostTaskManager::Sleep</span><span class="sxs-lookup"><span data-stu-id="40ca3-103">IHostTaskManager::Sleep Method</span></span>

<span data-ttu-id="40ca3-104">Уведомляет узел о том, что текущая задача переходит в спящий режим.</span><span class="sxs-lookup"><span data-stu-id="40ca3-104">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ca3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40ca3-105">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40ca3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="40ca3-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="40ca3-107">окне Интервал времени в миллисекундах, в течение которого поток будет в спящем режиме.</span><span class="sxs-lookup"><span data-stu-id="40ca3-107">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="40ca3-108">окне Одно из значений перечисления [WAIT_OPTION](wait-option-enumeration.md) , указывающее, какое действие должно предпринять узел при блокировке этого действия.</span><span class="sxs-lookup"><span data-stu-id="40ca3-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40ca3-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="40ca3-109">Return Value</span></span>  
  
|<span data-ttu-id="40ca3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40ca3-110">HRESULT</span></span>|<span data-ttu-id="40ca3-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="40ca3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40ca3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="40ca3-112">S_OK</span></span>|<span data-ttu-id="40ca3-113">`Sleep` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="40ca3-113">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="40ca3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40ca3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40ca3-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="40ca3-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40ca3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40ca3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40ca3-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="40ca3-117">The call timed out.</span></span>|  
|<span data-ttu-id="40ca3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40ca3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40ca3-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="40ca3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40ca3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40ca3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40ca3-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="40ca3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40ca3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40ca3-122">E_FAIL</span></span>|<span data-ttu-id="40ca3-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="40ca3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40ca3-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="40ca3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40ca3-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="40ca3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40ca3-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="40ca3-126">Remarks</span></span>  

 <span data-ttu-id="40ca3-127">Среда CLR обычно вызывает `IHostTaskManager::Sleep` метод <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> , когда вызывается из пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="40ca3-127">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ca3-128">Требования</span><span class="sxs-lookup"><span data-stu-id="40ca3-128">Requirements</span></span>  

 <span data-ttu-id="40ca3-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ca3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ca3-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40ca3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40ca3-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40ca3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ca3-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ca3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ca3-133">См. также</span><span class="sxs-lookup"><span data-stu-id="40ca3-133">See also</span></span>

- [<span data-ttu-id="40ca3-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="40ca3-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="40ca3-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="40ca3-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="40ca3-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="40ca3-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="40ca3-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="40ca3-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
