---
description: 'Дополнительные сведения о: интерфейс IHostCrst'
title: Интерфейс IHostCrst
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 7945f0087667c1d610a1a2370528b055af74d579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708883"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="c490f-103">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="c490f-103">IHostCrst Interface</span></span>

<span data-ttu-id="c490f-104">Служит в качестве представления критической секции для потоков в основном приложении.</span><span class="sxs-lookup"><span data-stu-id="c490f-104">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c490f-105">Методы</span><span class="sxs-lookup"><span data-stu-id="c490f-105">Methods</span></span>  
  
|<span data-ttu-id="c490f-106">Метод</span><span class="sxs-lookup"><span data-stu-id="c490f-106">Method</span></span>|<span data-ttu-id="c490f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c490f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c490f-108">Метод Enter</span><span class="sxs-lookup"><span data-stu-id="c490f-108">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="c490f-109">Входит в критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="c490f-109">Enters the critical section.</span></span>|  
|[<span data-ttu-id="c490f-110">Метод Leave</span><span class="sxs-lookup"><span data-stu-id="c490f-110">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="c490f-111">Оставляет критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="c490f-111">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="c490f-112">Метод SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="c490f-112">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="c490f-113">Задает счетчик счетчиков для критической секции.</span><span class="sxs-lookup"><span data-stu-id="c490f-113">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="c490f-114">Метод TryEnter</span><span class="sxs-lookup"><span data-stu-id="c490f-114">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="c490f-115">Пытается войти в критическую секцию и немедленно сообщает об успешном или неуспешном завершении.</span><span class="sxs-lookup"><span data-stu-id="c490f-115">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c490f-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="c490f-116">Remarks</span></span>  

 <span data-ttu-id="c490f-117">`IHostCrst` позволяет среде CLR взаимодействовать непосредственно с представлением критического раздела узла, а не использовать функции Win32, такие как `EnterCriticalSection` или `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="c490f-117">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c490f-118">Требования</span><span class="sxs-lookup"><span data-stu-id="c490f-118">Requirements</span></span>  

 <span data-ttu-id="c490f-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c490f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c490f-120">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c490f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c490f-121">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c490f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c490f-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c490f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c490f-123">См. также</span><span class="sxs-lookup"><span data-stu-id="c490f-123">See also</span></span>

- [<span data-ttu-id="c490f-124">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c490f-124">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c490f-125">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c490f-125">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="c490f-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="c490f-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
