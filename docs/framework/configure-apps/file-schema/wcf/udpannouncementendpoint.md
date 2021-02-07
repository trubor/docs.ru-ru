---
description: 'Дополнительные сведения: <udpAnnouncementEndpoint>'
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: f59e3e5365666835e910249e2cb37c2ce0e465e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749263"
---
# \<udpAnnouncementEndpoint>

<span data-ttu-id="f5152-102">Этот элемент конфигурации определяет стандартную конечную точку, используемую службами для отправки сообщений с объявлениями по привязке UDP.</span><span class="sxs-lookup"><span data-stu-id="f5152-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="f5152-103">Имеет фиксированный контракт и поддерживает две версии обнаружения.</span><span class="sxs-lookup"><span data-stu-id="f5152-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="f5152-104">Кроме того, она имеет фиксированную привязку UDP и значение адреса по умолчанию, как определено в спецификациях WS-Discovery (WS-Discovery от апреля 2005 или WS-Discovery версии 1.1).</span><span class="sxs-lookup"><span data-stu-id="f5152-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="f5152-105">Можно задать многопоточный адрес, который будет использовать для отправки и получения сообщений объявлений.</span><span class="sxs-lookup"><span data-stu-id="f5152-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="f5152-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5152-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5152-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f5152-107">Attributes and Elements</span></span>  

 <span data-ttu-id="f5152-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f5152-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5152-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f5152-109">Attributes</span></span>  
  
|<span data-ttu-id="f5152-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f5152-110">Attribute</span></span>|<span data-ttu-id="f5152-111">Описание</span><span class="sxs-lookup"><span data-stu-id="f5152-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5152-112">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f5152-112">discoveryVersion</span></span>|<span data-ttu-id="f5152-113">Строка, указывающая одну из двух версий протокола WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="f5152-113">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f5152-114">Допустимые значения: WSDiscovery11 и WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="f5152-114">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f5152-115">Это значение имеет тип <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="f5152-115">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="f5152-116">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="f5152-116">maxAnnouncementDelay</span></span>|<span data-ttu-id="f5152-117">Значение «Timespan», указывающее максимальную задержку, в течение которой протокол Discovery не будет отправлять сообщение Hello.</span><span class="sxs-lookup"><span data-stu-id="f5152-117">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="f5152-118">Перед отправкой сообщения ожидают произвольное время в диапазоне от 0 до значения этого атрибута.</span><span class="sxs-lookup"><span data-stu-id="f5152-118">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="f5152-119">Этот атрибут используется для назначения короткой произвольной задержки для предотвращения перегрузки сети, когда сеть становится недоступной, а все службы входят в сеть одновременно.</span><span class="sxs-lookup"><span data-stu-id="f5152-119">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="f5152-120">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="f5152-120">multicastAddress</span></span>|<span data-ttu-id="f5152-121">URI, в котором указывается адрес многоадресной рассылки, используемый для отправки и получения сообщений об обнаружении.</span><span class="sxs-lookup"><span data-stu-id="f5152-121">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="f5152-122">Значением по умолчанию является многопоточный адрес, который соответствует спецификации протокола.</span><span class="sxs-lookup"><span data-stu-id="f5152-122">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="f5152-123">name</span><span class="sxs-lookup"><span data-stu-id="f5152-123">name</span></span>|<span data-ttu-id="f5152-124">Строка, указывающая имя конфигурации стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="f5152-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f5152-125">Это имя используется в атрибуте `endpointConfiguration` конечной точки службы для связывания стандартной конечной точки с ее конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="f5152-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5152-126">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f5152-126">Child Elements</span></span>  
  
|<span data-ttu-id="f5152-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="f5152-127">Element</span></span>|<span data-ttu-id="f5152-128">Описание</span><span class="sxs-lookup"><span data-stu-id="f5152-128">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="f5152-129">Коллекция параметров, которые позволят настроить транспорт UDP для конечной точки UDP.</span><span class="sxs-lookup"><span data-stu-id="f5152-129">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5152-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f5152-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f5152-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="f5152-131">Element</span></span>|<span data-ttu-id="f5152-132">Описание</span><span class="sxs-lookup"><span data-stu-id="f5152-132">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="f5152-133">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="f5152-133">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5152-134">Пример</span><span class="sxs-lookup"><span data-stu-id="f5152-134">Example</span></span>  

 <span data-ttu-id="f5152-135">В следующем примере показано прослушивание клиентом сообщений с объявлением по многоадресному протоколу UDP с адресом многоадресной рассылки по умолчанию, а также с указанным адресом многоадресной рассылки UDP.</span><span class="sxs-lookup"><span data-stu-id="f5152-135">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="f5152-136">См. также</span><span class="sxs-lookup"><span data-stu-id="f5152-136">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
