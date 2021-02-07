---
description: 'Дополнительные сведения о методе: ICLRTaskManager:: CreateTask'
title: Метод ICLRTaskManager::CreateTask
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: 98a287f10a84b18579ebf2a4294cbb8a67cabc9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728617"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="11f20-103">Метод ICLRTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="11f20-103">ICLRTaskManager::CreateTask Method</span></span>

<span data-ttu-id="11f20-104">Явно запрашивает создание новой задачи средой CLR.</span><span class="sxs-lookup"><span data-stu-id="11f20-104">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f20-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11f20-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f20-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="11f20-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="11f20-107">заполняет Указатель на адрес только что созданного файла [ICLRTask](iclrtask-interface.md)или значение null, если задачу не удалось создать.</span><span class="sxs-lookup"><span data-stu-id="11f20-107">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11f20-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="11f20-108">Return Value</span></span>  
  
|<span data-ttu-id="11f20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11f20-109">HRESULT</span></span>|<span data-ttu-id="11f20-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="11f20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11f20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="11f20-111">S_OK</span></span>|<span data-ttu-id="11f20-112">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="11f20-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="11f20-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11f20-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11f20-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="11f20-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11f20-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11f20-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11f20-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="11f20-116">The call timed out.</span></span>|  
|<span data-ttu-id="11f20-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11f20-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11f20-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="11f20-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11f20-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11f20-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11f20-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="11f20-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11f20-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11f20-121">E_FAIL</span></span>|<span data-ttu-id="11f20-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="11f20-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11f20-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="11f20-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11f20-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11f20-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11f20-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="11f20-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="11f20-126">Недостаточно памяти для выделения запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="11f20-126">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11f20-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="11f20-127">Remarks</span></span>  

 <span data-ttu-id="11f20-128">Среда CLR автоматически создает новую задачу при инициализации, когда пользовательский код создает поток с помощью типов в <xref:System.Threading> пространстве имен или увеличивается размер пула потоков.</span><span class="sxs-lookup"><span data-stu-id="11f20-128">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="11f20-129">Он также создает задачи, когда неуправляемый код вызывает управляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="11f20-129">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="11f20-130">`CreateTask` позволяет узлу выполнить явный запрос о том, что среда CLR создает новую задачу.</span><span class="sxs-lookup"><span data-stu-id="11f20-130">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="11f20-131">Например, узел может вызвать этот метод для прединициализации структур данных.</span><span class="sxs-lookup"><span data-stu-id="11f20-131">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="11f20-132">Новая задача возвращается в приостановленном состоянии и остается приостановленной до тех пор, пока узел явно не вызывает метод [IHostTask:: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="11f20-132">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f20-133">Требования</span><span class="sxs-lookup"><span data-stu-id="11f20-133">Requirements</span></span>  

 <span data-ttu-id="11f20-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f20-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f20-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11f20-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11f20-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11f20-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11f20-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f20-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f20-138">См. также</span><span class="sxs-lookup"><span data-stu-id="11f20-138">See also</span></span>

- [<span data-ttu-id="11f20-139">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="11f20-139">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="11f20-140">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="11f20-140">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="11f20-141">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="11f20-141">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="11f20-142">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="11f20-142">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
