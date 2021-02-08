---
description: 'Дополнительные сведения: <connectionPoolSettings>'
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 5acf2d800f1a18f45750d0fabd23516f987b2c5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782173"
---
# \<connectionPoolSettings>

<span data-ttu-id="9f471-102">Задает дополнительные параметры пула подключений для привязки именованного канала.</span><span class="sxs-lookup"><span data-stu-id="9f471-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9f471-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f471-103">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f471-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9f471-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9f471-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9f471-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f471-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9f471-106">Attributes</span></span>  
  
|<span data-ttu-id="9f471-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9f471-107">Attribute</span></span>|<span data-ttu-id="9f471-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9f471-108">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="9f471-109">Строка, определяющая имя пула подключений, используемого для исходящих каналов.</span><span class="sxs-lookup"><span data-stu-id="9f471-109">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="9f471-110">В потоковом режиме общий доступ к подключениям не предоставляется, то есть пул подключений отключен.</span><span class="sxs-lookup"><span data-stu-id="9f471-110">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="9f471-111">Значение по умолчанию - строка «default».</span><span class="sxs-lookup"><span data-stu-id="9f471-111">The default is a "default" string.</span></span> <span data-ttu-id="9f471-112">Это значение можно изменить, чтобы изолировать подключения для конкретного клиента в отдельные группы.</span><span class="sxs-lookup"><span data-stu-id="9f471-112">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="9f471-113">Положительное значение <xref:System.TimeSpan>, указывающее максимальное время бездействия для подключения перед его закрытием.</span><span class="sxs-lookup"><span data-stu-id="9f471-113">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="9f471-114">Значение по умолчанию - 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="9f471-114">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="9f471-115">Положительное целое число, указывающее максимальное число подключений к удаленной конечной точке, инициированных одной службой.</span><span class="sxs-lookup"><span data-stu-id="9f471-115">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="9f471-116">Соединения сверх лимита помещаются в очередь до высвобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="9f471-116">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="9f471-117">Параметр `idleTimeout` ограничивает продолжительность времени, в течение которого подключения остаются в очереди до возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="9f471-117">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="9f471-118">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="9f471-118">The default is 10.</span></span><br /><br /> <span data-ttu-id="9f471-119">Этот атрибут ограничивает число одновременных активных подключений клиента к конкретной конечной точке службы.</span><span class="sxs-lookup"><span data-stu-id="9f471-119">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="9f471-120">В случае превышения этого значения при наличии большего числа активных соединений клиентов служба может прекратить отвечать на запросы клиента.</span><span class="sxs-lookup"><span data-stu-id="9f471-120">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="9f471-121">В таком случае это значение следует скорректировать, чтобы оно было больше предполагаемого максимума одновременных подключений клиента к конкретной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="9f471-121">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f471-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9f471-122">Child Elements</span></span>  

 <span data-ttu-id="9f471-123">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9f471-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f471-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9f471-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9f471-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="9f471-125">Element</span></span>|<span data-ttu-id="9f471-126">Описание</span><span class="sxs-lookup"><span data-stu-id="9f471-126">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="9f471-127">Определяет транспорт, вызывающий передачу сообщений с использованием именованных каналов.</span><span class="sxs-lookup"><span data-stu-id="9f471-127">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f471-128">См. также</span><span class="sxs-lookup"><span data-stu-id="9f471-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9f471-129">Транспорты</span><span class="sxs-lookup"><span data-stu-id="9f471-129">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9f471-130">Выбор транспортов</span><span class="sxs-lookup"><span data-stu-id="9f471-130">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9f471-131">Привязки</span><span class="sxs-lookup"><span data-stu-id="9f471-131">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f471-132">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="9f471-132">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9f471-133">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="9f471-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
