---
description: 'Дополнительные сведения о службе: количество транзакций, обработанных за секунду'
title: 'Служба: количество поступивших транзакций в секунду'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: aae78853272b46a97ce25a710039661f36bf7079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759501"
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="d0fe4-103">Служба: количество поступивших транзакций в секунду</span><span class="sxs-lookup"><span data-stu-id="d0fe4-103">Service: Transactions Flowed Per Second</span></span>

<span data-ttu-id="d0fe4-104">Имя счетчика: Transactions Flowed Per Second.</span><span class="sxs-lookup"><span data-stu-id="d0fe4-104">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d0fe4-105">Описание</span><span class="sxs-lookup"><span data-stu-id="d0fe4-105">Description</span></span>  

 <span data-ttu-id="d0fe4-106">Количество транзакций в операциях для данной службы в секунду.</span><span class="sxs-lookup"><span data-stu-id="d0fe4-106">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="d0fe4-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="d0fe4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d0fe4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d0fe4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
