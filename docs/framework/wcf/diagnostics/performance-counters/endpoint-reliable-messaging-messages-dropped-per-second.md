---
description: 'Дополнительные сведения: конечная точка: отброшенных сообщений надежного обмена в секунду'
title: 'Конечная точка: количество отброшенных сообщений, передаваемых по надежным каналам, в секунду'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 257ea74aeb23ef8962ce8910dee635b83f76d960
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735885"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="97cc2-103">Конечная точка: количество отброшенных сообщений, передаваемых по надежным каналам, в секунду</span><span class="sxs-lookup"><span data-stu-id="97cc2-103">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>

<span data-ttu-id="97cc2-104">Имя счетчика: Reliable Messaging Sessions Dropped Per Second.</span><span class="sxs-lookup"><span data-stu-id="97cc2-104">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="97cc2-105">Описание</span><span class="sxs-lookup"><span data-stu-id="97cc2-105">Description</span></span>  

 <span data-ttu-id="97cc2-106">Общее количество сообщений системы надежного обмена сообщениями, которое было отброшено в данной конечной точке в секунду.</span><span class="sxs-lookup"><span data-stu-id="97cc2-106">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="97cc2-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="97cc2-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="97cc2-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="97cc2-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
