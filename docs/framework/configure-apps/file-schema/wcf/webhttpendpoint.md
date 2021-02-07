---
description: 'Дополнительные сведения: <webHttpEndpoint>'
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: d1bcda1fc97dece833c8163e5facbefe614af0ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682596"
---
# \<webHttpEndpoint>

<span data-ttu-id="76fcb-102">Этот элемент конфигурации определяет стандартную конечную точку с фиксированной [\<webHttpBinding>](webhttpbinding.md) привязкой, которая автоматически добавляет [\<webHttp>](webhttp.md) поведение.</span><span class="sxs-lookup"><span data-stu-id="76fcb-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="76fcb-103">Используйте эту конечную точку при написании службы REST.</span><span class="sxs-lookup"><span data-stu-id="76fcb-103">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="76fcb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76fcb-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76fcb-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="76fcb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="76fcb-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="76fcb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76fcb-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="76fcb-107">Attributes</span></span>  
  
|<span data-ttu-id="76fcb-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="76fcb-108">Attribute</span></span>|<span data-ttu-id="76fcb-109">Описание</span><span class="sxs-lookup"><span data-stu-id="76fcb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76fcb-110">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="76fcb-110">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="76fcb-111">Логическое значение, указывающее, включен ли автоматический выбор формата.</span><span class="sxs-lookup"><span data-stu-id="76fcb-111">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="76fcb-112">Если автоматический выбор формата включен, инфраструктура выполняет синтаксический анализ заголовка `Accept` сообщения запроса и определяет наиболее подходящий формат ответа.</span><span class="sxs-lookup"><span data-stu-id="76fcb-112">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="76fcb-113">Если в заголовке `Accept` не указан подходящий формат ответа, инфраструктура использует тип `Content-Type` сообщения запроса или формат ответа, заданный для этой операции по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="76fcb-113">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="76fcb-114">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="76fcb-114">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="76fcb-115">Атрибут, определяющий формат исходящего ответа по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="76fcb-115">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="76fcb-116">Это атрибут типа <xref:System.ServiceModel.Web.WebMessageFormat>.</span><span class="sxs-lookup"><span data-stu-id="76fcb-116">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="76fcb-117">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="76fcb-117">helpEnabled</span></span>|<span data-ttu-id="76fcb-118">Логическое значение, указывающее, включена ли страница справки HTTP для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="76fcb-118">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="76fcb-119">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="76fcb-119">webEndpointType</span></span>|<span data-ttu-id="76fcb-120">Строка, указывающая тип конечной точки.</span><span class="sxs-lookup"><span data-stu-id="76fcb-120">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76fcb-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="76fcb-121">Child Elements</span></span>  

 <span data-ttu-id="76fcb-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="76fcb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76fcb-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="76fcb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="76fcb-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="76fcb-124">Element</span></span>|<span data-ttu-id="76fcb-125">Описание</span><span class="sxs-lookup"><span data-stu-id="76fcb-125">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="76fcb-126">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="76fcb-126">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76fcb-127">См. также</span><span class="sxs-lookup"><span data-stu-id="76fcb-127">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
