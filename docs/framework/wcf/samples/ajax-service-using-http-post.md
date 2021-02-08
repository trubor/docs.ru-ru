---
description: 'Дополнительные сведения: служба AJAX с использованием HTTP POST'
title: Служба AJAX с использованием HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 4d319d4120310d79af5bda6026a2192d1270943b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779105"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="43843-103">Служба AJAX с использованием HTTP POST</span><span class="sxs-lookup"><span data-stu-id="43843-103">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="43843-104">В этом примере показано, как использовать Windows Communication Foundation (WCF) для создания асинхронной службы JavaScript и XML (AJAX) ASP.NET, использующей HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="43843-104">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="43843-105">Обращаться к службе AJAX можно с использованием кода JavaScript из клиента на основе веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="43843-105">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="43843-106">Этот пример основан на образце [базовой службы AJAX](basic-ajax-service.md) ; Единственное различие между двумя примерами — использование HTTP POST вместо HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="43843-106">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="43843-107">Поддержка AJAX в Windows Communication Foundation (WCF) оптимизирована для использования с ASP.NET AJAX через `ScriptManager` элемент управления.</span><span class="sxs-lookup"><span data-stu-id="43843-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="43843-108">Пример использования WCF с ASP.NET AJAX см. в разделе [примеры AJAX](ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="43843-108">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="43843-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="43843-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="43843-110">Служба в следующем примере представляет собой службу WCF без кода, зависящего от AJAX.</span><span class="sxs-lookup"><span data-stu-id="43843-110">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="43843-111">Если <xref:System.ServiceModel.Web.WebInvokeAttribute> атрибут применяется к операции или <xref:System.ServiceModel.Web.WebGetAttribute> атрибут не применяется, используется HTTP-команда по умолчанию (POST).</span><span class="sxs-lookup"><span data-stu-id="43843-111">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="43843-112">Запросы POST строить тяжелее, чем запросы GET, однако они не кэшируются; запросы POST следует использовать для всех операций, в которых нельзя использовать кэширование.</span><span class="sxs-lookup"><span data-stu-id="43843-112">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="43843-113">Создайте конечную точку AJAX в службе с помощью <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> точно так же, как в образце базовой службы AJAX.</span><span class="sxs-lookup"><span data-stu-id="43843-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="43843-114">В отличие от запросов GET вызывать службы POST из браузера нельзя.</span><span class="sxs-lookup"><span data-stu-id="43843-114">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="43843-115">Например, переход к `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` выдает ошибку, так как служба POST ожидает, что `n1` `n2` Параметры и будут отправлены в тексте сообщения в формате JSON, а не в URL-адресе.</span><span class="sxs-lookup"><span data-stu-id="43843-115">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="43843-116">Клиентская веб-страница PostAjaxClientPage.aspx содержит код ASP.NET для вызова службы, когда пользователь нажимает одну из кнопок операций на странице.</span><span class="sxs-lookup"><span data-stu-id="43843-116">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="43843-117">Служба реагирует так же, как и в образце [базовой службы AJAX](basic-ajax-service.md) , с запросом GET.</span><span class="sxs-lookup"><span data-stu-id="43843-117">The service responds in the same way as in the [Basic AJAX Service](basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43843-118">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="43843-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="43843-119">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="43843-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="43843-120">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="43843-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43843-121">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="43843-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43843-122">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="43843-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="43843-123">Убедитесь, что инструкции по установке выполняются [однократным образом для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43843-123">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="43843-124">Создайте решение Постажакссервице. sln, как описано в разделе [Создание примеров Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43843-124">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="43843-125">Перейдите к `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (не открывайте постажаксклиентпаже. aspx в браузере из каталога проекта).</span><span class="sxs-lookup"><span data-stu-id="43843-125">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
