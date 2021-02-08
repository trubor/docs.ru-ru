---
description: Дополнительные сведения см. в статье сериализация в JSON с помощью программирования на уровне сообщений.
title: Сериализация в Json с помощью программирования на уровне сообщений
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 715e44b0e2137197f5883e2327288555513f29cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793549"
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="1a48a-103">Сериализация в Json с помощью программирования на уровне сообщений</span><span class="sxs-lookup"><span data-stu-id="1a48a-103">Serializing in Json with Message Level Programming</span></span>

<span data-ttu-id="1a48a-104">WCF поддерживает сериализацию данных в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="1a48a-104">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="1a48a-105">В этом разделе описывается, как в WCF выполнить сериализацию типов с помощью <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1a48a-105">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="1a48a-106">Программирование типизированных сообщений</span><span class="sxs-lookup"><span data-stu-id="1a48a-106">Typed Message Programming</span></span>  

 <span data-ttu-id="1a48a-107"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> используется, когда к операции службы применяется атрибут <xref:System.ServiceModel.Web.WebGetAttribute> или атрибут <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1a48a-107">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="1a48a-108">Оба атрибута позволяют задать формат запроса `RequestFormat` и формат ответа `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="1a48a-108">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="1a48a-109">Для использования JSON в запросах и ответах.</span><span class="sxs-lookup"><span data-stu-id="1a48a-109">To use JSON for requests and responses.</span></span> <span data-ttu-id="1a48a-110">Задайте для обоих свойств значение `WebMessageFormat.Json` .</span><span class="sxs-lookup"><span data-stu-id="1a48a-110">set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="1a48a-111">Чтобы использовать JSON, необходимо использовать <xref:System.ServiceModel.WebHttpBinding> , который автоматически настраивает <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="1a48a-111">In order to use JSON, you must use the <xref:System.ServiceModel.WebHttpBinding>, which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="1a48a-112">Дополнительные сведения о сериализации WCF см. в разделе [сериализация и десериализация](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="1a48a-112">For more information about WCF serialization, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span> <span data-ttu-id="1a48a-113">Дополнительные сведения о JSON и WCF см. в разделе [служебная станция — введение в службы RESTful с помощью WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="1a48a-113">For more information about JSON and WCF, see [Service Station - An Introduction To RESTful Services With WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a48a-114">Для использования с JSON требуется привязка <xref:System.ServiceModel.WebHttpBinding> и поведение <xref:System.ServiceModel.Description.WebHttpBehavior>, которые не поддерживают связь по протоколу SOAP.</span><span class="sxs-lookup"><span data-stu-id="1a48a-114">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="1a48a-115">Службы, взаимодействующие с, <xref:System.ServiceModel.WebHttpBinding> не поддерживают предоставление метаданных службы, поэтому вы не сможете использовать функциональные возможности Visual Studio Добавление ссылки на службу или программу командной строки Svcutil для создания прокси на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="1a48a-115">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="1a48a-116">Дополнительные сведения о программном вызове служб, использующих <xref:System.ServiceModel.WebHttpBinding> , см. в разделе Использование [служб RESTFUL с WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="1a48a-116">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="1a48a-117">Программирование нетипизированных сообщений</span><span class="sxs-lookup"><span data-stu-id="1a48a-117">Untyped Message Programming</span></span>  

 <span data-ttu-id="1a48a-118">При работе напрямую с объектами нетипизированного сообщения следует явно задать свойства нетипизированного сообщения для его сериализации в виде JSON.</span><span class="sxs-lookup"><span data-stu-id="1a48a-118">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="1a48a-119">В следующем фрагменте кода показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="1a48a-119">The following code snippet shows how to do this.</span></span>  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a48a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="1a48a-120">See also</span></span>

- [<span data-ttu-id="1a48a-121">Интеграция с AJAX и поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="1a48a-121">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)
- [<span data-ttu-id="1a48a-122">Автономная сериализация JSON</span><span class="sxs-lookup"><span data-stu-id="1a48a-122">Stand-Alone JSON Serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="1a48a-123">Сериализация JSON</span><span class="sxs-lookup"><span data-stu-id="1a48a-123">JSON Serialization</span></span>](../samples/json-serialization.md)
