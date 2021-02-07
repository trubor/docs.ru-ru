---
description: 'Дополнительные сведения <connectionPoolSettings> о: <tcpTransport>'
title: <connectionPoolSettings> из <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 065d3529740714ffd740c2cec71832a7b386b4a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698392"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="18bcc-103">\<connectionPoolSettings> из \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="18bcc-103">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="18bcc-104">Задает дополнительные параметры пула подключений для транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="18bcc-104">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="18bcc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18bcc-105">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18bcc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="18bcc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="18bcc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="18bcc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18bcc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="18bcc-108">Attributes</span></span>  
  
|<span data-ttu-id="18bcc-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="18bcc-109">Attribute</span></span>|<span data-ttu-id="18bcc-110">Описание</span><span class="sxs-lookup"><span data-stu-id="18bcc-110">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="18bcc-111">Строка, определяющая имя пула подключений, используемого для исходящих каналов.</span><span class="sxs-lookup"><span data-stu-id="18bcc-111">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="18bcc-112">В потоковом режиме общий доступ к подключениям не предоставляется, то есть пул подключений отключен.</span><span class="sxs-lookup"><span data-stu-id="18bcc-112">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="18bcc-113">Значение по умолчанию - строка «default».</span><span class="sxs-lookup"><span data-stu-id="18bcc-113">The default is a "default" string.</span></span> <span data-ttu-id="18bcc-114">Это значение можно изменить, чтобы изолировать подключения для конкретного клиента в отдельные группы.</span><span class="sxs-lookup"><span data-stu-id="18bcc-114">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="18bcc-115">Положительное значение <xref:System.TimeSpan>, указывающее максимальное время бездействия для подключения перед его закрытием.</span><span class="sxs-lookup"><span data-stu-id="18bcc-115">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="18bcc-116">Значение по умолчанию - 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="18bcc-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="18bcc-117">Параметр <xref:System.TimeSpan>, задающий время ожидания перед закрытием активного подключения.</span><span class="sxs-lookup"><span data-stu-id="18bcc-117">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="18bcc-118">Значение по умолчанию - 00:05:00.</span><span class="sxs-lookup"><span data-stu-id="18bcc-118">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="18bcc-119">Подключение закрывается после возврата в кэш подключений, а не во время активной передачи.</span><span class="sxs-lookup"><span data-stu-id="18bcc-119">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="18bcc-120">Кэш подключений, используемый транспортом TCP, по мере необходимости создает новые подключения для каждой конечной точки, до достижения лимита кэша, который задается параметром `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="18bcc-120">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="18bcc-121">Положительное целое число, указывающее максимальное число подключений к удаленной конечной точке, инициированных одной службой.</span><span class="sxs-lookup"><span data-stu-id="18bcc-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="18bcc-122">Соединения сверх лимита помещаются в очередь до высвобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="18bcc-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="18bcc-123">Параметр `idleTimeout` ограничивает продолжительность времени, в течение которого подключения остаются в очереди до возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="18bcc-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="18bcc-124">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="18bcc-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="18bcc-125">Этот атрибут ограничивает число одновременных активных подключений клиента к конкретной конечной точке службы.</span><span class="sxs-lookup"><span data-stu-id="18bcc-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="18bcc-126">В случае превышения этого значения при наличии большего числа активных соединений клиентов служба может прекратить отвечать на запросы клиента.</span><span class="sxs-lookup"><span data-stu-id="18bcc-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="18bcc-127">В таком случае это значение следует скорректировать, чтобы оно было больше предполагаемого максимума одновременных подключений клиента к конкретной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="18bcc-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18bcc-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="18bcc-128">Child Elements</span></span>  

 <span data-ttu-id="18bcc-129">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="18bcc-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18bcc-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="18bcc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="18bcc-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="18bcc-131">Element</span></span>|<span data-ttu-id="18bcc-132">Описание</span><span class="sxs-lookup"><span data-stu-id="18bcc-132">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="18bcc-133">Определяет транспорт, вызывающий передачу сообщений с использованием именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="18bcc-133">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18bcc-134">См. также</span><span class="sxs-lookup"><span data-stu-id="18bcc-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="18bcc-135">Транспорты</span><span class="sxs-lookup"><span data-stu-id="18bcc-135">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="18bcc-136">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="18bcc-136">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="18bcc-137">Привязки</span><span class="sxs-lookup"><span data-stu-id="18bcc-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="18bcc-138">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="18bcc-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="18bcc-139">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="18bcc-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
