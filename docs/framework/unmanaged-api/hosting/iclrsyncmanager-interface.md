---
description: 'Дополнительные сведения о: интерфейс ICLRSyncManager'
title: Интерфейс ICLRSyncManager
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 188d1c913d75666aea09b17244012401d377fa10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785020"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="22ce7-103">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="22ce7-103">ICLRSyncManager Interface</span></span>

<span data-ttu-id="22ce7-104">Определяет методы, позволяющие узлу получать сведения о запрошенных задачах и обнаруживать взаимоблокировки в своей реализации синхронизации.</span><span class="sxs-lookup"><span data-stu-id="22ce7-104">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22ce7-105">Методы</span><span class="sxs-lookup"><span data-stu-id="22ce7-105">Methods</span></span>  
  
|<span data-ttu-id="22ce7-106">Метод</span><span class="sxs-lookup"><span data-stu-id="22ce7-106">Method</span></span>|<span data-ttu-id="22ce7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="22ce7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22ce7-108">Метод CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="22ce7-108">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="22ce7-109">Запрашивает, что среда CLR создает итератор для узла, который будет использоваться для определения набора задач, ожидающих блокировки чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="22ce7-109">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="22ce7-110">Метод DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="22ce7-110">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="22ce7-111">Запрашивает удаление итератора, который был создан при вызове среды CLR `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="22ce7-111">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="22ce7-112">Метод GetMonitorOwner</span><span class="sxs-lookup"><span data-stu-id="22ce7-112">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="22ce7-113">Возвращает задачу, которая владеет указанным монитором.</span><span class="sxs-lookup"><span data-stu-id="22ce7-113">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="22ce7-114">Метод GetRWLockOwnerNext</span><span class="sxs-lookup"><span data-stu-id="22ce7-114">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="22ce7-115">Возвращает следующую задачу, ожидающую текущую блокировку модуля чтения-записи.</span><span class="sxs-lookup"><span data-stu-id="22ce7-115">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22ce7-116">Требования</span><span class="sxs-lookup"><span data-stu-id="22ce7-116">Requirements</span></span>  

 <span data-ttu-id="22ce7-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22ce7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22ce7-118">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22ce7-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22ce7-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22ce7-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22ce7-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22ce7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ce7-121">См. также</span><span class="sxs-lookup"><span data-stu-id="22ce7-121">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="22ce7-122">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="22ce7-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="22ce7-123">[Управляемые и неуправляемые потоки](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22ce7-123">[Managed and Unmanaged Threading](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="22ce7-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="22ce7-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
