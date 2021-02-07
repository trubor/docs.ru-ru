---
description: 'Дополнительные сведения: <webScriptEndpoint>'
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: eef4eb8e8e7345492f967c85b6245f733a4c824f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682505"
---
# \<webScriptEndpoint>

<span data-ttu-id="90104-102">Этот элемент конфигурации определяет стандартную конечную точку с фиксированной [\<webHttpBinding>](webhttpbinding.md) привязкой, которая автоматически добавляет [\<enableWebScript>](enablewebscript.md) поведение.</span><span class="sxs-lookup"><span data-stu-id="90104-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="90104-103">Используйте эту конечную точку при написании службы, вызываемой из приложения ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="90104-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="90104-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90104-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90104-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="90104-105">Attributes and Elements</span></span>  

 <span data-ttu-id="90104-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="90104-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90104-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="90104-107">Attributes</span></span>  
  
|<span data-ttu-id="90104-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="90104-108">Attribute</span></span>|<span data-ttu-id="90104-109">Описание</span><span class="sxs-lookup"><span data-stu-id="90104-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90104-110">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="90104-110">webEndpointType</span></span>|<span data-ttu-id="90104-111">Строка, указывающая тип конечной точки.</span><span class="sxs-lookup"><span data-stu-id="90104-111">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90104-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="90104-112">Child Elements</span></span>  

 <span data-ttu-id="90104-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="90104-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90104-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="90104-114">Parent Elements</span></span>  
  
|<span data-ttu-id="90104-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="90104-115">Element</span></span>|<span data-ttu-id="90104-116">Описание</span><span class="sxs-lookup"><span data-stu-id="90104-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="90104-117">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="90104-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90104-118">См. также</span><span class="sxs-lookup"><span data-stu-id="90104-118">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
