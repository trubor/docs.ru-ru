---
description: 'Дополнительные сведения: очереди недоставленных сообщений'
title: Очереди недоставленных сообщений
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 5cec218f993fd99d1419aab884addfba686337c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632156"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="e1fa5-103">Очереди недоставленных сообщений</span><span class="sxs-lookup"><span data-stu-id="e1fa5-103">Dead Letter Queues</span></span>

<span data-ttu-id="e1fa5-104">В этом образце показано, как обрабатывать недоставленные сообщения.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-104">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="e1fa5-105">Он основан на образце [транзакционной привязки MSMQ](transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="e1fa5-105">It is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="e1fa5-106">В этом примере используется привязка `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-106">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="e1fa5-107">Служба представляет собой резидентное консольное приложение, позволяющее наблюдать за получением службой сообщений из очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-107">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fa5-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fa5-109">В этом примере демонстрируется использование очереди недоставленных сообщений приложения, которая доступна только в Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-109">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="e1fa5-110">Этот пример можно изменить, чтобы использовать системные очереди по умолчанию для MSMQ 3,0 в Windows Server 2003 и Windows XP.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-110">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="e1fa5-111">При использовании очередей клиент взаимодействует со службой посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="e1fa5-112">Конкретно, клиент отправляет сообщения в очередь.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="e1fa5-113">Служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-113">The service receives messages from the queue.</span></span> <span data-ttu-id="e1fa5-114">Поэтому клиенту и службе не обязательно выполняться одновременно, чтобы взаимодействовать посредством очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="e1fa5-115">Связь с использованием очереди может приводить к определенным задержкам, поэтому следует назначать для сообщений срок жизни, чтобы сообщения не доставлялись приложению позже положенного времени.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-115">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="e1fa5-116">В некоторых случаях приложению нужно знать, что приложение не доставлено.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-116">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="e1fa5-117">В таких ситуациях, если истек срок жизни сообщения или его не удалось доставить, сообщение помещается в очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-117">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="e1fa5-118">Отправляющее приложение может после этого выполнить чтение сообщений из очереди недоставленных сообщений и предпринять корректирующие действия (к ним относятся ситуации от бездействия приложения до исправления причины ошибки доставки и повторной отправки сообщения).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-118">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="e1fa5-119">Очередь недоставленных сообщений в привязке `NetMsmqBinding` выражается в следующих свойствах.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-119">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="e1fa5-120">Свойство <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> выражает тип очереди недоставленных сообщений, который необходим клиенту.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-120"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="e1fa5-121">Значения перечисления указаны ниже:</span><span class="sxs-lookup"><span data-stu-id="e1fa5-121">This enumeration has the following values:</span></span>

