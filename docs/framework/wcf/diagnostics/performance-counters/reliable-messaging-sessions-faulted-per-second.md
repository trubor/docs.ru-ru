---
description: Дополнительные сведения о сбоях сеансов надежного обмена сообщениями в секунду
title: Количество надежных сеансов обмена сообщениями, в которых произошел сбой, в секунду
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: 11759ad659d9e860c94b4428091fc0852ebf038c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716293"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="eafb3-103">Количество надежных сеансов обмена сообщениями, в которых произошел сбой, в секунду</span><span class="sxs-lookup"><span data-stu-id="eafb3-103">Reliable Messaging Sessions Faulted Per Second</span></span>

<span data-ttu-id="eafb3-104">Имя счетчика: Reliable Messaging Sessions Faulted Per Second.</span><span class="sxs-lookup"><span data-stu-id="eafb3-104">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eafb3-105">Описание</span><span class="sxs-lookup"><span data-stu-id="eafb3-105">Description</span></span>  

 <span data-ttu-id="eafb3-106">Количество надежных сессий обмена сообщениями этой службы, в которых произошел сбой в течение секунды.</span><span class="sxs-lookup"><span data-stu-id="eafb3-106">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="eafb3-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="eafb3-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="eafb3-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="eafb3-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
