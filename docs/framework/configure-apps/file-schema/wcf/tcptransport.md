---
description: 'Дополнительные сведения: <tcpTransport>'
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: b660443ac58e8ed72d70adb5bf9e9e87b060e3af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786620"
---
# \<tcpTransport>

<span data-ttu-id="a7e98-102">Определяет транспорт TCP, который может использоваться каналом для передачи сообщений для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="a7e98-102">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="a7e98-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7e98-103">Syntax</span></span>  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
              connectionBufferSize="Integer"
              hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
              listenBacklog="Integer"
              manualAddressing="Boolean"
              maxBufferPoolSize="Integer"
              maxBufferSize="Integer"
              maxOutputDelay="TimeSpan"
              maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              maxReceivedMessageSize="Integer"
              portSharingEnabled="Boolean"
              teredoEnabled="Boolean"
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7e98-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a7e98-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a7e98-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a7e98-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7e98-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a7e98-106">Attributes</span></span>  
  
|<span data-ttu-id="a7e98-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a7e98-107">Attribute</span></span>|<span data-ttu-id="a7e98-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a7e98-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7e98-109">channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a7e98-109">channelInitializationTimeout</span></span>|<span data-ttu-id="a7e98-110">Возвращает или задает ограничение по времени для приема инициализации канала.</span><span class="sxs-lookup"><span data-stu-id="a7e98-110">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="a7e98-111">Максимальное время в секундах, в течение которого канал может находиться в состоянии инициализации, прежде чем будет отключен.</span><span class="sxs-lookup"><span data-stu-id="a7e98-111">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="a7e98-112">Эта квота включает в себя время, которое TCP-подключение может пройти для проверки подлинности с помощью протокола кадрирования сообщений .NET.</span><span class="sxs-lookup"><span data-stu-id="a7e98-112">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="a7e98-113">Клиенту необходимо отправить некоторые исходные данные, прежде чем сервер получит достаточно сведений для аутентификации.</span><span class="sxs-lookup"><span data-stu-id="a7e98-113">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="a7e98-114">По умолчанию это 30 секунд.</span><span class="sxs-lookup"><span data-stu-id="a7e98-114">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="a7e98-115">коннектионбуфферсизе</span><span class="sxs-lookup"><span data-stu-id="a7e98-115">connectionBufferSize</span></span>|<span data-ttu-id="a7e98-116">Возвращает или задает размер буфера, используемого для передачи фрагмента сериализованного сообщения от клиента серверу по сети.</span><span class="sxs-lookup"><span data-stu-id="a7e98-116">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="a7e98-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a7e98-117">hostNameComparisonMode</span></span>|<span data-ttu-id="a7e98-118">Возвращает или задает значение, указывающее, используется ли имя узла для доступа к службе при сопоставлении по универсальному коду ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="a7e98-118">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="a7e98-119">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="a7e98-119">listenBacklog</span></span>|<span data-ttu-id="a7e98-120">Максимальное количество запросов на соединение в очереди, которые могут ожидать обработки веб-службой.</span><span class="sxs-lookup"><span data-stu-id="a7e98-120">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="a7e98-121">Атрибут `connectionLeaseTimeout` ограничивает время ожидания подключения клиентом до создания исключения подключения.</span><span class="sxs-lookup"><span data-stu-id="a7e98-121">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="a7e98-122">Это свойство уровня сокетов, которое определяет максимальное количество запросов на подключение в очереди, которые могут ожидать обработки веб-службой.</span><span class="sxs-lookup"><span data-stu-id="a7e98-122">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="a7e98-123">Если Листенбакклог имеет слишком малое значение, WCF перестанет принимать запросы и, следовательно, удалит новые подключения, пока сервер не подтвердит некоторые существующие соединения в очереди.</span><span class="sxs-lookup"><span data-stu-id="a7e98-123">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="a7e98-124">Значение по умолчанию — 16 \* число процессоров.</span><span class="sxs-lookup"><span data-stu-id="a7e98-124">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="a7e98-125">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="a7e98-125">manualAddressing</span></span>|<span data-ttu-id="a7e98-126">Возвращает или задает значение, показывающее, требуется ли создание адреса сообщения вручную.</span><span class="sxs-lookup"><span data-stu-id="a7e98-126">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="a7e98-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a7e98-127">maxBufferPoolSize</span></span>|<span data-ttu-id="a7e98-128">Возвращает или задает максимальное значение буферных пулов, используемых транспортом.</span><span class="sxs-lookup"><span data-stu-id="a7e98-128">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="a7e98-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a7e98-129">maxBufferSize</span></span>|<span data-ttu-id="a7e98-130">Возвращает или задает максимальный размер используемого буфера.</span><span class="sxs-lookup"><span data-stu-id="a7e98-130">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="a7e98-131">Для потоковых сообщений это значение не должно быть меньше максимального возможного размера заголовков сообщения, считываемых в режиме буферизации.</span><span class="sxs-lookup"><span data-stu-id="a7e98-131">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="a7e98-132">максаутпутделай</span><span class="sxs-lookup"><span data-stu-id="a7e98-132">maxOutputDelay</span></span>|<span data-ttu-id="a7e98-133">Возвращает или задает максимальный промежуток времени, в течение которого фрагмент сообщения или все сообщение может оставаться в буфере перед отправкой.</span><span class="sxs-lookup"><span data-stu-id="a7e98-133">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="a7e98-134">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a7e98-134">maxPendingAccepts</span></span>|<span data-ttu-id="a7e98-135">Возвращает или задает максимальное число ожидающих асинхронных операций приема, доступных для обработки входящих подключений к службе.</span><span class="sxs-lookup"><span data-stu-id="a7e98-135">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="a7e98-136">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a7e98-136">maxPendingConnections</span></span>|<span data-ttu-id="a7e98-137">Возвращает или задает максимальное число подключений, ожидающих распределения в службе.</span><span class="sxs-lookup"><span data-stu-id="a7e98-137">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a7e98-138">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a7e98-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="a7e98-139">Возвращает и задает максимально допустимый размер принимаемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="a7e98-139">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="a7e98-140">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="a7e98-140">portSharingEnabled</span></span>|<span data-ttu-id="a7e98-141">Логическое значение, определяющее, включено ли совместное использование порта TCP для этого подключения.</span><span class="sxs-lookup"><span data-stu-id="a7e98-141">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="a7e98-142">Если атрибут имеет значение `false`, каждая привязка будет использовать уникальный порт.</span><span class="sxs-lookup"><span data-stu-id="a7e98-142">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="a7e98-143">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="a7e98-143">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a7e98-144">Этот параметр действителен только для служб.</span><span class="sxs-lookup"><span data-stu-id="a7e98-144">This setting is relevant only to services.</span></span> <span data-ttu-id="a7e98-145">Клиенты не затрагиваются.</span><span class="sxs-lookup"><span data-stu-id="a7e98-145">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="a7e98-146">Использование этого параметра требует включения службы общего доступа к портам TCP Windows Communication Foundation (WCF) путем изменения типа запуска на «Вручную» или «Авто».</span><span class="sxs-lookup"><span data-stu-id="a7e98-146">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="a7e98-147">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="a7e98-147">teredoEnabled</span></span>|<span data-ttu-id="a7e98-148">Логическое значение, указывающее, используется ли Teredo (технология адресации клиентов, защищенных брандмауэром).</span><span class="sxs-lookup"><span data-stu-id="a7e98-148">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="a7e98-149">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="a7e98-149">The default is `false`.</span></span><br /><br /> <span data-ttu-id="a7e98-150">Это свойство включает использование Teredo для базового сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="a7e98-150">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="a7e98-151">Дополнительные сведения см. в разделе [Общие сведения о Teredo](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="a7e98-151">For more information, see [Teredo Overview](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="a7e98-152">Это свойство применимо только в Windows XP с пакетом обновления 2 (SP2) и Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="a7e98-152">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="a7e98-153">В Windows Vista используется параметр конфигурации на уровне компьютера для Teredo, поэтому при запуске Vista это свойство игнорируется.</span><span class="sxs-lookup"><span data-stu-id="a7e98-153">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="a7e98-154">Для Teredo необходимо, чтобы на компьютере, где работает служба, и на компьютере-клиенте был установлен и настроен правильно для использования Teredo стек протокола Microsoft IPv6.</span><span class="sxs-lookup"><span data-stu-id="a7e98-154">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="a7e98-155">transferMode</span><span class="sxs-lookup"><span data-stu-id="a7e98-155">transferMode</span></span>|<span data-ttu-id="a7e98-156">Возвращает или задает значение, указывающее, следует ли помещать сообщения в буфер или передавать их потоком с использованием транспорта, ориентированного на подключение.</span><span class="sxs-lookup"><span data-stu-id="a7e98-156">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="a7e98-157">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a7e98-157">connectionPoolSettings</span></span>|<span data-ttu-id="a7e98-158">Задает дополнительные параметры пула подключений для привязки именованного канала.</span><span class="sxs-lookup"><span data-stu-id="a7e98-158">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7e98-159">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a7e98-159">Child Elements</span></span>  

 <span data-ttu-id="a7e98-160">None</span><span class="sxs-lookup"><span data-stu-id="a7e98-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7e98-161">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a7e98-161">Parent Elements</span></span>  
  
