---
description: 'Дополнительные сведения о методе IHostTask:: Join'
title: Метод IHostTask::Join
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 8231401ab01ee040f225b78a52b61eb7d59af1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784656"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="7726c-103">Метод IHostTask::Join</span><span class="sxs-lookup"><span data-stu-id="7726c-103">IHostTask::Join Method</span></span>

<span data-ttu-id="7726c-104">Блокирует вызывающую задачу до тех пор, пока не завершится задача, представленная текущим экземпляром [IHostTask](ihosttask-interface.md) , истечет указанный интервал времени, или будет вызван метод [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7726c-104">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7726c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7726c-105">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7726c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7726c-106">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="7726c-107">окне Интервал времени в миллисекундах, в течение которого ожидается завершение задачи.</span><span class="sxs-lookup"><span data-stu-id="7726c-107">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="7726c-108">Если этот интервал истекает до завершения задачи, вызывающая задача разблокируется.</span><span class="sxs-lookup"><span data-stu-id="7726c-108">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="7726c-109">окне Одно из значений [WAIT_OPTION](wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7726c-109">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="7726c-110">Значение WAIT_ALERTABLE указывает узлу вывести задачу из спящего режима, если `Alert` вызывается до `milliseconds` истечения времени.</span><span class="sxs-lookup"><span data-stu-id="7726c-110">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7726c-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7726c-111">Return Value</span></span>  
  
|<span data-ttu-id="7726c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7726c-112">HRESULT</span></span>|<span data-ttu-id="7726c-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="7726c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7726c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7726c-114">S_OK</span></span>|<span data-ttu-id="7726c-115">`Join` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7726c-115">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="7726c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7726c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7726c-117">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7726c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7726c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7726c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7726c-119">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7726c-119">The call timed out.</span></span>|  
|<span data-ttu-id="7726c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7726c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7726c-121">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7726c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7726c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7726c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7726c-123">Событие было отменено, пока заблокированный поток или волокно ожидают его, или текущий `IHostTask` экземпляр не связан с задачей.</span><span class="sxs-lookup"><span data-stu-id="7726c-123">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="7726c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7726c-124">E_FAIL</span></span>|<span data-ttu-id="7726c-125">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7726c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7726c-126">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7726c-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7726c-127">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7726c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7726c-128">Требования</span><span class="sxs-lookup"><span data-stu-id="7726c-128">Requirements</span></span>  

 <span data-ttu-id="7726c-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7726c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7726c-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7726c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7726c-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7726c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7726c-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7726c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7726c-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7726c-133">See also</span></span>

- [<span data-ttu-id="7726c-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7726c-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7726c-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7726c-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7726c-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="7726c-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7726c-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7726c-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7726c-138">Перечисление WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="7726c-138">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
