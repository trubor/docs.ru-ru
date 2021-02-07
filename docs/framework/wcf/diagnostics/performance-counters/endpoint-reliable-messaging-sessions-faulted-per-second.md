---
description: 'Дополнительные сведения: конечная точка: сбои в сеансах надежного обмена сообщениями за секунду'
title: 'Конечная точка: количество надежных сеансов обмена сообщениями, в которых произошел сбой, в секунду'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 5c92239d00926e04024c49abde67bb9900fe479b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735787"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="c2754-103">Конечная точка: количество надежных сеансов обмена сообщениями, в которых произошел сбой, в секунду</span><span class="sxs-lookup"><span data-stu-id="c2754-103">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>

<span data-ttu-id="c2754-104">Имя счетчика: Reliable Messaging Sessions Faulted Per Second.</span><span class="sxs-lookup"><span data-stu-id="c2754-104">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c2754-105">Описание</span><span class="sxs-lookup"><span data-stu-id="c2754-105">Description</span></span>  

 <span data-ttu-id="c2754-106">Количество сеансов надежного обмена сообщениями, в которых произошел сбой на этой конечной точке в течение секунды.</span><span class="sxs-lookup"><span data-stu-id="c2754-106">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="c2754-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="c2754-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c2754-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c2754-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
