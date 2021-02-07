---
description: 'Дополнительные сведения о: количество сообщений, отклоненных в очереди, в секунду'
title: Количество сообщений из очереди, отклоненных за секунду
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: d0d227a26a49921449786d2c9f885fac13a82bde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744075"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="f64ce-103">Количество сообщений из очереди, отклоненных за секунду</span><span class="sxs-lookup"><span data-stu-id="f64ce-103">Queued Rejected Messages Per Second</span></span>

<span data-ttu-id="f64ce-104">Имя счетчика: Queued Messages Rejected Per Second.</span><span class="sxs-lookup"><span data-stu-id="f64ce-104">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f64ce-105">Описание</span><span class="sxs-lookup"><span data-stu-id="f64ce-105">Description</span></span>  

 <span data-ttu-id="f64ce-106">Количество сообщений, отклоненных транспортом очередей этой службы за секунду.</span><span class="sxs-lookup"><span data-stu-id="f64ce-106">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="f64ce-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="f64ce-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f64ce-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="f64ce-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
