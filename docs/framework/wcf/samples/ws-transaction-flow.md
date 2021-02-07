---
description: Дополнительные сведения о потоке транзакций WS
title: Поток транзакций WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 4d0a0af77dd516bf98c5dc8318ac110a31e731e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668374"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="699e3-103">Поток транзакций WS</span><span class="sxs-lookup"><span data-stu-id="699e3-103">WS Transaction Flow</span></span>

<span data-ttu-id="699e3-104">В этом образце показано использование координируемой клиентом транзакции и параметры клиента и сервера для организации потока транзакции с использованием протокола WS-Atomic Transaction или OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="699e3-104">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="699e3-105">Этот пример основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора, но операции являются атрибутами, чтобы продемонстрировать использование `TransactionFlowAttribute` с перечислением **TransactionFlowOption** , чтобы определить степень включения потока транзакций.</span><span class="sxs-lookup"><span data-stu-id="699e3-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="699e3-106">В области поточной транзакции в базу данных записывается журнал запрошенных операций, который сохраняется до завершения транзакции, координируемой клиентом, и если транзакция клиента не завершена, транзакция веб-службы следит, чтобы соответствующие обновления базы данных не были зафиксированы.</span><span class="sxs-lookup"><span data-stu-id="699e3-106">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="699e3-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="699e3-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="699e3-108">После установления связи со службой и транзакцией клиент обращается к нескольким операциям службы.</span><span class="sxs-lookup"><span data-stu-id="699e3-108">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="699e3-109">Контракт службы определяется показанным ниже образом, при этом все операции показывают различные параметры `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="699e3-109">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);
}  
```

 <span data-ttu-id="699e3-110">Определяет операции в порядке их выполнения:</span><span class="sxs-lookup"><span data-stu-id="699e3-110">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="699e3-111">запрос операции `Add` должен включать поточную транзакцию;</span><span class="sxs-lookup"><span data-stu-id="699e3-111">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="699e3-112">запрос операции `Subtract` может включать поточную транзакцию;</span><span class="sxs-lookup"><span data-stu-id="699e3-112">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="699e3-113">запрос операции `Multiply` не может содержать поточную транзакцию из-за явно установленного параметра NotAllowed;</span><span class="sxs-lookup"><span data-stu-id="699e3-113">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="699e3-114">запрос операции `Divide` не может содержать поточную транзакцию из-за отсутствия атрибута `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="699e3-114">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="699e3-115">Чтобы включить поток транзакций, необходимо использовать привязки с [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) включенным свойством в дополнение к соответствующим атрибутам операции.</span><span class="sxs-lookup"><span data-stu-id="699e3-115">To enable transaction flow, bindings with the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="699e3-116">В этом образце конфигурация службы предоставляет в дополнение к конечной точке обмена метаданными конечные точки TCP и HTTP.</span><span class="sxs-lookup"><span data-stu-id="699e3-116">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="699e3-117">Конечная точка TCP и конечная точка HTTP используют следующие привязки, для которых [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) включено свойство.</span><span class="sxs-lookup"><span data-stu-id="699e3-117">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
