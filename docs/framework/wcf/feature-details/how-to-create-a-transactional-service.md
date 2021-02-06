---
description: Дополнительные сведения о том, как создать транзакционную службу.
title: Практическое руководство. Создание транзакционной службы
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 78ad922a7e1f174715be7bd1a8466572425411be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643440"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="655ae-103">Практическое руководство. Создание транзакционной службы</span><span class="sxs-lookup"><span data-stu-id="655ae-103">How to: Create a Transactional Service</span></span>

<span data-ttu-id="655ae-104">В этом примере показаны различные аспекты создания транзакционной службы и использования инициируемых клиентом транзакций для координации операций службы.</span><span class="sxs-lookup"><span data-stu-id="655ae-104">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="655ae-105">Создание транзакционной службы</span><span class="sxs-lookup"><span data-stu-id="655ae-105">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="655ae-106">Создайте контракт службы и аннотируйте операции с выбранным параметром из перечисления <xref:System.ServiceModel.TransactionFlowOption>, чтобы задать требования входящих транзакций.</span><span class="sxs-lookup"><span data-stu-id="655ae-106">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="655ae-107">Обратите внимание, что в реализуемый класс службы также можно включить атрибут <xref:System.ServiceModel.TransactionFlowAttribute>.</span><span class="sxs-lookup"><span data-stu-id="655ae-107">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="655ae-108">Это позволит одной реализации интерфейса, а не всем реализациям, использовать эти параметры транзакции.</span><span class="sxs-lookup"><span data-stu-id="655ae-108">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. <span data-ttu-id="655ae-109">Создайте класс реализации и воспользуйтесь атрибутом <xref:System.ServiceModel.ServiceBehaviorAttribute>, чтобы задать значения свойств <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> и <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> (необязательно).</span><span class="sxs-lookup"><span data-stu-id="655ae-109">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="655ae-110">Обратите внимание, что во многих случаях можно использовать значения по умолчанию для свойств <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> (60 секунд) и <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> (`Unspecified`).</span><span class="sxs-lookup"><span data-stu-id="655ae-110">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="655ae-111">Для каждой операции можно с помощью атрибута <xref:System.ServiceModel.OperationBehaviorAttribute> определить, должны ли операции, расположенные внутри метода, выполняться в области действия транзакции в соответствии со значением атрибута <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>.</span><span class="sxs-lookup"><span data-stu-id="655ae-111">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="655ae-112">В этом случае транзакция, используемая для метода `Add`, будет совпадать с обязательной входящей транзакцией, которая поступает от клиента, а транзакция, используемая для метода `Subtract`, либо совпадает со входящей транзакцией, если она поступила от клиента, либо является новой созданной явно локальной транзакцией.</span><span class="sxs-lookup"><span data-stu-id="655ae-112">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. <span data-ttu-id="655ae-113">Настройте привязки в файле конфигурации, указав, что контекст транзакций должен передаваться, и необходимые для этого протоколы.</span><span class="sxs-lookup"><span data-stu-id="655ae-113">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="655ae-114">Дополнительные сведения см. в статье о [конфигурации транзакций ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="655ae-114">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="655ae-115">В частности тип привязки задается в атрибуте `binding` элемента конечной точки.</span><span class="sxs-lookup"><span data-stu-id="655ae-115">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="655ae-116">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md)Элемент содержит `bindingConfiguration` атрибут, который ссылается на конфигурацию привязки с именем `transactionalOleTransactionsTcpBinding` , как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="655ae-116">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="655ae-117">Поток транзакций настраивается на уровне конфигурации с помощью атрибута `transactionFlow`, а протокол транзакций задается с помощью атрибута `transactionProtocol`, как показано в следующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="655ae-117">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="655ae-118">Поддержка нескольких протоколов транзакций</span><span class="sxs-lookup"><span data-stu-id="655ae-118">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="655ae-119">Для оптимальной производительности следует использовать протокол OleTransactions для сценариев, включающих клиент и службу, написанную с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="655ae-119">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="655ae-120">Однако в сценариях, требующих взаимодействия со сторонним стеком протоколов, удобно использовать протокол WS-AtomicTransaction (WS-AT).</span><span class="sxs-lookup"><span data-stu-id="655ae-120">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="655ae-121">Службы WCF можно настроить для приема обоих протоколов, предоставив несколько конечных точек с соответствующими привязками для конкретного протокола, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="655ae-121">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="655ae-122">Протокол транзакций задается с помощью атрибута `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="655ae-122">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="655ae-123">Однако в предоставляемой системой привязке `wsHttpBinding` этого атрибута нет, поскольку эта привязка может использовать только протокол WS-AT.</span><span class="sxs-lookup"><span data-stu-id="655ae-123">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="655ae-124">Управление завершением транзакций</span><span class="sxs-lookup"><span data-stu-id="655ae-124">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="655ae-125">По умолчанию операции WCF автоматически завершают транзакции, если необработанные исключения не возникают.</span><span class="sxs-lookup"><span data-stu-id="655ae-125">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="655ae-126">Такое поведение можно изменить с помощью свойства <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> и метода <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="655ae-126">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="655ae-127">Если операция должна произойти в той же транзакции, что и другая операция (например, операции дебета и кредита), можно отключить автоматическое завершение, задав для свойства <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> значение `false`, как показано в приведенном ниже примере операции `Debit`.</span><span class="sxs-lookup"><span data-stu-id="655ae-127">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="655ae-128">Транзакция, используемая операцией `Debit`, остается незавершенной, пока не будет вызван метод, у которого свойство <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> имеет значение `true`, как показано в операции `Credit1`, или пока не будет вызван метод <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>, явным образом показывающий, что транзакция завершена, как показано в операции `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="655ae-128">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="655ae-129">Обратите внимание, что две операции кредита показаны в этом примере для иллюстрации, и в реальной ситуации обычно используется одна операция кредита.</span><span class="sxs-lookup"><span data-stu-id="655ae-129">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. <span data-ttu-id="655ae-130">Если для согласования транзакций свойству <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> присваивается значение `false`, необходимо использовать привязку с отслеживанием состояния.</span><span class="sxs-lookup"><span data-stu-id="655ae-130">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="655ae-131">Это требование задается с помощью свойства `SessionMode` класса <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="655ae-131">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="655ae-132">Управление временем существования экземпляра транзакционной службы</span><span class="sxs-lookup"><span data-stu-id="655ae-132">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="655ae-133">WCF использует <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> свойство, чтобы указать, освобожден ли базовый экземпляр службы после завершения транзакции.</span><span class="sxs-lookup"><span data-stu-id="655ae-133">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="655ae-134">Так как по умолчанию используется значение `true` , то WCF не является эффективным и предсказуемым поведением JIT-активации, если иное не настроено.</span><span class="sxs-lookup"><span data-stu-id="655ae-134">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="655ae-135">При вызове службы в последующей транзакции используется новый экземпляр службы, который не содержит признаков состояний предыдущих транзакций.</span><span class="sxs-lookup"><span data-stu-id="655ae-135">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="655ae-136">Хотя такой подход зачастую бывает удобным, иногда может возникнуть необходимость сохранения состояния службы после завершения транзакции.</span><span class="sxs-lookup"><span data-stu-id="655ae-136">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="655ae-137">Например, такая ситуация возникает, если извлечение или восстановление требуемого состояния или дескриптора требует большого объема ресурсов.</span><span class="sxs-lookup"><span data-stu-id="655ae-137">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="655ae-138">В этом случае можно задать для свойства <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="655ae-138">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="655ae-139">Если этот параметр задан, экземпляр и связанное состояние будут доступны в последующих вызовах.</span><span class="sxs-lookup"><span data-stu-id="655ae-139">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="655ae-140">При использовании этого сценария необходимо внимательно следить за тем, как и когда происходят очистка и завершение состояний и транзакций.</span><span class="sxs-lookup"><span data-stu-id="655ae-140">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="655ae-141">В следующем примере показано, как реализовать это, поддерживая экземпляр с помощью переменной `runningTotal`.</span><span class="sxs-lookup"><span data-stu-id="655ae-141">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="655ae-142">Поскольку время существования экземпляра определяется внутри службы и управляется через свойство <xref:System.ServiceModel.ServiceBehaviorAttribute>, чтобы задать поведение экземпляра, изменять конфигурацию службы или контракт службы не требуется.</span><span class="sxs-lookup"><span data-stu-id="655ae-142">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="655ae-143">Кроме того, это не отразится на сети.</span><span class="sxs-lookup"><span data-stu-id="655ae-143">In addition, the wire will contain no representation of this.</span></span>
