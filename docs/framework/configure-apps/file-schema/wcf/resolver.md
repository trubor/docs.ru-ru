---
description: 'Дополнительные сведения: <resolver>'
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 338f9342d1ef14f3d96dada17fb9f6d893c86bee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683363"
---
# \<resolver>

<span data-ttu-id="d57cd-102">Указывает распознаватель одноранговых узлов, используемый для распознавания идентификатора сетки с IP-адресами в набор адресов одноранговых узлов, которые представляют несколько узлов, входящих в сетку.</span><span class="sxs-lookup"><span data-stu-id="d57cd-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="d57cd-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d57cd-103">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d57cd-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d57cd-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d57cd-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d57cd-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d57cd-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d57cd-106">Attributes</span></span>  
  
|<span data-ttu-id="d57cd-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d57cd-107">Attribute</span></span>|<span data-ttu-id="d57cd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d57cd-108">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d57cd-109">Строка, которая указывает, зависит ли экземпляр распознавателя одноранговых узлов, связанный с данной службой, от PNRP, является ли он пользовательским распознавателем или определяется автоматически.</span><span class="sxs-lookup"><span data-stu-id="d57cd-109">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="d57cd-110">Это атрибут типа <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="d57cd-110">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="d57cd-111">Строка, указывающая, каким образом отсылки распределяются между одноранговыми узлами.</span><span class="sxs-lookup"><span data-stu-id="d57cd-111">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="d57cd-112">Это атрибут типа <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="d57cd-112">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d57cd-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d57cd-113">Child Elements</span></span>  
  
|<span data-ttu-id="d57cd-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="d57cd-114">Element</span></span>|<span data-ttu-id="d57cd-115">Описание</span><span class="sxs-lookup"><span data-stu-id="d57cd-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="d57cd-116">Задает параметры службы пользовательского распознавателя одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="d57cd-116">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d57cd-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d57cd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d57cd-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="d57cd-118">Element</span></span>|<span data-ttu-id="d57cd-119">Описание</span><span class="sxs-lookup"><span data-stu-id="d57cd-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d57cd-120">Определяет все возможности привязки [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d57cd-120">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d57cd-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="d57cd-121">Remarks</span></span>  

 <span data-ttu-id="d57cd-122">Распознаватель одноранговых узлов представляет собой службу обнаружения, используемую одноранговыми каналами для поиска одноранговых узлов, участвующих в сетке с IP-адресами.</span><span class="sxs-lookup"><span data-stu-id="d57cd-122">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="d57cd-123">Он также используется для «регистрации» узла в сетке с IP-адресами; с помощью такого механизма одноранговый узел становится известным и доступным из сетки с IP-адресами.</span><span class="sxs-lookup"><span data-stu-id="d57cd-123">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="d57cd-124">Дополнительные сведения об одноранговых решениях см. в разделе [одноранговые арбитры конфликтов](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="d57cd-124">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57cd-125">См. также</span><span class="sxs-lookup"><span data-stu-id="d57cd-125">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="d57cd-126">Одноранговые распознаватели</span><span class="sxs-lookup"><span data-stu-id="d57cd-126">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="d57cd-127">[Добавление в приложение PeerChannel пользовательского распознавателя](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d57cd-127">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
