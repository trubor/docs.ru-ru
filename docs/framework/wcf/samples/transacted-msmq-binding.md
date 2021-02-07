---
description: 'Дополнительные сведения: транзакционная Привязка MSMQ'
title: Привязка MSMQ с поддержкой транзакций
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 17fdcdb169c9e57c1a95d5aea4c79654e3739664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668530"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="5416a-103">Привязка MSMQ с поддержкой транзакций</span><span class="sxs-lookup"><span data-stu-id="5416a-103">Transacted MSMQ Binding</span></span>

<span data-ttu-id="5416a-104">В этом образце показано, как осуществлять транзакционное взаимодействие с использованием очередей с помощью очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5416a-104">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="5416a-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="5416a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5416a-106">При использовании очередей клиент взаимодействует со службой посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="5416a-107">Конкретно, клиент отправляет сообщения в очередь.</span><span class="sxs-lookup"><span data-stu-id="5416a-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="5416a-108">Служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-108">The service receives messages from the queue.</span></span> <span data-ttu-id="5416a-109">Поэтому при взаимодействии посредством очереди клиенту и службе не обязательно работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="5416a-109">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="5416a-110">При использовании транзакций для отправки и получения сообщений это фактически две отдельные транзакции.</span><span class="sxs-lookup"><span data-stu-id="5416a-110">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="5416a-111">При отправке клиентом сообщений в области транзакции эта транзакция локальна для клиента и диспетчера очереди клиента.</span><span class="sxs-lookup"><span data-stu-id="5416a-111">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="5416a-112">При получении службой сообщений в области транзакции эта транзакция локальна для службы и диспетчера принимающей очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-112">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="5416a-113">Очень важно помнить, что клиент и служба не участвуют в одной транзакции, а используют разные транзакции при выполнении операций с очередью (например, отправки и получения).</span><span class="sxs-lookup"><span data-stu-id="5416a-113">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="5416a-114">В этом образце клиент отправляет службе пакет сообщений из области транзакции.</span><span class="sxs-lookup"><span data-stu-id="5416a-114">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="5416a-115">Сообщения, отправленные в очередь, принимаются после этого службой в области транзакции, определенной службой.</span><span class="sxs-lookup"><span data-stu-id="5416a-115">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="5416a-116">Контракт службы - `IOrderProcessor`, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="5416a-116">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="5416a-117">Интерфейс определяет одностороннюю службу, которую можно использовать с очередями.</span><span class="sxs-lookup"><span data-stu-id="5416a-117">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="5416a-118">Поведение службы определяет поведение операции со значением `TransactionScopeRequired`, равным `true`.</span><span class="sxs-lookup"><span data-stu-id="5416a-118">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="5416a-119">Это обеспечивает использование любыми диспетчерами ресурсов, к которым обращается метод, той же области транзакции, что и для получения сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-119">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="5416a-120">Кроме того, этим гарантируется возврат сообщения в очередь, если метод создаст исключение.</span><span class="sxs-lookup"><span data-stu-id="5416a-120">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="5416a-121">Если не установить такое поведение операции, канал в очереди создает транзакцию для чтения сообщения из очереди и автоматически фиксирует ее перед передачей, поэтому при ошибке операции сообщение теряется.</span><span class="sxs-lookup"><span data-stu-id="5416a-121">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="5416a-122">Обычная схема для операций служб заключается в зачислении транзакции, которая используется для чтения сообщения из очереди, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="5416a-122">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

<span data-ttu-id="5416a-123">Служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="5416a-123">The service is self hosted.</span></span> <span data-ttu-id="5416a-124">При работе с транспортом MSMQ используемую очередь следует создавать заранее.</span><span class="sxs-lookup"><span data-stu-id="5416a-124">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="5416a-125">Это можно сделать вручную или с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="5416a-125">This can be done manually or through code.</span></span> <span data-ttu-id="5416a-126">В данном образце служба содержит код для проверки наличия очереди и ее создания, если очереди нет.</span><span class="sxs-lookup"><span data-stu-id="5416a-126">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="5416a-127">Имя очереди считывается из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5416a-127">The queue name is read from the configuration file.</span></span> <span data-ttu-id="5416a-128">Базовый адрес используется [средством служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для создания прокси-сервера для службы.</span><span class="sxs-lookup"><span data-stu-id="5416a-128">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);

    // Create a ServiceHost for the OrderProcessorService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="5416a-129">Имя очереди MSMQ задается в разделе appSettings файла конфигурации, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5416a-129">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="5416a-130">В имени очереди для определения локального компьютера используется точка (.), а при создании очереди с помощью <xref:System.Messaging> в пути в качестве разделителей используются символы обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="5416a-130">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="5416a-131">Конечная точка Windows Communication Foundation (WCF) использует адрес очереди в схеме NET. MSMQ, использует "localhost" для обозначения локального компьютера и использует косую черту в пути.</span><span class="sxs-lookup"><span data-stu-id="5416a-131">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="5416a-132">Клиент создает область транзакции.</span><span class="sxs-lookup"><span data-stu-id="5416a-132">The client creates a transaction scope.</span></span> <span data-ttu-id="5416a-133">Связь с очередью происходит в области транзакции, поэтому она обрабатывается как единый модуль, в котором либо все сообщения отправляются в очередь, либо в очередь не отправляется ни одного сообщения.</span><span class="sxs-lookup"><span data-stu-id="5416a-133">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="5416a-134">Транзакция фиксируется вызовом метода <xref:System.Transactions.TransactionScope.Complete%2A> для области транзакции.</span><span class="sxs-lookup"><span data-stu-id="5416a-134">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

