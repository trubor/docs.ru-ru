---
description: 'Дополнительные сведения о методе: IHostTaskManager:: GetCurrentTask'
title: Метод IHostTaskManager::GetCurrentTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: 7e7e516fe4a706fce8b0302f318cfbb164a86eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753813"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="efd81-103">Метод IHostTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="efd81-103">IHostTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="efd81-104">Возвращает указатель интерфейса на задачу, которая выполняется в данный момент в потоке операционной системы, из которого выполняется этот вызов.</span><span class="sxs-lookup"><span data-stu-id="efd81-104">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd81-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="efd81-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd81-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="efd81-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="efd81-107">заполняет Указатель на адрес экземпляра [IHostTask](ihosttask-interface.md) , представляющий выполняемую в данный момент задачу, или значение null, если ни одна из задач в данный момент не выполняется.</span><span class="sxs-lookup"><span data-stu-id="efd81-107">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efd81-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="efd81-108">Return Value</span></span>  
  
|<span data-ttu-id="efd81-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efd81-109">HRESULT</span></span>|<span data-ttu-id="efd81-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="efd81-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efd81-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="efd81-111">S_OK</span></span>|<span data-ttu-id="efd81-112">`GetCurrentTask` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="efd81-112">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="efd81-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efd81-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efd81-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="efd81-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="efd81-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="efd81-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="efd81-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="efd81-116">The call timed out.</span></span>|  
|<span data-ttu-id="efd81-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="efd81-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="efd81-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="efd81-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="efd81-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="efd81-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="efd81-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="efd81-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="efd81-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="efd81-121">E_FAIL</span></span>|<span data-ttu-id="efd81-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="efd81-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="efd81-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="efd81-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="efd81-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="efd81-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="efd81-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="efd81-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="efd81-126">`GetCurrentTask` был вызван в потоке операционной системы за пределами элемента управления узла.</span><span class="sxs-lookup"><span data-stu-id="efd81-126">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efd81-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="efd81-127">Remarks</span></span>  

 <span data-ttu-id="efd81-128">Узел также может присвоить `pTask` параметру значение null, чтобы предотвратить запуск задачи, которая не была инициирована при входе в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="efd81-128">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd81-129">Требования</span><span class="sxs-lookup"><span data-stu-id="efd81-129">Requirements</span></span>  

 <span data-ttu-id="efd81-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd81-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd81-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="efd81-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efd81-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efd81-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efd81-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd81-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd81-134">См. также</span><span class="sxs-lookup"><span data-stu-id="efd81-134">See also</span></span>

- [<span data-ttu-id="efd81-135">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="efd81-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="efd81-136">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="efd81-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="efd81-137">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="efd81-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="efd81-138">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="efd81-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
