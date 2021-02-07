---
description: 'Дополнительные сведения: <webSocketSettings>'
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: a0b67a0088491c73ed0214191283ae5292a654b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682492"
---
# \<webSocketSettings>

<span data-ttu-id="ae68f-102">Элемент конфигурации, который служит для задания параметров веб-сокета.</span><span class="sxs-lookup"><span data-stu-id="ae68f-102">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="ae68f-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ae68f-103">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae68f-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ae68f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ae68f-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ae68f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae68f-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ae68f-106">Attributes</span></span>  
  
|<span data-ttu-id="ae68f-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ae68f-107">Attribute</span></span>|<span data-ttu-id="ae68f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ae68f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae68f-109">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="ae68f-109">createNotificationOnConnection</span></span>|<span data-ttu-id="ae68f-110">Определяет, следует ли отправлять уведомления при соединении.</span><span class="sxs-lookup"><span data-stu-id="ae68f-110">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="ae68f-111">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="ae68f-111">disablePayloadMasking</span></span>|<span data-ttu-id="ae68f-112">Определяет, отключено ли маскирование веб-сокета.</span><span class="sxs-lookup"><span data-stu-id="ae68f-112">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="ae68f-113">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="ae68f-113">keepAliveInterval</span></span>|<span data-ttu-id="ae68f-114">Определяет интервал поддержки активности канала.</span><span class="sxs-lookup"><span data-stu-id="ae68f-114">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="ae68f-115">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="ae68f-115">maxPendingConnections</span></span>|<span data-ttu-id="ae68f-116">Определяет максимальное число подключений, ожидающих распределения в службе.</span><span class="sxs-lookup"><span data-stu-id="ae68f-116">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="ae68f-117">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="ae68f-117">receiveBufferSize</span></span>|<span data-ttu-id="ae68f-118">Определяет размер буфера приема.</span><span class="sxs-lookup"><span data-stu-id="ae68f-118">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="ae68f-119">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="ae68f-119">sendBufferSize</span></span>|<span data-ttu-id="ae68f-120">Определяет размер буфера отправки.</span><span class="sxs-lookup"><span data-stu-id="ae68f-120">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="ae68f-121">subProtocol</span><span class="sxs-lookup"><span data-stu-id="ae68f-121">subProtocol</span></span>|<span data-ttu-id="ae68f-122">Определяет подпротокол веб-сокета.</span><span class="sxs-lookup"><span data-stu-id="ae68f-122">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="ae68f-123">transportUsage</span><span class="sxs-lookup"><span data-stu-id="ae68f-123">transportUsage</span></span>|<span data-ttu-id="ae68f-124">Указывает, когда использовать веб-сокеты.</span><span class="sxs-lookup"><span data-stu-id="ae68f-124">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="ae68f-125">Атрибут transportUsage</span><span class="sxs-lookup"><span data-stu-id="ae68f-125">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="ae68f-126">Значение</span><span class="sxs-lookup"><span data-stu-id="ae68f-126">Value</span></span>|<span data-ttu-id="ae68f-127">Описание</span><span class="sxs-lookup"><span data-stu-id="ae68f-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae68f-128">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="ae68f-128">WhenDuplex</span></span>|<span data-ttu-id="ae68f-129">Использовать протокол веб-сокета, если контракт является дуплексным.</span><span class="sxs-lookup"><span data-stu-id="ae68f-129">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="ae68f-130">Всегда</span><span class="sxs-lookup"><span data-stu-id="ae68f-130">Always</span></span>|<span data-ttu-id="ae68f-131">Всегда использовать протокол веб-сокетов независимо от контракта.</span><span class="sxs-lookup"><span data-stu-id="ae68f-131">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="ae68f-132">Никогда</span><span class="sxs-lookup"><span data-stu-id="ae68f-132">Never</span></span>|<span data-ttu-id="ae68f-133">Никогда не использовать протокол веб-сокетов.</span><span class="sxs-lookup"><span data-stu-id="ae68f-133">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae68f-134">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ae68f-134">Child Elements</span></span>  

 <span data-ttu-id="ae68f-135">None</span><span class="sxs-lookup"><span data-stu-id="ae68f-135">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae68f-136">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ae68f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ae68f-137">Элемент</span><span class="sxs-lookup"><span data-stu-id="ae68f-137">Element</span></span>|<span data-ttu-id="ae68f-138">Описание</span><span class="sxs-lookup"><span data-stu-id="ae68f-138">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="ae68f-139">Определяет привязку NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ae68f-139">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae68f-140">Пример</span><span class="sxs-lookup"><span data-stu-id="ae68f-140">Example</span></span>  

 <span data-ttu-id="ae68f-141">В следующем примере показано использование элемента \<webSocketSettings>.</span><span class="sxs-lookup"><span data-stu-id="ae68f-141">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="ae68f-142">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ae68f-142">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="ae68f-143">Привязки</span><span class="sxs-lookup"><span data-stu-id="ae68f-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ae68f-144">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="ae68f-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ae68f-145">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="ae68f-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
