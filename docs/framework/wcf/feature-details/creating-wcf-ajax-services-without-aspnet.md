---
description: 'Дополнительные сведения: создание служб WCF AJAX без ASP.NET'
title: Создание служб WCF AJAX без использования ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 98171a67b3dd2f267edf2281396bb0da1858b0b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705152"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="fc353-103">Создание служб WCF AJAX без использования ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fc353-103">Creating WCF AJAX Services without ASP.NET</span></span>

<span data-ttu-id="fc353-104">Доступ к службам AJAX Windows Communication Foundation (WCF) можно получить с любой веб-страницы с поддержкой JavaScript, не требуя ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="fc353-104">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="fc353-105">В этом разделе описывается создание такой службы WCF.</span><span class="sxs-lookup"><span data-stu-id="fc353-105">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="fc353-106">Инструкции по использованию WCF с ASP.NET AJAX см. в разделе [Создание служб WCF для ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="fc353-106">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="fc353-107">Создание службы WCF AJAX состоит из трех частей:</span><span class="sxs-lookup"><span data-stu-id="fc353-107">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="fc353-108">Создание конечной точки AJAX, доступ к которой можно получить из браузера.</span><span class="sxs-lookup"><span data-stu-id="fc353-108">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="fc353-109">Создание контракта службы, совместимого с технологией AJAX.</span><span class="sxs-lookup"><span data-stu-id="fc353-109">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="fc353-110">Доступ к службам AJAX WCF.</span><span class="sxs-lookup"><span data-stu-id="fc353-110">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="fc353-111">Создание конечной точки AJAX</span><span class="sxs-lookup"><span data-stu-id="fc353-111">Creating an AJAX Endpoint</span></span>  

 <span data-ttu-id="fc353-112">Самый простой способ включить поддержку AJAX в службе WCF — использовать <xref:System.ServiceModel.Activation.WebServiceHostFactory> в SVC-файле, связанном со службой, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="fc353-112">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="fc353-113">Также для добавления конечной точки AJAX можно использовать конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="fc353-113">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="fc353-114">Используйте <xref:System.ServiceModel.WebHttpBinding> в конечной точке службы и настройте эту конечную точку с помощью <xref:System.ServiceModel.Description.WebHttpBehavior>, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="fc353-114">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fc353-115">Рабочий пример см. в разделе [Служба AJAX с JSON и XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fc353-115">For a working example, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="fc353-116">Создание контракта службы, совместимого с технологией AJAX</span><span class="sxs-lookup"><span data-stu-id="fc353-116">Creating an AJAX-Compatible Service Contract</span></span>  

 <span data-ttu-id="fc353-117">По умолчанию контракты служб, предоставляемые через конечную точку AJAX, возвращают данные в формате XML.</span><span class="sxs-lookup"><span data-stu-id="fc353-117">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="fc353-118">Кроме того, по умолчанию доступ к операциям службы предоставляется через HTTP-запросы POST, поступающие в URL-адреса, содержащие адрес конечной точки, после которого следует имя операции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="fc353-118">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="fc353-119">Эта операция доступна с помощью HTTP POST `http://serviceaddress/endpointaddress/GetCities` и возврата сообщения XML.</span><span class="sxs-lookup"><span data-stu-id="fc353-119">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="fc353-120">Можно использовать полную модель веб-программирования, чтобы настроить эти основные аспекты.</span><span class="sxs-lookup"><span data-stu-id="fc353-120">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="fc353-121">Например, можно использовать атрибут <xref:System.ServiceModel.Web.WebGetAttribute> или атрибут <xref:System.ServiceModel.Web.WebInvokeAttribute> для управления HTTP-командой, на которую отвечает операция, или использовать свойство `UriTemplate` этих соответствующих атрибутов для указания пользовательских универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="fc353-121">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="fc353-122">Дополнительные сведения см. в разделе [модель программирования WCF Web HTTP](wcf-web-http-programming-model.md) .</span><span class="sxs-lookup"><span data-stu-id="fc353-122">For more information, see the [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="fc353-123">В службах AJAX часто используется формат данных JSON.</span><span class="sxs-lookup"><span data-stu-id="fc353-123">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="fc353-124">Чтобы создать операцию, возвращающую JSON вместо XML, присвойте свойству <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (или свойству <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) значение <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="fc353-124">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="fc353-125">В разделе [автономной СЕРИАЛИЗАЦИИ JSON](stand-alone-json-serialization.md) показано, как встроенные типы .NET и типы контрактов данных сопоставляются с JSON.</span><span class="sxs-lookup"><span data-stu-id="fc353-125">The [Stand-Alone JSON Serialization](stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="fc353-126">Обычно запросы и ответы JSON состоят из одного элемента.</span><span class="sxs-lookup"><span data-stu-id="fc353-126">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="fc353-127">Для предыдущей операции `GetCities` запрос выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fc353-127">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="fc353-128">Ответ на этот запрос выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="fc353-128">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="fc353-129">Если операция принимает дополнительный параметр, стиль запроса необходимо поместить в оболочку, чтобы заключить в оболочку оба параметра в одном объекте JSON.</span><span class="sxs-lookup"><span data-stu-id="fc353-129">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="fc353-130">Ниже приводится пример такого стиля сообщения JSON.</span><span class="sxs-lookup"><span data-stu-id="fc353-130">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="fc353-131">Следующий контракт принимает это сообщение.</span><span class="sxs-lookup"><span data-stu-id="fc353-131">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="fc353-132">Доступ к службам AJAX</span><span class="sxs-lookup"><span data-stu-id="fc353-132">Accessing AJAX Services</span></span>  

 <span data-ttu-id="fc353-133">Конечные точки AJAX WCF всегда принимают запросы JSON и XML.</span><span class="sxs-lookup"><span data-stu-id="fc353-133">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="fc353-134">Запросы HTTP POST с типом содержимого "Application/JSON" рассматриваются как JSON, а те, которые имеют тип содержимого, указывающий на XML (например, "Text/XML"), обрабатываются как XML.</span><span class="sxs-lookup"><span data-stu-id="fc353-134">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="fc353-135">HTTP-запросы GET содержат все параметры запросов в самом URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="fc353-135">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="fc353-136">Пользователь определяет, как создавать HTTP-запрос в конечную точку.</span><span class="sxs-lookup"><span data-stu-id="fc353-136">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="fc353-137">Кроме того, пользователь имеет полный контроль над созданием JSON, формирующим тело запроса.</span><span class="sxs-lookup"><span data-stu-id="fc353-137">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="fc353-138">Пример создания запроса из JavaScript см. в разделе [Служба AJAX с JSON и XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fc353-138">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>
