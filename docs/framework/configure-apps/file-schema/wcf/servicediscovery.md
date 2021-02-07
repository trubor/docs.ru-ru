---
description: 'Дополнительные сведения: <serviceDiscovery>'
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: d6df5b8d51763429829c2ea3c2593003720b7179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682856"
---
# \<serviceDiscovery>

<span data-ttu-id="d9732-102">Указывает возможность обнаружения конечных точек службы.</span><span class="sxs-lookup"><span data-stu-id="d9732-102">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="d9732-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9732-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9732-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d9732-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d9732-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d9732-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9732-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d9732-106">Attributes</span></span>  

 <span data-ttu-id="d9732-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d9732-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9732-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d9732-108">Child Elements</span></span>  
  
|<span data-ttu-id="d9732-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="d9732-109">Element</span></span>|<span data-ttu-id="d9732-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d9732-110">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="d9732-111">Коллекция конечных точек объявления.</span><span class="sxs-lookup"><span data-stu-id="d9732-111">A collection of announcement endpoints.</span></span> <span data-ttu-id="d9732-112">Используйте этот раздел, чтобы задать конечные точки, которые будут использоваться для отправки сообщений с объявлениями.</span><span class="sxs-lookup"><span data-stu-id="d9732-112">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="d9732-113">Коллекция конечных точек обнаружения.</span><span class="sxs-lookup"><span data-stu-id="d9732-113">A collection of discovery endpoints.</span></span> <span data-ttu-id="d9732-114">Используйте этот раздел, чтобы задать конечные точки, которые будут прослушиваться на предмет сообщений об обнаружении.</span><span class="sxs-lookup"><span data-stu-id="d9732-114">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9732-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d9732-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d9732-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="d9732-116">Element</span></span>|<span data-ttu-id="d9732-117">Описание</span><span class="sxs-lookup"><span data-stu-id="d9732-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d9732-118">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="d9732-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9732-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9732-119">Remarks</span></span>  

 <span data-ttu-id="d9732-120">При добавлении к конфигурации поведения службы этот элемент конфигурации делает все конечные точки этой службы обнаруживаемыми.</span><span class="sxs-lookup"><span data-stu-id="d9732-120">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="d9732-121">Можно дополнительно настроить функции обнаружения таких конечных точек с помощью [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) дочерних элементов или.</span><span class="sxs-lookup"><span data-stu-id="d9732-121">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="d9732-122">Используйте [\<announcementEndpoint>](announcementendpoint.md) раздел для настройки объявлений, указав конфигурацию конечной точки, которая будет использоваться для отправки объявлений службы (в сети, Hello и offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="d9732-122">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="d9732-123">Используйте [\<discoveryEndpoint>](discoveryendpoint.md) раздел, чтобы вручную указать конечную точку для прослушивания сообщений обнаружения.</span><span class="sxs-lookup"><span data-stu-id="d9732-123">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9732-124">Пример</span><span class="sxs-lookup"><span data-stu-id="d9732-124">Example</span></span>  

 <span data-ttu-id="d9732-125">В следующем примере конфигурации указано, что объект CalculatorService является обнаруживаемым. Дополнительно также указана конечная точка, используемая для объявления.</span><span class="sxs-lookup"><span data-stu-id="d9732-125">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="d9732-126">См. также</span><span class="sxs-lookup"><span data-stu-id="d9732-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
