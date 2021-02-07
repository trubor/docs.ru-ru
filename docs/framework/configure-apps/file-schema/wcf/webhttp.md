---
description: 'Дополнительные сведения: <webHttp>'
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: acd8d77e00828d132d076c867ff3164ca1ba7230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664383"
---
# \<webHttp>

<span data-ttu-id="1ed55-102">Данный элемент задает <xref:System.ServiceModel.Description.WebHttpBehavior> на конечной точке в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1ed55-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="1ed55-103">Такое поведение при использовании в сочетании со [\<webHttpBinding>](webhttpbinding.md) стандартной привязкой позволяет использовать модель веб-программирования для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1ed55-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="1ed55-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ed55-104">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ed55-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1ed55-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1ed55-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1ed55-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ed55-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1ed55-107">Attributes</span></span>  
  
|<span data-ttu-id="1ed55-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1ed55-108">Attribute</span></span>|<span data-ttu-id="1ed55-109">Описание</span><span class="sxs-lookup"><span data-stu-id="1ed55-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ed55-110">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="1ed55-110">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="1ed55-111">Если это свойство имеет значение `true`, то инфраструктура WCF определяет лучший формат для использования.</span><span class="sxs-lookup"><span data-stu-id="1ed55-111">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="1ed55-112">Автоматический выбор формата отключен по умолчанию в целях обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="1ed55-112">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="1ed55-113">Автоматический выбор формата можно включить программно или через конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="1ed55-113">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="1ed55-114">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="1ed55-114">defaultBodyStyle</span></span>|<span data-ttu-id="1ed55-115">Задает стиль по умолчанию для текста возвращаемых сообщений.</span><span class="sxs-lookup"><span data-stu-id="1ed55-115">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="1ed55-116">Дополнительные сведения см. в разделе <xref:System.ServiceModel.Web.WebMessageBodyStyle> и [веб-форматирование WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="1ed55-116">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="1ed55-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="1ed55-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="1ed55-118">Определяет формат ответа по умолчанию для исходящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="1ed55-118">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="1ed55-119">Дополнительные сведения см. в разделе [веб-форматирование WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="1ed55-119">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="1ed55-120">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="1ed55-120">faultExceptionEnabled</span></span>|<span data-ttu-id="1ed55-121">Возвращает или задает флаг, указывающий, будет ли создаваться исключение FaultException при возникновении внутренней ошибки сервера (код состояния HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="1ed55-121">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="1ed55-122">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="1ed55-122">helpEnabled</span></span>|<span data-ttu-id="1ed55-123">Возвращает или задает значение, определяющее, будет ли включена страница справки.</span><span class="sxs-lookup"><span data-stu-id="1ed55-123">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ed55-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1ed55-124">Child Elements</span></span>  

 <span data-ttu-id="1ed55-125">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1ed55-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ed55-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1ed55-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1ed55-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="1ed55-127">Element</span></span>|<span data-ttu-id="1ed55-128">Описание</span><span class="sxs-lookup"><span data-stu-id="1ed55-128">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1ed55-129">Задает набор поведений конечной точки.</span><span class="sxs-lookup"><span data-stu-id="1ed55-129">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ed55-130">См. также</span><span class="sxs-lookup"><span data-stu-id="1ed55-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="1ed55-131">Интеграция с AJAX и поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="1ed55-131">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
