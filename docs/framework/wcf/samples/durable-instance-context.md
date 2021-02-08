---
description: Дополнительные сведения о устойчивом контексте экземпляра
title: Устойчивый контекст экземпляра
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 6f879b2f6c592e5d8f7294405fda403e918070ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793302"
---
# <a name="durable-instance-context"></a><span data-ttu-id="007f9-103">Устойчивый контекст экземпляра</span><span class="sxs-lookup"><span data-stu-id="007f9-103">Durable Instance Context</span></span>

<span data-ttu-id="007f9-104">В этом примере демонстрируется настройка среды выполнения Windows Communication Foundation (WCF) для включения устойчивых контекстов экземпляра.</span><span class="sxs-lookup"><span data-stu-id="007f9-104">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="007f9-105">В качестве резервного хранилища в этом примере используется SQL Server 2005, а именно SQL Server 2005 Express.</span><span class="sxs-lookup"><span data-stu-id="007f9-105">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="007f9-106">Этот сервер также предоставляет возможность доступа к пользовательским механизмам хранения.</span><span class="sxs-lookup"><span data-stu-id="007f9-106">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="007f9-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="007f9-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="007f9-108">Этот пример включает расширение уровня канала и уровня модели службы WCF.</span><span class="sxs-lookup"><span data-stu-id="007f9-108">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="007f9-109">Поэтому прежде чем перейти к реализации, необходимо ознакомиться с основными понятиями.</span><span class="sxs-lookup"><span data-stu-id="007f9-109">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="007f9-110">Устойчивые контексты экземпляров довольно часто встречаются в реальных сценариях.</span><span class="sxs-lookup"><span data-stu-id="007f9-110">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="007f9-111">Например, приложение покупательской корзины может приостанавливать покупки на посередине по и продолжать работу в течение другого дня.</span><span class="sxs-lookup"><span data-stu-id="007f9-111">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="007f9-112">Таким образом, при обращении к покупательской корзине на следующий день восстанавливается исходный контекст.</span><span class="sxs-lookup"><span data-stu-id="007f9-112">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="007f9-113">Важно отметить, что приложение (на сервере) не хранит экземпляр покупательской корзины, когда пользователь отключен от приложения.</span><span class="sxs-lookup"><span data-stu-id="007f9-113">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="007f9-114">Вместо этого оно сохраняет его состояние на устойчивом носителе, который затем используется, чтобы создать новый экземпляр для восстановленного контекста.</span><span class="sxs-lookup"><span data-stu-id="007f9-114">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="007f9-115">Поэтому экземпляр службы, используемый для того же контекста, отличается от предыдущего экземпляра (т. е. имеет другой адрес памяти).</span><span class="sxs-lookup"><span data-stu-id="007f9-115">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="007f9-116">Устойчивый контекст экземпляра обеспечивается несложным протоколом, с помощью которого выполняется обмен ИД контекста между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="007f9-116">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="007f9-117">Этот ИД контекста создается на клиенте и передается службе.</span><span class="sxs-lookup"><span data-stu-id="007f9-117">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="007f9-118">При создании экземпляра службы среда выполнения службы пытается загрузить сохраненное состояние, соответствующее данному ИД контекста, из постоянного хранилища (которым по умолчанию является база данных SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="007f9-118">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="007f9-119">Если состояние недоступно, новый экземпляр имеет состояние по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="007f9-119">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="007f9-120">Реализация службы использует пользовательский атрибут для отметки операций, изменяющих состояние реализации службы, чтобы среда выполнения могла сохранять экземпляр службы после выполнения этих операций.</span><span class="sxs-lookup"><span data-stu-id="007f9-120">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="007f9-121">Для достижения этой цели необходимо выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="007f9-121">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="007f9-122">изменить сообщение, передаваемое по линии связи, включив в него ИД контекста;</span><span class="sxs-lookup"><span data-stu-id="007f9-122">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="007f9-123">изменить локальное поведение службы для реализации пользовательской логики создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="007f9-123">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="007f9-124">Поскольку первая из них в списке влияет на сообщения в сети, она должна быть реализована как пользовательский канал и подключена к уровню канала.</span><span class="sxs-lookup"><span data-stu-id="007f9-124">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="007f9-125">Последнее действие влияет только на локальное поведение службы и поэтому может быть реализовано путем расширения нескольких точек расширяемости службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-125">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="007f9-126">Каждое из таких расширений рассматривается в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="007f9-126">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="007f9-127">Устойчивый канал InstanceContext</span><span class="sxs-lookup"><span data-stu-id="007f9-127">Durable InstanceContext Channel</span></span>

<span data-ttu-id="007f9-128">Прежде всего необходимо обратить внимание на расширение уровня канала.</span><span class="sxs-lookup"><span data-stu-id="007f9-128">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="007f9-129">Первый этап создания пользовательского канала - определение структуры взаимодействия канала.</span><span class="sxs-lookup"><span data-stu-id="007f9-129">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="007f9-130">После того как появился новый протокол передачи, канал должен работать почти с любым другим каналом в стеке каналов.</span><span class="sxs-lookup"><span data-stu-id="007f9-130">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="007f9-131">Поэтому он должен поддерживать все шаблоны обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="007f9-131">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="007f9-132">Однако основная функциональность канала остается прежней несмотря на его структуру взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="007f9-132">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="007f9-133">Конкретнее, на стороне клиента он должен записывать ИД контекста в сообщения, а на стороне службы он должен считывать этот ИД контекста из сообщений и передавать его на верхние уровни.</span><span class="sxs-lookup"><span data-stu-id="007f9-133">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="007f9-134">Поэтому создается класс `DurableInstanceContextChannelBase`, являющийся абстрактным базовым классом для всех реализаций канала устойчивого контекста экземпляра.</span><span class="sxs-lookup"><span data-stu-id="007f9-134">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="007f9-135">Этот класс содержит функции управления на основе общего конечного автомата и два защищенных члена для применения сведений контекста к сообщениям и чтения этих сведений из них.</span><span class="sxs-lookup"><span data-stu-id="007f9-135">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="007f9-136">Эти два метода используют реализации `IContextManager` для записи ИД контекста в сообщения и чтения его из них.</span><span class="sxs-lookup"><span data-stu-id="007f9-136">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="007f9-137">( `IContextManager` — это пользовательский интерфейс, используемый для определения контракта для всех диспетчеров контекста.) Канал может либо включать идентификатор контекста в пользовательский заголовок SOAP, либо в заголовок HTTP cookie.</span><span class="sxs-lookup"><span data-stu-id="007f9-137">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="007f9-138">Каждая реализация диспетчера контекста наследуется от класса `ContextManagerBase`, в котором содержатся общие функции для всех диспетчеров контекста.</span><span class="sxs-lookup"><span data-stu-id="007f9-138">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="007f9-139">Метод `GetContextId` в этом классе используется для получения ИД контекста от клиента.</span><span class="sxs-lookup"><span data-stu-id="007f9-139">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="007f9-140">При первом получении ИД контекста этот метод сохраняет его в текстовый файл, имя которого создается на основе адреса удаленной конечной точки (недопустимые символы имени файла в типичных URI заменяются символами "@").</span><span class="sxs-lookup"><span data-stu-id="007f9-140">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="007f9-141">Затем при запросе ИД контекста той же удаленной конечной точкой этот метод проверяет, существует ли соответствующий файл.</span><span class="sxs-lookup"><span data-stu-id="007f9-141">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="007f9-142">Если файл существует, метод считывает и возвращает ИД контекста.</span><span class="sxs-lookup"><span data-stu-id="007f9-142">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="007f9-143">В противном случае он возвращает вновь созданный ИД контекста и сохраняет его в файл.</span><span class="sxs-lookup"><span data-stu-id="007f9-143">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="007f9-144">В конфигурации по умолчанию эти файлы помещаются в каталог с именем Контекстсторе, который находится в каталоге Temp текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="007f9-144">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="007f9-145">Однако это расположение настраивается с помощью элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="007f9-145">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="007f9-146">Механизм, используемый для передачи ИД контекста, является настраиваемым.</span><span class="sxs-lookup"><span data-stu-id="007f9-146">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="007f9-147">Он может быть записан в заголовок файла cookie HTTP или в пользовательский заголовок SOAP.</span><span class="sxs-lookup"><span data-stu-id="007f9-147">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="007f9-148">В случае подхода на основе пользовательского заголовка SOAP можно использовать этот протокол с протоколами, отличными от HTTP (например, с протоколом TCP или протоколом именованных каналов).</span><span class="sxs-lookup"><span data-stu-id="007f9-148">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="007f9-149">Эти две возможности реализуют два класса - `MessageHeaderContextManager` и `HttpCookieContextManager`.</span><span class="sxs-lookup"><span data-stu-id="007f9-149">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="007f9-150">Оба класса позволяют записывать ИД контекста в сообщение соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="007f9-150">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="007f9-151">Например, класс `MessageHeaderContextManager` позволяет записать его в заголовок SOAP с помощью метода `WriteContext`.</span><span class="sxs-lookup"><span data-stu-id="007f9-151">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="007f9-152">Методы `ApplyContext` и `ReadContextId` класса `DurableInstanceContextChannelBase` вызывают `IContextManager.ReadContext` и `IContextManager.WriteContext` соответственно.</span><span class="sxs-lookup"><span data-stu-id="007f9-152">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="007f9-153">Однако эти диспетчеры контекста не создаются непосредственно с помощью класса `DurableInstanceContextChannelBase`.</span><span class="sxs-lookup"><span data-stu-id="007f9-153">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="007f9-154">Для выполнения этой задачи используется класс `ContextManagerFactory`.</span><span class="sxs-lookup"><span data-stu-id="007f9-154">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="007f9-155">Метод `ApplyContext` вызывается отправляющими каналами.</span><span class="sxs-lookup"><span data-stu-id="007f9-155">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="007f9-156">Он вставляет ИД контекста в исходящие сообщения.</span><span class="sxs-lookup"><span data-stu-id="007f9-156">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="007f9-157">Метод `ReadContextId` вызывается получающими каналами.</span><span class="sxs-lookup"><span data-stu-id="007f9-157">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="007f9-158">Этот метод обеспечивает доступность ИД контекста во входящих сообщениях и добавляет его в коллекцию `Properties` класса `Message`.</span><span class="sxs-lookup"><span data-stu-id="007f9-158">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="007f9-159">Кроме того, в случае ошибки чтения ИД контекста метод вызывает исключение `CommunicationException`, что приводит к прерыванию работы канала.</span><span class="sxs-lookup"><span data-stu-id="007f9-159">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="007f9-160">Прежде чем продолжить, важно понять принцип использования коллекции `Properties` в классе `Message`.</span><span class="sxs-lookup"><span data-stu-id="007f9-160">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="007f9-161">Как правило, коллекция `Properties` используется при передаче данных с нижнего на верхние уровни канала.</span><span class="sxs-lookup"><span data-stu-id="007f9-161">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="007f9-162">Таким образом требуемые данные можно согласованно передавать на верхние уровни независимо от подробностей работы протокола.</span><span class="sxs-lookup"><span data-stu-id="007f9-162">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="007f9-163">Иными словами, уровень канала может отправлять и получать идентификатор контекста как заголовок SOAP или заголовок HTTP cookie.</span><span class="sxs-lookup"><span data-stu-id="007f9-163">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="007f9-164">Однако знание этих подробностей на верхних уровнях не требуется, поскольку уровень канала делает эту информацию доступной в коллекции `Properties`.</span><span class="sxs-lookup"><span data-stu-id="007f9-164">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="007f9-165">Теперь, при наличии класса `DurableInstanceContextChannelBase`, следует реализовать все десять необходимых интерфейсов (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="007f9-165">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="007f9-166">Они похожи на каждый доступный шаблон обмена сообщениями (Datagram, симплексная, дуплексный и их варианты сеансов).</span><span class="sxs-lookup"><span data-stu-id="007f9-166">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="007f9-167">Каждая из этих реализаций наследует базовый класс, описанный ранее, и вызывает `ApplyContext` и `ReadContextId` соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="007f9-167">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="007f9-168">Например, канал `DurableInstanceContextOutputChannel`, реализующий интерфейс IOutputChannel, вызывает метод `ApplyContext` для каждого метода, который отправляет сообщения.</span><span class="sxs-lookup"><span data-stu-id="007f9-168">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="007f9-169">С другой стороны, `DurableInstanceContextInputChannel` —, реализующий `IInputChannel` интерфейс, вызывает `ReadContextId` метод в каждом методе, который получает сообщения.</span><span class="sxs-lookup"><span data-stu-id="007f9-169">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="007f9-170">Кроме того, эти реализации каналов делегируют вызовы методов каналу, расположенному ниже них в стеке каналов.</span><span class="sxs-lookup"><span data-stu-id="007f9-170">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="007f9-171">Однако у связанных с сеансами разновидностей имеется базовая логика, обеспечивающая отправку и чтение ИД контекста только для первого сообщения, которое приводит к созданию сеанса.</span><span class="sxs-lookup"><span data-stu-id="007f9-171">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="007f9-172">Эти реализации каналов затем добавляются в среду выполнения канала WCF `DurableInstanceContextBindingElement` классом и `DurableInstanceContextBindingElementSection` классом соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="007f9-172">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="007f9-173">Дополнительные сведения об элементах привязки и разделах привязки элементов см. в образце документации по каналу [хттпкукиесессион](httpcookiesession.md) .</span><span class="sxs-lookup"><span data-stu-id="007f9-173">See the [HttpCookieSession](httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="007f9-174">Расширения уровня модели служб</span><span class="sxs-lookup"><span data-stu-id="007f9-174">Service Model Layer Extensions</span></span>

<span data-ttu-id="007f9-175">Теперь, когда ИД контекста прошел через уровень канала, можно реализовать поведение службы для настройки создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="007f9-175">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="007f9-176">В этом образце диспетчер хранилища используется для загрузки состояния из постоянного хранилища, а также сохранения состояния в него.</span><span class="sxs-lookup"><span data-stu-id="007f9-176">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="007f9-177">Как отмечалось ранее, этот образец предоставляет диспетчер хранилища SQL Server 2005 в качестве резервного хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-177">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="007f9-178">Однако также можно добавить к этому расширению пользовательские механизмы хранения.</span><span class="sxs-lookup"><span data-stu-id="007f9-178">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="007f9-179">Для этого объявляется открытый интерфейс, который должен быть реализован всеми диспетчерами хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-179">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="007f9-180">Класс `SqlServerStorageManager` содержит реализацию `IStorageManager` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="007f9-180">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="007f9-181">В своем `SaveInstance` методе данный объект сериализуется с помощью XmlSerializer и сохраняется в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="007f9-181">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="007f9-182">В `GetInstance` методе сериализованные данные считываются для заданного идентификатора контекста, а объект, созданный из него, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="007f9-182">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="007f9-183">Пользователи этих диспетчеров хранилища не должны создавать их экземпляры непосредственно.</span><span class="sxs-lookup"><span data-stu-id="007f9-183">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="007f9-184">Они используют класс `StorageManagerFactory`, абстрагирующий их от подробностей создания диспетчера хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-184">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="007f9-185">В этом классе имеется один статический член, `GetStorageManager`, который создает экземпляр заданного типа диспетчера хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-185">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="007f9-186">Если параметр типа имеет значение `null`, этот метод создает и возвращает экземпляр класса по умолчанию `SqlServerStorageManager`.</span><span class="sxs-lookup"><span data-stu-id="007f9-186">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="007f9-187">Он также проверяет, что заданный тип реализует интерфейс `IStorageManager`.</span><span class="sxs-lookup"><span data-stu-id="007f9-187">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="007f9-188">Инфраструктура, необходимая для чтения и записи экземпляров из постоянного хранилища, реализована.</span><span class="sxs-lookup"><span data-stu-id="007f9-188">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="007f9-189">Теперь следует выполнить необходимые шаги по изменению поведения службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-189">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="007f9-190">На первом шаге этого процесса нужно сохранить ИД контекста, поступивший через уровень канала в текущий контекст InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="007f9-190">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="007f9-191">InstanceContext — это компонент среды выполнения, который выступает в качестве связи между диспетчером WCF и экземпляром службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-191">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="007f9-192">Его можно использовать для предоставления дополнительного состояния и поведения экземпляру службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-192">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="007f9-193">Это важно, поскольку в связанном с сеансами взаимодействии ИД контекста отправляется только с первым сообщением.</span><span class="sxs-lookup"><span data-stu-id="007f9-193">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="007f9-194">WCF позволяет расширять компонент среды выполнения InstanceContext, добавляя новое состояние и поведение с помощью шаблона расширяемых объектов.</span><span class="sxs-lookup"><span data-stu-id="007f9-194">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="007f9-195">Шаблон расширяемого объекта используется в WCF для расширения существующих классов среды выполнения с новыми функциональными возможностями или для добавления новых функций состояния в объект.</span><span class="sxs-lookup"><span data-stu-id="007f9-195">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="007f9-196">В расширяемых шаблонах объектов-IExtensibleObject \<T> , IExtension и иекстенсионколлектион есть три интерфейса \<T> \<T> :</span><span class="sxs-lookup"><span data-stu-id="007f9-196">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="007f9-197">Интерфейс IExtensibleObject \<T> реализуется объектами, разрешающими расширения, которые настраивают их функциональность.</span><span class="sxs-lookup"><span data-stu-id="007f9-197">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="007f9-198">Интерфейс IExtension \<T> реализуется объектами, которые являются расширениями классов типа T.</span><span class="sxs-lookup"><span data-stu-id="007f9-198">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="007f9-199">Интерфейс Иекстенсионколлектион \<T> — это коллекция иекстенсионс, которая позволяет извлекать иекстенсионс по типу.</span><span class="sxs-lookup"><span data-stu-id="007f9-199">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="007f9-200">Таким образом, необходимо создать класс InstanceContextExtension, реализующий интерфейс IExtension и определяющий требуемое состояние для сохранения идентификатора контекста.</span><span class="sxs-lookup"><span data-stu-id="007f9-200">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="007f9-201">Этот класс также предоставляет состояние для фиксации используемого диспетчера хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-201">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="007f9-202">После сохранения нового состояния его должно быть невозможно изменить.</span><span class="sxs-lookup"><span data-stu-id="007f9-202">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="007f9-203">Поэтому состояние предоставляется и сохраняется в экземпляре в момент его создания, после чего доступ к нему осуществляется только с помощью свойств, доступных только для чтения.</span><span class="sxs-lookup"><span data-stu-id="007f9-203">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="007f9-204">Класс InstanceContextInitializer реализует интерфейс IInstanceContextInitializer и добавляет расширение контекста экземпляра в коллекцию Extensions создаваемого контекста InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="007f9-204">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="007f9-205">Как отмечалось ранее, ИД контекста считывается из коллекции `Properties` класса `Message` и передается конструктору класса расширения.</span><span class="sxs-lookup"><span data-stu-id="007f9-205">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="007f9-206">Это демонстрирует, как можно согласованно обмениваться информацией между уровнями.</span><span class="sxs-lookup"><span data-stu-id="007f9-206">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="007f9-207">Следующий важный шаг - переопределение процесса создания экземпляров службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-207">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="007f9-208">WCF позволяет реализовать поведение пользовательских экземпляров и присоединить их к среде выполнения с помощью интерфейса Иинстанцепровидер.</span><span class="sxs-lookup"><span data-stu-id="007f9-208">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="007f9-209">Для выполнения этой задачи реализуется новый класс `InstanceProvider`.</span><span class="sxs-lookup"><span data-stu-id="007f9-209">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="007f9-210">Тип службы, ожидаемый от поставщика экземпляра, принимается в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="007f9-210">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="007f9-211">Затем он используется для создания новых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="007f9-211">Later this is used to create new instances.</span></span> <span data-ttu-id="007f9-212">В `GetInstance` реализации создается экземпляр диспетчера хранилища, который ищет сохраняемый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="007f9-212">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="007f9-213">Если он возвращает `null` , создается новый экземпляр типа службы, который возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="007f9-213">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="007f9-214">Следующим важным шагом является установка `InstanceContextExtension` `InstanceContextInitializer` классов, и `InstanceProvider` в среду выполнения модели службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-214">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="007f9-215">С помощью пользовательского атрибута можно отметить классы реализации службы для установки поведения.</span><span class="sxs-lookup"><span data-stu-id="007f9-215">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="007f9-216">`DurableInstanceContextAttribute` содержит реализацию этого атрибута и реализует интерфейс `IServiceBehavior` для расширения всей среды выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-216">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="007f9-217">В этом классе имеется свойство, принимающее тип используемого диспетчера хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-217">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="007f9-218">Таким образом, реализация позволяет пользователям указать собственную `IStorageManager` реализацию в качестве параметра этого атрибута.</span><span class="sxs-lookup"><span data-stu-id="007f9-218">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="007f9-219">В `ApplyDispatchBehavior` реализации выполняется `InstanceContextMode` `ServiceBehavior` Проверка текущего атрибута.</span><span class="sxs-lookup"><span data-stu-id="007f9-219">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="007f9-220">Если это свойство имеет значение Singleton, устойчивое создание экземпляров невозможно и для уведомления узла создается исключение `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="007f9-220">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="007f9-221">После этого экземпляры диспетчера хранилища, инициализатор контекста экземпляра и поставщик экземпляров создаются и устанавливаются в объекте `DispatchRuntime`, созданном для каждой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="007f9-221">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="007f9-222">Итак, на данный момент создан канал, который обеспечивает пользовательский протокол передачи данных по линии связи для обмена пользовательским ИД контекста и переопределяет поведение создания экземпляров по умолчанию для загрузки экземпляров из постоянного хранилища.</span><span class="sxs-lookup"><span data-stu-id="007f9-222">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="007f9-223">Остается найти способ сохранения экземпляра службы в хранилище сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="007f9-223">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="007f9-224">Как отмечалось ранее, уже имеется требуемая функциональность для сохранения состояния в реализации `IStorageManager`.</span><span class="sxs-lookup"><span data-stu-id="007f9-224">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="007f9-225">Теперь это необходимо интегрировать со средой выполнения WCF.</span><span class="sxs-lookup"><span data-stu-id="007f9-225">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="007f9-226">Требуется другой атрибут, применимый к методам в классе реализации службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-226">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="007f9-227">Этот атрибут должен применяться к методам, изменяющим состояние экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-227">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="007f9-228">Класс `SaveStateAttribute` реализует данную функциональность.</span><span class="sxs-lookup"><span data-stu-id="007f9-228">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="007f9-229">Он также реализует `IOperationBehavior` класс для изменения среды выполнения WCF для каждой операции.</span><span class="sxs-lookup"><span data-stu-id="007f9-229">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="007f9-230">Если метод помечен с помощью этого атрибута, среда выполнения WCF вызывает `ApplyBehavior` метод при `DispatchOperation` создании соответствующего.</span><span class="sxs-lookup"><span data-stu-id="007f9-230">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="007f9-231">В реализации этого метода существует одна строка кода:</span><span class="sxs-lookup"><span data-stu-id="007f9-231">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="007f9-232">Эта инструкция создает экземпляр типа `OperationInvoker` и присваивает его свойству `Invoker` создаваемого объекта `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="007f9-232">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="007f9-233">Класс `OperationInvoker` является оболочкой для средства вызова операции по умолчанию, созданного для `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="007f9-233">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="007f9-234">Этот класс реализует интерфейс `IOperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="007f9-234">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="007f9-235">В `Invoke` реализации метода фактический вызов метода делегируется внутреннему вызывающему операциям.</span><span class="sxs-lookup"><span data-stu-id="007f9-235">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="007f9-236">Однако перед возвратом результатов диспетчер хранилища в `InstanceContext` используется для сохранения экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-236">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="007f9-237">Использование расширения</span><span class="sxs-lookup"><span data-stu-id="007f9-237">Using the Extension</span></span>

<span data-ttu-id="007f9-238">Расширения уровня канала и модели службы выполняются, и теперь их можно использовать в приложениях WCF.</span><span class="sxs-lookup"><span data-stu-id="007f9-238">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="007f9-239">Службы должны добавить канал в стек каналов с помощью пользовательской привязки, а затем пометить классы реализации службы соответствующими атрибутами.</span><span class="sxs-lookup"><span data-stu-id="007f9-239">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="007f9-240">Клиентским приложениям необходимо добавить канал DurableInstanceContextChannel в стек каналов с помощью пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="007f9-240">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="007f9-241">Чтобы настроить канал декларативно в файле конфигурации, необходимо добавить раздел элемента привязки в коллекцию расширений элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="007f9-241">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="007f9-242">Теперь элемент привязки можно использовать с пользовательской привязкой аналогично другим стандартным элементам привязки.</span><span class="sxs-lookup"><span data-stu-id="007f9-242">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="007f9-243">Заключение</span><span class="sxs-lookup"><span data-stu-id="007f9-243">Conclusion</span></span>

<span data-ttu-id="007f9-244">В этом образце показано, как создать пользовательский канал протокола и настроить поведение службы, чтобы задействовать этот канал.</span><span class="sxs-lookup"><span data-stu-id="007f9-244">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="007f9-245">Расширение можно усовершенствовать, позволив пользователям указывать реализацию `IStorageManager` с помощью раздела конфигурации.</span><span class="sxs-lookup"><span data-stu-id="007f9-245">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="007f9-246">Это делает возможным изменение резервного хранилища без повторной компиляции кода службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-246">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="007f9-247">Более того, можно попытаться реализовать класс (например, `StateBag`), инкапсулирующий состояние экземпляра.</span><span class="sxs-lookup"><span data-stu-id="007f9-247">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="007f9-248">Этот класс отвечает за сохранение состояния при каждом его изменении.</span><span class="sxs-lookup"><span data-stu-id="007f9-248">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="007f9-249">Таким образом можно избегать использования атрибута `SaveState` и более точно выполнять операции сохранения (например, можно сохранять состояние при его фактическом изменении, а не при каждом вызове метода с атрибутом `SaveState`).</span><span class="sxs-lookup"><span data-stu-id="007f9-249">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="007f9-250">При выполнении образца получается следующий результат.</span><span class="sxs-lookup"><span data-stu-id="007f9-250">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="007f9-251">Клиент добавляет две единицы продукции в свою покупательскую корзину и получает список имеющихся в ней единиц продукции от службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-251">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="007f9-252">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="007f9-252">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="007f9-253">Повторное построение службы приводит к перезаписи файла базы данных.</span><span class="sxs-lookup"><span data-stu-id="007f9-253">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="007f9-254">Для просмотра состояния, сохраняемого между несколькими запусками образца, не следует выполнять повторная сборка образца между запусками.</span><span class="sxs-lookup"><span data-stu-id="007f9-254">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="007f9-255">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="007f9-255">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="007f9-256">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="007f9-256">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="007f9-257">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="007f9-257">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="007f9-258">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="007f9-258">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="007f9-259">Для выполнения этого образца необходимо использовать SQL Server 2005 или SQL Express 2005.</span><span class="sxs-lookup"><span data-stu-id="007f9-259">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="007f9-260">При использовании SQL Server 2005 необходимо изменить конфигурацию строки подключения службы.</span><span class="sxs-lookup"><span data-stu-id="007f9-260">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="007f9-261">При выполнении примера на нескольких компьютерах использование SQL Server требуется только на компьютере-сервере.</span><span class="sxs-lookup"><span data-stu-id="007f9-261">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="007f9-262">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="007f9-262">The samples may already be installed on your machine.</span></span> <span data-ttu-id="007f9-263">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="007f9-263">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="007f9-264">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="007f9-264">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="007f9-265">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="007f9-265">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
