---
description: 'Дополнительные сведения: количество отправленных сообщений из очереди в секунду'
title: Количество удаленных из очереди сообщений в секунду
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: e5959b76795514dec03d6ae4d08ac248994777fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759553"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="c8ba5-103">Количество удаленных из очереди сообщений в секунду</span><span class="sxs-lookup"><span data-stu-id="c8ba5-103">Queue Dropped Messages Per Second</span></span>

<span data-ttu-id="c8ba5-104">Имя счетчика: Queued Messages Dropped Per Second.</span><span class="sxs-lookup"><span data-stu-id="c8ba5-104">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8ba5-105">Описание</span><span class="sxs-lookup"><span data-stu-id="c8ba5-105">Description</span></span>  

 <span data-ttu-id="c8ba5-106">Количество сообщений, отброшенных транспортом очередей этой службы за секунду.</span><span class="sxs-lookup"><span data-stu-id="c8ba5-106">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="c8ba5-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="c8ba5-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c8ba5-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c8ba5-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
