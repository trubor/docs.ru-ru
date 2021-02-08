---
description: Дополнительные сведения о интерфейсе IHostTask
title: Интерфейс IHostTask
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: c46bbdd2e881c20d1ffd634bec8ddfa3b70b0f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784669"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="ecd3f-103">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="ecd3f-103">IHostTask Interface</span></span>

<span data-ttu-id="ecd3f-104">Предоставляет методы, позволяющие среде CLR взаимодействовать с узлом для управления задачами.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-104">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecd3f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ecd3f-105">Methods</span></span>  
  
|<span data-ttu-id="ecd3f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ecd3f-106">Method</span></span>|<span data-ttu-id="ecd3f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ecd3f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecd3f-108">Метод Alert</span><span class="sxs-lookup"><span data-stu-id="ecd3f-108">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="ecd3f-109">Запрашивает выход узла из задачи, представленной текущим `IHostTask` экземпляром, поэтому задачу можно прервать.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-109">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="ecd3f-110">Метод GetPriority</span><span class="sxs-lookup"><span data-stu-id="ecd3f-110">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="ecd3f-111">Возвращает уровень приоритета потока задачи, представленной текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-111">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ecd3f-112">Метод Join</span><span class="sxs-lookup"><span data-stu-id="ecd3f-112">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="ecd3f-113">Блокирует вызывающую задачу до тех пор, пока задача, представленная текущим `IHostTask` экземпляром, не завершится, истечет указанный интервал времени, или будет вызван метод [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ecd3f-113">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="ecd3f-114">Метод SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="ecd3f-114">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="ecd3f-115">Связывает экземпляр [интерфейса ICLRTask](iclrtask-interface.md) с текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-115">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ecd3f-116">Метод SetPriority</span><span class="sxs-lookup"><span data-stu-id="ecd3f-116">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="ecd3f-117">Запрашивает у узла настройку уровня приоритета потока для задачи, представленной текущим `IHostTask` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-117">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ecd3f-118">Метод Start</span><span class="sxs-lookup"><span data-stu-id="ecd3f-118">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="ecd3f-119">Запрашивает, что узел перемещает задачу, представленную текущим `IHostTask` экземпляром, из приостановленного состояния в активное состояние, в котором может выполняться код.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-119">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd3f-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ecd3f-120">Remarks</span></span>  

 <span data-ttu-id="ecd3f-121">Среда CLR вызывает методы, определенные `IHostTask` для запуска задачи, установки ее уровня приоритета и т. д.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-121">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd3f-122">Требования</span><span class="sxs-lookup"><span data-stu-id="ecd3f-122">Requirements</span></span>  

 <span data-ttu-id="ecd3f-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd3f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd3f-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecd3f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecd3f-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecd3f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecd3f-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd3f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd3f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ecd3f-127">See also</span></span>

- [<span data-ttu-id="ecd3f-128">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="ecd3f-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ecd3f-129">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="ecd3f-129">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ecd3f-130">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ecd3f-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="ecd3f-131">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="ecd3f-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
