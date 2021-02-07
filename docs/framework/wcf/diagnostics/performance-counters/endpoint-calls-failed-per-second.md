---
description: 'Дополнительные сведения: Endpoint: сбоев вызовов в секунду'
title: 'Конечная точка: количество сбоев вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 262f0fdf0750e8fdb179d41d1a99788784270023
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759644"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="62105-103">Конечная точка: количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="62105-103">Endpoint: Calls Failed Per Second</span></span>

<span data-ttu-id="62105-104">Имя счетчика: Calls Failed Per Second.</span><span class="sxs-lookup"><span data-stu-id="62105-104">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62105-105">Описание</span><span class="sxs-lookup"><span data-stu-id="62105-105">Description</span></span>  

 <span data-ttu-id="62105-106">Количество вызовов, имеющих необработанные исключения и получаемых этой конечной точкой в секунду.</span><span class="sxs-lookup"><span data-stu-id="62105-106">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="62105-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="62105-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62105-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="62105-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="62105-109">Значение этого счетчика увеличивается при каждом обнаружении необработанного исключения в данной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="62105-109">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62105-110">См. также</span><span class="sxs-lookup"><span data-stu-id="62105-110">See also</span></span>

- [<span data-ttu-id="62105-111">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="62105-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
