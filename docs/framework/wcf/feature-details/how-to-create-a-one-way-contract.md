---
description: Дополнительные сведения о том, как создать контракт One-Way.
title: Практическое руководство. Создание одностороннего контракта
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 465dc2da20288c918a70743fcbe3ed931620b33b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734728"
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="bc46e-103">Практическое руководство. Создание одностороннего контракта</span><span class="sxs-lookup"><span data-stu-id="bc46e-103">How to: Create a One-Way Contract</span></span>

<span data-ttu-id="bc46e-104">В этом разделе приведены основные этапы создания методов, использующих односторонние контракты.</span><span class="sxs-lookup"><span data-stu-id="bc46e-104">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="bc46e-105">Такие методы вызывают операции в службе Windows Communication Foundation (WCF) от клиента, но не предполагают ответа.</span><span class="sxs-lookup"><span data-stu-id="bc46e-105">Such methods invoke operations on a Windows Communication Foundation (WCF) service from a client but do not expect a reply.</span></span> <span data-ttu-id="bc46e-106">Контракты этого типа можно использовать, к примеру, для публикации уведомлений для большого количества подписчиков.</span><span class="sxs-lookup"><span data-stu-id="bc46e-106">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="bc46e-107">Также можно использовать односторонние контракты при создании дуплексного (двустороннего) контракта, что позволяет клиентам и серверам взаимодействовать независимо (клиент может инициировать вызовы сервера, а сервер - вызовы клиента).</span><span class="sxs-lookup"><span data-stu-id="bc46e-107">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="bc46e-108">В частности, это позволяет серверу выполнять односторонние вызовы клиента, которые клиент может воспринимать как события.</span><span class="sxs-lookup"><span data-stu-id="bc46e-108">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="bc46e-109">Подробные сведения об указании односторонних методов см. в описаниях свойства <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> и класса <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc46e-109">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 <span data-ttu-id="bc46e-110">Дополнительные сведения о создании клиентского приложения для дуплексного контракта см. в разделе [руководство. доступ к службам с помощью One-Way и Request-Reply контрактов](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="bc46e-110">For more information about creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="bc46e-111">Рабочий пример см. в разделе [односторонний](../samples/one-way.md) пример.</span><span class="sxs-lookup"><span data-stu-id="bc46e-111">For a working sample, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="bc46e-112">Создание одностороннего контракта</span><span class="sxs-lookup"><span data-stu-id="bc46e-112">To create a one-way contract</span></span>  
  
1. <span data-ttu-id="bc46e-113">Создайте контракт службы, применив класс <xref:System.ServiceModel.ServiceContractAttribute> к интерфейсу, определяющему реализуемые службой методы.</span><span class="sxs-lookup"><span data-stu-id="bc46e-113">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2. <span data-ttu-id="bc46e-114">Укажите, какие именно методы интерфейса может вызвать клиент, применив к ним класс <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bc46e-114">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3. <span data-ttu-id="bc46e-115">Отметьте операции, не имеющие выходных данных (возвращаемого значения и параметров out и ref), как односторонние, присвоив свойству <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="bc46e-115">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="bc46e-116">Обратите внимание, что все операции с классом <xref:System.ServiceModel.OperationContractAttribute> по умолчанию соответствуют требованиям контракта типа запрос-ответ, поскольку свойство <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> по умолчанию имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="bc46e-116">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="bc46e-117">Поэтому необходимо явно задать свойству атрибута значение `true`, если требуется использовать односторонний контракт для метода.</span><span class="sxs-lookup"><span data-stu-id="bc46e-117">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc46e-118">Пример</span><span class="sxs-lookup"><span data-stu-id="bc46e-118">Example</span></span>  

 <span data-ttu-id="bc46e-119">В следующем примере кода определяется контракт для службы, включающей несколько односторонних методов.</span><span class="sxs-lookup"><span data-stu-id="bc46e-119">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="bc46e-120">Все методы имеют односторонние контракты, за исключением метода `Equals`, по умолчанию имеющего контракт типа запрос-ответ и возвращающего результат.</span><span class="sxs-lookup"><span data-stu-id="bc46e-120">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc46e-121">См. также</span><span class="sxs-lookup"><span data-stu-id="bc46e-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="bc46e-122">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="bc46e-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="bc46e-123">Практическое руководство. Определение контракта службы</span><span class="sxs-lookup"><span data-stu-id="bc46e-123">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="bc46e-124">Session</span><span class="sxs-lookup"><span data-stu-id="bc46e-124">Session</span></span>](../samples/session.md)
- [<span data-ttu-id="bc46e-125">Практическое руководство. Создание двухстороннего контракта</span><span class="sxs-lookup"><span data-stu-id="bc46e-125">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
