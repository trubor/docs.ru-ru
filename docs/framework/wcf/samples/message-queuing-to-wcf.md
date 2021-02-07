---
description: Дополнительные сведения см. в статье очередь сообщений для Windows Communication Foundation
title: Передача сообщений из приложения MSMQ в приложение Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 53c535379584bcb8fa50d1b550f87ea7acc15175
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704008"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="9c399-103">Передача сообщений из приложения MSMQ в приложение Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9c399-103">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="9c399-104">В этом примере показано, как приложение очереди сообщений (MSMQ) может отправить сообщение MSMQ в службу Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9c399-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9c399-105">Служба представляет собой резидентное консольное приложение, позволяющее наблюдать за получением службой сообщений из очереди.</span><span class="sxs-lookup"><span data-stu-id="9c399-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="9c399-106">Контракт службы `IOrderProcessor` определяет одностороннюю службу, которую можно использовать с очередями.</span><span class="sxs-lookup"><span data-stu-id="9c399-106">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="9c399-107">Сообщение MSMQ не содержит заголовка Action, поэтому автоматически соотнести различные сообщения MSMQ с контрактами операций невозможно.</span><span class="sxs-lookup"><span data-stu-id="9c399-107">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="9c399-108">Поэтому может существовать только один контракт операции.</span><span class="sxs-lookup"><span data-stu-id="9c399-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="9c399-109">Если нужно определить для службы несколько контрактов операций, приложение должно сообщать, какой заголовок сообщения MSMQ (например, метку или correlationID) можно использовать для выбора контракта операции.</span><span class="sxs-lookup"><span data-stu-id="9c399-109">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="9c399-110">Сообщение MSMQ не содержит сведений о том, какие заголовки соответствуют различным параметрам контракта операции.</span><span class="sxs-lookup"><span data-stu-id="9c399-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="9c399-111">Параметр имеет тип <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), содержащий сообщение MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9c399-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="9c399-112">Тип "T" в классе <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) представляет данные, сериализованные в основную часть сообщения MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9c399-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="9c399-113">В этом образце тип `PurchaseOrder` сериализован в основную часть сообщения MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9c399-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="9c399-114">В следующем образце кода показан контракт службы, обрабатывающей заказы.</span><span class="sxs-lookup"><span data-stu-id="9c399-114">The following sample code shows the service contract of the order processing service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="9c399-115">Служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="9c399-115">The service is self hosted.</span></span> <span data-ttu-id="9c399-116">При работе с MSMQ используемую очередь следует создавать заранее.</span><span class="sxs-lookup"><span data-stu-id="9c399-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="9c399-117">Это можно сделать вручную или с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="9c399-117">This can be done manually or through code.</span></span> <span data-ttu-id="9c399-118">В данном образце служба проверяет наличие очереди и создает ее, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="9c399-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="9c399-119">Имя очереди считывается из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9c399-119">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="9c399-120">Служба создает и открывает <xref:System.ServiceModel.ServiceHost> для службы `OrderProcessorService`, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="9c399-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="9c399-121">Имя очереди MSMQ задается в разделе appSettings файла конфигурации, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9c399-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="9c399-122">В имени очереди для определения локального компьютера используется точка (.), а в пути в качестве разделителей используются символы обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="9c399-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="9c399-123">Адрес конечной точки WCF указывает схему MSMQ. formatname и использует localhost для локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="9c399-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="9c399-124">Адрес очереди для каждого имени формата MSMQ по рекомендациям о создании адресов следует схеме msmq.formatname.</span><span class="sxs-lookup"><span data-stu-id="9c399-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="9c399-125">Клиентское приложение — это приложение MSMQ, использующее метод <xref:System.Messaging.MessageQueue.Send%2A> для отправки в очередь устойчивого и транзакционного сообщения, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="9c399-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="9c399-126">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="9c399-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9c399-127">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="9c399-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9c399-128">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="9c399-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="9c399-129">Обратите внимание, что поскольку используется очередь, клиенту и службе не обязательно быть запущенными и работать одновременно.</span><span class="sxs-lookup"><span data-stu-id="9c399-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="9c399-130">Например, можно запустить клиент, выключить его, а затем запустить службу и все равно получить сообщения клиента.</span><span class="sxs-lookup"><span data-stu-id="9c399-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="9c399-131">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="9c399-131">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="9c399-132">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c399-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9c399-133">При первом запуске служба проверит наличие очереди.</span><span class="sxs-lookup"><span data-stu-id="9c399-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="9c399-134">Если очередь отсутствует, служба ее создаст.</span><span class="sxs-lookup"><span data-stu-id="9c399-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="9c399-135">Можно сначала запустить службу, чтобы создать очередь, либо создать ее с помощью диспетчера очередей MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9c399-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="9c399-136">Чтобы создать очередь в Windows 2008, выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="9c399-136">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="9c399-137">Откройте диспетчер сервера в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="9c399-137">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="9c399-138">Разверните вкладку **функции** .</span><span class="sxs-lookup"><span data-stu-id="9c399-138">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="9c399-139">Щелкните правой кнопкой мыши **частные очереди сообщений** и выберите **создать**, **Частная очередь**.</span><span class="sxs-lookup"><span data-stu-id="9c399-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="9c399-140">Установите флажок **транзакционная** .</span><span class="sxs-lookup"><span data-stu-id="9c399-140">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="9c399-141">Введите в `ServiceModelSamplesTransacted` качестве имени новой очереди.</span><span class="sxs-lookup"><span data-stu-id="9c399-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="9c399-142">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c399-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="9c399-143">Чтобы запустить пример в конфигурации с одним компьютером, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c399-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="9c399-144">Запуск примера на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="9c399-144">Run the sample across computers</span></span>

1. <span data-ttu-id="9c399-145">Скопируйте на компьютер службы файлы служебной программы из папки \service\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="9c399-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="9c399-146">Скопируйте на клиентские компьютеры файлы из папки \client\bin\ в папку языка.</span><span class="sxs-lookup"><span data-stu-id="9c399-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="9c399-147">В файле Client.exe.config измените orderQueueName, указав имя компьютера службы вместо «.».</span><span class="sxs-lookup"><span data-stu-id="9c399-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="9c399-148">На компьютере службы запустите из командной строки программу Service.exe.</span><span class="sxs-lookup"><span data-stu-id="9c399-148">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="9c399-149">На клиентском компьютере из командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="9c399-149">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c399-150">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="9c399-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9c399-151">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="9c399-151">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9c399-152">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="9c399-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c399-153">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="9c399-153">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="9c399-154">См. также</span><span class="sxs-lookup"><span data-stu-id="9c399-154">See also</span></span>

- [<span data-ttu-id="9c399-155">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="9c399-155">Queues in WCF</span></span>](../feature-details/queues-in-wcf.md)
- [<span data-ttu-id="9c399-156">Практическое руководство. Обмен сообщениями с конечными точками WCF и приложениями очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="9c399-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="9c399-157">[служба очередей сообщений](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9c399-157">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
