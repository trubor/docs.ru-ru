---
description: 'Дополнительные сведения о: Хттпкукиесессион'
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: b5b5a94cd6c019e39d95c1581ce88dbca4460ba6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631961"
---
# <a name="httpcookiesession"></a><span data-ttu-id="bf8fe-103">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="bf8fe-103">HttpCookieSession</span></span>

<span data-ttu-id="bf8fe-104">В этом образце показано, как построить пользовательский канал протокола, который использует для управления сеансами протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-104">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="bf8fe-105">Этот канал обеспечивает взаимодействие между службами Windows Communication Foundation (WCF) и клиентами ASMX или между клиентами WCF и службами ASMX.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-105">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="bf8fe-106">Когда клиент вызывает веб-метод в веб-службе ASMX, которая основана на сеансе, подсистема ASP.NET выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-106">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="bf8fe-107">создает уникальный идентификатор сеанса;</span><span class="sxs-lookup"><span data-stu-id="bf8fe-107">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="bf8fe-108">создает объект сеанса и связывает его с уникальным идентификатором;</span><span class="sxs-lookup"><span data-stu-id="bf8fe-108">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="bf8fe-109">добавляет уникальный идентификатор в заголовок HTTP-ответа Set-Cookie и отправляет его клиенту;</span><span class="sxs-lookup"><span data-stu-id="bf8fe-109">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="bf8fe-110">определяет клиент в последующих вызовах по идентификатору сеанса и использует его для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-110">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="bf8fe-111">Клиент включает этот идентификатор сеанса во все дальнейшие запросы к серверу.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-111">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="bf8fe-112">Сервер использует идентификатор сеанса клиента, чтобы загружать соответствующий объект сеанса для текущего контекста HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-112">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf8fe-113">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf8fe-114">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bf8fe-115">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf8fe-116">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="bf8fe-117">Шаблон обмена сообщениями канала HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="bf8fe-117">HttpCookieSession Channel Message Exchange Pattern</span></span>  

 <span data-ttu-id="bf8fe-118">В этом примере включаются сеансы для сценариев, подобных применению служб ASMX.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-118">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="bf8fe-119">В нижней части стека каналов имеется транспорт HTTP, который поддерживает <xref:System.ServiceModel.Channels.IRequestChannel> и <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-119">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="bf8fe-120">Именно канал отвечает за то, чтобы предоставлять сеансы каналам стека более высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-120">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="bf8fe-121">В образце реализуются два канала (<xref:System.ServiceModel.Channels.IRequestSessionChannel> и <xref:System.ServiceModel.Channels.IReplySessionChannel>), поддерживающих сеансы.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-121">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="bf8fe-122">Канал службы</span><span class="sxs-lookup"><span data-stu-id="bf8fe-122">Service Channel</span></span>  

 <span data-ttu-id="bf8fe-123">В этом образце создается канал службы в классе `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-123">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="bf8fe-124">Этот класс реализует интерфейс <xref:System.ServiceModel.Channels.IChannelListener> и преобразует канал <xref:System.ServiceModel.Channels.IReplyChannel> из нижнего канала в стеке в канал <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-124">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="bf8fe-125">Этот процесс можно разбить на следующие части.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-125">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="bf8fe-126">Когда открывается прослушиватель канала, он принимает от своего внутреннего прослушивателя внутренний канал.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-126">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="bf8fe-127">Поскольку внутренний прослушиватель является прослушивателем датаграмм, а время существования принятого канала вычитается из времени существования прослушивателя, можно закрыть внутренний прослушиватель и работать только с внутренним каналом.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-127">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="bf8fe-128">После завершения процесса открытия мы настраиваем цикл сообщений, чтобы получать сообщения от внутреннего канала.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-128">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="bf8fe-129">Когда сообщение прибывает, канал службы проверяет идентификатор сеанса и демультиплексирует его в соответствующий канал сеанса.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-129">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="bf8fe-130">Прослушиватель канала поддерживает словарь, который сопоставляет идентификаторы сеансов с экземплярами каналов сеансов.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-130">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="bf8fe-131">`HttpCookieReplySessionChannel`Класс реализует <xref:System.ServiceModel.Channels.IReplySessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="bf8fe-131">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="bf8fe-132">Более высокие уровня стека каналов вызывают метод <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> для чтения запросов для этого сеанса.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-132">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="bf8fe-133">У каждого канала сеанса имеется закрытая очередь сообщений, заполняемая каналом службы.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-133">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="bf8fe-134">Если происходит вызов метода <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A>, а в очереди сообщений нет сообщений, то канал ждет в течение заданного времени, а затем отключается.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-134">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="bf8fe-135">Это приведет к очистке каналов сеанса, созданных для клиентов, не являющихся WCF.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-135">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="bf8fe-136">Мы используем `channelMapping` для отслеживания `ReplySessionChannels` и не закрываем соответствующий канал `innerChannel`, пока не будут закрыты все принятые каналы.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-136">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="bf8fe-137">Таким образом, канал `HttpCookieReplySessionChannel` может существовать после истечения времени существования `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-137">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="bf8fe-138">Кроме того, нам не нужно беспокоиться о попадании прослушивателя под сборку мусора, поскольку принятые каналы сохраняют ссылку на свой прослушиватель с помощью обратного вызова `OnClosed`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-138">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="bf8fe-139">Клиентский канал</span><span class="sxs-lookup"><span data-stu-id="bf8fe-139">Client channel</span></span>  

 <span data-ttu-id="bf8fe-140">Соответствующий клиентский канал создается в классе `HttpCookieSessionChannelFactory`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-140">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="bf8fe-141">Во время создания канал фабрика каналов с помощью `HttpCookieRequestSessionChannel` создает оболочку для внутреннего канала запросов.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-141">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="bf8fe-142">Класс `HttpCookieRequestSessionChannel` перенаправляет вызовы в соответствующий канал запросов.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-142">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="bf8fe-143">Когда клиент закрывает прокси, `HttpCookieRequestSessionChannel` отправляет службе сообщение о том, что канал закрывается.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-143">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="bf8fe-144">Таким образом, стек каналов службы может безопасно закрыть используемый канал сеанса.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-144">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="bf8fe-145">Привязка и элемент привязки</span><span class="sxs-lookup"><span data-stu-id="bf8fe-145">Binding and Binding Element</span></span>  

 <span data-ttu-id="bf8fe-146">После создания канала службы и клиента следующий шаг заключается в их интеграции в среду выполнения WCF.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-146">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="bf8fe-147">Каналы предоставляются WCF с помощью привязок и элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-147">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="bf8fe-148">Привязка состоит из одного или нескольких элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-148">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="bf8fe-149">WCF предлагает несколько определяемых системой привязок. Например, BasicHttpBinding или WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-149">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="bf8fe-150">Класс `HttpCookieSessionBindingElement` содержит реализацию элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-150">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="bf8fe-151">Он переопределяет прослушиватель канала и методы создания фабрики канала для создания нужных экземпляров прослушивателя канала и фабрики каналов.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-151">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="bf8fe-152">В этом образце для описания службы используются утверждения политики.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-152">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="bf8fe-153">Это позволяет образцу публиковать свои требования к каналам для других клиентов, которые могут пользоваться службой.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-153">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="bf8fe-154">Например, этот элемент привязки публикует утверждения политики, позволяющие потенциальным клиентам узнать, служба поддерживает сеансы.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-154">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="bf8fe-155">Поскольку в конфигурации элемента привязки этого образца включено свойство `ExchangeTerminateMessage`, оно добавляет необходимые утверждения, чтобы показать, что служба поддерживает дополнительные действия обмена сообщениями для завершения сеанса.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-155">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="bf8fe-156">Клиенты могут использовать это действие.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-156">Clients can then use this action.</span></span> <span data-ttu-id="bf8fe-157">В следующем коде WSDL показаны утверждения политики, созданные на базе элемента `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-157">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="bf8fe-158">Класс `HttpCookieSessionBinding` является предоставляемой системой привязкой, которая использует описанный выше элемент привязки.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-158">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="bf8fe-159">Добавление канала в систему конфигурации</span><span class="sxs-lookup"><span data-stu-id="bf8fe-159">Adding the Channel to the Configuration System</span></span>  

 <span data-ttu-id="bf8fe-160">В этом образце имеется два канала, делающие канал доступным через конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-160">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="bf8fe-161">Первый - элемент <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> для `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-161">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="bf8fe-162">Основная часть реализации делегируется классу `HttpCookieSessionBindingConfigurationElement`, наследуемому от класса <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-162">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="bf8fe-163">Элемент `HttpCookieSessionBindingConfigurationElement` имеет свойства, которые соответствуют свойствам элемента `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-163">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="bf8fe-164">Раздел расширения элемента привязки</span><span class="sxs-lookup"><span data-stu-id="bf8fe-164">Binding Element Extension Section</span></span>  

 <span data-ttu-id="bf8fe-165">Раздел `HttpCookieSessionBindingElementSection` представляет собой <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> , который предоставляет `HttpCookieSessionBindingElement` системе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-165">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="bf8fe-166">С помощью нескольких простых переопределений определяется имя раздела конфигурации, тип элемента привязки и способ создания элемента привязки.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-166">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="bf8fe-167">Мы можем затем зарегистрировать раздел расширения в файле конфигурации следующим образом.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-167">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>
    <system.serviceModel>
      <extensions>
        <bindingElementExtensions>
          <add name="httpCookieSession"
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,
                    HttpCookieSessionExtension, Version=1.0.0.0,
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>
    </system.serviceModel>
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="bf8fe-168">Тестовый код</span><span class="sxs-lookup"><span data-stu-id="bf8fe-168">Test Code</span></span>  

 <span data-ttu-id="bf8fe-169">Тестовый код для использования этого примера транспорта находится в каталогах Client и Service.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-169">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="bf8fe-170">Он состоит из двух тестов — один тест использует привязку с параметром, равным `allowCookies` `true` , на клиенте.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-170">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="bf8fe-171">Второй тест включает на привязке явное отключение (с помощью обмена сообщениями завершения).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-171">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="bf8fe-172">При запуске примера результат должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bf8fe-172">When you run the sample, you should see the following output:</span></span>  
  
```console  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf8fe-173">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="bf8fe-173">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bf8fe-174">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="bf8fe-174">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="bf8fe-175">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="bf8fe-176">Чтобы выполнить сборку решения, следуйте инструкциям в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-176">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="bf8fe-177">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf8fe-177">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
