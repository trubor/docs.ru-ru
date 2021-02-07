---
description: 'Дополнительные сведения: <sendMessageChannelCache>'
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: 2c77372bb44df74a1d2186500367c5164e1e5042
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739785"
---
# \<sendMessageChannelCache>

<span data-ttu-id="4cbdc-102">Поведение службы, которое позволяет изменить уровни доступа к кэшу, параметры кэша фабрики канала и параметры кэша канала для рабочих процессов, которые отправляют сообщения в конечные точки служб с использованием действий отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**  
  
## <a name="syntax"></a><span data-ttu-id="4cbdc-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4cbdc-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cbdc-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4cbdc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4cbdc-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cbdc-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4cbdc-106">Attributes</span></span>  
  
|<span data-ttu-id="4cbdc-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4cbdc-107">Attribute</span></span>|<span data-ttu-id="4cbdc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4cbdc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4cbdc-109">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="4cbdc-109">allowUnsafeCaching</span></span>|<span data-ttu-id="4cbdc-110">Логическое значение, указывающее, следует ли включить кэширование.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-110">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="4cbdc-111">Если служба рабочего процесса имеет пользовательские привязки или поведения, то кэширование может оказаться небезопасным (и будет отключено по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4cbdc-111">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="4cbdc-112">Однако если вы хотите включить кэширование, присвойте этому свойству значение **true**.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-112">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cbdc-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4cbdc-113">Child Elements</span></span>  
  
|<span data-ttu-id="4cbdc-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="4cbdc-114">Element</span></span>|<span data-ttu-id="4cbdc-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4cbdc-115">Description</span></span>|  
|-------------|-----------------|  
|[\<channelSettings>](channelsettings.md)|<span data-ttu-id="4cbdc-116">Указывает параметры кэша канала.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-116">Specifies the settings of the channel cache.</span></span>|  
|[\<factorySettings>](factorysettings.md)|<span data-ttu-id="4cbdc-117">Указывает параметры кэша фабрики канала.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-117">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4cbdc-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4cbdc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4cbdc-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="4cbdc-119">Element</span></span>|<span data-ttu-id="4cbdc-120">Описание</span><span class="sxs-lookup"><span data-stu-id="4cbdc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cbdc-121">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4cbdc-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4cbdc-122">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cbdc-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="4cbdc-123">Remarks</span></span>  

 <span data-ttu-id="4cbdc-124">Это поведение службы предназначено для рабочих процессов, отправляющих сообщения в конечные точки служб.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-124">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="4cbdc-125">Эти рабочие процессы обычно являются клиентскими, но также могут быть службами рабочих процессов, размещенными в <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-125">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="4cbdc-126">По умолчанию в рабочем процессе, размещенном в <xref:System.ServiceModel.WorkflowServiceHost>, кэш, используемый действиями обмена сообщениями <xref:System.ServiceModel.Activities.Send>, совместно используется всеми экземплярами рабочих процессов в <xref:System.ServiceModel.WorkflowServiceHost> (кэширование уровня узла).</span><span class="sxs-lookup"><span data-stu-id="4cbdc-126">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="4cbdc-127">Для клиентского рабочего процесса, не размещенного в <xref:System.ServiceModel.WorkflowServiceHost>, кэш доступен только для экземпляра рабочего процесса (кэширование уровня экземпляра).</span><span class="sxs-lookup"><span data-stu-id="4cbdc-127">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="4cbdc-128">По умолчанию кэширование отключено для всех действий отправки в рабочем процессе, в конфигурации которого определены конечные точки.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-128">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="4cbdc-129">Дополнительные сведения о том, как изменить уровни общего доступа к кэшу по умолчанию и параметры кэша для фабрики каналов и кэша каналов, см. [в разделе изменение уровней общего доступа к кэшу для действий отправки](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="4cbdc-129">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cbdc-130">Пример</span><span class="sxs-lookup"><span data-stu-id="4cbdc-130">Example</span></span>  

 <span data-ttu-id="4cbdc-131">В размещенной службе рабочего процесса в файле конфигурации приложения можно указать параметры кэша фабрики и канала.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-131">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="4cbdc-132">Для этого необходимо создать поведение службы, содержащее параметры для кэша фабрики и канала, и добавить это поведение в службу.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-132">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="4cbdc-133">В следующем примере показано содержимое файла конфигурации, содержащего `MyChannelCacheBehavior`  поведение службы с настройками кэша настраиваемой фабрики и канала.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-133">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="4cbdc-134">Это поведение службы добавляется в службу с помощью `behaviorConfiguration` атрибута.</span><span class="sxs-lookup"><span data-stu-id="4cbdc-134">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cbdc-135">См. также</span><span class="sxs-lookup"><span data-stu-id="4cbdc-135">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="4cbdc-136">Изменение уровней совместного использования кэша для действий «Send»</span><span class="sxs-lookup"><span data-stu-id="4cbdc-136">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
