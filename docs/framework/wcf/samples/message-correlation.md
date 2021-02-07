---
description: 'Дополнительные сведения: корреляция сообщений'
title: Корреляция сообщений
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e38e2e8d6936132e165fd3372ac57fef27240d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704034"
---
# <a name="message-correlation"></a><span data-ttu-id="6c2fc-103">Корреляция сообщений</span><span class="sxs-lookup"><span data-stu-id="6c2fc-103">Message Correlation</span></span>

<span data-ttu-id="6c2fc-104">В этом примере показано, как приложение очереди сообщений (MSMQ) может отправить сообщение MSMQ в службу Windows Communication Foundation (WCF) и как можно связать сообщения между приложениями отправителя и получателя в сценарии "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="6c2fc-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="6c2fc-105">В этом образце используется привязка msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-105">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="6c2fc-106">В данном случае служба представляет собой резидентное консольное приложение, позволяющее наблюдать за тем, как служба получает сообщения из очереди.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-106">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="6c2fc-107">k</span><span class="sxs-lookup"><span data-stu-id="6c2fc-107">k</span></span>

 <span data-ttu-id="6c2fc-108">Служба обрабатывает полученное от отправителя сообщение и отправляет отправителю ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-108">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="6c2fc-109">Отправитель согласует полученный ответ с изначально отправленным запросом.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-109">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="6c2fc-110">Свойства `MessageID` и `CorrelationID` сообщения служат для согласования сообщений запроса и ответа.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-110">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="6c2fc-111">Контракт службы `IOrderProcessor` определяет одностороннюю операцию службы, которую можно использовать с очередями.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-111">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="6c2fc-112">Сообщение MSMQ не содержит заголовка Action, поэтому автоматически соотнести различные сообщения MSMQ с контрактами операций невозможно.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-112">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="6c2fc-113">Поэтому в данном случае может существовать только один контракт операции.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-113">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="6c2fc-114">Если нужно определить для службы несколько контрактов операций, приложение должно сообщать, какой заголовок сообщения MSMQ (например, метку или correlationID) можно использовать для выбора контракта операции.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-114">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="6c2fc-115">Кроме того, сообщение MSMQ не содержит сведений о том, какие заголовки соответствуют различным параметрам контракта операции.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="6c2fc-116">Поэтому в данном случае в контракте операции может существовать только один параметр.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="6c2fc-117">Параметр имеет тип <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , который содержит базовое сообщение MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-117">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="6c2fc-118">Тип "T" в классе `MsmqMessage<T>` представляет данные, сериализованные в тело сообщения MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="6c2fc-119">В этом образце тип `PurchaseOrder` сериализован в основную часть сообщения MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="6c2fc-120">Операция службы обрабатывает заказ на закупку и отображает содержимое заказа и его статус в окне консоли службы.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="6c2fc-121">Атрибут <xref:System.ServiceModel.OperationBehaviorAttribute> настраивает операцию для включения в список в транзакции с очередью и для пометки транзакции как завершенной после завершения операции.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="6c2fc-122">`PurchaseOrder` содержит сведения о заказе, которые необходимо обработать службе.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="6c2fc-123">Служба использует пользовательский клиентский метод `OrderResponseClient` для отправки сообщения MSMQ в очередь.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="6c2fc-124">Так как приложение, получающее и обрабатывающее сообщение, является приложением MSMQ, а не приложением WCF, неявный контракт службы между двумя приложениями отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-124">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="6c2fc-125">То есть в данном сценарии нельзя создать прокси-класс с помощью средства Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="6c2fc-126">По сути, пользовательский прокси-сервер одинаков для всех приложений WCF, использующих `msmqIntegrationBinding` привязку для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-126">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="6c2fc-127">В отличии от других прокси, он не включает ряда операций службы.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="6c2fc-128">В него входит только операция отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-128">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="6c2fc-129">Служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-129">The service is self hosted.</span></span> <span data-ttu-id="6c2fc-130">При работе с транспортом интеграции MSMQ используемую очередь следует создавать заранее.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="6c2fc-131">Это можно сделать вручную или с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-131">This can be done manually or through code.</span></span> <span data-ttu-id="6c2fc-132">В данном образце служба содержит код <xref:System.Messaging> для проверки наличия очереди и ее создания, если требуется.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="6c2fc-133">Имя очереди считывается из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-133">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 <span data-ttu-id="6c2fc-134">Очередь MSMQ, в которую отправляются запросы заказов, задается в разделе appSettings файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="6c2fc-135">Конечные точки клиента и службы задаются в разделе system.serviceModel файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="6c2fc-136">Обе конечные точки задают привязку `msmqIntegrationbinding`.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-136">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="6c2fc-137">Клиентское приложение использует для отправки в очередь устойчивых и транзакционных сообщений пространство имен <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="6c2fc-138">Заказ на закупку содержится в теле сообщения.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-138">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="6c2fc-139">Очередь MSMQ, из которой получаются ответы о заказах, задается в разделе appSettings файла конфигурации, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="6c2fc-140">В имени очереди для определения локального компьютера используется точка (.), а в пути в качестве разделителей используются символы обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="6c2fc-141">Адрес конечной точки WCF указывает схему MSMQ. formatname и использует "localhost" для локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-141">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="6c2fc-142">Правильно составленное имя формата соответствует шаблону msmq.имя_формата к коде URI в соответствии с указаниями MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="6c2fc-143">Клиентское приложение сохраняет `messageID` сообщения запроса заказа, которое было отправлено службе, и ждет от службы ответа.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="6c2fc-144">После получения ответа в очереди клиент согласовывает его с отправленным сообщением заказа с помощью свойства `correlationID` сообщения, которое содержит значение `messageID` сообщения заказа, которое клиент изначально отправил службе.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="6c2fc-145">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="6c2fc-146">Можно видеть, как служба получает сообщения от клиента и отправляет ему ответные сообщения.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="6c2fc-147">Клиент отображает запросы, получаемые от службы.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-147">The client displays the response received from the service.</span></span> <span data-ttu-id="6c2fc-148">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-148">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="6c2fc-149">Данный образец требует установки очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="6c2fc-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="6c2fc-150">Инструкции по установке MSMQ см. в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="6c2fc-150">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="6c2fc-151">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="6c2fc-151">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="6c2fc-152">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2fc-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6c2fc-153">При первом запуске служба проверит наличие очереди.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="6c2fc-154">Если очередь отсутствует, служба ее создаст.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="6c2fc-155">Можно сначала запустить службу, чтобы создать очередь, либо создать ее с помощью диспетчера очередей MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="6c2fc-156">Чтобы создать очередь в Windows 2008, выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-156">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="6c2fc-157">Откройте диспетчер сервера в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-157">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="6c2fc-158">Разверните вкладку **функции** .</span><span class="sxs-lookup"><span data-stu-id="6c2fc-158">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="6c2fc-159">Щелкните правой кнопкой мыши **частные очереди сообщений** и выберите **создать**, **Частная очередь**.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="6c2fc-160">Установите флажок **транзакционная** .</span><span class="sxs-lookup"><span data-stu-id="6c2fc-160">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="6c2fc-161">Введите в `ServiceModelSamplesTransacted` качестве имени новой очереди.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="6c2fc-162">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2fc-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="6c2fc-163">Чтобы запустить пример в конфигурации с одним компьютером, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2fc-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="6c2fc-164">Запуск примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="6c2fc-164">Run the sample across computers</span></span>

1. <span data-ttu-id="6c2fc-165">Скопируйте на компьютер службы файлы служебной программы из папки \service\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="6c2fc-166">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="6c2fc-167">В файле Client.exe.config измените orderQueueName, указав имя компьютера службы вместо «.».</span><span class="sxs-lookup"><span data-stu-id="6c2fc-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="6c2fc-168">В файле Service.exe.config измените адрес конечной точки клиента, указав имя клиентского компьютера вместо «.».</span><span class="sxs-lookup"><span data-stu-id="6c2fc-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="6c2fc-169">На компьютере службы запустите из командной строки программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-169">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="6c2fc-170">На клиентском компьютере из командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-170">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c2fc-171">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6c2fc-172">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="6c2fc-172">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6c2fc-173">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c2fc-174">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="6c2fc-174">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="6c2fc-175">См. также</span><span class="sxs-lookup"><span data-stu-id="6c2fc-175">See also</span></span>

- [<span data-ttu-id="6c2fc-176">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="6c2fc-176">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="6c2fc-177">[служба очередей сообщений](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6c2fc-177">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
