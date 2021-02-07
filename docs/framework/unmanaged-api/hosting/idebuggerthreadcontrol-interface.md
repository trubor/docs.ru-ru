---
description: 'Дополнительные сведения о: интерфейс Идебугжерсреадконтрол'
title: Интерфейс IDebuggerThreadControl
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 293a120d44b9b04d7e367546c477fb273f535310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709775"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="dfeac-103">Интерфейс IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="dfeac-103">IDebuggerThreadControl Interface</span></span>

<span data-ttu-id="dfeac-104">Предоставляет методы для уведомления узла о блокировке и разблокировке потоков службами отладки.</span><span class="sxs-lookup"><span data-stu-id="dfeac-104">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfeac-105">Методы</span><span class="sxs-lookup"><span data-stu-id="dfeac-105">Methods</span></span>  
  
|<span data-ttu-id="dfeac-106">Метод</span><span class="sxs-lookup"><span data-stu-id="dfeac-106">Method</span></span>|<span data-ttu-id="dfeac-107">Описание</span><span class="sxs-lookup"><span data-stu-id="dfeac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfeac-108">Метод ThreadIsBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="dfeac-108">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="dfeac-109">Уведомляет узел о том, что поток, отправляющий этот обратный вызов, будет заблокирован в службах отладки.</span><span class="sxs-lookup"><span data-stu-id="dfeac-109">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="dfeac-110">Метод ReleaseAllRuntimeThreads</span><span class="sxs-lookup"><span data-stu-id="dfeac-110">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="dfeac-111">Уведомляет узел о том, что службы отладки собирается освободить все заблокированные потоки.</span><span class="sxs-lookup"><span data-stu-id="dfeac-111">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="dfeac-112">Метод StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="dfeac-112">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="dfeac-113">Уведомляет узел о том, что служба отладки собирается начать блокирование всех потоков.</span><span class="sxs-lookup"><span data-stu-id="dfeac-113">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfeac-114">Требования</span><span class="sxs-lookup"><span data-stu-id="dfeac-114">Requirements</span></span>  

 <span data-ttu-id="dfeac-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfeac-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfeac-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dfeac-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfeac-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfeac-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfeac-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfeac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeac-119">См. также</span><span class="sxs-lookup"><span data-stu-id="dfeac-119">See also</span></span>

- [<span data-ttu-id="dfeac-120">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="dfeac-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
