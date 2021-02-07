---
description: 'Дополнительные сведения: <enableWebScript>'
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: f357bf1ab726cd434a16b2daa9c8115afe7d4430
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725887"
---
# \<enableWebScript>

<span data-ttu-id="7bd26-102">Этот элемент включает поведение конечной точки, которое позволяет использовать службу с веб-страниц ASP.NET с поддержкой технологии AJAX.</span><span class="sxs-lookup"><span data-stu-id="7bd26-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="7bd26-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7bd26-103">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd26-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7bd26-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7bd26-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7bd26-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd26-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7bd26-106">Attributes</span></span>  

 <span data-ttu-id="7bd26-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7bd26-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7bd26-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7bd26-108">Child Elements</span></span>  

 <span data-ttu-id="7bd26-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7bd26-109">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd26-110">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7bd26-110">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd26-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="7bd26-111">Element</span></span>|<span data-ttu-id="7bd26-112">Описание</span><span class="sxs-lookup"><span data-stu-id="7bd26-112">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7bd26-113">Задает набор поведений конечной точки.</span><span class="sxs-lookup"><span data-stu-id="7bd26-113">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd26-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="7bd26-114">Remarks</span></span>  

 <span data-ttu-id="7bd26-115">Это поведение следует использовать только в сочетании со [\<webHttpBinding>](webhttpbinding.md) стандартной привязкой или с [\<webMessageEncoding>](webmessageencoding.md) элементом Binding.</span><span class="sxs-lookup"><span data-stu-id="7bd26-115">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="7bd26-116">Дополнительные сведения об этом поведении см. в разделе <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7bd26-116">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd26-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7bd26-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="7bd26-118">Интеграция с AJAX и поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="7bd26-118">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
