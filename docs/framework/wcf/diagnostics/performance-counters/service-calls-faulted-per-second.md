---
description: 'Дополнительные сведения: служба: вызовов с ошибками в секунду'
title: 'Служба: количество сбоев вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 87b4ec8a6868f2694f7aefa34d977e618db16e16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705425"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="13f01-103">Служба: количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="13f01-103">Service: Calls Faulted Per Second</span></span>

<span data-ttu-id="13f01-104">Имя счетчика: Calls Faulted Per Second.</span><span class="sxs-lookup"><span data-stu-id="13f01-104">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="13f01-105">Описание</span><span class="sxs-lookup"><span data-stu-id="13f01-105">Description</span></span>  

 <span data-ttu-id="13f01-106">Число вызовов, которые возвратили сбой этой службе за секунду.</span><span class="sxs-lookup"><span data-stu-id="13f01-106">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="13f01-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="13f01-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="13f01-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="13f01-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="13f01-109">В приложениях Windows Communication Foundation (WCF) методы служб обмениваются сведениями об ошибках обработки с помощью сообщений о сбоях SOAP.</span><span class="sxs-lookup"><span data-stu-id="13f01-109">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="13f01-110">Сообщения об ошибках SOAP - это типы сообщений, которые включаются в метаданные, связанные с операцией службы, и таким образом создают контракт ошибок, который клиенты могут использовать для повышения надежности и интерактивности своей работы.</span><span class="sxs-lookup"><span data-stu-id="13f01-110">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="13f01-111">Поскольку сообщения об ошибках SOAP передаются клиентам в формате XML, они поддерживают возможность взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="13f01-111">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f01-112">См. также</span><span class="sxs-lookup"><span data-stu-id="13f01-112">See also</span></span>

- [<span data-ttu-id="13f01-113">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="13f01-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
