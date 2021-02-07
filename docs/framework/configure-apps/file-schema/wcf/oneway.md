---
description: 'Дополнительные сведения: <oneWay>'
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 8e3314dd14525b5f7585a7336c00b615da56d1c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683844"
---
# \<oneWay>

<span data-ttu-id="17482-102">Включает поддержку маршрутизации пакетов и использования односторонних методов для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="17482-102">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="17482-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17482-103">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17482-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="17482-104">Attributes and Elements</span></span>  

 <span data-ttu-id="17482-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="17482-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17482-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="17482-106">Attributes</span></span>  
  
|<span data-ttu-id="17482-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="17482-107">Attribute</span></span>|<span data-ttu-id="17482-108">Описание</span><span class="sxs-lookup"><span data-stu-id="17482-108">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="17482-109">Логическое значение, указывающее, включена ли поддержка маршрутизации пакетов.</span><span class="sxs-lookup"><span data-stu-id="17482-109">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="17482-110">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="17482-110">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="17482-111">Целое число, указывающее максимальное количество принимаемых каналов.</span><span class="sxs-lookup"><span data-stu-id="17482-111">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17482-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="17482-112">Child Elements</span></span>  
  
|<span data-ttu-id="17482-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="17482-113">Element</span></span>|<span data-ttu-id="17482-114">Описание</span><span class="sxs-lookup"><span data-stu-id="17482-114">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="17482-115">Объект <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>, содержащий свойства пула каналов для текущего канала.</span><span class="sxs-lookup"><span data-stu-id="17482-115">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17482-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="17482-116">Parent Elements</span></span>  
  
|<span data-ttu-id="17482-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="17482-117">Element</span></span>|<span data-ttu-id="17482-118">Описание</span><span class="sxs-lookup"><span data-stu-id="17482-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="17482-119">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="17482-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17482-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="17482-120">Remarks</span></span>  

 <span data-ttu-id="17482-121">Чтобы включить поддержку маршрутизации пакетов, необходим уровень одностороннего преобразования, предоставляемый данным элементом.</span><span class="sxs-lookup"><span data-stu-id="17482-121">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="17482-122">Пользователь может создавать пользовательские привязки, которые выполняют наложение данной привязки на транспорт с поддержкой сеансов или типа «запрос-отклик», чтобы включить для него поддержку маршрутизации пакетов.</span><span class="sxs-lookup"><span data-stu-id="17482-122">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="17482-123">Этот элемент также полезен, если необходимо предоставить односторонние методы более естественным образом.</span><span class="sxs-lookup"><span data-stu-id="17482-123">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="17482-124">К данному уровню могут применяться дополнительные преобразования, например Composite Duplex и Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="17482-124">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17482-125">См. также</span><span class="sxs-lookup"><span data-stu-id="17482-125">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="17482-126">Привязки</span><span class="sxs-lookup"><span data-stu-id="17482-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17482-127">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="17482-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="17482-128">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="17482-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
