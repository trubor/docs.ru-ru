---
description: 'Дополнительные сведения о: интерфейс Ихостаутоевент'
title: Интерфейс IHostAutoEvent
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: 4aea282dbe2067d50214b237650ba01fb8bf22a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789493"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="d3683-103">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="d3683-103">IHostAutoEvent Interface</span></span>

<span data-ttu-id="d3683-104">Предоставляет представление реализации события автоматического сброса в узле.</span><span class="sxs-lookup"><span data-stu-id="d3683-104">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3683-105">Методы</span><span class="sxs-lookup"><span data-stu-id="d3683-105">Methods</span></span>  
  
|<span data-ttu-id="d3683-106">Метод</span><span class="sxs-lookup"><span data-stu-id="d3683-106">Method</span></span>|<span data-ttu-id="d3683-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d3683-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3683-108">Метод Set</span><span class="sxs-lookup"><span data-stu-id="d3683-108">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="d3683-109">Устанавливает для текущего `IHostAutoEvent` экземпляра сигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="d3683-109">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="d3683-110">Метод Wait</span><span class="sxs-lookup"><span data-stu-id="d3683-110">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="d3683-111">Заставляет текущий `IHostAutoEvent` экземпляр ожидать, пока событие не будет присвоено, или истечет указанное время.</span><span class="sxs-lookup"><span data-stu-id="d3683-111">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3683-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d3683-112">Requirements</span></span>  

 <span data-ttu-id="d3683-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3683-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3683-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3683-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3683-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3683-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3683-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3683-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3683-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d3683-117">See also</span></span>

- [<span data-ttu-id="d3683-118">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d3683-118">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d3683-119">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="d3683-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d3683-120">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d3683-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="d3683-121">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="d3683-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
