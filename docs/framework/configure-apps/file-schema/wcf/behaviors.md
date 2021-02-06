---
description: 'Дополнительные сведения: <behaviors>'
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639514"
---
# \<behaviors>

<span data-ttu-id="d2779-102">Данный элемент определяет две дочерние коллекции с именами `endpointBehaviors` и `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d2779-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d2779-103">Каждая коллекция определяет элементы поведений, используемые конечными точками и службами соответственно.</span><span class="sxs-lookup"><span data-stu-id="d2779-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="d2779-104">Каждый элемент поведения идентифицируется по уникальному атрибуту `name`.</span><span class="sxs-lookup"><span data-stu-id="d2779-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="d2779-105">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="d2779-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d2779-106">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2779-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="d2779-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2779-107">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2779-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d2779-108">Attributes and Elements</span></span>  

 <span data-ttu-id="d2779-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d2779-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2779-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d2779-110">Attributes</span></span>  

 <span data-ttu-id="d2779-111">None</span><span class="sxs-lookup"><span data-stu-id="d2779-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d2779-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d2779-112">Child Elements</span></span>  
  
|<span data-ttu-id="d2779-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="d2779-113">Element</span></span>|<span data-ttu-id="d2779-114">Описание</span><span class="sxs-lookup"><span data-stu-id="d2779-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="d2779-115">Данный раздел конфигурации представляет все типы поведения, определенные для конкретной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="d2779-115">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="d2779-116">В данном разделе конфигурации представлены все поведения, определенные для конкретной службы.</span><span class="sxs-lookup"><span data-stu-id="d2779-116">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2779-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d2779-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d2779-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="d2779-118">Element</span></span>|<span data-ttu-id="d2779-119">Описание</span><span class="sxs-lookup"><span data-stu-id="d2779-119">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="d2779-120">Корневой элемент всех элементов конфигурации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d2779-120">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2779-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2779-121">Remarks</span></span>  

 <span data-ttu-id="d2779-122">Элемент `<remove>` можно использовать для удаления определенного поведения из коллекции.</span><span class="sxs-lookup"><span data-stu-id="d2779-122">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="d2779-123">Для этого нужно просто указать имя удаляемого поведения в атрибуте `name` элемента `<remove>`.</span><span class="sxs-lookup"><span data-stu-id="d2779-123">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="d2779-124">Также можно использовать элемент `<clear>`, очищающий все содержимое коллекции, чтобы обеспечить запуск пустой коллекции.</span><span class="sxs-lookup"><span data-stu-id="d2779-124">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2779-125">См. также</span><span class="sxs-lookup"><span data-stu-id="d2779-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="d2779-126">Настройка и расширение среды выполнения с помощью поведений</span><span class="sxs-lookup"><span data-stu-id="d2779-126">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="d2779-127">Настройка поведений клиентов</span><span class="sxs-lookup"><span data-stu-id="d2779-127">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="d2779-128">Задание поведения клиента во время выполнения</span><span class="sxs-lookup"><span data-stu-id="d2779-128">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="d2779-129">Указание поведения службы во время выполнения</span><span class="sxs-lookup"><span data-stu-id="d2779-129">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="d2779-130">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="d2779-130">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
