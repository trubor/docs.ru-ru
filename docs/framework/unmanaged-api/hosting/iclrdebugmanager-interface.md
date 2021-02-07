---
description: 'Дополнительные сведения о: интерфейс ICLRDebugManager'
title: Интерфейс ICLRDebugManager
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 4306e38b7c868561276d5b00e7730b6fcee46fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746031"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="eebc1-103">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="eebc1-103">ICLRDebugManager Interface</span></span>

<span data-ttu-id="eebc1-104">Предоставляет методы, позволяющие узлу связать набор задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="eebc1-104">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eebc1-105">Методы</span><span class="sxs-lookup"><span data-stu-id="eebc1-105">Methods</span></span>  
  
|<span data-ttu-id="eebc1-106">Метод</span><span class="sxs-lookup"><span data-stu-id="eebc1-106">Method</span></span>|<span data-ttu-id="eebc1-107">Описание</span><span class="sxs-lookup"><span data-stu-id="eebc1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eebc1-108">Метод BeginConnection</span><span class="sxs-lookup"><span data-stu-id="eebc1-108">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="eebc1-109">Устанавливает новое соединение между узлом и отладчиком для связывания задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="eebc1-109">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="eebc1-110">Метод EndConnection</span><span class="sxs-lookup"><span data-stu-id="eebc1-110">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="eebc1-111">Удаляет связь между списком задач и идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="eebc1-111">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="eebc1-112">Метод GetDacl</span><span class="sxs-lookup"><span data-stu-id="eebc1-112">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="eebc1-113">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="eebc1-113">This method is not implemented.</span></span>|  
|[<span data-ttu-id="eebc1-114">Метод IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="eebc1-114">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="eebc1-115">Получает значение, показывающее, присоединен ли отладчик к процессу.</span><span class="sxs-lookup"><span data-stu-id="eebc1-115">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="eebc1-116">Метод SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="eebc1-116">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="eebc1-117">Связывает список экземпляров [ICLRTask](iclrtask-interface.md) с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="eebc1-117">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="eebc1-118">Метод SetDacl</span><span class="sxs-lookup"><span data-stu-id="eebc1-118">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="eebc1-119">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="eebc1-119">This method is not implemented.</span></span>|  
|[<span data-ttu-id="eebc1-120">Метод SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="eebc1-120">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="eebc1-121">Задает политику чтения файлов базы данных программы (PDB).</span><span class="sxs-lookup"><span data-stu-id="eebc1-121">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="eebc1-122">Политика определяет, включаются ли в стеки вызовов сведения о номерах строк и файлах.</span><span class="sxs-lookup"><span data-stu-id="eebc1-122">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eebc1-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="eebc1-123">Remarks</span></span>  

 <span data-ttu-id="eebc1-124">В сценариях отладки узлу может потребоваться сгруппировать задачи в соответствии с собственной логикой программирования.</span><span class="sxs-lookup"><span data-stu-id="eebc1-124">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="eebc1-125">Например, группирование позволит разработчику видеть только задачи, необходимые API разработчика, а не выполнять все задачи, выполняемые в процессе.</span><span class="sxs-lookup"><span data-stu-id="eebc1-125">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="eebc1-126">`ICLRDebugManager` позволяет ведущему приложению реализовать такой тип группирования.</span><span class="sxs-lookup"><span data-stu-id="eebc1-126">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eebc1-127">Три `ICLRDebugManager` метода, `BeginConnection` `SetConnectionTasks` и, `EndConnection` зависят друг от друга.</span><span class="sxs-lookup"><span data-stu-id="eebc1-127">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="eebc1-128">Их необходимо вызывать в заданном порядке, чтобы работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="eebc1-128">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="eebc1-129">Группирование и идентификаторы и понятные имена, которые узел назначает группе, не имеют смысла для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="eebc1-129">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="eebc1-130">CLR просто передает информацию в отладчик.</span><span class="sxs-lookup"><span data-stu-id="eebc1-130">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eebc1-131">Требования</span><span class="sxs-lookup"><span data-stu-id="eebc1-131">Requirements</span></span>  

 <span data-ttu-id="eebc1-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eebc1-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eebc1-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eebc1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eebc1-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eebc1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eebc1-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eebc1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebc1-136">См. также</span><span class="sxs-lookup"><span data-stu-id="eebc1-136">See also</span></span>

- [<span data-ttu-id="eebc1-137">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="eebc1-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