// Create the purchase order.
PurchaseOrder po = new PurchaseOrder();
po.CustomerId = "somecustomer.com";
po.PONumber = Guid.NewGuid().ToString();

PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
lineItem1.ProductId = "Blue Widget";
lineItem1.Quantity = 54;
lineItem1.UnitCost = 29.99F;

PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
lineItem2.ProductId = "Red Widget";
lineItem2.Quantity = 890;
lineItem2.UnitCost = 45.89F;

po.orderLineItems = new PurchaseOrderLineItem[2];
po.orderLineItems[0] = lineItem1;
po.orderLineItems[1] = lineItem2;

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="5416a-135">Чтобы убедиться, что транзакции работают, измените клиент, преобразовав область транзакции в комментарий, как показано в следующем фрагменте кода, снова выполните построение решения и запустите клиент.</span><span class="sxs-lookup"><span data-stu-id="5416a-135">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="5416a-136">Так как транзакция не завершена, сообщения не отправляются в очередь.</span><span class="sxs-lookup"><span data-stu-id="5416a-136">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="5416a-137">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="5416a-137">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5416a-138">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="5416a-138">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5416a-139">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="5416a-139">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5416a-140">Обратите внимание, что поскольку используется очередь, клиенту и службе не обязательно быть запущенными и работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="5416a-140">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5416a-141">Можно запустить клиент, выключить его, а затем запустить службу и все равно получить сообщения клиента.</span><span class="sxs-lookup"><span data-stu-id="5416a-141">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5416a-142">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="5416a-142">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5416a-143">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5416a-143">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5416a-144">При первом запуске служба проверит наличие очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-144">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5416a-145">Если очередь отсутствует, служба ее создаст.</span><span class="sxs-lookup"><span data-stu-id="5416a-145">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5416a-146">Можно сначала запустить службу, чтобы создать очередь, либо создать ее с помощью диспетчера очередей MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5416a-146">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5416a-147">Чтобы создать очередь в Windows 2008, выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="5416a-147">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="5416a-148">Откройте диспетчер сервера в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5416a-148">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="5416a-149">Разверните вкладку **функции** .</span><span class="sxs-lookup"><span data-stu-id="5416a-149">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="5416a-150">Щелкните правой кнопкой мыши **частные очереди сообщений** и выберите **создать**, **Частная очередь**.</span><span class="sxs-lookup"><span data-stu-id="5416a-150">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="5416a-151">Установите флажок **транзакционная** .</span><span class="sxs-lookup"><span data-stu-id="5416a-151">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="5416a-152">Введите в `ServiceModelSamplesTransacted` качестве имени новой очереди.</span><span class="sxs-lookup"><span data-stu-id="5416a-152">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="5416a-153">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5416a-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="5416a-154">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5416a-154">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="5416a-155">По умолчанию с привязкой <xref:System.ServiceModel.NetMsmqBinding> безопасность транспорта включена.</span><span class="sxs-lookup"><span data-stu-id="5416a-155">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="5416a-156">Имеется два соответствующих свойства для обеспечения безопасности транспорта MSMQ: <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> и <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="5416a-156">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="5416a-157">По умолчанию задан режим проверки подлинности `Windows` и уровень защиты `Sign`.</span><span class="sxs-lookup"><span data-stu-id="5416a-157">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="5416a-158">Чтобы служба MSMQ обеспечивала возможности проверки подлинности и подписывания, она должна входить в домен, а также должна быть установлена возможность интеграции MSMQ со службой каталогов Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5416a-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="5416a-159">Если запустить этот образец на компьютере, который не удовлетворяет этому условию, возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="5416a-159">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="5416a-160">Выполнение образца на компьютере, входящем в рабочую группу, или без интеграции с Active Directory</span><span class="sxs-lookup"><span data-stu-id="5416a-160">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="5416a-161">Если компьютер не входит в домен или не установлена интеграция с Active Directory, отключите безопасность транспорта, задав для режима проверки подлинности и уровня защиты значение `None`, как показано в следующем образце кода конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5416a-161">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="5416a-162">Перед выполнением примера убедитесь, что изменена конфигурация как сервера, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="5416a-162">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5416a-163">Задание для `security mode` значения `None` эквивалентно заданию для параметров безопасности <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> и `Message` значения `None`.</span><span class="sxs-lookup"><span data-stu-id="5416a-163">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5416a-164">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5416a-164">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5416a-165">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5416a-165">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5416a-166">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5416a-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5416a-167">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5416a-167">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
