---
description: 'Дополнительные сведения о: интерфейс IHostGCManager'
title: Интерфейс IHostGCManager
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: da229c04eb5f5a27c34c133b5c88183d00f47c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708662"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="b6d86-103">Интерфейс IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="b6d86-103">IHostGCManager Interface</span></span>

<span data-ttu-id="b6d86-104">Предоставляет методы, которые уведомляют узел о событиях в механизме сборки мусора, реализованном средой CLR.</span><span class="sxs-lookup"><span data-stu-id="b6d86-104">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="b6d86-105">Элементы</span><span class="sxs-lookup"><span data-stu-id="b6d86-105">Members</span></span>  
  
|<span data-ttu-id="b6d86-106">Член</span><span class="sxs-lookup"><span data-stu-id="b6d86-106">Member</span></span>|<span data-ttu-id="b6d86-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b6d86-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6d86-108">Метод SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="b6d86-108">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="b6d86-109">Уведомляет узел о том, что среда CLR возобновляет выполнение задач в потоках, которые были приостановлены для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="b6d86-109">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="b6d86-110">Метод SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="b6d86-110">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="b6d86-111">Уведомляет узел о том, что среда CLR приостанавливает выполнение задач, для выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="b6d86-111">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="b6d86-112">Метод ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="b6d86-112">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="b6d86-113">Уведомляет узел о том, что поток, из которого был сделан вызов метода, собирается блокироваться для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="b6d86-113">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6d86-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b6d86-114">Requirements</span></span>  

 <span data-ttu-id="b6d86-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6d86-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d86-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6d86-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6d86-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6d86-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6d86-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d86-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d86-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b6d86-119">See also</span></span>

- [<span data-ttu-id="b6d86-120">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b6d86-120">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b6d86-121">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b6d86-121">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b6d86-122">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="b6d86-122">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b6d86-123">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b6d86-123">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b6d86-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="b6d86-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
