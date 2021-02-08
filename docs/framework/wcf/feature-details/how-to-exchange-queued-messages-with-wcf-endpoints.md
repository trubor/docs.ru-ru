---
description: Дополнительные сведения см. в статье как обмениваться сообщениями в очереди с помощью конечных точек WCF.
title: Практическое руководство. Обмен сообщениями в очереди с конечными точками WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: fe7195719c57454cb0035c1b6f06134cf3380a46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802896"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="b1561-103">Практическое руководство. Обмен сообщениями в очереди с конечными точками WCF</span><span class="sxs-lookup"><span data-stu-id="b1561-103">How to: Exchange Queued Messages with WCF Endpoints</span></span>

<span data-ttu-id="b1561-104">Очереди обеспечивают надежный обмен сообщениями между клиентом и службой Windows Communication Foundation (WCF), даже если служба недоступна во время обмена данными.</span><span class="sxs-lookup"><span data-stu-id="b1561-104">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="b1561-105">В следующих процедурах показано, как обеспечить устойчивое взаимодействие между клиентом и службой с помощью стандартной привязки в очереди при реализации службы WCF.</span><span class="sxs-lookup"><span data-stu-id="b1561-105">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="b1561-106">В этом разделе объясняется, как использовать <xref:System.ServiceModel.NetMsmqBinding> для обмена данными между клиентом WCF и службой WCF.</span><span class="sxs-lookup"><span data-stu-id="b1561-106">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="b1561-107">Использование очередей в службе WCF.</span><span class="sxs-lookup"><span data-stu-id="b1561-107">To use queuing in a WCF service</span></span>  
  
1. <span data-ttu-id="b1561-108">Определите контракт службы с использованием интерфейса, отмеченного атрибутом <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b1561-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="b1561-109">Пометьте операции в интерфейсе, которые являются частью контракта службы с <xref:System.ServiceModel.OperationContractAttribute> и задайте их как односторонние, так как методу ответ не возвращается.</span><span class="sxs-lookup"><span data-stu-id="b1561-109">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="b1561-110">Следующий код представляет пример контракта службы и определение его операций.</span><span class="sxs-lookup"><span data-stu-id="b1561-110">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. <span data-ttu-id="b1561-111">Необходимо определить контракты данных для определяемых пользователем типов, если их передает контракт службы.</span><span class="sxs-lookup"><span data-stu-id="b1561-111">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="b1561-112">В следующем коде показано два контракта данных - `PurchaseOrder` и `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="b1561-112">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="b1561-113">Эти два типа определяют данные, отправляемые службе.</span><span class="sxs-lookup"><span data-stu-id="b1561-113">These two types define data that is sent to the service.</span></span> <span data-ttu-id="b1561-114">(Обратите внимание, что классы, определяющие этот контракт данных, определяют и число методов.</span><span class="sxs-lookup"><span data-stu-id="b1561-114">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="b1561-115">Эти методы не являются частью контракта данных.</span><span class="sxs-lookup"><span data-stu-id="b1561-115">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="b1561-116">Частью контракта данных являются только члены, объявленные с атрибутом <xref:System.Runtime.Serialization.DataMemberAttribute>.)</span><span class="sxs-lookup"><span data-stu-id="b1561-116">Only those members that are declared with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. <span data-ttu-id="b1561-117">Реализуйте методы контракта службы, определенные в интерфейсе в классе.</span><span class="sxs-lookup"><span data-stu-id="b1561-117">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="b1561-118">Заметьте, что в методе <xref:System.ServiceModel.OperationBehaviorAttribute> указывается атрибут `SubmitPurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="b1561-118">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="b1561-119">Это значит, что данная операция должна вызываться в рамках транзакции, которая автоматически завершается при завершении метода.</span><span class="sxs-lookup"><span data-stu-id="b1561-119">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4. <span data-ttu-id="b1561-120">Создайте очередь транзакций с использованием <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="b1561-120">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="b1561-121">Вместо этого можно создать очередь с использованием консоли управления (MMC) «Очередь сообщений Майкрософт (MSMQ)».</span><span class="sxs-lookup"><span data-stu-id="b1561-121">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="b1561-122">В этом случае убедитесь, что создается очередь транзакций.</span><span class="sxs-lookup"><span data-stu-id="b1561-122">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. <span data-ttu-id="b1561-123">Определите класс <xref:System.ServiceModel.Description.ServiceEndpoint> в конфигурации, которая задает адрес службы и использует стандартную привязку <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="b1561-123">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="b1561-124">Дополнительные сведения об использовании конфигурации WCF см. в разделе [Настройка служб WCF](../configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="b1561-124">For more information about using WCF configuration, see [Configuring WCF services](../configuring-services.md).</span></span>  

6. <span data-ttu-id="b1561-125">Создайте узел для службы `OrderProcessing` с использованием <xref:System.ServiceModel.ServiceHost>, считывающий и обрабатывающий сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="b1561-125">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="b1561-126">Откройте узел службы для обеспечения доступности службы.</span><span class="sxs-lookup"><span data-stu-id="b1561-126">Open the service host to make the service available.</span></span> <span data-ttu-id="b1561-127">Выведите для пользователя сообщение о том, что нужно нажать любую клавишу для завершения службы.</span><span class="sxs-lookup"><span data-stu-id="b1561-127">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="b1561-128">Вызовите метод `ReadLine`, чтобы включить ожидания нажатия клавиши, а затем закройте службу.</span><span class="sxs-lookup"><span data-stu-id="b1561-128">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="b1561-129">Создание клиента для службы в очереди</span><span class="sxs-lookup"><span data-stu-id="b1561-129">To create a client for the queued service</span></span>  
  
1. <span data-ttu-id="b1561-130">В следующем примере показано, как запустить приложение размещения и использовать средство Svcutil.exe для создания клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="b1561-130">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. <span data-ttu-id="b1561-131">Определите объект <xref:System.ServiceModel.Description.ServiceEndpoint> в конфигурации, которая указывает адрес и использует стандартную привязку <xref:System.ServiceModel.NetMsmqBinding>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b1561-131">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  

3. <span data-ttu-id="b1561-132">Создайте область транзакции для записи в транзакционную очередь, вызовите `SubmitPurchaseOrder` операцию и закройте клиент WCF, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b1561-132">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b1561-133">Пример</span><span class="sxs-lookup"><span data-stu-id="b1561-133">Example</span></span>  

 <span data-ttu-id="b1561-134">В следующих примерах показан код службы, ведущее приложение, файл App.config и код клиента для этого примера.</span><span class="sxs-lookup"><span data-stu-id="b1561-134">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a><span data-ttu-id="b1561-135">См. также</span><span class="sxs-lookup"><span data-stu-id="b1561-135">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="b1561-136">Привязка MSMQ с поддержкой транзакций</span><span class="sxs-lookup"><span data-stu-id="b1561-136">Transacted MSMQ Binding</span></span>](../samples/transacted-msmq-binding.md)
- [<span data-ttu-id="b1561-137">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="b1561-137">Queuing in WCF</span></span>](queuing-in-wcf.md)
- [<span data-ttu-id="b1561-138">Практическое руководство. Обмен сообщениями с конечными точками WCF и приложениями очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="b1561-138">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="b1561-139">Отправка сообщений из приложения Windows Communication Foundation в приложение MSMQ</span><span class="sxs-lookup"><span data-stu-id="b1561-139">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="b1561-140">Установка системы очередей сообщений (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="b1561-140">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="b1561-141">Передача сообщений из приложения MSMQ в приложение Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b1561-141">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="b1561-142">Безопасность сообщений при использовании очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="b1561-142">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
