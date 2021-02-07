---
description: 'Дополнительные сведения о: интерфейс IGCThreadControl'
title: Интерфейс IGCThreadControl
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 07c76848668b1525f4ff45ba5de746beefe0e004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709288"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="6a122-103">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="6a122-103">IGCThreadControl Interface</span></span>

<span data-ttu-id="6a122-104">Предоставляет методы для участия в планировании потоков, которые в противном случае были бы заблокированы для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6a122-104">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a122-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6a122-105">Methods</span></span>  
  
|<span data-ttu-id="6a122-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6a122-106">Method</span></span>|<span data-ttu-id="6a122-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6a122-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a122-108">Метод SuspensionEnding</span><span class="sxs-lookup"><span data-stu-id="6a122-108">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="6a122-109">Уведомляет узел о том, что среда выполнения возобновляет потоки после сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="6a122-109">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="6a122-110">Метод SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="6a122-110">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="6a122-111">Уведомляет узел о том, что среда выполнения начинает приостановку потока для сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="6a122-111">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="6a122-112">Метод ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="6a122-112">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="6a122-113">Уведомляет узел о том, что поток, выполняющий вызов, будет заблокирован, возможно, для сборки мусора или другой приостановки.</span><span class="sxs-lookup"><span data-stu-id="6a122-113">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a122-114">Требования</span><span class="sxs-lookup"><span data-stu-id="6a122-114">Requirements</span></span>  

 <span data-ttu-id="6a122-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a122-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a122-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a122-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a122-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a122-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a122-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a122-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a122-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6a122-119">See also</span></span>

- [<span data-ttu-id="6a122-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="6a122-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
