---
description: 'Дополнительные сведения: Endpoint: вызовов с ошибками за секунду'
title: 'Конечная точка: количество сбоев вызовов в секунду'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 160680f215dbb3eea5ad15c756c7dc68a0629a90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759618"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="8d38b-103">Конечная точка: количество сбоев вызовов в секунду</span><span class="sxs-lookup"><span data-stu-id="8d38b-103">Endpoint: Calls Faulted Per Second</span></span>

<span data-ttu-id="8d38b-104">Имя счетчика: Calls Faulted Per Second.</span><span class="sxs-lookup"><span data-stu-id="8d38b-104">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d38b-105">Описание</span><span class="sxs-lookup"><span data-stu-id="8d38b-105">Description</span></span>  

 <span data-ttu-id="8d38b-106">Количество вызовов, которые возвратили сбой данной конечной точке в секунду.</span><span class="sxs-lookup"><span data-stu-id="8d38b-106">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="8d38b-107">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="8d38b-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8d38b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="8d38b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="8d38b-109">В приложениях Windows Communication Foundation (WCF) методы служб обмениваются сведениями об ошибках обработки с помощью сообщений о сбоях SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d38b-109">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="8d38b-110">Сообщения об ошибках SOAP - это типы сообщений, которые включаются в метаданные, связанные с операцией службы, и таким образом создают контракт ошибок, который клиенты могут использовать для повышения надежности и интерактивности своей работы.</span><span class="sxs-lookup"><span data-stu-id="8d38b-110">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="8d38b-111">Поскольку сообщения об ошибках SOAP передаются клиентам в формате XML, они поддерживают возможность взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="8d38b-111">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d38b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="8d38b-112">See also</span></span>

- [<span data-ttu-id="8d38b-113">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="8d38b-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
