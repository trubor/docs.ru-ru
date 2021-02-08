---
description: 'Подробнее о службе: количество вызовов, завершившихся сбоем, в секунду'
title: 'Служба: количество сбоев вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: b271d5076d0f0c89c4d33b124e0184584795466a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803364"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="86214-103">Служба: количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="86214-103">Service: Calls Failed Per Second</span></span>

<span data-ttu-id="86214-104">Имя счетчика: Calls Failed Per Second.</span><span class="sxs-lookup"><span data-stu-id="86214-104">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="86214-105">Описание</span><span class="sxs-lookup"><span data-stu-id="86214-105">Description</span></span>  

 <span data-ttu-id="86214-106">Число вызовов с необработанными исключениями, получаемых этой службой за секунду.</span><span class="sxs-lookup"><span data-stu-id="86214-106">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="86214-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="86214-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="86214-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="86214-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="86214-109">В управляемом коде исключения создаются в случае возникновения ошибки.</span><span class="sxs-lookup"><span data-stu-id="86214-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="86214-110">В управляемом коде исключения создаются в случае возникновения ошибки.</span><span class="sxs-lookup"><span data-stu-id="86214-110">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="86214-111">Значение этого счетчика увеличивается при каждом обнаружении необработанного исключения в данной службе.</span><span class="sxs-lookup"><span data-stu-id="86214-111">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86214-112">См. также</span><span class="sxs-lookup"><span data-stu-id="86214-112">See also</span></span>

- [<span data-ttu-id="86214-113">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="86214-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
