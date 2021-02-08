---
description: 'Дополнительные сведения о: интерфейс ICLRTaskManager'
title: Интерфейс ICLRTaskManager
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: 0ce3641042725bc2f3acb95933ccd7a5bbe3bc4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789753"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="5833d-103">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="5833d-103">ICLRTaskManager Interface</span></span>

<span data-ttu-id="5833d-104">Предоставляет методы, позволяющие узлу явно запрашивать, что среда CLR создает новую задачу, получает выполняемую в данный момент задачу и задает язык и региональные параметры для задачи.</span><span class="sxs-lookup"><span data-stu-id="5833d-104">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5833d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="5833d-105">Methods</span></span>  
  
|<span data-ttu-id="5833d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="5833d-106">Method</span></span>|<span data-ttu-id="5833d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="5833d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5833d-108">Метод CreateTask</span><span class="sxs-lookup"><span data-stu-id="5833d-108">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="5833d-109">Явно запрашивает, что среда CLR создает новый экземпляр [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5833d-109">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="5833d-110">Метод GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="5833d-110">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="5833d-111">Возвращает `ICLRTask` экземпляр, представляющий выполняемую в данный момент задачу.</span><span class="sxs-lookup"><span data-stu-id="5833d-111">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5833d-112">Метод GetCurrentTaskType</span><span class="sxs-lookup"><span data-stu-id="5833d-112">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="5833d-113">Возвращает тип выполняемой в данный момент задачи.</span><span class="sxs-lookup"><span data-stu-id="5833d-113">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="5833d-114">Метод SetLocale</span><span class="sxs-lookup"><span data-stu-id="5833d-114">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="5833d-115">Уведомляет среду CLR о том, что узел изменил идентификатор локали в выполняющейся задаче.</span><span class="sxs-lookup"><span data-stu-id="5833d-115">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="5833d-116">Метод SetUILocale</span><span class="sxs-lookup"><span data-stu-id="5833d-116">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="5833d-117">Уведомляет среду CLR о том, что узел изменил идентификатор локали пользовательского интерфейса для выполняемой в данный момент задачи.</span><span class="sxs-lookup"><span data-stu-id="5833d-117">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5833d-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="5833d-118">Remarks</span></span>  

 <span data-ttu-id="5833d-119">Каждая задача, выполняемая в среде размещения, имеет представления на стороне размещения (экземпляр [IHostTask](ihosttask-interface.md)) и на стороне среды CLR (экземпляре [ICLRTask](iclrtask-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="5833d-119">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="5833d-120">Приложение или среда CLR могут инициировать создание задачи, но представление на стороне главного приложения должно быть связано с соответствующим представлением на стороне среды CLR для обеспечения успешной связи между узлом и средой CLR, относящейся к задаче.</span><span class="sxs-lookup"><span data-stu-id="5833d-120">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="5833d-121">Перед выполнением управляемого кода в потоке операционной системы необходимо создать и создать экземпляры этих двух объектов.</span><span class="sxs-lookup"><span data-stu-id="5833d-121">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5833d-122">Требования</span><span class="sxs-lookup"><span data-stu-id="5833d-122">Requirements</span></span>  

 <span data-ttu-id="5833d-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5833d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5833d-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5833d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5833d-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5833d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5833d-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5833d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5833d-127">См. также</span><span class="sxs-lookup"><span data-stu-id="5833d-127">See also</span></span>

- [<span data-ttu-id="5833d-128">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="5833d-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5833d-129">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="5833d-129">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5833d-130">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="5833d-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="5833d-131">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="5833d-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
