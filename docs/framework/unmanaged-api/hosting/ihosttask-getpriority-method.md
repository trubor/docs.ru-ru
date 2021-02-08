---
description: 'Дополнительные сведения о методе IHostTask:: предшествовал'
title: Метод IHostTask::GetPriority
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: fb64164a54806a362888e93f031713ccc0ac3578
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784695"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="7fce5-103">Метод IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="7fce5-103">IHostTask::GetPriority Method</span></span>

<span data-ttu-id="7fce5-104">Возвращает уровень приоритета потока задачи, представленной текущим экземпляром [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7fce5-104">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fce5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7fce5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fce5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7fce5-106">Parameters</span></span>  

 `pPriority`  
 <span data-ttu-id="7fce5-107">заполняет Указатель на целое число, указывающий уровень приоритета потока задачи, представленной текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="7fce5-107">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fce5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7fce5-108">Return Value</span></span>  
  
|<span data-ttu-id="7fce5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fce5-109">HRESULT</span></span>|<span data-ttu-id="7fce5-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="7fce5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fce5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fce5-111">S_OK</span></span>|<span data-ttu-id="7fce5-112">`GetPriority` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7fce5-112">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="7fce5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fce5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fce5-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7fce5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fce5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fce5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fce5-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7fce5-116">The call timed out.</span></span>|  
|<span data-ttu-id="7fce5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fce5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fce5-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7fce5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fce5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fce5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fce5-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7fce5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fce5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fce5-121">E_FAIL</span></span>|<span data-ttu-id="7fce5-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7fce5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fce5-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7fce5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fce5-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fce5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fce5-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="7fce5-125">Remarks</span></span>  

 <span data-ttu-id="7fce5-126">Значения уровня приоритета потока определяются функцией Win32 `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="7fce5-126">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fce5-127">Требования</span><span class="sxs-lookup"><span data-stu-id="7fce5-127">Requirements</span></span>  

 <span data-ttu-id="7fce5-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fce5-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fce5-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fce5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fce5-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fce5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fce5-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fce5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fce5-132">См. также</span><span class="sxs-lookup"><span data-stu-id="7fce5-132">See also</span></span>

- [<span data-ttu-id="7fce5-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7fce5-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7fce5-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7fce5-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7fce5-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="7fce5-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7fce5-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7fce5-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
