---
description: 'Дополнительные сведения: <namedPipeTransport>'
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 68714404492be92ce789dbde95a39199f5de16d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684104"
---
# \<namedPipeTransport>

<span data-ttu-id="8e048-102">Задает транспорт, принуждающий канал передавать сообщения с использованием именованных каналов, когда он включается в пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="8e048-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="8e048-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e048-103">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e048-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8e048-104">Attributes and Elements</span></span>  

<span data-ttu-id="8e048-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8e048-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e048-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8e048-106">Attributes</span></span>  

<span data-ttu-id="8e048-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8e048-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e048-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8e048-108">Child Elements</span></span>  
  
|<span data-ttu-id="8e048-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="8e048-109">Element</span></span>|<span data-ttu-id="8e048-110">Описание</span><span class="sxs-lookup"><span data-stu-id="8e048-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e048-111">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8e048-111">ChannelInitializationTimeout</span></span>|<span data-ttu-id="8e048-112">Получает или задает <xref:System.TimeSpan>, определяющий максимальное время, в течение которого канал может находиться в состоянии инициализации перед отключением.</span><span class="sxs-lookup"><span data-stu-id="8e048-112">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="8e048-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8e048-113">ConnectionBufferSize</span></span>|<span data-ttu-id="8e048-114">Возвращает или задает размер буфера, используемого для передачи фрагмента сериализованного сообщения от клиента серверу по сети.</span><span class="sxs-lookup"><span data-stu-id="8e048-114">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="8e048-115">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="8e048-115">hostNameComparisonMode</span></span>|<span data-ttu-id="8e048-116">Возвращает или задает значение, указывающее, используется ли имя узла для доступа к службе при сопоставлении по универсальному коду ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="8e048-116">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="8e048-117">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="8e048-117">manualAddressing</span></span>|<span data-ttu-id="8e048-118">Возвращает или задает значение, показывающее, требуется ли создание адреса сообщения вручную.</span><span class="sxs-lookup"><span data-stu-id="8e048-118">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="8e048-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8e048-119">maxBufferPoolSize</span></span>|<span data-ttu-id="8e048-120">Получает или задает максимальный размер (в байтах) буферных пулов, используемых транспортом.</span><span class="sxs-lookup"><span data-stu-id="8e048-120">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="8e048-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8e048-121">maxBufferSize</span></span>|<span data-ttu-id="8e048-122">Возвращает или задает максимальный размер используемого буфера.</span><span class="sxs-lookup"><span data-stu-id="8e048-122">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="8e048-123">Для потоковых сообщений это значение не должно быть меньше максимального возможного размера заголовков сообщения, считываемых в режиме буферизации.</span><span class="sxs-lookup"><span data-stu-id="8e048-123">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="8e048-124">максаутпутделай</span><span class="sxs-lookup"><span data-stu-id="8e048-124">maxOutputDelay</span></span>|<span data-ttu-id="8e048-125">Возвращает или задает максимальный промежуток времени, в течение которого фрагмент сообщения или все сообщение может оставаться в буфере перед отправкой.</span><span class="sxs-lookup"><span data-stu-id="8e048-125">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="8e048-126">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8e048-126">maxPendingAccepts</span></span>|<span data-ttu-id="8e048-127">Получает или задает максимальное количество у службы каналов, ожидающих на прослушивателе для обработки входящих подключений к службе.</span><span class="sxs-lookup"><span data-stu-id="8e048-127">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="8e048-128">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8e048-128">maxPendingConnections</span></span>|<span data-ttu-id="8e048-129">Возвращает или задает максимальное число подключений, ожидающих распределения в службе.</span><span class="sxs-lookup"><span data-stu-id="8e048-129">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="8e048-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8e048-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="8e048-131">Возвращает и задает максимально допустимый размер сообщения (в байтах), который может быть получен.</span><span class="sxs-lookup"><span data-stu-id="8e048-131">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="8e048-132">transferMode</span><span class="sxs-lookup"><span data-stu-id="8e048-132">transferMode</span></span>|<span data-ttu-id="8e048-133">Возвращает или задает значение, указывающее, следует ли помещать сообщения в буфер или передавать их потоком с использованием транспорта, ориентированного на подключение.</span><span class="sxs-lookup"><span data-stu-id="8e048-133">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="8e048-134">\<connectionPoolSettings> из \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="8e048-134">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="8e048-135">Задает дополнительные параметры пула подключений для привязки именованного канала.</span><span class="sxs-lookup"><span data-stu-id="8e048-135">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e048-136">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8e048-136">Parent Elements</span></span>  
  
|<span data-ttu-id="8e048-137">Элемент</span><span class="sxs-lookup"><span data-stu-id="8e048-137">Element</span></span>|<span data-ttu-id="8e048-138">Описание</span><span class="sxs-lookup"><span data-stu-id="8e048-138">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8e048-139">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="8e048-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e048-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="8e048-140">Remarks</span></span>  

<span data-ttu-id="8e048-141">Этот транспорт использует универсальные коды ресурсов (URI) вида net.pipe://hostname/path.</span><span class="sxs-lookup"><span data-stu-id="8e048-141">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="8e048-142">Другие элементы универсального кода ресурса (URI) не обязательны.</span><span class="sxs-lookup"><span data-stu-id="8e048-142">Other URI components are optional.</span></span>  
  
<span data-ttu-id="8e048-143">Элемент `namedPipeTransport` является отправной точкой для создания пользовательской привязки, реализующей именованные каналы транспорта HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8e048-143">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="8e048-144">Этот транспорт используется для взаимодействия служб WCF на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8e048-144">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e048-145">См. также</span><span class="sxs-lookup"><span data-stu-id="8e048-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8e048-146">Транспорты</span><span class="sxs-lookup"><span data-stu-id="8e048-146">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="8e048-147">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="8e048-147">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="8e048-148">Привязки</span><span class="sxs-lookup"><span data-stu-id="8e048-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8e048-149">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="8e048-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8e048-150">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="8e048-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
