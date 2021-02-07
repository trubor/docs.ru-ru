---
description: 'Дополнительные сведения о: интерфейс Ихостмануалевент'
title: Интерфейс IHostManualEvent
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 1c70935568b9ff4080fd5bcdc372c02d354aa06f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708168"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="a9283-103">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="a9283-103">IHostManualEvent Interface</span></span>

<span data-ttu-id="a9283-104">Предоставляет реализацию представления события ручного сброса в узле.</span><span class="sxs-lookup"><span data-stu-id="a9283-104">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9283-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a9283-105">Methods</span></span>  
  
|<span data-ttu-id="a9283-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a9283-106">Method</span></span>|<span data-ttu-id="a9283-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a9283-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9283-108">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="a9283-108">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="a9283-109">Сбрасывает текущий `IHostManualEvent` экземпляр в несигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="a9283-109">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="a9283-110">Метод Set</span><span class="sxs-lookup"><span data-stu-id="a9283-110">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="a9283-111">Устанавливает для текущего `IHostManualEvent` экземпляра сигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="a9283-111">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="a9283-112">Метод Wait</span><span class="sxs-lookup"><span data-stu-id="a9283-112">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="a9283-113">Вызывает `IHostManualEvent` Ожидание текущего экземпляра до его признания или истечения указанного периода времени.</span><span class="sxs-lookup"><span data-stu-id="a9283-113">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9283-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a9283-114">Requirements</span></span>  

 <span data-ttu-id="a9283-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9283-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9283-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9283-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9283-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9283-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9283-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9283-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9283-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a9283-119">See also</span></span>

- [<span data-ttu-id="a9283-120">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a9283-120">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a9283-121">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="a9283-121">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="a9283-122">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="a9283-122">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="a9283-123">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a9283-123">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="a9283-124">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="a9283-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
