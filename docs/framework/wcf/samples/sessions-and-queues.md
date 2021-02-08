---
description: 'Дополнительные сведения: сеансы и очереди'
title: Сеансы и очереди
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 94ff58fca628e44b78b002291fa78a39cc10a14f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793016"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="af921-103">Сеансы и очереди</span><span class="sxs-lookup"><span data-stu-id="af921-103">Sessions and queues</span></span>

<span data-ttu-id="af921-104">В этом образце показано, как отправлять и принимать набор связанных сообщений при взаимодействии с использованием очередей с помощью транспорта очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="af921-104">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="af921-105">В этом примере используется привязка `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="af921-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="af921-106">Служба представляет собой резидентное консольное приложение, позволяющее наблюдать за получением службой сообщений из очереди.</span><span class="sxs-lookup"><span data-stu-id="af921-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af921-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="af921-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="af921-108">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="af921-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af921-109">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="af921-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="af921-110">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="af921-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af921-111">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="af921-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="af921-112">При использовании очередей клиент взаимодействует со службой посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="af921-112">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="af921-113">Конкретно, клиент отправляет сообщения в очередь.</span><span class="sxs-lookup"><span data-stu-id="af921-113">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="af921-114">Служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="af921-114">The service receives messages from the queue.</span></span> <span data-ttu-id="af921-115">Поэтому клиенту и службе не обязательно выполняться одновременно, чтобы взаимодействовать посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="af921-115">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="af921-116">Иногда клиент отправляет набор сообщений, связанных между собой в группу.</span><span class="sxs-lookup"><span data-stu-id="af921-116">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="af921-117">Если сообщения должны обрабатываться совместно или в определенном порядке, с помощью очереди можно сгруппировать их вместе для обработки одним принимающим приложением.</span><span class="sxs-lookup"><span data-stu-id="af921-117">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="af921-118">Это особенно важно, если имеется несколько принимающих приложений на группе серверов и необходимо обеспечить, чтобы группа сообщений обрабатывалась одним и тем же принимающим приложением.</span><span class="sxs-lookup"><span data-stu-id="af921-118">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="af921-119">В качестве механизма отправки и приема связанного набора сообщений, которые должны обрабатываться одновременно, используются сеансы с очередями.</span><span class="sxs-lookup"><span data-stu-id="af921-119">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="af921-120">Чтобы сеанс с очередями демонстрировал такое поведение, требуется транзакция.</span><span class="sxs-lookup"><span data-stu-id="af921-120">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="af921-121">В этом образце клиент отправляет ряд сообщений в службу как часть сеанса в рамках одной транзакции.</span><span class="sxs-lookup"><span data-stu-id="af921-121">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="af921-122">Контракт службы `IOrderTaker` определяет одностороннюю службу, которую можно использовать с очередями.</span><span class="sxs-lookup"><span data-stu-id="af921-122">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="af921-123">Класс <xref:System.ServiceModel.SessionMode>, использованный в контракте, показанном в следующем образце кода, означает, что сообщения являются частью сеанса.</span><span class="sxs-lookup"><span data-stu-id="af921-123">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="af921-124">Служба определяет операции службы таким образом, что первая операция зачисляется в транзакцию, но не завершает транзакцию автоматически.</span><span class="sxs-lookup"><span data-stu-id="af921-124">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="af921-125">Последующие операции также зачисляются в эту же транзакцию, но не производят ее автоматического завершения.</span><span class="sxs-lookup"><span data-stu-id="af921-125">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="af921-126">Последняя операция в сеансе автоматически завершает транзакцию.</span><span class="sxs-lookup"><span data-stu-id="af921-126">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="af921-127">Таким образом, одна и та же транзакция используется для вызова нескольких операций в контракте службы.</span><span class="sxs-lookup"><span data-stu-id="af921-127">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="af921-128">Если любая из операций вызывает исключение, производится откат транзакции и сеанс возвращается в очередь.</span><span class="sxs-lookup"><span data-stu-id="af921-128">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="af921-129">После успешного завершения последней операции производится фиксация транзакции.</span><span class="sxs-lookup"><span data-stu-id="af921-129">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="af921-130">В службе значение `PerSession` параметра <xref:System.ServiceModel.InstanceContextMode> используется для того, чтобы все сообщения в сеансе получались одним экземпляром службы.</span><span class="sxs-lookup"><span data-stu-id="af921-130">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="af921-131">Служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="af921-131">The service is self hosted.</span></span> <span data-ttu-id="af921-132">При работе с транспортом MSMQ используемую очередь следует создавать заранее.</span><span class="sxs-lookup"><span data-stu-id="af921-132">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="af921-133">Это можно сделать вручную или с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="af921-133">This can be done manually or through code.</span></span> <span data-ttu-id="af921-134">В данном образце служба содержит код <xref:System.Messaging> для проверки наличия очереди и ее создания, если требуется.</span><span class="sxs-lookup"><span data-stu-id="af921-134">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="af921-135">Имя очереди считывается из файла конфигурации с помощью класса <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span><span class="sxs-lookup"><span data-stu-id="af921-135">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();
    }  
}  
```

 <span data-ttu-id="af921-136">Имя очереди MSMQ задается в разделе appSettings файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af921-136">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="af921-137">Конечная точка для службы задается в разделе system.serviceModel файла конфигурации и определяет привязку `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="af921-137">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="af921-138">Клиент создает область транзакции.</span><span class="sxs-lookup"><span data-stu-id="af921-138">The client creates a transaction scope.</span></span> <span data-ttu-id="af921-139">Все сообщения в сеансе отправляются в очередь в области транзакции, поэтому она обрабатывается как единый модуль, в котором все сообщения завершаются успехом или сбоем.</span><span class="sxs-lookup"><span data-stu-id="af921-139">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="af921-140">Транзакция фиксируется путем вызова метода <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="af921-140">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> <span data-ttu-id="af921-141">Можно использовать только одну транзакцию для всех сообщений в сеансе, и все сообщения в сеансе должны быть отправлены до фиксации транзакции.</span><span class="sxs-lookup"><span data-stu-id="af921-141">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="af921-142">При закрытии клиента сеанс также закрывается.</span><span class="sxs-lookup"><span data-stu-id="af921-142">Closing the client closes the session.</span></span> <span data-ttu-id="af921-143">Поэтому для отправки всех сообщений в сеансе в очередь клиент должен быть закрыт до завершения транзакции.</span><span class="sxs-lookup"><span data-stu-id="af921-143">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="af921-144">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="af921-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="af921-145">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="af921-145">You can see the service receive messages from the client.</span></span> <span data-ttu-id="af921-146">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="af921-146">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="af921-147">Поскольку используется очередь, клиенту и службе не обязательно быть запущенными и работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="af921-147">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="af921-148">Можно запустить клиент, выключить его, а затем запустить службу, которая все равно получит сообщения клиента.</span><span class="sxs-lookup"><span data-stu-id="af921-148">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="af921-149">На клиенте.</span><span class="sxs-lookup"><span data-stu-id="af921-149">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="af921-150">В службе.</span><span class="sxs-lookup"><span data-stu-id="af921-150">On the service.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="af921-151">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="af921-151">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="af921-152">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af921-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="af921-153">Чтобы создать выпуск решения на C#, C++ или Visual Basic .NET, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af921-153">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="af921-154">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af921-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
 <span data-ttu-id="af921-155">По умолчанию с привязкой <xref:System.ServiceModel.NetMsmqBinding> безопасность транспорта включена.</span><span class="sxs-lookup"><span data-stu-id="af921-155">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="af921-156">Есть два соответствующих свойства для безопасности транспорта MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> и по <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` умолчанию для режима проверки подлинности задано значение, `Windows` а для уровня защиты — `Sign` .</span><span class="sxs-lookup"><span data-stu-id="af921-156">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="af921-157">Чтобы служба MSMQ обеспечивала возможности проверки подлинности и подписывания, она должна входить в домен, а также должна быть установлена возможность интеграции MSMQ со службой каталогов Active Directory.</span><span class="sxs-lookup"><span data-stu-id="af921-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="af921-158">Если запустить этот образец на компьютере, который не удовлетворяет этому условию, возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="af921-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="af921-159">Запуск примера на компьютере, присоединенном к Рабочей группе</span><span class="sxs-lookup"><span data-stu-id="af921-159">Run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="af921-160">Если компьютер не входит в домен или не установлена интеграция с Active Directory, отключите безопасность транспорта, задав для режима проверки подлинности и уровня защиты значение `None`, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af921-160">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="af921-161">Перед выполнением примера убедитесь, что изменена конфигурация как сервера, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="af921-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="af921-162">Установка для режима безопасности значения `None` равносильна установке для <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> и безопасности `Message` значения `None`.</span><span class="sxs-lookup"><span data-stu-id="af921-162">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
