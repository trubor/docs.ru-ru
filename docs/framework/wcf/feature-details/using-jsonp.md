---
description: 'Дополнительные сведения о: использование JSONP'
title: Использование средства JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: f4d21670cf468328b8579fa8a9cf2c2e06f09337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632195"
---
# <a name="using-jsonp"></a><span data-ttu-id="80f02-103">Использование средства JSONP</span><span class="sxs-lookup"><span data-stu-id="80f02-103">Using JSONP</span></span>

<span data-ttu-id="80f02-104">JSONP - это механизм, используемый для поддержки межсайтовых скриптов в веб-браузерах.</span><span class="sxs-lookup"><span data-stu-id="80f02-104">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="80f02-105">JSONP основан на возможности веб-браузеров загружать скрипты не с тех сайтов, с которых загружается исходный документ.</span><span class="sxs-lookup"><span data-stu-id="80f02-105">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="80f02-106">Этот механизм работает посредством дополнения полезных данных JSON именем определяемой пользователем функции обратного вызова, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="80f02-106">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="80f02-107">В предыдущем примере полезные данные JSON, `{"a" = \\"b\\"}`, помещены в вызов функции `callback`.</span><span class="sxs-lookup"><span data-stu-id="80f02-107">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="80f02-108">Функция обратного вызова должна быть уже определена на текущей веб-странице.</span><span class="sxs-lookup"><span data-stu-id="80f02-108">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="80f02-109">Тип содержимого ответа JSONP — `application/javascript` .</span><span class="sxs-lookup"><span data-stu-id="80f02-109">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="80f02-110">JSONP не включается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="80f02-110">JSONP is not automatically enabled.</span></span> <span data-ttu-id="80f02-111">Чтобы включить его, задайте для атрибута `javascriptCallbackEnabled` значение `true` в одной из стандартных конечных точек HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> или <xref:System.ServiceModel.Description.WebScriptEndpoint>), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="80f02-111">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="80f02-112">Имя функции обратного вызова может указываться в переменной запроса callback, как показано в следующем URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="80f02-112">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="80f02-113">При вызове служба отправляет ответ следующего вида.</span><span class="sxs-lookup"><span data-stu-id="80f02-113">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="80f02-114">Имя функции обратного вызова также можно указать с помощью применения атрибута <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> к классу службы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="80f02-114">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

<span data-ttu-id="80f02-115">Для показанной выше службы запрос выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="80f02-115">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="80f02-116">При вызове служба отправляет следующий ответ.</span><span class="sxs-lookup"><span data-stu-id="80f02-116">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="80f02-117">Коды состояния HTTP</span><span class="sxs-lookup"><span data-stu-id="80f02-117">HTTP Status Codes</span></span>

<span data-ttu-id="80f02-118">В ответах JSONP с кодом состояния HTTP, отличным от 200, содержится второй параметр - численное представление кода состояния HTTP, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="80f02-118">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="80f02-119">Проверки</span><span class="sxs-lookup"><span data-stu-id="80f02-119">Validations</span></span>

<span data-ttu-id="80f02-120">При включении JSONP выполняются следующие проверки.</span><span class="sxs-lookup"><span data-stu-id="80f02-120">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="80f02-121">Инфраструктура WCF формирует исключение, если `javascriptCallback` включен, указан параметр строки запроса обратного вызова, а формат ответа установлен в JSON.</span><span class="sxs-lookup"><span data-stu-id="80f02-121">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="80f02-122">Если запрос содержит параметр строки запроса обратного вызова, но выполняется не операция HTTP GET, параметр обратного вызова не учитывается.</span><span class="sxs-lookup"><span data-stu-id="80f02-122">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="80f02-123">Если имя обратного вызова равно `null` или пустой строке, то ответ не приводится к формату JSONP.</span><span class="sxs-lookup"><span data-stu-id="80f02-123">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="80f02-124">См. также</span><span class="sxs-lookup"><span data-stu-id="80f02-124">See also</span></span>

- [<span data-ttu-id="80f02-125">Общие сведения о модели программирования WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="80f02-125">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
