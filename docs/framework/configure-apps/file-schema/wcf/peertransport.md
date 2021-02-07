---
description: 'Дополнительные сведения: <peerTransport>'
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: babc4196c63d46b7515ac67812d5d584eb3ffcac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683623"
---
# \<peerTransport>

<span data-ttu-id="c428c-102">Определяет одноранговый транспорт для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="c428c-102">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="c428c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c428c-103">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c428c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c428c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c428c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c428c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c428c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c428c-106">Attributes</span></span>  
  
|<span data-ttu-id="c428c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c428c-107">Attribute</span></span>|<span data-ttu-id="c428c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c428c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c428c-109">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="c428c-109">listenIpAddress</span></span>|<span data-ttu-id="c428c-110">Строка, указывающая IP-адрес, на котором одноранговый узел будет ожидать TCP-сообщения.</span><span class="sxs-lookup"><span data-stu-id="c428c-110">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="c428c-111">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="c428c-111">The default is `null`.</span></span>|  
|<span data-ttu-id="c428c-112">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c428c-112">maxBufferPoolSize</span></span>|<span data-ttu-id="c428c-113">Положительное целое число, указывающее максимальный размер буферного пула.</span><span class="sxs-lookup"><span data-stu-id="c428c-113">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="c428c-114">Значение по умолчанию — 524288.</span><span class="sxs-lookup"><span data-stu-id="c428c-114">The default is 524288.</span></span><br /><br /> <span data-ttu-id="c428c-115">Многие элементы WCF используют буферы.</span><span class="sxs-lookup"><span data-stu-id="c428c-115">Many parts of WCF use buffers.</span></span> <span data-ttu-id="c428c-116">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c428c-116">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c428c-117">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="c428c-117">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c428c-118">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="c428c-118">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="c428c-119">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c428c-119">maxReceivedMessageSize</span></span>|<span data-ttu-id="c428c-120">Положительное целое число, определяющее максимальный размер сообщения (в байтах), включая заголовки.</span><span class="sxs-lookup"><span data-stu-id="c428c-120">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="c428c-121">Отправитель сообщения получает ошибку протокола SOAP, когда размер сообщения оказывается слишком большим для получателя.</span><span class="sxs-lookup"><span data-stu-id="c428c-121">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="c428c-122">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="c428c-122">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c428c-123">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="c428c-123">The default is 65536.</span></span>|  
|<span data-ttu-id="c428c-124">порт</span><span class="sxs-lookup"><span data-stu-id="c428c-124">port</span></span>|<span data-ttu-id="c428c-125">Целое число, задающее порт сетевого интерфейса, на котором эта привязка будет обрабатывать TCP-сообщения однорангового канала.</span><span class="sxs-lookup"><span data-stu-id="c428c-125">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="c428c-126">Это значение должно принадлежать диапазону от <xref:System.Net.IPEndPoint.MinPort> до <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="c428c-126">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="c428c-127">Значение по умолчанию — 0.</span><span class="sxs-lookup"><span data-stu-id="c428c-127">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c428c-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c428c-128">Child Elements</span></span>  
  
|<span data-ttu-id="c428c-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="c428c-129">Element</span></span>|<span data-ttu-id="c428c-130">Описание</span><span class="sxs-lookup"><span data-stu-id="c428c-130">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="c428c-131">Определяет параметры безопасности для данного транспорта.</span><span class="sxs-lookup"><span data-stu-id="c428c-131">Defines the security settings for this transport.</span></span> <span data-ttu-id="c428c-132">Это элемент типа <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c428c-132">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c428c-133">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c428c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="c428c-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="c428c-134">Element</span></span>|<span data-ttu-id="c428c-135">Описание</span><span class="sxs-lookup"><span data-stu-id="c428c-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c428c-136">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="c428c-136">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c428c-137">Remarks</span><span class="sxs-lookup"><span data-stu-id="c428c-137">Remarks</span></span>  

 <span data-ttu-id="c428c-138">Данный транспорт нельзя использовать с контрактами, имеющими операции запроса-ответа.</span><span class="sxs-lookup"><span data-stu-id="c428c-138">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c428c-139">См. также</span><span class="sxs-lookup"><span data-stu-id="c428c-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c428c-140">Транспорты</span><span class="sxs-lookup"><span data-stu-id="c428c-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="c428c-141">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="c428c-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c428c-142">Привязки</span><span class="sxs-lookup"><span data-stu-id="c428c-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c428c-143">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="c428c-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c428c-144">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="c428c-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
