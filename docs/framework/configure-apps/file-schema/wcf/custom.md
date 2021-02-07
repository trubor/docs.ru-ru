---
description: 'Дополнительные сведения: <custom>'
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 327a5d7ff1bab88a1633d7a10095e708e6b1a533
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725913"
---
# \<custom>

<span data-ttu-id="aedcf-102">Задает параметры службы пользовательского распознавателя одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="aedcf-102">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="aedcf-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aedcf-103">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aedcf-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="aedcf-104">Attributes and Elements</span></span>  

 <span data-ttu-id="aedcf-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="aedcf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aedcf-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="aedcf-106">Attributes</span></span>  
  
|<span data-ttu-id="aedcf-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="aedcf-107">Attribute</span></span>|<span data-ttu-id="aedcf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="aedcf-108">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="aedcf-109">URI, указывающий адрес конечной точки однорангового узла, на котором размещается пользовательская служба распознавателя одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="aedcf-109">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="aedcf-110">Строка, задающая тип пользовательской службы распознавателя одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="aedcf-110">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aedcf-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="aedcf-111">Child Elements</span></span>  
  
|<span data-ttu-id="aedcf-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="aedcf-112">Element</span></span>|<span data-ttu-id="aedcf-113">Описание</span><span class="sxs-lookup"><span data-stu-id="aedcf-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="aedcf-114">Задает идентификатор пользовательских распознавателей одноранговых узлов, настроенных для данного элемента.</span><span class="sxs-lookup"><span data-stu-id="aedcf-114">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="aedcf-115">Это элемент типа <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="aedcf-115">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="aedcf-116">Коллекция заголовков адреса, используемых для сообщений SOAP, обрабатываемых пользовательским распознавателем одноранговых узлов.</span><span class="sxs-lookup"><span data-stu-id="aedcf-116">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aedcf-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="aedcf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aedcf-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="aedcf-118">Element</span></span>|<span data-ttu-id="aedcf-119">Описание</span><span class="sxs-lookup"><span data-stu-id="aedcf-119">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="aedcf-120">Распознаватель одноранговых узлов, используемый для разрешения идентификатора сетки с IP-адресами в набор адресов одноранговых узлов, представляющих несколько узлов, входящих в сетку.</span><span class="sxs-lookup"><span data-stu-id="aedcf-120">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aedcf-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="aedcf-121">Remarks</span></span>  

 <span data-ttu-id="aedcf-122">Этот элемент определяет основные параметры пользовательской службы распознавателя одноранговых узлов, включая адрес конечной точки однорангового узла, на котором размещена служба, и любые специальные параметры привязки.</span><span class="sxs-lookup"><span data-stu-id="aedcf-122">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="aedcf-123">Дополнительные сведения о создании пользовательского сопоставителя см. в разделе [Добавление пользовательского сопоставителя в приложение PeerChannel](/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="aedcf-123">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedcf-124">См. также</span><span class="sxs-lookup"><span data-stu-id="aedcf-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="aedcf-125">Одноранговые распознаватели</span><span class="sxs-lookup"><span data-stu-id="aedcf-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="aedcf-126">[Добавление в приложение PeerChannel пользовательского распознавателя](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="aedcf-126">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
