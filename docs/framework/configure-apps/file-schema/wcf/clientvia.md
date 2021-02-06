---
description: 'Дополнительные сведения: <clientVia>'
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 651af0c310504f7672ca172d7df609365c319506
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638777"
---
# \<clientVia>

<span data-ttu-id="0d5b0-102">Задает универсальный код ресурса (URI), для которого необходимо создать канал транспорта.</span><span class="sxs-lookup"><span data-stu-id="0d5b0-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="0d5b0-103">Для получения дополнительной информации см. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="0d5b0-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="0d5b0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d5b0-104">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d5b0-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0d5b0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0d5b0-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0d5b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d5b0-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0d5b0-107">Attributes</span></span>  
  
|<span data-ttu-id="0d5b0-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0d5b0-108">Attribute</span></span>|<span data-ttu-id="0d5b0-109">Описание</span><span class="sxs-lookup"><span data-stu-id="0d5b0-109">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="0d5b0-110">Строка, задающая универсальный код ресурса (URI), который указывает маршрут для сообщения.</span><span class="sxs-lookup"><span data-stu-id="0d5b0-110">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d5b0-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0d5b0-111">Child Elements</span></span>  

 <span data-ttu-id="0d5b0-112">None</span><span class="sxs-lookup"><span data-stu-id="0d5b0-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d5b0-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0d5b0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0d5b0-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d5b0-114">Element</span></span>|<span data-ttu-id="0d5b0-115">Описание</span><span class="sxs-lookup"><span data-stu-id="0d5b0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0d5b0-116">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="0d5b0-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d5b0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0d5b0-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
