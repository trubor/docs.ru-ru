---
description: 'Дополнительные сведения о: интерфейс IHostThreadPoolManager'
title: Интерфейс IHostThreadPoolManager
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 0361b7a08f781a8748e43959f65ce0e9f21bbac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728423"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="958cd-103">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="958cd-103">IHostThreadPoolManager Interface</span></span>

<span data-ttu-id="958cd-104">Предоставляет методы, позволяющие среде CLR настроить пул потоков и поместить рабочие элементы в очередь в пул потоков.</span><span class="sxs-lookup"><span data-stu-id="958cd-104">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="958cd-105">Методы</span><span class="sxs-lookup"><span data-stu-id="958cd-105">Methods</span></span>  
  
|<span data-ttu-id="958cd-106">Метод</span><span class="sxs-lookup"><span data-stu-id="958cd-106">Method</span></span>|<span data-ttu-id="958cd-107">Описание</span><span class="sxs-lookup"><span data-stu-id="958cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="958cd-108">Метод GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="958cd-108">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="958cd-109">Возвращает число потоков в пуле потоков, которые в данный момент не обрабатывают рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="958cd-109">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="958cd-110">Метод GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="958cd-110">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="958cd-111">Возвращает максимальное число потоков, которые обслуживается одновременно в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="958cd-111">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="958cd-112">Метод GetMinThreads</span><span class="sxs-lookup"><span data-stu-id="958cd-112">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="958cd-113">Возвращает минимальное число бездействующих потоков, поддерживаемых узлом в ожидаемых запросах.</span><span class="sxs-lookup"><span data-stu-id="958cd-113">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="958cd-114">Метод QueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="958cd-114">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="958cd-115">Ставит в очередь функцию для выполнения и предоставляет объект, содержащий данные, которые будут использоваться функцией.</span><span class="sxs-lookup"><span data-stu-id="958cd-115">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="958cd-116">Метод SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="958cd-116">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="958cd-117">Задает максимальное число потоков, которые узел может поддерживать в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="958cd-117">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="958cd-118">Метод SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="958cd-118">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="958cd-119">Задает минимальное число бездействующих потоков, которые должны поддерживаться узлом в ожидаемых запросах.</span><span class="sxs-lookup"><span data-stu-id="958cd-119">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="958cd-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="958cd-120">Remarks</span></span>  

 <span data-ttu-id="958cd-121">Узел не требуется для настройки пула потоков с использованием значений, указанных в вызовах `SetMaxThreads` `SetMinThreads` методов и.</span><span class="sxs-lookup"><span data-stu-id="958cd-121">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="958cd-122">В этом случае узел должен вернуть значение HRESULT E_NOTIMPL из этих методов.</span><span class="sxs-lookup"><span data-stu-id="958cd-122">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="958cd-123">Требования</span><span class="sxs-lookup"><span data-stu-id="958cd-123">Requirements</span></span>  

 <span data-ttu-id="958cd-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="958cd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958cd-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="958cd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="958cd-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="958cd-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="958cd-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="958cd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958cd-128">См. также</span><span class="sxs-lookup"><span data-stu-id="958cd-128">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="958cd-129">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="958cd-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
