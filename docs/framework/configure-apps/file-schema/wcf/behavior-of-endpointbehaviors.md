---
description: 'Дополнительные сведения <behavior> о: <endpointBehaviors>'
title: <behavior> из <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: a72bb69cce96d72cdc00d48546244bdcde20271f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802337"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="2793f-103">\<behavior> из \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="2793f-103">\<behavior> of \<endpointBehaviors></span></span>

<span data-ttu-id="2793f-104">Элемент `behavior` содержит коллекцию параметров поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="2793f-104">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="2793f-105">Каждое поведение индексируется по атрибуту `name`.</span><span class="sxs-lookup"><span data-stu-id="2793f-105">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="2793f-106">Конечные точки могут ссылаться на каждое поведение по этому имени.</span><span class="sxs-lookup"><span data-stu-id="2793f-106">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="2793f-107">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="2793f-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2793f-108">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2793f-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="2793f-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2793f-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2793f-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2793f-110">Attributes and Elements</span></span>  

 <span data-ttu-id="2793f-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2793f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2793f-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2793f-112">Attributes</span></span>  
  
|<span data-ttu-id="2793f-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2793f-113">Attribute</span></span>|<span data-ttu-id="2793f-114">Описание</span><span class="sxs-lookup"><span data-stu-id="2793f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2793f-115">name</span><span class="sxs-lookup"><span data-stu-id="2793f-115">name</span></span>|<span data-ttu-id="2793f-116">Уникальная строка, содержащая имя конфигурации поведения.</span><span class="sxs-lookup"><span data-stu-id="2793f-116">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="2793f-117">Это значение является заданной пользователем строкой, которая должна быть уникальной, поскольку она действует как строка идентификации для элемента.</span><span class="sxs-lookup"><span data-stu-id="2793f-117">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="2793f-118">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="2793f-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2793f-119">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2793f-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2793f-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2793f-120">Child Elements</span></span>  
  
|<span data-ttu-id="2793f-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="2793f-121">Element</span></span>|<span data-ttu-id="2793f-122">Описание</span><span class="sxs-lookup"><span data-stu-id="2793f-122">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="2793f-123">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="2793f-123">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="2793f-124">Указывает отладку службы для объекта обратного вызова Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2793f-124">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="2793f-125">Задает время ожидания для обратного вызова клиента.</span><span class="sxs-lookup"><span data-stu-id="2793f-125">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="2793f-126">Задает маршрут, по которому должно быть передано сообщение.</span><span class="sxs-lookup"><span data-stu-id="2793f-126">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="2793f-127">Содержит данные конфигурации для DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="2793f-127">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="2793f-128">Указывает поведение конечной точки, которое позволяет службе отправлять ответы в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="2793f-128">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="2793f-129">Включает поведение конечной точки, позволяющее использовать службу с веб-страниц ASP.NET с поддержкой технологии AJAX.</span><span class="sxs-lookup"><span data-stu-id="2793f-129">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="2793f-130">Поведение следует использовать только в сочетании со \<webHttpBinding> стандартной привязкой или с \<webMessageEncoding> элементом Binding.</span><span class="sxs-lookup"><span data-stu-id="2793f-130">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="2793f-131">Указывает различные параметры обнаружения для конечной точки, такие как возможность обнаружения, области и любые пользовательские модули для ее метаданных.</span><span class="sxs-lookup"><span data-stu-id="2793f-131">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="2793f-132">Определяет поведение конечной точки клиента, используемое для маршалинга сообщений между различными типами привязок и версиями сообщения.</span><span class="sxs-lookup"><span data-stu-id="2793f-132">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="2793f-133">Задает поведение времени выполнения для получения сообщений в службе или клиентском приложении.</span><span class="sxs-lookup"><span data-stu-id="2793f-133">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="2793f-134">Он не имеет атрибутов или дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="2793f-134">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="2793f-135">Указывает, поддерживается ли объединение транзакций для операций получения.</span><span class="sxs-lookup"><span data-stu-id="2793f-135">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="2793f-136">Задает WebHttpBehavior в конечной точке посредством настройки конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2793f-136">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="2793f-137">Такое поведение при использовании в сочетании со \<webHttpBinding> стандартной привязкой включает в себя модель веб-программирования для службы WCF.</span><span class="sxs-lookup"><span data-stu-id="2793f-137">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2793f-138">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2793f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2793f-139">Элемент</span><span class="sxs-lookup"><span data-stu-id="2793f-139">Element</span></span>|<span data-ttu-id="2793f-140">Описание</span><span class="sxs-lookup"><span data-stu-id="2793f-140">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="2793f-141">Коллекция элементов поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="2793f-141">A collection of endpoint behavior elements.</span></span>|
