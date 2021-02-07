---
description: 'Дополнительные сведения: JSONP'
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 83236f3d40a9dfeaf2ab0e521a227fb6dfc461f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726342"
---
# <a name="jsonp"></a><span data-ttu-id="1b76a-103">JSONP</span><span class="sxs-lookup"><span data-stu-id="1b76a-103">JSONP</span></span>

<span data-ttu-id="1b76a-104">В этом образце показано, как обеспечить поддержку JSONP(JSON with Padding) в службах WCF REST.</span><span class="sxs-lookup"><span data-stu-id="1b76a-104">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="1b76a-105">JSONP является правилом, используемым для вызова скриптов между доменами путем создания тегов скриптов в текущем документе.</span><span class="sxs-lookup"><span data-stu-id="1b76a-105">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="1b76a-106">Результат возвращается в заданной функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="1b76a-106">The result is returned in a specified callback function.</span></span> <span data-ttu-id="1b76a-107">JSONP основан на идее того, что теги, такие как, `<script src="http://..." >` могут оценивать сценарии из любого домена, а скрипт, полученный этими тегами, вычисляется в области, в которой уже могут быть определены другие функции.</span><span class="sxs-lookup"><span data-stu-id="1b76a-107">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1b76a-108">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="1b76a-108">Demonstrates</span></span>

 <span data-ttu-id="1b76a-109">Междоменная работа со скриптами с JSONP.</span><span class="sxs-lookup"><span data-stu-id="1b76a-109">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="1b76a-110">Разговор</span><span class="sxs-lookup"><span data-stu-id="1b76a-110">Discussion</span></span>

 <span data-ttu-id="1b76a-111">В образец входит веб-страница, которая динамически добавляет блок скрипта после отображения страницы в веб-браузере.</span><span class="sxs-lookup"><span data-stu-id="1b76a-111">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="1b76a-112">В этом блоке скрипта вызывается служба WCF REST, содержащая одну операцию `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="1b76a-112">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="1b76a-113">Служба WCF REST возвращает имя и адрес клиента, заключенные в оболочку функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="1b76a-113">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="1b76a-114">Когда служба WCF REST отправляет ответ, вызывается функция обратного вызова на веб-странице с данными о клиенте, и функция обратного вызова выводит эти данные на веб-странице.</span><span class="sxs-lookup"><span data-stu-id="1b76a-114">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="1b76a-115">Вставка тега скрипта и выполнение функции обратного вызова автоматически обрабатываются элементом управления ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="1b76a-115">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="1b76a-116">Схема использования та же, что и для всех прокси ASP.NET AJAX, плюс добавляется строка для включения JSONP, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="1b76a-116">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="1b76a-117">Веб-страница может вызывать службу WCF REST, поскольку эта служба использует объект <xref:System.ServiceModel.Description.WebScriptEndpoint>, где свойство `crossDomainScriptAccessEnabled` установлено в значении `true`.</span><span class="sxs-lookup"><span data-stu-id="1b76a-117">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="1b76a-118">Обе эти конфигурации выполняются в файле Web.config в \<system.serviceModel> элементе.</span><span class="sxs-lookup"><span data-stu-id="1b76a-118">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="1b76a-119">ScriptManager управляет взаимодействием со службой и устраняет сложности реализации доступа JSONP вручную.</span><span class="sxs-lookup"><span data-stu-id="1b76a-119">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="1b76a-120">Если параметр `crossDomainScriptAccessEnabled` имеет значение `true` и формат ответа для операции — JSON, инфраструктура WCF проверяет URI запроса на наличие параметра строки запроса обратного вызова и заключает ответ JSON в значение параметра строки запроса обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="1b76a-120">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="1b76a-121">В образце веб-страница вызывает службу WCF REST со следующим URI.</span><span class="sxs-lookup"><span data-stu-id="1b76a-121">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="1b76a-122">Поскольку строковый параметр запроса обратного вызова имеет значение `JsonPCallback`, служба WCF возвращает ответ JSONP, показанный в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="1b76a-122">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="1b76a-123">Этот ответ JSONP содержит данные о клиенте в формате JSON, заключенные в имя функции обратного вызова, запрошенной веб-страницей.</span><span class="sxs-lookup"><span data-stu-id="1b76a-123">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="1b76a-124">ScriptManager будет выполнять этот обратный вызов, используя тег скрипта для междоменного запроса, а затем передаст результат в обработчик onSuccess, который передан в операцию GetCustomer прокси ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="1b76a-124">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="1b76a-125">Пример состоит из двух веб-приложений ASP.NET: один содержит только службу WCF, а другой — веб-страницу. aspx, которая вызывает службу.</span><span class="sxs-lookup"><span data-stu-id="1b76a-125">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="1b76a-126">При запуске решения Visual Studio 2012 будет размещать два веб-сайта на разных портах, что создает среду, в которой служба и клиент находятся в разных доменах.</span><span class="sxs-lookup"><span data-stu-id="1b76a-126">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b76a-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1b76a-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1b76a-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1b76a-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1b76a-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1b76a-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b76a-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1b76a-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="1b76a-131">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="1b76a-131">To run the sample</span></span>  
  
1. <span data-ttu-id="1b76a-132">Откройте решение для образца JSONP.</span><span class="sxs-lookup"><span data-stu-id="1b76a-132">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="1b76a-133">Нажмите клавишу F5 для запуска `http://localhost:26648/JSONPClientPage.aspx` в браузере.</span><span class="sxs-lookup"><span data-stu-id="1b76a-133">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="1b76a-134">Обратите внимание, что после загрузки страницы входные текстовые значения "Name" и "Address" заполняются значениями.</span><span class="sxs-lookup"><span data-stu-id="1b76a-134">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="1b76a-135">Эти значения были предоставлены из вызова службы WCF после того, как браузер завершил отрисовку страницы.</span><span class="sxs-lookup"><span data-stu-id="1b76a-135">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
