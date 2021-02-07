---
description: 'Дополнительные сведения: конечная точка: вызовов в секунду'
title: 'Конечная точка: количество вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 10e3cb892119999225abaa8b85ea59065650795d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759579"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="2194c-103">Конечная точка: количество вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="2194c-103">Endpoint: Calls Per Second</span></span>

<span data-ttu-id="2194c-104">Имя счетчика: Calls Per Second.</span><span class="sxs-lookup"><span data-stu-id="2194c-104">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2194c-105">Описание</span><span class="sxs-lookup"><span data-stu-id="2194c-105">Description</span></span>  

 <span data-ttu-id="2194c-106">Количество вызовов данной конечной точки в секунду.</span><span class="sxs-lookup"><span data-stu-id="2194c-106">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2194c-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="2194c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2194c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2194c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
