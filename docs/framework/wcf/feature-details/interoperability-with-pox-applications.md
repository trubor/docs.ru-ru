---
description: 'Дополнительные сведения: взаимодействие с приложениями POX'
title: Взаимодействие с приложениями POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 832b9ae93f6046ca9995b57bdcbbfbfeb46d2a09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802714"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="46ffc-103">Взаимодействие с приложениями POX</span><span class="sxs-lookup"><span data-stu-id="46ffc-103">Interoperability with POX applications</span></span>

<span data-ttu-id="46ffc-104">«Обычные старые XML-приложения (POX) обмениваются данными путем обмена необработанными HTTP-сообщениями, которые содержат только данные приложения XML, не заключенные в конверт SOAP.</span><span class="sxs-lookup"><span data-stu-id="46ffc-104">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="46ffc-105">Windows Communication Foundation (WCF) может предоставлять как службы, так и клиенты, использующие сообщения POX.</span><span class="sxs-lookup"><span data-stu-id="46ffc-105">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="46ffc-106">В службе WCF можно использовать для реализации служб, предоставляющих конечные точки клиентам, таким как веб-браузеры и языки сценариев, которые отправляют и получают сообщения POX.</span><span class="sxs-lookup"><span data-stu-id="46ffc-106">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="46ffc-107">На клиенте модель программирования WCF может использоваться для реализации клиентов, взаимодействующих со службами на основе POX.</span><span class="sxs-lookup"><span data-stu-id="46ffc-107">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46ffc-108">Этот документ был первоначально написан для платформа .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="46ffc-108">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="46ffc-109">Платформа .NET Framework 3,5 имеет встроенную поддержку работы с POX приложениями.</span><span class="sxs-lookup"><span data-stu-id="46ffc-109">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="46ffc-110">Дополнительные сведения о [модели программирования WCF Web HTTP](wcf-web-http-programming-model.md)см. здесь.</span><span class="sxs-lookup"><span data-stu-id="46ffc-110">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="46ffc-111">Программирование POX с помощью WCF</span><span class="sxs-lookup"><span data-stu-id="46ffc-111">POX programming with WCF</span></span>

<span data-ttu-id="46ffc-112">Службы WCF, взаимодействующие по протоколу HTTP с помощью сообщений POX, используют [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="46ffc-112">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="46ffc-113">Эта пользовательская привязка содержит два элемента:</span><span class="sxs-lookup"><span data-stu-id="46ffc-113">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="46ffc-114">Стандартный кодировщик SMS-сообщений WCF специально настроен для использования <xref:System.ServiceModel.Channels.MessageVersion.None%2A> значения, что позволяет ему обрабатывать полезные данные XML-сообщений, которые не поступают в оболочку SOAP.</span><span class="sxs-lookup"><span data-stu-id="46ffc-114">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="46ffc-115">Клиенты WCF, взаимодействующие по протоколу HTTP с помощью сообщений POX, используют аналогичную привязку (показанную в следующем императивном коде).</span><span class="sxs-lookup"><span data-stu-id="46ffc-115">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="46ffc-116">Так как клиенты POX должны явно задавать универсальные коды ресурса (URI), которым они отправляют сообщения, им обычно требуется настроить для элемента <xref:System.ServiceModel.Channels.HttpTransportBindingElement> режим ручной адресации, задав в этом элементе для свойства <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="46ffc-116">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="46ffc-117">Это обеспечивает явную адресацию сообщений в коде приложения, исключая необходимость создавать новую фабрику <xref:System.ServiceModel.ChannelFactory> каждый раз, когда приложение передает сообщение другому универсальному коду ресурса (URI) протокола HTTP.</span><span class="sxs-lookup"><span data-stu-id="46ffc-117">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="46ffc-118">Так как сообщения POX не используют заголовки SOAP для передачи важной информации о протоколе, клиенты и службы POX часто должны обрабатывать части базового запроса HTTP, использованного для отправки или приема сообщения.</span><span class="sxs-lookup"><span data-stu-id="46ffc-118">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="46ffc-119">Сведения о протоколе HTTP, такие как заголовки HTTP и коды состояния, отображаются в модели программирования WCF с помощью двух классов:</span><span class="sxs-lookup"><span data-stu-id="46ffc-119">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="46ffc-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, содержащий информацию о запросе HTTP, такую как метод HTTP и заголовки запроса.</span><span class="sxs-lookup"><span data-stu-id="46ffc-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="46ffc-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, содержащий информацию об ответе HTTP, такую как код состояния и описание состояния HTTP, а также все заголовки ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="46ffc-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="46ffc-122">В следующем примере кода показано, как создать сообщение HTTP-запроса GET, адресованное `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="46ffc-122">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="46ffc-123">Сначала создается пустой запрос <xref:System.ServiceModel.Channels.Message> путем вызова метода <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="46ffc-123">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="46ffc-124">Параметр <xref:System.ServiceModel.Channels.MessageVersion.None%2A> используется для указания того, что конверт SOAP не требуется, а параметр <xref:System.String.Empty> передается как действие.</span><span class="sxs-lookup"><span data-stu-id="46ffc-124">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="46ffc-125">Затем сообщение запроса адресуется путем задания в заголовке <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> требуемого универсального кода ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="46ffc-125">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="46ffc-126">Далее создается <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, для параметра <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> задается HTTP-команда GET, а для параметра <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> задается значение `true`, указывающее, что в теле исходящего сообщения запроса HTTP не должны передаваться никакие данные.</span><span class="sxs-lookup"><span data-stu-id="46ffc-126">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="46ffc-127">Наконец, в коллекцию <xref:System.ServiceModel.Channels.Message.Properties%2A> сообщения запроса добавляется свойство запроса, чтобы можно было влиять на способ передачи запроса транспортом HTTP.</span><span class="sxs-lookup"><span data-stu-id="46ffc-127">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="46ffc-128">После этого сообщение готово к отправке через соответствующий экземпляр класса <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="46ffc-128">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="46ffc-129">Аналогичные приемы могут использоваться в службе для извлечения свойства <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> из входящего сообщения и построения ответа.</span><span class="sxs-lookup"><span data-stu-id="46ffc-129">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
