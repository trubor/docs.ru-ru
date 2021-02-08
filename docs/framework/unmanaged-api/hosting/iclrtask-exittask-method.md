---
description: 'Дополнительные сведения о методе ICLRTask:: ExitTask'
title: Метод ICLRTask::ExitTask
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 267b7f284ccac5b535a72dab425c035b6c689361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784969"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="9e501-103">Метод ICLRTask::ExitTask</span><span class="sxs-lookup"><span data-stu-id="9e501-103">ICLRTask::ExitTask Method</span></span>

<span data-ttu-id="9e501-104">Уведомляет среду CLR о том, что задача, представленная текущим экземпляром [ICLRTask](iclrtask-interface.md) , завершается, и пытается корректно завершить задачу.</span><span class="sxs-lookup"><span data-stu-id="9e501-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e501-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e501-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9e501-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9e501-106">Return Value</span></span>  
  
|<span data-ttu-id="9e501-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e501-107">HRESULT</span></span>|<span data-ttu-id="9e501-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="9e501-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e501-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e501-109">S_OK</span></span>|<span data-ttu-id="9e501-110">`ExitTask` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="9e501-110">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="9e501-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e501-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e501-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="9e501-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e501-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e501-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e501-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="9e501-114">The call timed out.</span></span>|  
|<span data-ttu-id="9e501-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e501-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e501-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="9e501-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e501-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e501-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e501-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="9e501-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e501-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e501-119">E_FAIL</span></span>|<span data-ttu-id="9e501-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="9e501-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e501-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="9e501-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e501-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e501-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e501-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e501-123">Remarks</span></span>  

 <span data-ttu-id="9e501-124">`ExitTask` пытается выполнить чистое завершение задачи, аналогично отсоединению потока из неуправляемой библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="9e501-124">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e501-125">Требования</span><span class="sxs-lookup"><span data-stu-id="9e501-125">Requirements</span></span>  

 <span data-ttu-id="9e501-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e501-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e501-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e501-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e501-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e501-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e501-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e501-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e501-130">См. также</span><span class="sxs-lookup"><span data-stu-id="9e501-130">See also</span></span>

- [<span data-ttu-id="9e501-131">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="9e501-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9e501-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="9e501-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9e501-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="9e501-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9e501-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="9e501-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
