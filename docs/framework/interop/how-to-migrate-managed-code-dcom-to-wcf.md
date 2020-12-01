---
title: Практическое руководство. Миграция DCOM с управляемым кодом в WCF
description: Перенос вызовов управляемого кода модели DCOM, которые выполнялись между серверами и клиентами, в Windows Communication Foundation (WCF).
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: eb84b8071d8dec5d3e70a2f1903f84ee64c31b08
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274846"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="7ed3a-103">Практическое руководство. Миграция DCOM с управляемым кодом в WCF</span><span class="sxs-lookup"><span data-stu-id="7ed3a-103">How to: Migrate Managed-Code DCOM to WCF</span></span>

<span data-ttu-id="7ed3a-104">Для вызовов управляемого кода между серверами и клиентами в распределенной среде рекомендуется использовать технологию Windows Communication Foundation (WCF), а не модель DCOM, из соображений безопасности.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-104">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="7ed3a-105">В этом разделе описывается, как перенести код из DCOM в WCF в перечисленных ниже ситуациях.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-105">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="7ed3a-106">Удаленная служба возвращает клиенту объект по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-106">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="7ed3a-107">Клиент отправляет удаленной службе объект по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-107">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="7ed3a-108">Удаленная служба возвращает клиенту объект по ссылке.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-108">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="7ed3a-109">По соображениям безопасности отправка объекта по ссылке от клиента службе в WCF запрещена.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-109">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="7ed3a-110">Сценарий, при котором клиенту и серверу необходимо обмениваться сообщениями друг с другом, можно реализовать в WCF с помощью дуплексной службы.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-110">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="7ed3a-111">Дополнительные сведения о дуплексных службах см. в разделе [Дуплексные службы](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-111">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="7ed3a-112">Дополнительные сведения о создании служб WCF и клиентов для них см. в разделах [Базовое программирование для WCF](../wcf/basic-wcf-programming.md), [Проектирование и реализация служб](../wcf/designing-and-implementing-services.md), а также [Создание клиентов](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-112">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="7ed3a-113">Пример кода DCOM</span><span class="sxs-lookup"><span data-stu-id="7ed3a-113">DCOM example code</span></span>  

 <span data-ttu-id="7ed3a-114">Для этих сценариев интерфейсы DCOM, проиллюстрированные с помощью WCF, имеют приведенную ниже структуру.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-114">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="7ed3a-115">Служба возвращает объект по значению</span><span class="sxs-lookup"><span data-stu-id="7ed3a-115">The service returns an object by-value</span></span>  

 <span data-ttu-id="7ed3a-116">В этом сценарии выполняется вызов службы, а ее метод возвращает объект, который передается по значению с сервера клиенту.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-116">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="7ed3a-117">Такой сценарий представляет приведенный ниже вызов COM.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-117">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="7ed3a-118">В этом случае клиент получает из удаленной службы десериализованную копию объекта.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-118">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="7ed3a-119">Клиент может взаимодействовать с этой локальной копией, не выполняя обратные вызовы в службу.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-119">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="7ed3a-120">Иными словами, клиент получает гарантию, что при вызове методов применительно к локальной копии служба не будет задействована никоим образом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-120">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="7ed3a-121">WCF всегда возвращает объекты из службы по значению, поэтому ниже описывается создание стандартной службы WCF.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-121">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="7ed3a-122">Шаг 1. Определение интерфейса службы WCF</span><span class="sxs-lookup"><span data-stu-id="7ed3a-122">Step 1: Define the WCF service interface</span></span>  

 <span data-ttu-id="7ed3a-123">Определите открытый интерфейс для службы WCF и пометьте его атрибутом [<xref:System.ServiceModel.ServiceContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="7ed3a-123">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="7ed3a-124">Пометьте атрибутом [<xref:System.ServiceModel.OperationContractAttribute>] методы, к которым необходимо предоставить доступ клиентам.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-124">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="7ed3a-125">В примере ниже показано использование этих атрибутов для определения интерфейса на стороне сервера и методов интерфейса, которые может вызывать клиент.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-125">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="7ed3a-126">Метод, используемый в этом сценарии, выделен полужирным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-126">The method used for this scenario is shown in bold.</span></span>  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="7ed3a-127">Шаг 2. Определение контракта данных</span><span class="sxs-lookup"><span data-stu-id="7ed3a-127">Step 2: Define the data contract</span></span>  

 <span data-ttu-id="7ed3a-128">Далее следует создать для службы контракт данных, описывающий то, как будет происходить обмен данными между службой и клиентами.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-128">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="7ed3a-129">Классы, описываемые в контракте данных, следует пометить атрибутом [<xref:System.Runtime.Serialization.DataContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="7ed3a-129">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="7ed3a-130">Отдельные свойства или поля, которые должны быть видны и для клиента, и для сервера, отмечаются атрибутом [<xref:System.Runtime.Serialization.DataMemberAttribute>].</span><span class="sxs-lookup"><span data-stu-id="7ed3a-130">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="7ed3a-131">Чтобы разрешить использование типов, производных от класса, в контракте данных, их следует указать с помощью атрибута [<xref:System.Runtime.Serialization.KnownTypeAttribute>].</span><span class="sxs-lookup"><span data-stu-id="7ed3a-131">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="7ed3a-132">WCF сериализует и десериализует только те типы, которые входят в интерфейс службы или определены как известные.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-132">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="7ed3a-133">При попытке использовать неизвестный тип возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-133">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="7ed3a-134">Дополнительные сведения о контрактах данных см. в разделе [Контракты данных](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-134">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="7ed3a-135">Шаг 3. Реализация службы WCF</span><span class="sxs-lookup"><span data-stu-id="7ed3a-135">Step 3: Implement the WCF service</span></span>  

 <span data-ttu-id="7ed3a-136">Далее следует реализовать класс службы WCF, который реализует интерфейс, определенный в предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-136">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="7ed3a-137">Шаг 4. Настройка службы и клиента</span><span class="sxs-lookup"><span data-stu-id="7ed3a-137">Step 4: Configure the service and the client</span></span>  

 <span data-ttu-id="7ed3a-138">Для запуска службы WCF необходимо объявить конечную точку, предоставляющую доступ к интерфейсу службы по определенному URL-адресу с помощью определенной привязки WCF.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-138">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="7ed3a-139">Привязка определяет транспорт, кодировку и протокол, используемые для обмена данными между клиентами и сервером.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-139">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="7ed3a-140">Привязки обычно добавляются в файл конфигурации проекта службы (web.config).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-140">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="7ed3a-141">Ниже приведен пример записи привязки для службы.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-141">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7ed3a-142">Затем нужно настроить клиент в соответствии с информацией о привязке, определенной в службе.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-142">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="7ed3a-143">Для этого добавьте в файл конфигурации клиентского приложения (app.config) приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-143">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="7ed3a-144">Шаг 5. Запуск службы</span><span class="sxs-lookup"><span data-stu-id="7ed3a-144">Step 5: Run the service</span></span>  

 <span data-ttu-id="7ed3a-145">Наконец, вы можете произвести резидентное размещение в консольном приложении, добавив в приложение службы приведенные ниже строки и запустив его.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-145">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="7ed3a-146">Дополнительные сведения о других способах размещения приложения службы WCF см. в разделе [Размещение служб](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-146">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="7ed3a-147">Шаг 6. Вызов службы из клиента</span><span class="sxs-lookup"><span data-stu-id="7ed3a-147">Step 6: Call the service from the client</span></span>  

 <span data-ttu-id="7ed3a-148">Для вызова службы из клиента нужно создать для нее фабрику каналов, а затем запросить канал, чтобы получить возможность вызывать метод `GetCustomer` непосредственно из клиента.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-148">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="7ed3a-149">Канал реализует интерфейс службы и отвечает за базовую логику запросов и ответов.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-149">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="7ed3a-150">Возвращаемое значение метода представляет собой десериализованную копию ответа службы.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-150">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="7ed3a-151">Клиент отправляет серверу объект по значению</span><span class="sxs-lookup"><span data-stu-id="7ed3a-151">The client sends a by-value object to the server</span></span>  

 <span data-ttu-id="7ed3a-152">В этом случае клиент отправляет серверу объект по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-152">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="7ed3a-153">Это означает, что сервер получит десериализованную копию объекта.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-153">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="7ed3a-154">Сервер может вызывать методы применительно к этой копии с гарантией того, что обратные вызовы кода клиента выполняться не будут.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-154">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="7ed3a-155">Как было замечено ранее, обмен данными с WCF обычно происходит по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-155">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="7ed3a-156">Это гарантирует, что вызовы методов объектов выполняются только локально без вызова кода клиента.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-156">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="7ed3a-157">Такой сценарий представляет приведенный ниже вызов метода COM.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-157">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="7ed3a-158">В этом сценарии используется тот же интерфейс службы и тот же контракт данных, что и в первом примере.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-158">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="7ed3a-159">Кроме того, клиент и служба настраиваются точно так же.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-159">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="7ed3a-160">В этом примере для отправки объекта создается и запускается канал аналогичным образом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-160">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="7ed3a-161">Однако в этом примере вы создадите клиент, который вызывает службу, передавая объект по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-161">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="7ed3a-162">Метод службы, который клиент вызывает в контракте службы, выделен полужирным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-162">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="7ed3a-163">Добавление в клиент кода для отправки объекта по значению</span><span class="sxs-lookup"><span data-stu-id="7ed3a-163">Add code to the client that sends a by-value object</span></span>  

 <span data-ttu-id="7ed3a-164">В приведенном ниже коде показано, как клиент создает объект customer для передачи по значению, создает канал для обмена данными со службой `ICustomerManager` и отправляет ей объект customer.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-164">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="7ed3a-165">Объект customer будет сериализован и отправлен в службу, где он десериализуется в новую копию этого объекта.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-165">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="7ed3a-166">Любые методы этого объекта, вызываемые службой, будут выполняться только локально на сервере.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-166">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="7ed3a-167">Важно отметить, что этот код иллюстрирует отправку производного типа (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-167">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="7ed3a-168">Контракт службы ожидает объекта `Customer`, но в контракте данных службы используется атрибут [<xref:System.Runtime.Serialization.KnownTypeAttribute>], указывающий, что объект `PremiumCustomer` также допустим.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-168">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="7ed3a-169">Попытка сериализации или десериализации любого другого типа посредством этого интерфейса службы WCF завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-169">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="7ed3a-170">Служба возвращает объект по ссылке</span><span class="sxs-lookup"><span data-stu-id="7ed3a-170">The service returns an object by reference</span></span>  

 <span data-ttu-id="7ed3a-171">В этом случае клиентское приложение вызывает удаленную службу, и метод возвращает объект, который передается по ссылке из службы в клиент.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-171">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="7ed3a-172">Как было замечено ранее, службы WCF всегда возвращают объекты по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-172">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="7ed3a-173">Однако вы можете получить требуемый результат с помощью класса <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-173">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="7ed3a-174"><xref:System.ServiceModel.EndpointAddress10> — это сериализуемый объект, передаваемый по значению, с помощью которого клиент может получить на сервере объект, переданный по ссылке в рамках сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-174">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="7ed3a-175">Поведение переданного по ссылке объекта в WCF, которое показано в этом сценарии, отличается от его поведения в DCOM.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-175">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="7ed3a-176">В DCOM сервер может вернуть клиенту объект по ссылке напрямую, и клиент может вызывать методы этого объекта, которые выполняются на сервере.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-176">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="7ed3a-177">Однако в WCF объекты всегда возвращаются по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-177">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="7ed3a-178">Клиент должен получить объект по значению, представленный <xref:System.ServiceModel.EndpointAddress10>, и с помощью него создать собственный объект, полученный по ссылке в рамках сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-178">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="7ed3a-179">Методы объекта сеанса, вызываемые клиентом, выполняются на сервере. Иными словами, этот полученный по ссылке объект в WCF является обычным объектом WCF, настроенным как объект сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-179">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="7ed3a-180">В WCF сеанс — это способ согласования нескольких сообщений, пересылаемых между двумя конечными точками.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-180">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="7ed3a-181">Это означает, что, как только клиент устанавливает подключение к службе, между ним и сервером создается сеанс.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-181">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="7ed3a-182">Клиент использует единственный уникальный экземпляр объекта на стороне сервера для любых взаимодействий в рамках данного сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-182">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="7ed3a-183">Контракты сеансов WCF аналогичны схемам запросов и ответов, ориентированным на подключения.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-183">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="7ed3a-184">Этот сценарий представлен приведенным ниже методом DCOM.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-184">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="7ed3a-185">Шаг 1. Определение интерфейса сеанса службы WCF и его реализация</span><span class="sxs-lookup"><span data-stu-id="7ed3a-185">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  

 <span data-ttu-id="7ed3a-186">Сначала определите интерфейс службы WCF, содержащий объект сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-186">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="7ed3a-187">В этом коде объект сеанса помечен атрибутом `ServiceContract`, который определяет его как обычный интерфейс службы WCF.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-187">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="7ed3a-188">Кроме того, свойству <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> присвоено значение, указывающее, что это будет служба сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-188">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```csharp  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="7ed3a-189">В приведенном ниже коде показана реализация службы.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-189">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="7ed3a-190">Служба помечена атрибутом [ServiceBehavior], а ее свойству InstanceContextMode присвоено значение InstanceContextMode.PerSessions, указывающее, что для каждого сеанса должен создаваться уникальный экземпляр этого типа.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-190">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="7ed3a-191">Шаг 2. Определение службы фабрики WCF для объекта сеанса</span><span class="sxs-lookup"><span data-stu-id="7ed3a-191">Step 2: Define the WCF factory service for the sessionful object</span></span>  

 <span data-ttu-id="7ed3a-192">Необходимо определить и реализовать службу, создающую объект сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-192">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="7ed3a-193">В следующем примере кода показано, как это сделать:</span><span class="sxs-lookup"><span data-stu-id="7ed3a-193">The following code shows how to do this.</span></span> <span data-ttu-id="7ed3a-194">Этот код создает еще одну службу WCF, которая возвращает объект <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-194">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="7ed3a-195">Это сериализуемая форма конечной точки, с помощью которой можно создать объект сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-195">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="7ed3a-196">Далее показана реализация этой службы.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-196">The following is the implementation of this service.</span></span> <span data-ttu-id="7ed3a-197">Эта реализация поддерживает единственную фабрику каналов для создания объектов, связанных с сеансами.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-197">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="7ed3a-198">При вызове метода `GetInstanceAddress` создается канал и объект <xref:System.ServiceModel.EndpointAddress10>, указывающий на удаленный адрес, связанный с этим каналом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-198">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="7ed3a-199"><xref:System.ServiceModel.EndpointAddress10> — это тип данных, который можно вернуть клиенту по значению.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-199"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
```csharp  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="7ed3a-200">Шаг 3. Настройка и запуск служб WCF</span><span class="sxs-lookup"><span data-stu-id="7ed3a-200">Step 3: Configure and start the WCF services</span></span>  

 <span data-ttu-id="7ed3a-201">Для размещения этих служб необходимо добавить указанные ниже записи в файл конфигурации сервера (web.config).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-201">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="7ed3a-202">Добавьте раздел `<client>`, который описывает конечную точку для объекта сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-202">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="7ed3a-203">В этом сценарии сервер также выступает в роли клиента, и его нужно настроить соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-203">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="7ed3a-204">В разделе `<services>` объявите конечные точки службы для фабрики и объекта сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-204">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="7ed3a-205">Это позволит клиенту связаться с конечными точками службы, получить адрес <xref:System.ServiceModel.EndpointAddress10> и создать канал сеанса.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-205">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="7ed3a-206">Далее приведен пример файла конфигурации с этими параметрами:</span><span class="sxs-lookup"><span data-stu-id="7ed3a-206">The following is an example configuration file with these settings:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7ed3a-207">Добавьте приведенные ниже строки в консольное приложение для резидентного размещения службы и запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-207">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="7ed3a-208">Шаг 4. Настройка клиента и вызов службы</span><span class="sxs-lookup"><span data-stu-id="7ed3a-208">Step 4: Configure the client and call the service</span></span>  

 <span data-ttu-id="7ed3a-209">Настройте клиент так, чтобы он мог связываться со службами WCF, добавив указанные ниже записи в файл конфигурации приложения проекта (app.config).</span><span class="sxs-lookup"><span data-stu-id="7ed3a-209">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"
                address="net.tcp://localhost:8081/SessionBoundObject"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"
                address="net.tcp://localhost:8081/SessionBoundFactory"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundFactory"/>  
    </client>
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7ed3a-210">Для вызова службы добавьте в клиент код, выполняющий следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="7ed3a-210">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="7ed3a-211">создание канала для связи со службой `ISessionBoundFactory`;</span><span class="sxs-lookup"><span data-stu-id="7ed3a-211">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="7ed3a-212">использование канала для вызова службы `ISessionBoundFactory` и получения объекта <xref:System.ServiceModel.EndpointAddress10>;</span><span class="sxs-lookup"><span data-stu-id="7ed3a-212">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="7ed3a-213">создание канала для получения объекта сеанса с помощью адреса <xref:System.ServiceModel.EndpointAddress10>;</span><span class="sxs-lookup"><span data-stu-id="7ed3a-213">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="7ed3a-214">вызов методов `SetCurrentValue` и `GetCurrentValue` для демонстрации того, что в рамках нескольких вызовов используется один и тот же экземпляр объекта.</span><span class="sxs-lookup"><span data-stu-id="7ed3a-214">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ed3a-215">См. также</span><span class="sxs-lookup"><span data-stu-id="7ed3a-215">See also</span></span>

- [<span data-ttu-id="7ed3a-216">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="7ed3a-216">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="7ed3a-217">Проектирование и реализация служб</span><span class="sxs-lookup"><span data-stu-id="7ed3a-217">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="7ed3a-218">Создание клиентов</span><span class="sxs-lookup"><span data-stu-id="7ed3a-218">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="7ed3a-219">Дуплексные службы</span><span class="sxs-lookup"><span data-stu-id="7ed3a-219">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
