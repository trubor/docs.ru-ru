---
description: Дополнительные сведения см. в статье о форматировании веб-страниц HTTP в WCF
title: Форматирование веб-HTTP WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 715c28635f097cb9f1a773aa3afb7a12faa9478c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752604"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="9be72-103">Форматирование веб-HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="9be72-103">WCF Web HTTP formatting</span></span>

<span data-ttu-id="9be72-104">Модель веб-программирования HTTP WCF позволяет динамически определять лучший формат возвращаемого ответа операции службы.</span><span class="sxs-lookup"><span data-stu-id="9be72-104">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="9be72-105">Поддерживается два метода для определения формата: автоматический и явный.</span><span class="sxs-lookup"><span data-stu-id="9be72-105">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="9be72-106">Автоматическое форматирование</span><span class="sxs-lookup"><span data-stu-id="9be72-106">Automatic formatting</span></span>  

 <span data-ttu-id="9be72-107">Если выбран этот метод, автоматическое форматирование выбирает наилучший формат возврата ответа.</span><span class="sxs-lookup"><span data-stu-id="9be72-107">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="9be72-108">Наилучший формат определяется путем проверки в следующем порядке.</span><span class="sxs-lookup"><span data-stu-id="9be72-108">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="9be72-109">Типы носителей в заголовке Accept сообщения запроса.</span><span class="sxs-lookup"><span data-stu-id="9be72-109">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="9be72-110">Тип содержимого сообщения запроса.</span><span class="sxs-lookup"><span data-stu-id="9be72-110">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="9be72-111">Параметр формата по умолчанию в операции.</span><span class="sxs-lookup"><span data-stu-id="9be72-111">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="9be72-112">Параметр формата по умолчанию в WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="9be72-112">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="9be72-113">Если сообщение запроса содержит заголовок Accept, инфраструктура Windows Communication Foundation (WCF) ищет поддерживаемый тип.</span><span class="sxs-lookup"><span data-stu-id="9be72-113">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="9be72-114">Если заголовок `Accept` указывает приоритеты типов носителей, то они учитываются.</span><span class="sxs-lookup"><span data-stu-id="9be72-114">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="9be72-115">Если в заголовке `Accept` не найден подходящий формат, используется тип содержимого сообщения запроса.</span><span class="sxs-lookup"><span data-stu-id="9be72-115">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="9be72-116">Если не указан подходящий тип содержимого, используется параметр формата по умолчанию для операции.</span><span class="sxs-lookup"><span data-stu-id="9be72-116">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="9be72-117">Формат по умолчанию задается с помощью параметра `ResponseFormat` атрибутов <xref:System.ServiceModel.Web.WebGetAttribute> и <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9be72-117">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="9be72-118">Если не указан формат по умолчанию для операции, используется значение свойства <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="9be72-118">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="9be72-119">Автоматическое форматирование основано на свойстве <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="9be72-119">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="9be72-120">Если это свойство имеет значение `true`, то инфраструктура WCF определяет лучший формат для использования.</span><span class="sxs-lookup"><span data-stu-id="9be72-120">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="9be72-121">Автоматический выбор формата отключен по умолчанию в целях обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="9be72-121">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="9be72-122">Автоматический выбор формата можно включить программно или через конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9be72-122">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="9be72-123">В следующем примере показано включение автоматического выбора формата в коде.</span><span class="sxs-lookup"><span data-stu-id="9be72-123">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="9be72-124">Автоматический выбор формата также можно включить через конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9be72-124">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="9be72-125">Можно задать свойство <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> напрямую в <xref:System.ServiceModel.Description.WebHttpBehavior> или с помощью <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9be72-125">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="9be72-126">В следующем примере показано включение автоматического выбора формата в <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9be72-126">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9be72-127">В следующем примере показано включение автоматического выбора формата с помощью <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9be72-127">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="9be72-128">Явное форматирование</span><span class="sxs-lookup"><span data-stu-id="9be72-128">Explicit formatting</span></span>  

 <span data-ttu-id="9be72-129">Как следует из названия, в явном форматировании разработчик определяет наилучший формат для использования внутри кода операции.</span><span class="sxs-lookup"><span data-stu-id="9be72-129">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="9be72-130">Если лучшим форматом является формат XML или JSON, разработчик устанавливает <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> в формат <xref:System.ServiceModel.Web.WebMessageFormat.Xml> либо <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="9be72-130">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="9be72-131">Если свойство <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> явно не задано, то используется формат операции по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9be72-131">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="9be72-132">В следующем примере для определения формата, который нужно использовать, проверяется параметр строки запроса формата.</span><span class="sxs-lookup"><span data-stu-id="9be72-132">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="9be72-133">Если этот параметр был указан, формат операции задается свойством <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="9be72-133">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="9be72-134">Если необходимо поддерживать форматы, отличающиеся от XML или JSON, операцию нужно определить таким образом, чтобы она возвращала тип <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="9be72-134">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="9be72-135">Внутри кода операции определите соответствующий формат для использования и создайте объект <xref:System.ServiceModel.Channels.Message> с помощью одного из следующих методов:</span><span class="sxs-lookup"><span data-stu-id="9be72-135">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="9be72-136">Каждый из этих методов принимает содержимое и создает сообщение соответствующего формата.</span><span class="sxs-lookup"><span data-stu-id="9be72-136">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="9be72-137">Метод `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` можно использовать для получения списка форматов, предпочитаемых клиентом в порядке снижения предпочтения.</span><span class="sxs-lookup"><span data-stu-id="9be72-137">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="9be72-138">В следующем примере показано применение `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` для определения используемого формата, а затем используется соответствующий метод создания ответа для создания ответного сообщения.</span><span class="sxs-lookup"><span data-stu-id="9be72-138">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9be72-139">См. также</span><span class="sxs-lookup"><span data-stu-id="9be72-139">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="9be72-140">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="9be72-140">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="9be72-141">UriTemplate и UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="9be72-141">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="9be72-142">Общие сведения о модели программирования WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="9be72-142">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="9be72-143">Объектная модель программирования WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="9be72-143">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
