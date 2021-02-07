---
description: 'Дополнительные сведения: транспорт: Пример пользовательских транзакций по протоколу UDP'
title: 'Транспорт: пример пользовательских транзакций по протоколу UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 609576c74a8a3c0cd55829335545818028d444bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668517"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="83547-103">Транспорт: пример пользовательских транзакций по протоколу UDP</span><span class="sxs-lookup"><span data-stu-id="83547-103">Transport: Custom Transactions over UDP Sample</span></span>

<span data-ttu-id="83547-104">Этот пример основан на образце [Transport: UDP](transport-udp.md) в средстве[расширения транспорта](transport-extensibility.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="83547-104">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="83547-105">Он расширяет пример транспорта UDP за счет поддержки пользовательского потока транзакций и иллюстрирует использование свойства <xref:System.ServiceModel.Channels.TransactionMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="83547-105">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="83547-106">Изменения кода в примере транспорта UDP</span><span class="sxs-lookup"><span data-stu-id="83547-106">Code Changes in the UDP Transport Sample</span></span>  

 <span data-ttu-id="83547-107">Чтобы продемонстрировать поток транзакций, в этом примере изменен контракт службы для `ICalculatorContract`. Здесь этот контракт требует область транзакции для `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="83547-107">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="83547-108">Кроме того, в контракт операции `System.Guid` добавлен параметр `Add`.</span><span class="sxs-lookup"><span data-stu-id="83547-108">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="83547-109">Этот параметр используется для передачи службе идентификатора транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="83547-109">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="83547-110">В примере [Transport: UDP](transport-udp.md) для передачи сообщений между клиентом и службой используются пакеты UDP.</span><span class="sxs-lookup"><span data-stu-id="83547-110">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="83547-111">В [примере "Транспорт: пользовательский транспорт](transport-custom-transactions-over-udp-sample.md) " используется тот же механизм передачи сообщений, но при передаче транзакции он вставляется в пакет UDP вместе с закодированным сообщением.</span><span class="sxs-lookup"><span data-stu-id="83547-111">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="83547-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer` - вспомогательный метод, содержащий новые функции для слияния маркера распространения для текущей транзакции с сущностью сообщения и его помещения в буфер.</span><span class="sxs-lookup"><span data-stu-id="83547-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="83547-113">Для настраиваемого транспорта потока транзакций клиентская реализация должна узнать, какие операции службы нуждаются в потоке транзакций и передать эти сведения в WCF.</span><span class="sxs-lookup"><span data-stu-id="83547-113">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="83547-114">Должен быть и механизм для передачи транзакции пользователя на транспортный уровень.</span><span class="sxs-lookup"><span data-stu-id="83547-114">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="83547-115">В этом примере для получения этих сведений используется "инспекторы сообщений WCF".</span><span class="sxs-lookup"><span data-stu-id="83547-115">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="83547-116">Инспектор сообщений клиента, реализованный здесь, называется `TransactionFlowInspector` и выполняет следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="83547-116">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="83547-117">Определяет, следует ли создать поток транзакции для данного действия сообщения (это происходит в `IsTxFlowRequiredForThisOperation()`);</span><span class="sxs-lookup"><span data-stu-id="83547-117">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="83547-118">Присоединяет к сообщению текущую внешнюю транзакцию с помощью `TransactionFlowProperty`, если транзакцию нужно заключить в поток (это делается в `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="83547-118">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="83547-119">Сам `TransactionFlowInspector` передается инфраструктуре с помощью пользовательского поведения `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="83547-119">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="83547-120">При наличии вышеуказанного механизма пользовательский код создает область `TransactionScope` перед вызовом операции службы.</span><span class="sxs-lookup"><span data-stu-id="83547-120">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="83547-121">Инспектор сообщений следит, чтобы транзакция была передана транспорту, если она должна быть заключена в поток для операции службы.</span><span class="sxs-lookup"><span data-stu-id="83547-121">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="83547-122">После получения от клиента пакета UPD служба десериализует его, чтобы извлечь сообщение и, возможно, транзакцию.</span><span class="sxs-lookup"><span data-stu-id="83547-122">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="83547-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` - это вспомогательный метод, обращающий процесс сериализации, выполняемый `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="83547-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="83547-124">Если транзакция получена в потоке, она присоединяется к сообщению в свойстве `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="83547-124">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="83547-125">Это обеспечивает принятие диспетчером транзакции в момент распределения и использование ее при вызове операции службы, которой адресовано сообщение.</span><span class="sxs-lookup"><span data-stu-id="83547-125">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83547-126">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="83547-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="83547-127">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83547-127">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="83547-128">Текущий пример должен выполняться аналогично примеру [Transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="83547-128">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="83547-129">Для его запуска запустите службу с UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="83547-129">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="83547-130">Если вы используете Windows Vista, необходимо запустить службу с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="83547-130">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="83547-131">Для этого щелкните правой кнопкой мыши UdpTestService.exe в проводнике и выберите команду **Запуск от имени администратора**.</span><span class="sxs-lookup"><span data-stu-id="83547-131">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="83547-132">Получатся следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="83547-132">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="83547-133">В этот момент можно запустить клиент, выполнив UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="83547-133">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="83547-134">Результаты работы клиента таковы.</span><span class="sxs-lookup"><span data-stu-id="83547-134">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="83547-135">Вывод службы имеют следующий вид.</span><span class="sxs-lookup"><span data-stu-id="83547-135">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="83547-136">Приложение службы отображает сообщение `The client transaction has flowed to the service`, если может сопоставить идентификатор, присланный клиентом в параметре `clientTransactionId` операции `CalculatorService.Add()`, идентификатору транзакции службы.</span><span class="sxs-lookup"><span data-stu-id="83547-136">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="83547-137">Сопоставление происходит, только если транзакция клиента доставлена службе в виде потока.</span><span class="sxs-lookup"><span data-stu-id="83547-137">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="83547-138">Для выполнения клиентского приложения относительно конечных точек, опубликованных с помощью конфигурации, нажмите в окне приложения службы клавишу ВВОД и снова запустите тестовый клиент.</span><span class="sxs-lookup"><span data-stu-id="83547-138">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="83547-139">Служба должна предоставить следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="83547-139">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="83547-140">Выполнение клиента относительно службы теперь дает такие же результаты, как раньше.</span><span class="sxs-lookup"><span data-stu-id="83547-140">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="83547-141">Для восстановления кода клиента и конфигурации с помощью Svcutil.exe запустите приложение службы и выполните следующую команду Svcutil.exe из корневого каталога образца.</span><span class="sxs-lookup"><span data-stu-id="83547-141">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="83547-142">Обратите внимание, что Svcutil.exe не создает конфигурацию расширения привязки для `sampleProfileUdpBinding`, поэтому ее нужно добавить вручную.</span><span class="sxs-lookup"><span data-stu-id="83547-142">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="83547-143">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="83547-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83547-144">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="83547-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="83547-145">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="83547-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83547-146">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="83547-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="83547-147">См. также</span><span class="sxs-lookup"><span data-stu-id="83547-147">See also</span></span>

- [<span data-ttu-id="83547-148">Транспорт: UDP</span><span class="sxs-lookup"><span data-stu-id="83547-148">Transport: UDP</span></span>](transport-udp.md)
