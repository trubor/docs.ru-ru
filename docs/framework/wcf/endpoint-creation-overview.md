---
description: 'Дополнительные сведения о: Общие сведения о создании конечной точки'
title: Общие сведения о создании конечных точек
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: ff806428922f2097f0d570118d6b5f7836c1797b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756829"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="a85b2-103">Общие сведения о создании конечных точек</span><span class="sxs-lookup"><span data-stu-id="a85b2-103">Endpoint Creation Overview</span></span>

<span data-ttu-id="a85b2-104">Все взаимодействия со службой Windows Communication Foundation (WCF) осуществляется через *конечные точки* службы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="a85b2-105">Конечные точки предоставляют клиентам доступ к функциональным возможностям, предлагаемым службой WCF.</span><span class="sxs-lookup"><span data-stu-id="a85b2-105">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="a85b2-106">В данном разделе приводится описание структуры конечной точки и способов определения конечной точки в конфигурации и в коде.</span><span class="sxs-lookup"><span data-stu-id="a85b2-106">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="a85b2-107">Структура конечной точки</span><span class="sxs-lookup"><span data-stu-id="a85b2-107">The Structure of an Endpoint</span></span>

<span data-ttu-id="a85b2-108">Каждая конечная точка содержит адрес, показывающий, где можно найти конечную точку, привязку, показывающую, как клиент может связаться с конечной точкой, и контракт, определяющий доступные методы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-108">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="a85b2-109">**Адрес**.</span><span class="sxs-lookup"><span data-stu-id="a85b2-109">**Address**.</span></span> <span data-ttu-id="a85b2-110">Адрес однозначно определяет конечную точку и указывает потенциальным потребителям на место расположения службы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-110">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="a85b2-111">Он представлен в объектной модели WCF <xref:System.ServiceModel.EndpointAddress> адресом, который содержит универсальный код ресурса (URI) и свойства адреса, включающие удостоверение, некоторые элементы языка описания веб-служб (WSDL) и коллекцию необязательных заголовков.</span><span class="sxs-lookup"><span data-stu-id="a85b2-111">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="a85b2-112">Необязательные заголовки содержат более подробную информацию для идентификации конечной точки и взаимодействия с ней.</span><span class="sxs-lookup"><span data-stu-id="a85b2-112">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="a85b2-113">Дополнительные сведения см. в разделе [Указание адреса конечной точки](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-113">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="a85b2-114">**Привязка**.</span><span class="sxs-lookup"><span data-stu-id="a85b2-114">**Binding**.</span></span> <span data-ttu-id="a85b2-115">Привязка задает способ связи клиента с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="a85b2-115">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="a85b2-116">Привязка задает способ связи конечной точки с внешним миром, включая используемый транспортный протокол (например, TCP или HTTP), используемое кодирование сообщений (например, текстовое или двоичное) и необходимые требования безопасности (например, безопасность сообщений SSL или SOAP).</span><span class="sxs-lookup"><span data-stu-id="a85b2-116">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="a85b2-117">Дополнительные сведения см. [в разделе Использование привязок для настройки служб и клиентов](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-117">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="a85b2-118">**Контракт службы**.</span><span class="sxs-lookup"><span data-stu-id="a85b2-118">**Service contract**.</span></span> <span data-ttu-id="a85b2-119">Контракт службы показывает, какие функциональные возможности предоставляет клиенту конечная точка.</span><span class="sxs-lookup"><span data-stu-id="a85b2-119">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="a85b2-120">Контракт указывает операции, которые может вызвать клиент, форму сообщения и тип входных параметров или данных, требуемых для вызова операции, а также тип обработки или ответного сообщения, которые может ожидать клиент.</span><span class="sxs-lookup"><span data-stu-id="a85b2-120">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="a85b2-121">Три базовых типа контрактов соответствуют базовым шаблонам обмена сообщениями (MEP): датаграмма (односторонняя связь), запрос-ответ и дуплексная связь (двунаправленная).</span><span class="sxs-lookup"><span data-stu-id="a85b2-121">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="a85b2-122">Контракт службы также может задействовать контракты данных и контракты сообщений, чтобы при обращении требовались определенные типы данных и форматы сообщений.</span><span class="sxs-lookup"><span data-stu-id="a85b2-122">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="a85b2-123">Дополнительные сведения о том, как определить контракт службы, см. в разделе [проектирование контрактов служб](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-123">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="a85b2-124">Обратите внимание, что клиент также может потребоваться для реализации определяемого службой контракта, называемого контрактом обратного вызова, чтобы получить сообщения от службы в дуплексном шаблоне обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="a85b2-124">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="a85b2-125">Дополнительные сведения см. в разделе [Дуплексные службы](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-125">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="a85b2-126">Конечную точку службы можно задать императивно с помощью кода или декларативно с помощью конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a85b2-126">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="a85b2-127">Если конечные точки не заданы, то среда выполнения предоставляет конечные точки по умолчанию, добавляя одну конечную точку по умолчанию для каждого базового адреса в каждом контракте службы, реализованном в службе.</span><span class="sxs-lookup"><span data-stu-id="a85b2-127">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="a85b2-128">Как правило, определять конечные точки в коде непрактично, поскольку привязки и адреса для развернутой службы чаще всего отличаются от привязок и адресов, используемых в процессе разработки службы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-128">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="a85b2-129">Обычно более целесообразно задать конечные точки службы в конфигурации, а не в коде.</span><span class="sxs-lookup"><span data-stu-id="a85b2-129">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="a85b2-130">Если не указывать привязку и адрес в коде, их можно изменять без повторной компиляции и повторного развертывания приложения.</span><span class="sxs-lookup"><span data-stu-id="a85b2-130">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="a85b2-131">При добавлении конечной точки службы, выполняющей олицетворение, необходимо использовать либо один из методов <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>, либо метод <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29>, чтобы правильно загрузить контракт в новый объект <xref:System.ServiceModel.Description.ServiceDescription>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-131">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="a85b2-132">Определение конечных точек в коде</span><span class="sxs-lookup"><span data-stu-id="a85b2-132">Defining Endpoints in Code</span></span>

<span data-ttu-id="a85b2-133">В следующем примере показано, как задать конечную точку в коде.</span><span class="sxs-lookup"><span data-stu-id="a85b2-133">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="a85b2-134">Определите контракт для `IEcho` типа службы, который принимает имя пользователя и эхо с ответом "Hello \<name> !".</span><span class="sxs-lookup"><span data-stu-id="a85b2-134">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="a85b2-135">Реализуйте службу `Echo` типа, определенного контрактом `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="a85b2-135">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="a85b2-136">Укажите адрес конечной точки `http://localhost:8000/Echo` для службы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-136">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="a85b2-137">Настройте службу `Echo` с помощью привязки <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-137">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="a85b2-138">Узел службы создается с базовым адресом, а затем остальная часть адреса, относящаяся к базовому адресу, задается как часть конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a85b2-138">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="a85b2-139">Такое секционирование адреса обеспечивает более удобное определение нескольких конечных точек для служб в узле.</span><span class="sxs-lookup"><span data-stu-id="a85b2-139">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="a85b2-140">Свойства объекта <xref:System.ServiceModel.Description.ServiceDescription> в приложении службы нельзя изменять после вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> для объекта <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-140">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="a85b2-141">Некоторые члены, такие как свойство <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> и методы `AddServiceEndpoint` для объектов <xref:System.ServiceModel.ServiceHostBase> и <xref:System.ServiceModel.ServiceHost>, создают исключение, если их изменить на этом этапе.</span><span class="sxs-lookup"><span data-stu-id="a85b2-141">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="a85b2-142">Другие члены можно изменять без появления исключения, но результат при этом будет неопределенным.</span><span class="sxs-lookup"><span data-stu-id="a85b2-142">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="a85b2-143">Аналогично, на стороне клиента нельзя изменять значения <xref:System.ServiceModel.Description.ServiceEndpoint> после вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> для объекта <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-143">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="a85b2-144">Если после этого изменить свойство <xref:System.ServiceModel.ChannelFactory.Credentials%2A>, создается исключение.</span><span class="sxs-lookup"><span data-stu-id="a85b2-144">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="a85b2-145">Изменение других значений описания клиента происходит без ошибок, но результат изменения в этом случае является неопределенным.</span><span class="sxs-lookup"><span data-stu-id="a85b2-145">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="a85b2-146">Как для службы, так и для клиента, рекомендуется изменять описание до вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-146">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="a85b2-147">Определение конечных точек в конфигурации</span><span class="sxs-lookup"><span data-stu-id="a85b2-147">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="a85b2-148">При создании приложения часто нужно отложить решения для администратора, который выполняет развертывание приложения.</span><span class="sxs-lookup"><span data-stu-id="a85b2-148">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="a85b2-149">Например, часто невозможно узнать заранее, каким будет адрес службы (универсальный код ресурса (URI)).</span><span class="sxs-lookup"><span data-stu-id="a85b2-149">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="a85b2-150">Вместо жестко запрограммированного адреса желательно разрешить администратору ввести его после создания службы.</span><span class="sxs-lookup"><span data-stu-id="a85b2-150">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="a85b2-151">Такая гибкость достигается благодаря конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a85b2-151">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="a85b2-152">Дополнительные сведения см. в разделе [Настройка служб](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-152">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a85b2-153">Для быстрого создания файлов конфигурации используйте [средство служебной программы метаданных ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) с `/config:`  `[,`  `]` параметром filename имя_файла.</span><span class="sxs-lookup"><span data-stu-id="a85b2-153">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="a85b2-154">Использование конечных точек по умолчанию</span><span class="sxs-lookup"><span data-stu-id="a85b2-154">Using Default Endpoints</span></span>

<span data-ttu-id="a85b2-155">Если конечные точки не заданы в коде или в конфигурации, то среда выполнения создает конечные точки по умолчанию, добавляя одну конечную точку по умолчанию для каждого базового адреса в каждом контракте службы, реализованном в службе.</span><span class="sxs-lookup"><span data-stu-id="a85b2-155">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="a85b2-156">Базовый адрес можно указывать в коде или в конфигурации, а конечные точки по умолчанию добавляются, когда вызывается метод <xref:System.ServiceModel.ICommunicationObject.Open> в объекте <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-156">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a85b2-157">Этот пример аналогичен примеру из предыдущего раздела, однако конечные точки не указаны, и поэтому добавляются конечные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a85b2-157">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="a85b2-158">Если конечные точки предоставляются явно, то конечные точки по умолчанию можно добавить, вызвав метод <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> класса <xref:System.ServiceModel.ServiceHost> перед вызовом <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="a85b2-158">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="a85b2-159">Дополнительные сведения о конечных точках по умолчанию см. в разделе [упрощенная конфигурация](simplified-configuration.md) и [упрощенная конфигурация для служб WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a85b2-159">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a85b2-160">См. также</span><span class="sxs-lookup"><span data-stu-id="a85b2-160">See also</span></span>

- [<span data-ttu-id="a85b2-161">Реализация контрактов служб</span><span class="sxs-lookup"><span data-stu-id="a85b2-161">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
