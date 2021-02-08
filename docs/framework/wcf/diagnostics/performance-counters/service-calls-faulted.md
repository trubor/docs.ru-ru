---
description: 'Дополнительные сведения: служба: вызовы с ошибками'
title: 'Служба: сбои вызовов'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: 8689c68be01447721d75763e23e83f6c2b0c053d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803338"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="8e14a-103">Служба: сбои вызовов</span><span class="sxs-lookup"><span data-stu-id="8e14a-103">Service: Calls Faulted</span></span>

<span data-ttu-id="8e14a-104">Имя счетчика: Calls Faulted</span><span class="sxs-lookup"><span data-stu-id="8e14a-104">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8e14a-105">Описание</span><span class="sxs-lookup"><span data-stu-id="8e14a-105">Description</span></span>  

 <span data-ttu-id="8e14a-106">Количество вызовов данной службы, которые возвратили сообщение о сбое.</span><span class="sxs-lookup"><span data-stu-id="8e14a-106">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="8e14a-107">В приложениях Windows Communication Foundation (WCF) методы служб обмениваются сведениями об ошибках обработки с помощью сообщений о сбоях SOAP.</span><span class="sxs-lookup"><span data-stu-id="8e14a-107">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="8e14a-108">Сообщения об ошибках SOAP - это типы сообщений, которые включаются в метаданные, связанные с операцией службы, и таким образом создают контракт ошибок, который клиенты могут использовать для повышения надежности и интерактивности своей работы.</span><span class="sxs-lookup"><span data-stu-id="8e14a-108">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="8e14a-109">Поскольку сообщения об ошибках SOAP передаются клиентам в формате XML, они поддерживают возможность взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="8e14a-109">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e14a-110">См. также</span><span class="sxs-lookup"><span data-stu-id="8e14a-110">See also</span></span>

- [<span data-ttu-id="8e14a-111">Задание и обработка сбоев в контрактах и службах</span><span class="sxs-lookup"><span data-stu-id="8e14a-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
