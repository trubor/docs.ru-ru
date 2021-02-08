---
description: 'Дополнительные сведения: поведение транзакций службы'
title: Транзакционное поведение службы
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 1f8b76de250ef87ec5ca2d4ea4353a9a28bac248
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793068"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="ba1ea-103">Транзакционное поведение службы</span><span class="sxs-lookup"><span data-stu-id="ba1ea-103">Service Transaction Behavior</span></span>

<span data-ttu-id="ba1ea-104">В этом образце показано использование координируемой клиентом транзакции и параметры ServiceBehaviorAttribute и OperationBehaviorAttribute, управляющие поведением транзакции службы.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-104">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="ba1ea-105">Этот пример основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора, но расширена для обслуживания журнала сервера выполненных операций в таблице базы данных и общей суммы с отслеживанием состояния для операций калькулятора.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="ba1ea-106">Операции записи в таблицу журнала сервера зависят от результата координируемой клиентом транзакции - если транзакция клиента не была завершена, транзакция веб-службы подтверждает, что обновления базы данных не будут зафиксированы.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-106">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="ba1ea-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ba1ea-108">Контракт этой службы определяет, что для всех операций требуется поток транзакций с запросами:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-108">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",
                    SessionMode = SessionMode.Required)]
public interface ICalculator
{
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Add(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Subtract(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Multiply(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Divide(double n);
}
```

<span data-ttu-id="ba1ea-109">Чтобы включить поток входящих транзакций, для службы настраивается системная привязка wsHttpBinding, атрибут transactionFlow которой имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-109">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="ba1ea-110">Эта привязка использует поддерживающий взаимодействие протокол WSAtomicTransactionOctober2004:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-110">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="ba1ea-111">После инициации подключения к службе и транзакции клиент обращается к нескольким операциям службы в пределах области транзакции, а затем завершает транзакцию и закрывает подключение:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-111">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
// Create a client
CalculatorClient client = new CalculatorClient();

// Create a transaction scope with the default isolation level of Serializable
using (TransactionScope tx = new TransactionScope())
{
    Console.WriteLine("Starting transaction");

    // Call the Add service operation.
    double value = 100.00D;
    Console.WriteLine("  Adding {0}, running total={1}",
                                        value, client.Add(value));

    // Call the Subtract service operation.
    value = 45.00D;
    Console.WriteLine("  Subtracting {0}, running total={1}",
                                        value, client.Subtract(value));

    // Call the Multiply service operation.
    value = 9.00D;
    Console.WriteLine("  Multiplying by {0}, running total={1}",
                                        value, client.Multiply(value));

    // Call the Divide service operation.
    value = 15.00D;
    Console.WriteLine("  Dividing by {0}, running total={1}",
                                        value, client.Divide(value));

    Console.WriteLine("  Completing transaction");
    tx.Complete();
}

Console.WriteLine("Transaction committed");

// Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

<span data-ttu-id="ba1ea-112">На стороне службы имеется три атрибута, которые влияют на поведение транзакции службы. Это происходит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-112">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="ba1ea-113">В атрибуте `ServiceBehaviorAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-113">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="ba1ea-114">Свойство `TransactionTimeout` задает период времени, в течение которого транзакция должна быть завершена.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-114">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="ba1ea-115">В этом образце это время составляет 30 секунд.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-115">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="ba1ea-116">Свойство `TransactionIsolationLevel` указывает уровень изоляции транзакций, поддерживаемый службой.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-116">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="ba1ea-117">Он должен совпадать с уровнем изоляции клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-117">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="ba1ea-118">Свойство `ReleaseServiceInstanceOnTransactionComplete` определяет, используется ли экземпляр службы повторно по завершении транзакции.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-118">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="ba1ea-119">При установке для него значения `false` служба использует один и тот же экземпляр службы для разных запросов операций.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-119">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="ba1ea-120">Это требуется для определения нарастающего итога.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-120">This is required to maintain the running total.</span></span> <span data-ttu-id="ba1ea-121">Если свойство имеет значение `true`, после каждого завершенного действия создается новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-121">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="ba1ea-122">Свойство `TransactionAutoCompleteOnSessionClose` определяет, завершаются ли ожидающие обработки транзакции при завершении сеанса.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-122">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="ba1ea-123">Если задать для него значение `false` , то отдельные операции должны либо задать <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> свойство равным, `true` либо явно требовать вызова <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> метода для завершения транзакций.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-123">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="ba1ea-124">В этом образце продемонстрированы оба подхода.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-124">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="ba1ea-125">В атрибуте `ServiceContractAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-125">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="ba1ea-126">Свойство `SessionMode` определяет, согласовывает ли служба соответствующие запросы в логический сеанс.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-126">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="ba1ea-127">Поскольку служба включает операции, для которых свойство OperationBehaviorAttribute TransactionAutoComplete имеет значение `false` (Multiply и Divide), необходимо задавать `SessionMode.Required`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-127">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="ba1ea-128">Например, операция Multiply не завершает свою транзакцию и вместо этого ожидает очередного вызова операции Divide, чтобы завершить транзакцию с помощью метода `SetTransactionComplete`; служба должна уметь определять, что операции выполняются в рамках одного сеанса.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-128">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="ba1ea-129">В атрибуте `OperationBehaviorAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-129">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="ba1ea-130">Свойство `TransactionScopeRequired` определяет, должны ли действия операции выполняться в области транзакции.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-130">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="ba1ea-131">Оно устанавливается равным `true` для всех операций в этом образце, и, поскольку клиент направляет свои транзакции всем операциям, действия выполняются в области соответствующей транзакции клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-131">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="ba1ea-132">Свойство `TransactionAutoComplete` указывает, следует ли автоматически завершать транзакцию, в которой выполняется метод, при отсутствии необработанных исключений.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-132">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="ba1ea-133">Как говорилось выше, это свойство устанавливается равным `true` для операций Add и Subtract и `false` для операций Multiply и Divide.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-133">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="ba1ea-134">Операции Add и Subtract завершают свои действия автоматически, операция Divide завершает свои действия через явный вызов метода `SetTransactionComplete`, а операция Multiply не завершает свои действия, а ожидает очередного вызова, например операции Divide, чтобы завершить свои действия.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-134">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="ba1ea-135">Реализация службы с атрибутами выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-135">The attributed service implementation is as follows:</span></span>

```csharp
[ServiceBehavior(
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,
    TransactionTimeout = "00:00:30",
    ReleaseServiceInstanceOnTransactionComplete = false,
    TransactionAutoCompleteOnSessionClose = false)]
public class CalculatorService : ICalculator
{
    double runningTotal;

    public CalculatorService()
    {
        Console.WriteLine("Creating new service instance...");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Add(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));
        runningTotal = runningTotal + n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Subtract(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));
        runningTotal = runningTotal - n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Multiply(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));
        runningTotal = runningTotal * n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Divide(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));
        runningTotal = runningTotal / n;
        OperationContext.Current.SetTransactionComplete();
        return runningTotal;
    }

    // Logging method omitted for brevity
}
```

<span data-ttu-id="ba1ea-136">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ba1ea-137">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-137">Press ENTER in the client window to shut down the client.</span></span>

```console
Starting transaction
Performing calculations...
  Adding 100, running total=100
  Subtracting 45, running total=55
  Multiplying by 9, running total=495
  Dividing by 15, running total=33
  Completing transaction
Transaction committed
Press <ENTER> to terminate client.
```

<span data-ttu-id="ba1ea-138">Журнал запросов операций службы отображается в окне консоли службы.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-138">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="ba1ea-139">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-139">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="ba1ea-140">Обратите внимание, что помимо сохранения нарастающего итога всех вычислений, служба также сообщает о создании экземпляров (в данном образце один экземпляр) и записывает запросы операций в базу данных.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-140">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="ba1ea-141">Поскольку все запросы выполняются в транзакции клиента, в случае невозможности завершить транзакцию происходит откат всех операций базы данных.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-141">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="ba1ea-142">Это можно показать несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-142">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="ba1ea-143">Скройте комментарием клиентский вызов метода `tx.Complete`() и выполните пример заново - клиент выйдет из области транзакции без завершения транзакции.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-143">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="ba1ea-144">Скройте комментарием вызов операции Divide службы - действие, вызванное операцией Multiply, не будет завершено, в результате чего не удастся завершить и транзакцию клиента.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-144">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="ba1ea-145">Создайте необработанное исключение в любом месте области транзакции клиента - в этом случае клиенту также не удастся завершить транзакцию.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-145">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="ba1ea-146">В результате реализации любого из этих сценариев ни одна из выполняемых в пределах области операций не будет зафиксирована, и чисто сохраняемых в базе данных строк не увеличится.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-146">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="ba1ea-147">В процессе построения файл базы данных копируется в папку bin.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-147">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="ba1ea-148">Чтобы следить за тем, какие строки сохраняются в журнале, необходимо проверять эту копию файла базы данных, а не файл, входящий в проект Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-148">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba1ea-149">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="ba1ea-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ba1ea-150">Убедитесь, что установлен SQL Server 2005 Express Edition или SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-150">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="ba1ea-151">В файле службы App.config может быть задано значение `connectionString` базы данных либо взаимодействие с базой данных может быть отключено (значение appSettings `usingSql` равно `false`).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-151">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="ba1ea-152">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="ba1ea-153">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="ba1ea-154">При запуске примера на нескольких компьютерах необходимо настроить Microsoft координатор распределенных транзакций (MSDTC) для включения потока сетевых транзакций и использовать средство WsatConfig.exe для включения поддержки сети транзакций Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-154">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="ba1ea-155">Настройка координатора распределенных транзакций (Майкрософт) на поддержку выполнения образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="ba1ea-155">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="ba1ea-156">На компьютере службы настройте координатор MSDTC на разрешение входящих сетевых транзакций.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-156">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="ba1ea-157">В меню **Пуск** последовательно выберите пункты **Панель управления**, **Администрирование** и **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-157">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="ba1ea-158">Щелкните правой кнопкой мыши **Мой компьютер** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-158">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="ba1ea-159">На вкладке **MSDTC** щелкните **Конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-159">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="ba1ea-160">Проверьте **доступ DTC к сети** и **разрешите входящий трафик**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-160">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="ba1ea-161">Нажмите кнопку **Да** , чтобы перезапустить службу MS DTC, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-161">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="ba1ea-162">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-162">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="ba1ea-163">На компьютере службы и на клиентском компьютере настройте брандмауэр Windows, чтобы включить координатор распределенных транзакций (Майкрософт) в список исключений.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-163">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="ba1ea-164">С панели управления запустите брандмауэр Windows.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-164">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="ba1ea-165">На вкладке **исключения** нажмите кнопку **Добавить программу**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-165">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="ba1ea-166">Перейдите в папку C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-166">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="ba1ea-167">Выберите Msdtc.exe и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-167">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="ba1ea-168">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Добавление программы** , и еще раз нажмите кнопку **ОК** , чтобы закрыть приложение брандмауэра Windows.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-168">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="ba1ea-169">На клиентском компьютере настройте координатор распределенных транзакций, чтобы он разрешал исходящие сетевые транзакции.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-169">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="ba1ea-170">В меню **Пуск** последовательно выберите пункты **Панель управления**, **Администрирование** и **службы компонентов**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="ba1ea-171">Щелкните правой кнопкой мыши **Мой компьютер** и выберите пункт **свойства**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-171">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="ba1ea-172">На вкладке **MSDTC** щелкните **Конфигурация безопасности**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-172">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="ba1ea-173">Проверьте **доступ к сети DTC** и **разрешите исходящие** подключения.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-173">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="ba1ea-174">Нажмите кнопку **Да** , чтобы перезапустить службу MS DTC, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-174">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="ba1ea-175">Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-175">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba1ea-176">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba1ea-177">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-177">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ba1ea-178">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba1ea-179">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-179">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
