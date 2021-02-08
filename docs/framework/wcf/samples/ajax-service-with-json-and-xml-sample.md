---
description: 'Дополнительные сведения: служба AJAX с примером JSON и XML'
title: Пример службы AJAX с JSON и XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e47f6cbd7e4659488325e158e5594ca94322c520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779066"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="17b6d-103">Пример службы AJAX с JSON и XML</span><span class="sxs-lookup"><span data-stu-id="17b6d-103">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="17b6d-104">В этом примере показано, как использовать Windows Communication Foundation (WCF) для создания асинхронной службы JavaScript и XML (AJAX), которая возвращает либо нотация объектов JavaScript (JSON), либо данные XML.</span><span class="sxs-lookup"><span data-stu-id="17b6d-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="17b6d-105">К службе AJAX можно обращаться с помощью кода JavaScript из веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="17b6d-105">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="17b6d-106">Этот пример основан на образце [базовой службы AJAX](basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="17b6d-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="17b6d-107">В отличие от других примеров AJAX, в данном примере не используется ASP.NET AJAX и управление <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="17b6d-107">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="17b6d-108">С некоторой дополнительной конфигурацией доступ к службам WCF AJAX можно получить с любой HTML-страницы через JavaScript. Этот сценарий показан здесь.</span><span class="sxs-lookup"><span data-stu-id="17b6d-108">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="17b6d-109">Пример использования WCF с ASP.NET AJAX см. в разделе [примеры AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="17b6d-109">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="17b6d-110">В данном разделе показано переключение типа отклика операции между JSON и XML.</span><span class="sxs-lookup"><span data-stu-id="17b6d-110">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="17b6d-111">Данная функциональность доступна независимо от того, настроена служба для доступа через клиентскую страницу ASP.NET AJAX или через HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="17b6d-111">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="17b6d-112">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="17b6d-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="17b6d-113">Чтобы разрешить использование клиентов, не являющихся клиентами ASP.NET AJAX, используйте <xref:System.ServiceModel.Activation.WebServiceHostFactory> (а не <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) в SVC-файле.</span><span class="sxs-lookup"><span data-stu-id="17b6d-113">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="17b6d-114">Объект <xref:System.ServiceModel.Activation.WebServiceHostFactory> добавляет стандартную конечную точку <xref:System.ServiceModel.Description.WebHttpEndpoint> в службу.</span><span class="sxs-lookup"><span data-stu-id="17b6d-114"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="17b6d-115">Конечная точка настраивается по пустому адресу относительно SVC-файла; Это означает, что адрес службы — `http://localhost/ServiceModelSamples/service.svc` , без дополнительных суффиксов, отличных от имени операции.</span><span class="sxs-lookup"><span data-stu-id="17b6d-115">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="17b6d-116">Следующий раздел в Web.config может использоваться для дополнительных изменений конфигурации конечной точки.</span><span class="sxs-lookup"><span data-stu-id="17b6d-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="17b6d-117">Если дополнительных изменений не требуется, он может быть удален.</span><span class="sxs-lookup"><span data-stu-id="17b6d-117">It can be removed if no extra changes are needed.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="17b6d-118">Формат данных по умолчанию для <xref:System.ServiceModel.Description.WebHttpEndpoint> XML, а формат данных по умолчанию для <xref:System.ServiceModel.Description.WebScriptEndpoint> — JSON.</span><span class="sxs-lookup"><span data-stu-id="17b6d-118">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="17b6d-119">Дополнительные сведения см. в разделе [Создание служб AJAX WCF без ASP.NET](../feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="17b6d-119">For more information, see [Creating WCF AJAX Services without ASP.NET](../feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="17b6d-120">Служба в следующем примере представляет собой стандартную службу WCF с двумя операциями.</span><span class="sxs-lookup"><span data-stu-id="17b6d-120">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="17b6d-121">Обе операции требуют использования основного стиля <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> в <xref:System.ServiceModel.Web.WebGetAttribute> или атрибутов <xref:System.ServiceModel.Web.WebInvokeAttribute>, которые относятся к поведению `webHttp` и не влияют на переключение формата данных JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="17b6d-121">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="17b6d-122">Формат ответа для операции указан как XML, что является значением по умолчанию для [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) поведения.</span><span class="sxs-lookup"><span data-stu-id="17b6d-122">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="17b6d-123">Тем не менее, рекомендуется явно указывать формат ответа.</span><span class="sxs-lookup"><span data-stu-id="17b6d-123">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="17b6d-124">Другая операция использует атрибут `WebInvokeAttribute` и явно указывает JSON вместо XML для ответа.</span><span class="sxs-lookup"><span data-stu-id="17b6d-124">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="17b6d-125">Обратите внимание, что в обоих случаях операции возвращают сложный тип, `MathResult` который является стандартным типом контракта данных WCF.</span><span class="sxs-lookup"><span data-stu-id="17b6d-125">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="17b6d-126">Веб-страница клиента XmlAjaxClientPage.htm содержит код JavaScript, который вызывает одну из двух предыдущих операций, когда пользователь нажимает на странице кнопку **выполнить вычисление (вернуть JSON)** или **выполнить вычисление (возврат XML)** .</span><span class="sxs-lookup"><span data-stu-id="17b6d-126">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="17b6d-127">Код, вызывающий службу, создает тело JSON и отправляет его с помощью HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="17b6d-127">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="17b6d-128">Запрос создается вручную в JavaScript, в отличие от примера [базовой службы AJAX](basic-ajax-service.md) и других примеров, использующих ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="17b6d-128">The request is created manually in JavaScript, unlike the [Basic AJAX Service](basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

<span data-ttu-id="17b6d-129">При ответе службы ответ отображается без какой-либо дополнительной обработки в текстовом поле страницы.</span><span class="sxs-lookup"><span data-stu-id="17b6d-129">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="17b6d-130">Это реализовано с целью демонстрации и дает возможность непосредственно ознакомиться с используемыми форматами данных XML и JSON.</span><span class="sxs-lookup"><span data-stu-id="17b6d-130">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="17b6d-131">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="17b6d-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="17b6d-132">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="17b6d-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="17b6d-133">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="17b6d-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17b6d-134">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="17b6d-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="17b6d-135">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="17b6d-135">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="17b6d-136">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="17b6d-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="17b6d-137">Создайте решение Ксмлажакссервице. sln, как описано в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="17b6d-137">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="17b6d-138">Перейдите к `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` разделу (не открывайте XmlAjaxClientPage.htm в браузере из каталога проекта).</span><span class="sxs-lookup"><span data-stu-id="17b6d-138">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="17b6d-139">См. также</span><span class="sxs-lookup"><span data-stu-id="17b6d-139">See also</span></span>

- [<span data-ttu-id="17b6d-140">Служба AJAX с использованием HTTP POST</span><span class="sxs-lookup"><span data-stu-id="17b6d-140">AJAX Service Using HTTP POST</span></span>](ajax-service-using-http-post.md)
