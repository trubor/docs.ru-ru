---
description: 'Дополнительные сведения <behavior> о: <serviceBehaviors>'
title: <behavior> из <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: e34254661026ad6dcb3429ad1b381cc3e6718f27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639540"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="95fc0-103">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="95fc0-103">\<behavior> of \<serviceBehaviors></span></span>

<span data-ttu-id="95fc0-104">Элемент `behavior` содержит коллекцию параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-104">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="95fc0-105">Каждое поведение индексируется по атрибуту `name`.</span><span class="sxs-lookup"><span data-stu-id="95fc0-105">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="95fc0-106">Службы могут ссылаться на каждое поведение с помощью этого имени, используя `behaviorConfiguration` атрибут [\<endpoint>](endpoint-element.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="95fc0-106">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="95fc0-107">Это позволяет конечным точкам иметь общие конфигурации поведений без переопределения параметров.</span><span class="sxs-lookup"><span data-stu-id="95fc0-107">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="95fc0-108">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="95fc0-108">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="95fc0-109">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="95fc0-109">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95fc0-110">Элементы поведения, относящиеся к действиям рабочего процесса Windows, таким как [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) элемент, описаны на [ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) странице.</span><span class="sxs-lookup"><span data-stu-id="95fc0-110">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="95fc0-111">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95fc0-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95fc0-112">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="95fc0-112">Attributes and Elements</span></span>  

 <span data-ttu-id="95fc0-113">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95fc0-114">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="95fc0-114">Attributes</span></span>  
  
|<span data-ttu-id="95fc0-115">Атрибут</span><span class="sxs-lookup"><span data-stu-id="95fc0-115">Attribute</span></span>|<span data-ttu-id="95fc0-116">Описание</span><span class="sxs-lookup"><span data-stu-id="95fc0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95fc0-117">name</span><span class="sxs-lookup"><span data-stu-id="95fc0-117">name</span></span>|<span data-ttu-id="95fc0-118">Уникальная строка, содержащая имя конфигурации поведения.</span><span class="sxs-lookup"><span data-stu-id="95fc0-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="95fc0-119">Это значение является заданной пользователем строкой, которая должна быть уникальной, поскольку она действует как строка идентификации для элемента.</span><span class="sxs-lookup"><span data-stu-id="95fc0-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="95fc0-120">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="95fc0-120">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="95fc0-121">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="95fc0-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95fc0-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="95fc0-122">Child Elements</span></span>  
  
|<span data-ttu-id="95fc0-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="95fc0-123">Element</span></span>|<span data-ttu-id="95fc0-124">Описание</span><span class="sxs-lookup"><span data-stu-id="95fc0-124">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="95fc0-125">Содержит данные конфигурации для DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="95fc0-125">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="95fc0-126">Задает тип используемой реализации поставщика сохраняемости, а также время ожидания операций сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="95fc0-126">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="95fc0-127">Обеспечивает доступ к службе маршрутизации во время выполнения, чтобы вносить динамические изменения в конфигурацию маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="95fc0-127">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="95fc0-128">Обеспечивает элемент конфигурации рабочего процесса, который устанавливает на уровне службы действительность передачи, сообщения или инициатора.</span><span class="sxs-lookup"><span data-stu-id="95fc0-128">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="95fc0-129">Задает параметры авторизации доступа к операциям службы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-129">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="95fc0-130">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="95fc0-130">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="95fc0-131">Указывает функции отладки и справочной информации для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95fc0-131">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="95fc0-132">Указывает возможность обнаружения конечных точек службы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-132">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="95fc0-133">Задает публикацию метаданных службы и связанных сведений.</span><span class="sxs-lookup"><span data-stu-id="95fc0-133">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="95fc0-134">Задает параметры, позволяющие проводить аудит событий безопасности во время обслуживания.</span><span class="sxs-lookup"><span data-stu-id="95fc0-134">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="95fc0-135">Указывает механизм регулирования службы WCF.</span><span class="sxs-lookup"><span data-stu-id="95fc0-135">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="95fc0-136">Задает время ожидания для службы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-136">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="95fc0-137">Задает параметры для экземпляра WorkflowRuntime для размещения служб WCF на основе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="95fc0-137">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="95fc0-138">Включает получение сведений об адресе метаданных из заголовков сообщений запросов.</span><span class="sxs-lookup"><span data-stu-id="95fc0-138">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95fc0-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="95fc0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="95fc0-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="95fc0-140">Element</span></span>|<span data-ttu-id="95fc0-141">Описание</span><span class="sxs-lookup"><span data-stu-id="95fc0-141">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="95fc0-142">Коллекция элементов поведений службы.</span><span class="sxs-lookup"><span data-stu-id="95fc0-142">A collection of service behavior elements.</span></span>|