> <span data-ttu-id="699e3-118">Предоставляемая системой привязка netTcpBinding позволяет задавать протокол transactionProtocol, а предоставляемая системой привязка wsHttpBinding использует только протокол WSAtomicTransactionOctober2004 с большими возможностями взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="699e3-118">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="699e3-119">Протокол OleTransactions доступен только для клиентов Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="699e3-119">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="699e3-120">Для класса, реализующего интерфейс `ICalculator`, всем методам в качестве атрибута задано свойство <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>, имеющее значение `true`.</span><span class="sxs-lookup"><span data-stu-id="699e3-120">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="699e3-121">Этот параметр означает, что все действия, предпринятые в рамках метода, происходят в области транзакции.</span><span class="sxs-lookup"><span data-stu-id="699e3-121">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="699e3-122">В этом случае предпринятые действия включают запись в журнал базы данных.</span><span class="sxs-lookup"><span data-stu-id="699e3-122">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="699e3-123">Если запрос операции включает поточную транзакцию, действия происходят в области входящей транзакции или автоматически создается новая область транзакции.</span><span class="sxs-lookup"><span data-stu-id="699e3-123">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="699e3-124">Свойство <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> определяет локальное поведение реализаций методов службы и не определяет возможность или требования клиента передавать транзакцию.</span><span class="sxs-lookup"><span data-stu-id="699e3-124">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="699e3-125">На стороне клиента параметры операций `TransactionFlowOption` службы отражаются в создаваемом определении интерфейса `ICalculator` клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-125">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="699e3-126">Параметры свойства `transactionFlow` службы также отражаются в конфигурации приложения клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-126">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="699e3-127">Клиент может выбрать транспорт и протокол, выбрав соответствующее имя `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="699e3-127">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="699e3-128">Поведение этого образца не зависит от выбранного протокола или транспорта.</span><span class="sxs-lookup"><span data-stu-id="699e3-128">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="699e3-129">После установления связи со службой клиент создает новую область `TransactionScope`, в которую заключены вызовы операций службы.</span><span class="sxs-lookup"><span data-stu-id="699e3-129">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="699e3-130">Используются следующие вызовы операций.</span><span class="sxs-lookup"><span data-stu-id="699e3-130">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="699e3-131">Запрос `Add` передает нужную транзакцию службе, а действия службы происходят в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-131">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="699e3-132">Первый запрос `Subtract` также передает разрешенную транзакцию службе, действия службы снова происходят в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-132">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="699e3-133">Второй запрос `Subtract` выполняется в новой области транзакции, объявленной с помощью параметра `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="699e3-133">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="699e3-134">Он подавляет первоначальную внешнюю транзакцию клиента, и запрос не передает транзакцию службе.</span><span class="sxs-lookup"><span data-stu-id="699e3-134">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="699e3-135">Этот подход позволяет клиенту явно отказаться и защититься от передачи транзакции службе, если в этом нет необходимости.</span><span class="sxs-lookup"><span data-stu-id="699e3-135">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="699e3-136">Действия службы происходят в области новой, несвязанной транзакции.</span><span class="sxs-lookup"><span data-stu-id="699e3-136">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="699e3-137">Запрос `Multiply` не передает транзакцию службе, так как созданное клиентом определение интерфейса `ICalculator` включает объект <xref:System.ServiceModel.TransactionFlowAttribute>, которому присвоено значение <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="699e3-137">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="699e3-138">Запрос `Divide` не передает транзакцию службе, так как, опять же, созданное клиентом определение интерфейса `ICalculator` не включает `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="699e3-138">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="699e3-139">Действия службы снова происходят в области новой, несвязанной транзакции.</span><span class="sxs-lookup"><span data-stu-id="699e3-139">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="699e3-140">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-140">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="699e3-141">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-141">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="699e3-142">Журнал запросов операций службы отображается в окне консоли службы.</span><span class="sxs-lookup"><span data-stu-id="699e3-142">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="699e3-143">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-143">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="699e3-144">После успешного выполнения область транзакции клиента завершается, а все действия, предпринятые в этой области, фиксируются.</span><span class="sxs-lookup"><span data-stu-id="699e3-144">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="699e3-145">В частности, в базе данных службы сохраняются 5 указанных записей.</span><span class="sxs-lookup"><span data-stu-id="699e3-145">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="699e3-146">Первые две произошли в области транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-146">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="699e3-147">Если в любом месте области `TransactionScope` клиента возникло исключение, транзакция не может завершиться.</span><span class="sxs-lookup"><span data-stu-id="699e3-147">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="699e3-148">Из-за этого записи, помещенные в журнал в этой области, не фиксируются в базе данных.</span><span class="sxs-lookup"><span data-stu-id="699e3-148">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="699e3-149">Чтобы посмотреть на эту ситуацию, повторите выполнение образца, преобразовав в комментарий вызов для завершения внешней области `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="699e3-149">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="699e3-150">При таком выполнении записываются только 3 последних действия (из второго запроса `Subtract` и запросов `Multiply` и `Divide`), потому что к ним не передавалась транзакция клиента.</span><span class="sxs-lookup"><span data-stu-id="699e3-150">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="699e3-151">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="699e3-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="699e3-152">Чтобы создать версию решения на C# или Visual Basic .NET, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md) .</span><span class="sxs-lookup"><span data-stu-id="699e3-152">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="699e3-153">Убедитесь, что установлен SQL Server Express Edition, SQL Server, а в файле конфигурации приложения службы правильно задана строка подключения.</span><span class="sxs-lookup"><span data-stu-id="699e3-153">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="699e3-154">Чтобы выполнить образец без использования базы данных, установите значение `usingSql` в файле конфигурации приложения службы равным `false`</span><span class="sxs-lookup"><span data-stu-id="699e3-154">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="699e3-155">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="699e3-155">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="699e3-156">Если планируется выполнять образец на нескольких компьютерах, включите координатор распределенных транзакций согласно приведенным ниже инструкциям и воспользуйтесь средством WsatConfig.exe из пакета Windows SDK для поддержки сетевых транзакций WCF.</span><span class="sxs-lookup"><span data-stu-id="699e3-156">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="699e3-157">Сведения о настройке WsatConfig.exe см. в разделе [Настройка поддержки транзакций WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="699e3-157">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="699e3-158">Независимо от того, запускается ли пример на том же компьютере или на разных компьютерах, необходимо настроить Microsoft координатор распределенных транзакций (MSDTC) для включения потока сетевых транзакций и использовать средство WsatConfig.exe для включения поддержки сети транзакций WCF.</span><span class="sxs-lookup"><span data-stu-id="699e3-158">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="699e3-159">Настройка координатора распределенных транзакций (Майкрософта) (MSDTC) на поддержку выполнения образца</span><span class="sxs-lookup"><span data-stu-id="699e3-159">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="699e3-160">На компьютере службы, работающем под управлением Windows Server 2003 или Windows XP настройте MSDTC, разрешите входящие сетевые транзакции, согласно следующим инструкциям.</span><span class="sxs-lookup"><span data-stu-id="699e3-160">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="699e3-161">В меню **Пуск** последовательно выберите пункты **Панель управления**, **Администрирование** и **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="699e3-161">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="699e3-162">Разверните узел **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="699e3-162">Expand **Component Services**.</span></span> <span data-ttu-id="699e3-163">Откройте папку " **Компьютеры** ".</span><span class="sxs-lookup"><span data-stu-id="699e3-163">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="699e3-164">Щелкните правой кнопкой мыши **Мой компьютер** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="699e3-164">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="699e3-165">На вкладке **MSDTC** щелкните **Конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="699e3-165">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="699e3-166">Проверьте **доступ DTC к сети** и **разрешите входящий трафик**.</span><span class="sxs-lookup"><span data-stu-id="699e3-166">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="699e3-167">Нажмите кнопку **ОК**, а затем нажмите кнопку **Да** , чтобы перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="699e3-167">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="699e3-168">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="699e3-168">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="699e3-169">На компьютере службы, работающем под управлением Windows Server 2008 или Windows Vista настройте MSDTC, разрешив входящие сетевые транзакции, согласно следующим инструкциям.</span><span class="sxs-lookup"><span data-stu-id="699e3-169">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="699e3-170">В меню **Пуск** последовательно выберите пункты **Панель управления**, **Администрирование** и **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="699e3-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="699e3-171">Разверните узел **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="699e3-171">Expand **Component Services**.</span></span> <span data-ttu-id="699e3-172">Откройте папку " **Компьютеры** ".</span><span class="sxs-lookup"><span data-stu-id="699e3-172">Open the **Computers** folder.</span></span> <span data-ttu-id="699e3-173">Выберите **координатор распределенных транзакций**.</span><span class="sxs-lookup"><span data-stu-id="699e3-173">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="699e3-174">Щелкните правой кнопкой мыши **координатор DTC** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="699e3-174">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="699e3-175">На вкладке **Безопасность** проверьте **доступ к сети DTC** и **разрешите входящие**.</span><span class="sxs-lookup"><span data-stu-id="699e3-175">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="699e3-176">Нажмите кнопку **ОК**, а затем нажмите кнопку **Да** , чтобы перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="699e3-176">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="699e3-177">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="699e3-177">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="699e3-178">На клиентском компьютере настройте координатор распределенных транзакций, чтобы он разрешал исходящие сетевые транзакции.</span><span class="sxs-lookup"><span data-stu-id="699e3-178">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="699e3-179">В меню **Пуск** выберите пункт `Control Panel` **Администрирование**, а затем — **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="699e3-179">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="699e3-180">Щелкните правой кнопкой мыши **Мой компьютер** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="699e3-180">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="699e3-181">На вкладке **MSDTC** щелкните **Конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="699e3-181">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="699e3-182">Проверьте **доступ к сети DTC** и **разрешите исходящие** подключения.</span><span class="sxs-lookup"><span data-stu-id="699e3-182">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="699e3-183">Нажмите кнопку **ОК**, а затем нажмите кнопку **Да** , чтобы перезапустить службу MSDTC.</span><span class="sxs-lookup"><span data-stu-id="699e3-183">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="699e3-184">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="699e3-184">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="699e3-185">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="699e3-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="699e3-186">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="699e3-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="699e3-187">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="699e3-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="699e3-188">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="699e3-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
