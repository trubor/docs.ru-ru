---
description: 'Дополнительные сведения: <channelPoolSettings>'
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 85220cac360aaf32195c0b0f1d2866729e11c442
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638981"
---
# \<channelPoolSettings>

<span data-ttu-id="7ab33-102">Задает параметры пула каналов для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="7ab33-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="7ab33-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ab33-103">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ab33-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7ab33-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7ab33-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7ab33-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ab33-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7ab33-106">Attributes</span></span>  
  
|<span data-ttu-id="7ab33-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7ab33-107">Attribute</span></span>|<span data-ttu-id="7ab33-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7ab33-108">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="7ab33-109">Положительное значение <xref:System.TimeSpan>, указывающее максимальное время бездействия канала в пуле перед отключением.</span><span class="sxs-lookup"><span data-stu-id="7ab33-109">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="7ab33-110">Значение по умолчанию - 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="7ab33-110">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="7ab33-111">Значение <xref:System.TimeSpan>, которое задает интервал времени, после которого канал закрывается при возвращении в пул.</span><span class="sxs-lookup"><span data-stu-id="7ab33-111">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="7ab33-112">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7ab33-112">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="7ab33-113">Положительное целое число, задающее максимальное количество каналов, которое можно хранить в пуле для каждой удаленной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="7ab33-113">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="7ab33-114">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="7ab33-114">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ab33-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7ab33-115">Child Elements</span></span>  

 <span data-ttu-id="7ab33-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7ab33-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ab33-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7ab33-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7ab33-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="7ab33-118">Element</span></span>|<span data-ttu-id="7ab33-119">Описание</span><span class="sxs-lookup"><span data-stu-id="7ab33-119">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="7ab33-120">Включает маршрутизацию пакетов для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="7ab33-120">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ab33-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ab33-121">Remarks</span></span>  

 <span data-ttu-id="7ab33-122">Квоты используются как механизм политики, служащий для предотвращения чрезмерного потребления ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-122">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="7ab33-123">Они препятствуют злонамеренным или неумышленным атакам типа «отказ в обслуживании» (DoS).</span><span class="sxs-lookup"><span data-stu-id="7ab33-123">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="7ab33-124">Этот элемент используется при установке квот на пользовательском канале.</span><span class="sxs-lookup"><span data-stu-id="7ab33-124">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="7ab33-125">`ChannelPoolSettings` задает три квоты.</span><span class="sxs-lookup"><span data-stu-id="7ab33-125">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="7ab33-126">Квота `idleTimeout` используется для ослабления эффекта атак типа «отказ в обслуживании» (DoS) на сервере, при котором ресурсы блокируются на продолжительный период времени.</span><span class="sxs-lookup"><span data-stu-id="7ab33-126">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="7ab33-127">На клиенте установка правильного значения может повысить надежность соединения со службой.</span><span class="sxs-lookup"><span data-stu-id="7ab33-127">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="7ab33-128">Значение по умолчанию основано на консервативно умеренном выделении ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-128">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="7ab33-129">Это подходит для среды разработки и небольших сценариев установок.</span><span class="sxs-lookup"><span data-stu-id="7ab33-129">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="7ab33-130">Администраторы должны обновлять значение, если данной установке начинает не хватать ресурсов или если число подключений ограничено, несмотря на доступность дополнительных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-130">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="7ab33-131">Квота `leaseTimeout` используется для интеграции с механизмами балансировки нагрузки и для повышения надежности.</span><span class="sxs-lookup"><span data-stu-id="7ab33-131">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="7ab33-132">Значение по умолчанию основано на консервативном выделении ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-132">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="7ab33-133">Это подходит для среды разработки и небольших сценариев установок.</span><span class="sxs-lookup"><span data-stu-id="7ab33-133">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="7ab33-134">Администраторы должны обновлять значение, если данной установке начинает не хватать ресурсов или если число подключений ограничено, несмотря на доступность дополнительных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-134">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="7ab33-135">Квота `maxOutboundChannelsPerEndpoint` устанавливает предельные значения кэша на сервере и на клиенте и используется для повышения надежности.</span><span class="sxs-lookup"><span data-stu-id="7ab33-135">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="7ab33-136">Значение по умолчанию основано на консервативно умеренном выделении ресурсов, которое подходит для среды разработки и небольших установок.</span><span class="sxs-lookup"><span data-stu-id="7ab33-136">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="7ab33-137">Администраторы должны обновлять значение, если данной установке начинает не хватать ресурсов или если число подключений ограничено, несмотря на доступность дополнительных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7ab33-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab33-138">См. также</span><span class="sxs-lookup"><span data-stu-id="7ab33-138">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="7ab33-139">Привязки</span><span class="sxs-lookup"><span data-stu-id="7ab33-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ab33-140">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="7ab33-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7ab33-141">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="7ab33-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
