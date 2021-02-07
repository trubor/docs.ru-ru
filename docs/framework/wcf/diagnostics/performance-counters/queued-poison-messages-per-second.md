---
description: Дополнительные сведения о наличии подозрительных сообщений в очереди в секунду
title: Количество подозрительных сообщений из очереди в секунду
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 3240974445debf86ff17187e4c6762b39610bd46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744088"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="49b82-103">Количество подозрительных сообщений из очереди в секунду</span><span class="sxs-lookup"><span data-stu-id="49b82-103">Queued Poison Messages Per Second</span></span>

<span data-ttu-id="49b82-104">Имя счетчика: Queued Poison Messages Per Second.</span><span class="sxs-lookup"><span data-stu-id="49b82-104">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49b82-105">Описание</span><span class="sxs-lookup"><span data-stu-id="49b82-105">Description</span></span>  

 <span data-ttu-id="49b82-106">Количество сообщений, отмеченных как подозрительные транспортом очередей в этой службе в секунду.</span><span class="sxs-lookup"><span data-stu-id="49b82-106">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="49b82-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="49b82-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="49b82-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="49b82-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
