---
description: Дополнительные сведения см. в статье интеграция AJAX и поддержка JSON.
title: Интеграция с AJAX и поддержка JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 13e52a3013e9c04f57d6303caf18fd23a41ebf25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643895"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="61e55-103">Интеграция с AJAX и поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="61e55-103">AJAX Integration and JSON Support</span></span>

<span data-ttu-id="61e55-104">Поддержка Windows Communication Foundation (WCF) для асинхронных сценариев JavaScript и XML (AJAX) и формата данных нотация объектов JavaScript (JSON) позволяет службам WCF предоставлять операции клиентам AJAX.</span><span class="sxs-lookup"><span data-stu-id="61e55-104">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="61e55-105">Клиенты AJAX — это веб-страницы, выполняющие код JavaScript и обращающиеся к этим службам WCF с помощью HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="61e55-105">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="61e55-106">В этом разделе приведены сведения о такой поддержке и способах ее реализации.</span><span class="sxs-lookup"><span data-stu-id="61e55-106">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="61e55-107">Дополнительные сведения о ASP.NET AJAX и его интеграции с ASP.NET 2,0 см. в разделе [Общие сведения о ASP.NET AJAX](/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="61e55-107">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61e55-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="61e55-108">In This Section</span></span>  

 [<span data-ttu-id="61e55-109">Создание служб WCF для ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="61e55-109">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="61e55-110">Описывает, как служба WCF может быть предоставлена клиентам AJAX путем добавления соответствующей конечной точки AJAX либо с помощью настройки, либо с помощью фабрики узла службы, настроенной для создания узла службы, который автоматически настраивает конечную точку AJAX.</span><span class="sxs-lookup"><span data-stu-id="61e55-110">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="61e55-111">Создание служб WCF AJAX без использования ASP.NET</span><span class="sxs-lookup"><span data-stu-id="61e55-111">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="61e55-112">Описывает, как создать службу WCF без использования ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="61e55-112">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="61e55-113">Поддержка JSON и других форматов передачи данных</span><span class="sxs-lookup"><span data-stu-id="61e55-113">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="61e55-114">Описывается поддержка формата JSON, который обычно используется для обмена сообщениями со службами ASP.NET AJAX (вместо XML).</span><span class="sxs-lookup"><span data-stu-id="61e55-114">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="61e55-115">Практическое руководство. Миграция веб-служб ASP.NET с поддержкой AJAX на платформу WCF</span><span class="sxs-lookup"><span data-stu-id="61e55-115">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="61e55-116">Описывает, как перенести веб-службу ASP.NET с поддержкой AJAX в веб-службу WCF.</span><span class="sxs-lookup"><span data-stu-id="61e55-116">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e55-117">См. также</span><span class="sxs-lookup"><span data-stu-id="61e55-117">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="61e55-118">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="61e55-118">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