- <span data-ttu-id="e1fa5-122">`None`: клиенту не требуется очередь недоставленных сообщений;</span><span class="sxs-lookup"><span data-stu-id="e1fa5-122">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="e1fa5-123">`System`: для хранения сообщений, которые не удалось доставить, служит системная очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-123">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="e1fa5-124">Системная очередь недоставленных сообщений общая для всех приложений, работающих на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-124">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="e1fa5-125">`Custom`: для хранения сообщений, которые не удалось доставить, служит пользовательская очередь недоставленных сообщений, определяемая с помощью свойства <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-125">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="e1fa5-126">Эта функция доступна только в Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-126">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="e1fa5-127">Используется, если приложению нужна собственная очередь недоставленных сообщений, независимая от других приложений, работающих на данном компьютере.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-127">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="e1fa5-128">Свойство <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> выражает конкретную очередь, которая используется как очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-128"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="e1fa5-129">Эта проблема доступна только в Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-129">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="e1fa5-130">В этом образце клиент отправляет службе пакет сообщений из области транзакции и задает неоправданно низкое значение срока жизни этих сообщений (около 2 секунд).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-130">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="e1fa5-131">Клиент также задает пользовательскую очередь недоставленных сообщений, в которую помещаются сообщения с истекшим сроком жизни.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-131">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="e1fa5-132">Клиентское приложение может после этого выполнить чтение сообщений из очереди недоставленных сообщений и попытаться повторно отправить сообщение или исправить ошибку, из-за которой сообщение оказалось в очереди недоставленных сообщений, и отправить его.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-132">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="e1fa5-133">В этом образце клиент отображает сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-133">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="e1fa5-134">Контракт службы - `IOrderProcessor`, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-134">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="e1fa5-135">Код службы в примере — это [Привязка транзакционной MSMQ](transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-135">The service code in the sample is that of the [Transacted MSMQ Binding](transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="e1fa5-136">Связь с службой осуществляется в области транзакции.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-136">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="e1fa5-137">Служба выполняет чтение сообщений из очереди, выполняет операцию и отображает результаты операции.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-137">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="e1fa5-138">Также приложение создает очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-138">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="e1fa5-139">В конфигурации клиента задается короткий срок, в течение которого сообщение должно достичь службы.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-139">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="e1fa5-140">Если за указанное время сообщение передать не удается, его срок жизни истекает и оно помещается в очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-140">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fa5-141">Клиент может доставить сообщение в очередь службы за указанное время.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-141">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="e1fa5-142">Чтобы увидеть работу службы недоставленных сообщений, следует сначала запустить клиент, а только затем - службу.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-142">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="e1fa5-143">Срок жизни сообщения истекает, и оно передается службе недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-143">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="e1fa5-144">Приложение должно определить очередь, которая используется в качестве очереди недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-144">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="e1fa5-145">Если очередь не задана, для недоставленных сообщений используется системная очередь недоставленных сообщений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-145">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="e1fa5-146">В этом примере клиентское приложение задает собственную очередь недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-146">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="e1fa5-147">Служба недоставленных сообщений выполняет чтение сообщений из очереди недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-147">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="e1fa5-148">Служба недоставленных сообщений реализует контракт `IOrderProcessor`.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-148">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="e1fa5-149">Эта реализация не связана с обработкой команд.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-149">Its implementation however is not to process orders.</span></span> <span data-ttu-id="e1fa5-150">Служба недоставленных сообщений - это клиентская служба, она не имеет возможности обрабатывать команды.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-150">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fa5-151">Очередь недоставленных сообщений - это клиентская очередь, локальная для диспетчера очереди клиента.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-151">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="e1fa5-152">Реализация службы недоставленных сообщений ищет причину, по которой сообщение не было доставлено, и принимает меры по исправлению ошибки.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-152">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="e1fa5-153">Причина ошибки доставки сообщения содержится в двух перечислениях: <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> и <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-153">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="e1fa5-154">Объект <xref:System.ServiceModel.Channels.MsmqMessageProperty> можно извлечь из объекта <xref:System.ServiceModel.OperationContext>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-154">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="e1fa5-155">Сообщения в очереди недоставленных сообщений - это сообщения, адресованные службе, обрабатывающей сообщение.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-155">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="e1fa5-156">Таким образом, когда Служба недоставленных сообщений считывает сообщения из очереди, уровень канала Windows Communication Foundation (WCF) находит несоответствие в конечных точках и не отправляет сообщение.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-156">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="e1fa5-157">В этом случае сообщение адресуется службе, обрабатывающей заказы, но доставляется оно службе недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-157">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="e1fa5-158">Для получения сообщений, адресованных другой конечной точке, в `ServiceBehavior` задается фильтр адресов, соответствующий любому адресу.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-158">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="e1fa5-159">Это необходимо для успешной обработки сообщений, считываемых из очереди недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-159">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="e1fa5-160">В этом примере служба недоставленных сообщений повторно отправляет сообщение, если причина сбоя заключается в том, что время ожидания сообщения истекло. По всем остальным причинам отображается ошибка доставки, как показано в следующем образце кода:</span><span class="sxs-lookup"><span data-stu-id="e1fa5-160">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="e1fa5-161">В следующем образце показана конфигурация для недоставленного сообщения:</span><span class="sxs-lookup"><span data-stu-id="e1fa5-161">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="e1fa5-162">В этом образце нужно запустить три исполняемых файла, чтобы посмотреть, как работает очередь недоставленных сообщений для всех приложений: клиента, службы и службы недоставленных сообщений, которая выполняет чтение очереди недоставленных сообщений для каждого приложения и повторно отправляет сообщение службе.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-162">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="e1fa5-163">Это консольные приложения, отображающие вывод в окнах консоли.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-163">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="e1fa5-164">Поскольку используется очередь, клиенту и службе не обязательно быть запущенными и работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-164">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="e1fa5-165">Можно запустить клиент, выключить его, а затем запустить службу, которая все равно получит сообщения клиента.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-165">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="e1fa5-166">Для создания очереди следует запустить и завершить службу.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-166">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="e1fa5-167">При запуске клиент отображает сообщение:</span><span class="sxs-lookup"><span data-stu-id="e1fa5-167">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="e1fa5-168">Клиент попытался отправить сообщение, но короткое время жизни сообщения истекло, и оно попало в очередь недоставленных сообщений для каждого приложения.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-168">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="e1fa5-169">После этого запускается служба недоставленных сообщений, которая выполняет чтение сообщения, отображает код ошибки и повторно отправляет сообщение службе.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-169">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="e1fa5-170">Служба запускается, выполняет чтение повторно отправленного сообщения и обрабатывает его.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-170">The service starts and then reads the resent message and processes it.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e1fa5-171">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="e1fa5-171">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e1fa5-172">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-172">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e1fa5-173">При первом запуске служба проверит наличие очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-173">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="e1fa5-174">Если очередь отсутствует, служба ее создаст.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-174">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="e1fa5-175">Можно сначала запустить службу, чтобы создать очередь, либо создать ее с помощью диспетчера очередей MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-175">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="e1fa5-176">Чтобы создать очередь в Windows 2008, выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-176">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="e1fa5-177">Откройте диспетчер сервера в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-177">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="e1fa5-178">Разверните вкладку **функции** .</span><span class="sxs-lookup"><span data-stu-id="e1fa5-178">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="e1fa5-179">Щелкните правой кнопкой мыши **частные очереди сообщений** и выберите **создать**, **Частная очередь**.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-179">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="e1fa5-180">Установите флажок **транзакционная** .</span><span class="sxs-lookup"><span data-stu-id="e1fa5-180">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="e1fa5-181">Введите в `ServiceModelSamplesTransacted` качестве имени новой очереди.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-181">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="e1fa5-182">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-182">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="e1fa5-183">Чтобы выполнить пример в конфигурации с одним или несколькими компьютерами соответствующим образом, замените localhost на полное имя компьютера и следуйте инструкциям в разделе [Запуск примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-183">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="e1fa5-184">Выполнение образца на компьютере, входящем в рабочую группу</span><span class="sxs-lookup"><span data-stu-id="e1fa5-184">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="e1fa5-185">Если компьютер не входит в домен, отключите безопасность транспорта, задав для режима проверки подлинности и уровня защиты значение `None`, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-185">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="e1fa5-186">Обеспечьте связь конечной точки с привязкой, задав атрибут `bindingConfiguration` конечной точки.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-186">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="e1fa5-187">Перед выполнением образца убедитесь, что изменена конфигурация службы DeadLetterService, сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-187">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e1fa5-188">Установка для `security mode` значения `None` эквивалентна присвоению свойствам `MsmqAuthenticationMode`, `MsmqProtectionLevel` и безопасности `Message` значения `None`.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-188">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="e1fa5-189">Комментарии</span><span class="sxs-lookup"><span data-stu-id="e1fa5-189">Comments</span></span>

 <span data-ttu-id="e1fa5-190">По умолчанию с транспортом привязки `netMsmqBinding` безопасность включена.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-190">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="e1fa5-191">Тип безопасности транспорта определяется двумя свойствами: `MsmqAuthenticationMode` и `MsmqProtectionLevel`.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-191">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="e1fa5-192">По умолчанию устанавливается режим проверки подлинности `Windows` и уровень защиты `Sign`.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-192">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="e1fa5-193">Чтобы служба MSMQ обеспечивала возможности проверки подлинности и подписывания, она должна входить в домен.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-193">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="e1fa5-194">При выполнении этого примера на компьютере, не входящем в домен, возникает следующая ошибка: "User's internal message queuing certificate does not exist" (не существует внутреннего сертификата очереди сообщений пользователя).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-194">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1fa5-195">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-195">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1fa5-196">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e1fa5-196">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e1fa5-197">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-197">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1fa5-198">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="e1fa5-198">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
