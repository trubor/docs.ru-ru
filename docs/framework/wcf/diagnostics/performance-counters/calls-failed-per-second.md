---
description: 'Дополнительные сведения: количество вызовов, завершившихся сбоем, в секунду'
title: Количество сбоев вызовов в секунду
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 3961754eb73743a1213922f7c9e1bd164334cd6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759722"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="b3b08-103">Количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="b3b08-103">Calls Failed Per Second</span></span>

<span data-ttu-id="b3b08-104">Имя счетчика: Calls Failed Per Second</span><span class="sxs-lookup"><span data-stu-id="b3b08-104">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3b08-105">Описание</span><span class="sxs-lookup"><span data-stu-id="b3b08-105">Description</span></span>  

 <span data-ttu-id="b3b08-106">Количество вызовов с необработанными исключениями в данной операции в секунду.</span><span class="sxs-lookup"><span data-stu-id="b3b08-106">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="b3b08-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="b3b08-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b3b08-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b3b08-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="b3b08-109">Этот счетчик увеличивается каждый раз, когда в этой операции имеется необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="b3b08-109">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b08-110">См. также</span><span class="sxs-lookup"><span data-stu-id="b3b08-110">See also</span></span>

- [<span data-ttu-id="b3b08-111">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="b3b08-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
