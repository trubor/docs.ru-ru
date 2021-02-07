---
description: 'Дополнительные сведения: <pnrpPeerResolver>'
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 4af6a63312fa300cfa33e578f01b8e07267ad3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683545"
---
# \<pnrpPeerResolver>

<span data-ttu-id="59c74-102">Задает использование распознавателя протокола PNRP (протокола однорангового разрешения имен) в качестве распознавателя.</span><span class="sxs-lookup"><span data-stu-id="59c74-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="59c74-103">Этот элемент является необязательным, поскольку протокол PNRP является распознавателем по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="59c74-103">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="59c74-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59c74-104">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59c74-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="59c74-105">Attributes and Elements</span></span>  

 <span data-ttu-id="59c74-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="59c74-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59c74-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="59c74-107">Attributes</span></span>  
  
|<span data-ttu-id="59c74-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="59c74-108">Attribute</span></span>|<span data-ttu-id="59c74-109">Описание</span><span class="sxs-lookup"><span data-stu-id="59c74-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59c74-110">resolverType</span><span class="sxs-lookup"><span data-stu-id="59c74-110">resolverType</span></span>|<span data-ttu-id="59c74-111">Строка, указывающая распознаватель для использования.</span><span class="sxs-lookup"><span data-stu-id="59c74-111">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="59c74-112">Этот атрибут является необязательным.</span><span class="sxs-lookup"><span data-stu-id="59c74-112">This attribute is optional.</span></span> <span data-ttu-id="59c74-113">Если значение не задано или равно пустой строке, используется протокол PNRP.</span><span class="sxs-lookup"><span data-stu-id="59c74-113">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59c74-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="59c74-114">Child Elements</span></span>  

 <span data-ttu-id="59c74-115">None</span><span class="sxs-lookup"><span data-stu-id="59c74-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59c74-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="59c74-116">Parent Elements</span></span>  
  
|<span data-ttu-id="59c74-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="59c74-117">Element</span></span>|<span data-ttu-id="59c74-118">Описание</span><span class="sxs-lookup"><span data-stu-id="59c74-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="59c74-119">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="59c74-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59c74-120">Пример</span><span class="sxs-lookup"><span data-stu-id="59c74-120">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="59c74-121">См. также</span><span class="sxs-lookup"><span data-stu-id="59c74-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="59c74-122">Привязки</span><span class="sxs-lookup"><span data-stu-id="59c74-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59c74-123">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="59c74-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="59c74-124">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="59c74-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="59c74-125">Одноранговые распознаватели</span><span class="sxs-lookup"><span data-stu-id="59c74-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
