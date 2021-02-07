---
description: 'Дополнительные сведения: <udpDiscoveryEndpoint>'
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: 9863b4bc768b9c1cca933d001f0db596ce502fa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749237"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="1d9e2-102">Этот элемент конфигурации указывает стандартную конечную точку, которая стандартно используется для операций обнаружения через привязку для многоадресной рассылки UDP.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-102">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="1d9e2-103">Эта конечная точка имеет фиксированный контракт и поддерживает две версии протокола WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-103">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="1d9e2-104">Кроме того, она имеет фиксированную привязку UDP и значение адреса по умолчанию, как определено в спецификациях WS-Discovery (WS-Discovery от апреля 2005 или WS-Discovery версии 1.1).</span><span class="sxs-lookup"><span data-stu-id="1d9e2-104">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1d9e2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1d9e2-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d9e2-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1d9e2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1d9e2-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d9e2-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1d9e2-108">Attributes</span></span>  
  
|<span data-ttu-id="1d9e2-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1d9e2-109">Attribute</span></span>|<span data-ttu-id="1d9e2-110">Описание</span><span class="sxs-lookup"><span data-stu-id="1d9e2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d9e2-111">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="1d9e2-111">discoveryMode</span></span>|<span data-ttu-id="1d9e2-112">Строка, указывающая режим протокола обнаружения.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-112">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="1d9e2-113">Допустимые значения: "нерегламентированный" и "управляемый".</span><span class="sxs-lookup"><span data-stu-id="1d9e2-113">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="1d9e2-114">В управляемом режиме протокол использует прокси-сервер обнаружения, который выступает в качестве репозитория обнаруживаемых служб.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-114">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="1d9e2-115">Для режима Adhoc требуется, чтобы для поиска доступных служб протокол использовал многопоточный механизм UDP.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-115">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="1d9e2-116">Это значение имеет тип <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-116">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="1d9e2-117">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1d9e2-117">discoveryVersion</span></span>|<span data-ttu-id="1d9e2-118">Строка, указывающая одну из двух версий протокола WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-118">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1d9e2-119">Допустимые значения: WSDiscovery11 и WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-119">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1d9e2-120">Это значение имеет тип <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-120">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1d9e2-121">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="1d9e2-121">maxResponseDelay</span></span>|<span data-ttu-id="1d9e2-122">Значение «Timespan», указывающее максимальную задержку, в течение которой протокол Discovery будет ожидать перед отправкой определенных сообщений, например Probe Match или Resolve Match.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-122">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="1d9e2-123">Если все сообщения ProbeMatches будут отправлены одновременно, может возникнуть перегрузка сети.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-123">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="1d9e2-124">Для ее предотвращения сообщения ProbeMatch отправляются с произвольной задержкой между сообщениями.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-124">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="1d9e2-125">Произвольная задержка находится в диапазоне от 0 до значения, заданного этим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-125">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="1d9e2-126">Если этот атрибут имеет значение 0, сообщения ProbeMatch отправляются одно за другим без задержки.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-126">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="1d9e2-127">В противном случае сообщения ProbeMatch отправляются с определенной произвольной задержкой так, что общее время на отправку всех сообщений ProbeMatch не превышает значение maxResponseDelay.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-127">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="1d9e2-128">Это значение действительно только для служб и не используется клиентами.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-128">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="1d9e2-129">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="1d9e2-129">multicastAddress</span></span>|<span data-ttu-id="1d9e2-130">URI, в котором указывается адрес многоадресной рассылки, используемый для отправки и получения сообщений об обнаружении.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-130">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="1d9e2-131">Значением по умолчанию является многопоточный адрес, который соответствует спецификации протокола.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-131">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="1d9e2-132">Строка, указывающая имя конфигурации стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1d9e2-133">Это имя используется в атрибуте `endpointConfiguration` конечной точки службы для связывания стандартной конечной точки с ее конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d9e2-134">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1d9e2-134">Child Elements</span></span>  
  
|<span data-ttu-id="1d9e2-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="1d9e2-135">Element</span></span>|<span data-ttu-id="1d9e2-136">Описание</span><span class="sxs-lookup"><span data-stu-id="1d9e2-136">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="1d9e2-137">Коллекция параметров, которые позволят настроить транспорт UDP для конечной точки UDP.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-137">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d9e2-138">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1d9e2-138">Parent Elements</span></span>  
  
|<span data-ttu-id="1d9e2-139">Элемент</span><span class="sxs-lookup"><span data-stu-id="1d9e2-139">Element</span></span>|<span data-ttu-id="1d9e2-140">Описание</span><span class="sxs-lookup"><span data-stu-id="1d9e2-140">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1d9e2-141">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d9e2-142">Пример</span><span class="sxs-lookup"><span data-stu-id="1d9e2-142">Example</span></span>  

 <span data-ttu-id="1d9e2-143">В следующем примере показано прослушивание сообщений об обнаружении через многоадресный протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="1d9e2-143">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="1d9e2-144">См. также</span><span class="sxs-lookup"><span data-stu-id="1d9e2-144">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