|<span data-ttu-id="a7e98-162">Элемент</span><span class="sxs-lookup"><span data-stu-id="a7e98-162">Element</span></span>|<span data-ttu-id="a7e98-163">Описание</span><span class="sxs-lookup"><span data-stu-id="a7e98-163">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a7e98-164">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="a7e98-164">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7e98-165">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7e98-165">Remarks</span></span>  

 <span data-ttu-id="a7e98-166">Этот транспорт использует универсальные коды ресурсов (URI) вида net.tcp://hostname:port/path.</span><span class="sxs-lookup"><span data-stu-id="a7e98-166">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="a7e98-167">Другие элементы универсального кода ресурса (URI) не обязательны.</span><span class="sxs-lookup"><span data-stu-id="a7e98-167">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="a7e98-168">Элемент `tcpTransport` является начальной точкой для создания пользовательской привязки, реализующей транспортный протокол TCP.</span><span class="sxs-lookup"><span data-stu-id="a7e98-168">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="a7e98-169">Этот транспорт оптимизирован для взаимодействия между службами WCF.</span><span class="sxs-lookup"><span data-stu-id="a7e98-169">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e98-170">См. также</span><span class="sxs-lookup"><span data-stu-id="a7e98-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a7e98-171">Транспорты</span><span class="sxs-lookup"><span data-stu-id="a7e98-171">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a7e98-172">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="a7e98-172">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a7e98-173">Привязки</span><span class="sxs-lookup"><span data-stu-id="a7e98-173">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7e98-174">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="a7e98-174">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7e98-175">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="a7e98-175">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
