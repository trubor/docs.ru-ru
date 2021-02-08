---
description: 'Дополнительные сведения о: Windows Communication Foundation в очередь сообщений'
title: Отправка сообщений из приложения Windows Communication Foundation в приложение MSMQ
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ef4fe5f23b4ce462b13e12b706a3a72225a74f8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798190"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="f6eb9-103">Отправка сообщений из приложения Windows Communication Foundation в приложение MSMQ</span><span class="sxs-lookup"><span data-stu-id="f6eb9-103">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="f6eb9-104">В этом примере показано, как приложение Windows Communication Foundation (WCF) может отправить сообщение в приложение очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-104">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="f6eb9-105">Служба представляет собой резидентное консольное приложение, позволяющее наблюдать за получением службой сообщений из очереди.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="f6eb9-106">Одновременная работа службы и клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-106">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="f6eb9-107">Служба получает сообщения от очереди и обрабатывает заказы.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-107">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="f6eb9-108">Служба создает транзакционную очередь и создает обработчик полученных сообщений, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-108">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="f6eb9-109">При получении сообщения в очереди вызывается обработчик сообщений `ProcessOrder`.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-109">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="f6eb9-110">Служба извлекает `ProcessOrder` из тела сообщения MSMQ и обрабатывает заказ.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-110">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="f6eb9-111">Имя очереди MSMQ задается в разделе appSettings файла конфигурации, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-111">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="f6eb9-112">В имени очереди для определения локального компьютера используется точка (.), а в пути в качестве разделителей используются символы обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-112">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="f6eb9-113">Клиент создает заказ на покупку и отправляет его в пределах транзакции, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-113">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="f6eb9-114">При отправке сообщения MSMQ в очередь клиент использует внутренний пользовательский порядок сообщений.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-114">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="f6eb9-115">Так как приложение, получающее и обрабатывающее сообщение, является приложением MSMQ, а не приложением WCF, неявный контракт службы между двумя приложениями отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-115">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="f6eb9-116">Таким образом, в данном сценарии невозможно создать прокси-класс при помощи средства Svculti.exe.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-116">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="f6eb9-117">По сути, Пользовательский клиент одинаков для всех приложений WCF, использующих `MsmqIntegration` привязку для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-117">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="f6eb9-118">В отличие от других клиентов, он не включает ряд операций службы.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-118">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="f6eb9-119">В него входит только операция отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-119">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="f6eb9-120">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-120">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f6eb9-121">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-121">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f6eb9-122">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-122">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="f6eb9-123">Обратите внимание, что поскольку используется очередь, клиенту и службе не обязательно быть запущенными и работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-123">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f6eb9-124">Например, можно запустить клиент, выключить его, а затем запустить службу и все равно получить сообщения клиента.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-124">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="f6eb9-125">Данный образец требует установки очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-125">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="f6eb9-126">См. инструкции по установке в [очереди сообщений](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-126">See the installation instructions in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f6eb9-127">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="f6eb9-127">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="f6eb9-128">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f6eb9-129">При первом запуске служба проверит наличие очереди.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-129">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f6eb9-130">Если очередь отсутствует, служба ее создаст.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-130">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f6eb9-131">Можно сначала запустить службу, чтобы создать очередь, либо создать ее с помощью диспетчера очередей MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-131">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f6eb9-132">Чтобы создать очередь в Windows 2008, выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-132">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f6eb9-133">Откройте диспетчер сервера в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-133">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f6eb9-134">Разверните вкладку **функции** .</span><span class="sxs-lookup"><span data-stu-id="f6eb9-134">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f6eb9-135">Щелкните правой кнопкой мыши **частные очереди сообщений**, а затем выберите **создать**  >  **частную очередь**.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-135">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="f6eb9-136">Установите флажок **транзакционная** .</span><span class="sxs-lookup"><span data-stu-id="f6eb9-136">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f6eb9-137">Введите в `ServiceModelSamplesTransacted` качестве имени новой очереди.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-137">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f6eb9-138">Чтобы создать выпуск решения на C# или Visual Basic, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-138">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f6eb9-139">Чтобы запустить пример в конфигурации с одним компьютером, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-139">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="f6eb9-140">Запуск примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="f6eb9-140">Run the sample across computers</span></span>

1. <span data-ttu-id="f6eb9-141">Скопируйте на компьютер службы файлы служебной программы из папки \service\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-141">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="f6eb9-142">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-142">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="f6eb9-143">В файле Client.exe.config измените адрес конечной точки клиента, указав имя компьютера службы вместо «.».</span><span class="sxs-lookup"><span data-stu-id="f6eb9-143">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="f6eb9-144">На компьютере службы запустите из командной строки программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-144">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="f6eb9-145">На клиентском компьютере из командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-145">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6eb9-146">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f6eb9-147">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="f6eb9-147">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f6eb9-148">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6eb9-149">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="f6eb9-149">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="f6eb9-150">См. также</span><span class="sxs-lookup"><span data-stu-id="f6eb9-150">See also</span></span>

- [<span data-ttu-id="f6eb9-151">Практическое руководство. Обмен сообщениями с конечными точками WCF и приложениями очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="f6eb9-151">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="f6eb9-152">[служба очередей сообщений](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f6eb9-152">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
