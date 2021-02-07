---
description: 'Дополнительные сведения о: интерфейс IHostSemaphore'
title: Интерфейс IHostSemaphore
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 682f1f70925310e93f88f1dc314052e801a5e87b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671364"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="52dc5-103">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="52dc5-103">IHostSemaphore Interface</span></span>

<span data-ttu-id="52dc5-104">Представляет реализацию семафора для потоков в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="52dc5-104">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52dc5-105">Методы</span><span class="sxs-lookup"><span data-stu-id="52dc5-105">Methods</span></span>  
  
|<span data-ttu-id="52dc5-106">Метод</span><span class="sxs-lookup"><span data-stu-id="52dc5-106">Method</span></span>|<span data-ttu-id="52dc5-107">Описание</span><span class="sxs-lookup"><span data-stu-id="52dc5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52dc5-108">Метод ReleaseSemaphore</span><span class="sxs-lookup"><span data-stu-id="52dc5-108">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="52dc5-109">Увеличивает количество текущего `IHostSemaphore` экземпляра на указанный объем.</span><span class="sxs-lookup"><span data-stu-id="52dc5-109">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="52dc5-110">Метод Wait</span><span class="sxs-lookup"><span data-stu-id="52dc5-110">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="52dc5-111">Вызывает `IHostSemaphore` Ожидание текущего экземпляра до его признания или указанного периода времени.</span><span class="sxs-lookup"><span data-stu-id="52dc5-111">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52dc5-112">Требования</span><span class="sxs-lookup"><span data-stu-id="52dc5-112">Requirements</span></span>  

 <span data-ttu-id="52dc5-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52dc5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52dc5-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52dc5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52dc5-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52dc5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52dc5-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52dc5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dc5-117">См. также</span><span class="sxs-lookup"><span data-stu-id="52dc5-117">See also</span></span>

- [<span data-ttu-id="52dc5-118">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="52dc5-118">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="52dc5-119">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="52dc5-119">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="52dc5-120">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="52dc5-120">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="52dc5-121">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="52dc5-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="52dc5-122">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="52dc5-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
