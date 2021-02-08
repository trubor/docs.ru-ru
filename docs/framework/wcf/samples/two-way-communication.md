---
description: 'Дополнительные сведения о связи: Two-Way'
title: Двусторонний обмен данными
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 8e7f87c6ecd672d270a673a8e933e3c9ed4b5c00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798255"
---
# <a name="two-way-communication"></a><span data-ttu-id="9231e-103">Двусторонний обмен данными</span><span class="sxs-lookup"><span data-stu-id="9231e-103">Two-Way Communication</span></span>

<span data-ttu-id="9231e-104">В этом образце показано, как осуществлять транзакционное двустороннее взаимодействие с использованием очередей с помощью MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9231e-104">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="9231e-105">В этом примере используется привязка `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="9231e-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="9231e-106">В данном случае служба представляет собой резидентное консольное приложение, позволяющее наблюдать за тем, как служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="9231e-106">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9231e-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="9231e-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9231e-108">Этот пример основан на [привязке MSMQ](transacted-msmq-binding.md)с поддержкой транзакций.</span><span class="sxs-lookup"><span data-stu-id="9231e-108">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="9231e-109">При использовании очередей клиент взаимодействует со службой посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="9231e-109">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="9231e-110">Клиент отправляет сообщения в очередь, а служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="9231e-110">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="9231e-111">Поэтому клиенту и службе не обязательно выполняться одновременно, чтобы взаимодействовать посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="9231e-111">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="9231e-112">В этом образце показано двустороннее взаимодействие с использованием очередей.</span><span class="sxs-lookup"><span data-stu-id="9231e-112">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="9231e-113">Клиент отправляет заказы на покупку в очередь из области транзакции.</span><span class="sxs-lookup"><span data-stu-id="9231e-113">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="9231e-114">Служба получает заказы, обрабатывает заказ и вызывает клиент с состоянием заказа из очереди из области транзакции.</span><span class="sxs-lookup"><span data-stu-id="9231e-114">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="9231e-115">Для двустороннего взаимодействия и клиент, и служба используют очереди для заказов на покупку и состояний заказов.</span><span class="sxs-lookup"><span data-stu-id="9231e-115">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="9231e-116">Контракт службы `IOrderProcessor` определяет односторонние операции службы, которые можно использовать с очередями.</span><span class="sxs-lookup"><span data-stu-id="9231e-116">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="9231e-117">Операция службы включает конечную точку ответа, на которую нужно отправлять состояния заказов.</span><span class="sxs-lookup"><span data-stu-id="9231e-117">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="9231e-118">Конечная точка ответа - это универсальный код ресурса (URI) очереди, служащей для отправки клиенту состояний заказов.</span><span class="sxs-lookup"><span data-stu-id="9231e-118">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="9231e-119">Приложение, обрабатывающее заказы, реализует этот контракт.</span><span class="sxs-lookup"><span data-stu-id="9231e-119">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="9231e-120">Контракт ответа для отправки состояния заказа задается клиентом.</span><span class="sxs-lookup"><span data-stu-id="9231e-120">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="9231e-121">Клиент реализует контракт состояния заказа.</span><span class="sxs-lookup"><span data-stu-id="9231e-121">The client implements the order status contract.</span></span> <span data-ttu-id="9231e-122">Служба использует созданный прокси этого контракта для отправки состояния заказа клиенту.</span><span class="sxs-lookup"><span data-stu-id="9231e-122">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="9231e-123">Операция службы обрабатывает отправленный заказ на покупку.</span><span class="sxs-lookup"><span data-stu-id="9231e-123">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="9231e-124">Объект <xref:System.ServiceModel.OperationBehaviorAttribute> применяется к операции службы, чтобы задать автоматическое зачисление в транзакции, использующейся для получения сообщения из очереди, и автоматическое завершение транзакций после завершения операции службы.</span><span class="sxs-lookup"><span data-stu-id="9231e-124">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="9231e-125">Класс `Orders` инкапсулирует функцию обработки заказа.</span><span class="sxs-lookup"><span data-stu-id="9231e-125">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="9231e-126">В данном случае он добавляет заказ на покупку в словарь.</span><span class="sxs-lookup"><span data-stu-id="9231e-126">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="9231e-127">Транзакция, в которую зачислена операция службы, доступна операциям в классе `Orders`.</span><span class="sxs-lookup"><span data-stu-id="9231e-127">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="9231e-128">Операция службы, помимо обработки отправленного заказа на закупку, отвечает клиенту о состоянии заказа.</span><span class="sxs-lookup"><span data-stu-id="9231e-128">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="9231e-129">Имя очереди MSMQ задается в разделе appSettings файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9231e-129">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="9231e-130">Конечная точка службы определяется в разделе System.ServiceModel файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9231e-130">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9231e-131">Правила адресации несколько различаются для имени очереди MSMQ и адреса конечной точки.</span><span class="sxs-lookup"><span data-stu-id="9231e-131">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="9231e-132">В имени очереди MSMQ для определения локального компьютера используется точка (.), а в пути в качестве разделителей используются символы обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="9231e-132">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="9231e-133">Адрес конечной точки Windows Communication Foundation (WCF) указывает схему "net. msmq:", использует "localhost" для локального компьютера и использует косую черту в пути.</span><span class="sxs-lookup"><span data-stu-id="9231e-133">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="9231e-134">Для чтения очереди, размещенной на удаленном компьютере, "." и "localhost" следует заменить именем удаленного компьютера.</span><span class="sxs-lookup"><span data-stu-id="9231e-134">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="9231e-135">Служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="9231e-135">The service is self hosted.</span></span> <span data-ttu-id="9231e-136">При работе с транспортом MSMQ используемую очередь следует создавать заранее.</span><span class="sxs-lookup"><span data-stu-id="9231e-136">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9231e-137">Это можно сделать вручную или с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="9231e-137">This can be done manually or through code.</span></span> <span data-ttu-id="9231e-138">В данном образце служба проверяет наличие очереди и создает ее, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="9231e-138">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="9231e-139">Имя очереди считывается из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9231e-139">The queue name is read from the configuration file.</span></span> <span data-ttu-id="9231e-140">Базовый адрес используется [средством служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) для создания прокси-сервера для службы.</span><span class="sxs-lookup"><span data-stu-id="9231e-140">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 <span data-ttu-id="9231e-141">Клиент создает транзакцию.</span><span class="sxs-lookup"><span data-stu-id="9231e-141">The client creates a transaction.</span></span> <span data-ttu-id="9231e-142">Связь с очередью происходит в области транзакции, поэтому она обрабатывается как единый модуль, в котором либо все сообщения отправляются успешно, либо не отправляется ни одного.</span><span class="sxs-lookup"><span data-stu-id="9231e-142">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="9231e-143">Код клиента реализует контракт `IOrderStatus` для получения от службы состояния заказа.</span><span class="sxs-lookup"><span data-stu-id="9231e-143">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="9231e-144">В данном случае он выводит состояние заказа.</span><span class="sxs-lookup"><span data-stu-id="9231e-144">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 <span data-ttu-id="9231e-145">Очередь состояний заказов создается в методе `Main`.</span><span class="sxs-lookup"><span data-stu-id="9231e-145">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="9231e-146">Конфигурация клиента включает конфигурацию службы состояния заказов, размещающую службу состояния заказов, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9231e-146">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9231e-147">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="9231e-147">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9231e-148">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="9231e-148">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9231e-149">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="9231e-149">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="9231e-150">Служба отображает сведения заказа на покупку и указывает, что отправляет состояние заказа в очередь состояний заказов.</span><span class="sxs-lookup"><span data-stu-id="9231e-150">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="9231e-151">Клиент отображает сведения о состоянии заказа, отправленные службой.</span><span class="sxs-lookup"><span data-stu-id="9231e-151">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9231e-152">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="9231e-152">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9231e-153">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9231e-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9231e-154">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9231e-154">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9231e-155">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9231e-155">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9231e-156">Если для восстановления конфигурации этого образца используется программа Svcutil.exe, измените имена конечных точек в конфигурации клиента для соответствия клиентскому коду.</span><span class="sxs-lookup"><span data-stu-id="9231e-156">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="9231e-157">По умолчанию с привязкой <xref:System.ServiceModel.NetMsmqBinding> безопасность транспорта включена.</span><span class="sxs-lookup"><span data-stu-id="9231e-157">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="9231e-158">Существует два соответствующих свойства безопасности транспорта MSMQ, и по <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` умолчанию для режима проверки подлинности задано значение `Windows` , а для уровня защиты — `Sign` .</span><span class="sxs-lookup"><span data-stu-id="9231e-158">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="9231e-159">Чтобы служба MSMQ обеспечивала возможности проверки подлинности и подписывания, она должна входить в домен, а также должна быть установлена возможность интеграции MSMQ со службой каталогов Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9231e-159">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="9231e-160">Если запустить данный образец на компьютере, который не удовлетворяет этому условию, возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="9231e-160">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="9231e-161">Запуск образца на компьютере, входящем в рабочую группу, или без интеграции с Active Directory</span><span class="sxs-lookup"><span data-stu-id="9231e-161">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="9231e-162">Если компьютер не входит в домен или не установлена интеграция с Active Directory, отключите безопасность транспорта, задав для режима проверки подлинности и уровня защиты значение `None`, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9231e-162">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="9231e-163">Отключение безопасности для конфигурации клиента дает следующий результат:</span><span class="sxs-lookup"><span data-stu-id="9231e-163">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="9231e-164">Служба в образце создает привязку в службе `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="9231e-164">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="9231e-165">Добавьте строку кода после создания экземпляра привязки, чтобы задать режим безопасности `None`.</span><span class="sxs-lookup"><span data-stu-id="9231e-165">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="9231e-166">Перед выполнением примера убедитесь, что изменена конфигурация как сервера, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="9231e-166">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9231e-167">Установка для `security mode` значения `None` равнозначна установке для безопасности <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> или `Message` значения `None`.</span><span class="sxs-lookup"><span data-stu-id="9231e-167">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9231e-168">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="9231e-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9231e-169">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="9231e-169">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9231e-170">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="9231e-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9231e-171">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="9231e-171">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
