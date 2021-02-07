---
description: 'Дополнительные сведения о методе: ICLRTaskManager:: GetCurrentTask'
title: Метод ICLRTaskManager::GetCurrentTask
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: d7435f9099d6a8ceb173afbf79c1d0f5d4005980
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728552"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="cc24d-103">Метод ICLRTaskManager::GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="cc24d-103">ICLRTaskManager::GetCurrentTask Method</span></span>

<span data-ttu-id="cc24d-104">Возвращает экземпляр [ICLRTask](iclrtask-interface.md) , который в данный момент выполняется в потоке операционной системы, из которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="cc24d-104">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc24d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc24d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc24d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cc24d-106">Parameters</span></span>  

 `ppTask`  
 <span data-ttu-id="cc24d-107">заполняет Указатель на адрес `ICLRTask` экземпляра, который в данный момент выполняется в потоке операционной системы, из которого был получен вызов, или значение null, если в данном потоке не выполняется ни одной задачи.</span><span class="sxs-lookup"><span data-stu-id="cc24d-107">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc24d-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cc24d-108">Return Value</span></span>  
  
|<span data-ttu-id="cc24d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc24d-109">HRESULT</span></span>|<span data-ttu-id="cc24d-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="cc24d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc24d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc24d-111">S_OK</span></span>|<span data-ttu-id="cc24d-112">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="cc24d-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="cc24d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc24d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc24d-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cc24d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc24d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc24d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc24d-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cc24d-116">The call timed out.</span></span>|  
|<span data-ttu-id="cc24d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc24d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc24d-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cc24d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc24d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc24d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc24d-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cc24d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc24d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc24d-121">E_FAIL</span></span>|<span data-ttu-id="cc24d-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cc24d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc24d-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cc24d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc24d-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc24d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc24d-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="cc24d-125">Remarks</span></span>  

 <span data-ttu-id="cc24d-126">`ICLRTask`Экземпляр, на который `ppTask` указывает параметр, представляет выполняемую в данный момент задачу для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="cc24d-126">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="cc24d-127">`ICLRTask`Экземпляр связан с соответствующим экземпляром [IHostTask](ihosttask-interface.md) , представляющим задачу для узла.</span><span class="sxs-lookup"><span data-stu-id="cc24d-127">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc24d-128">Требования</span><span class="sxs-lookup"><span data-stu-id="cc24d-128">Requirements</span></span>  

 <span data-ttu-id="cc24d-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc24d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc24d-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc24d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc24d-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc24d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc24d-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc24d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc24d-133">См. также</span><span class="sxs-lookup"><span data-stu-id="cc24d-133">See also</span></span>

- [<span data-ttu-id="cc24d-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="cc24d-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="cc24d-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="cc24d-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="cc24d-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="cc24d-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="cc24d-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cc24d-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
