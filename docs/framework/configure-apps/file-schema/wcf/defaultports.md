---
description: 'Дополнительные сведения: <defaultPorts>'
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7cd0635568bf80734900f5e54f918150ea657322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803910"
---
# \<defaultPorts>

<span data-ttu-id="32c71-102">Коллекция портов по умолчанию со списком конечных точек связи по умолчанию, которые прослушивает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="32c71-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="32c71-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32c71-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c71-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="32c71-104">Attributes and Elements</span></span>  

 <span data-ttu-id="32c71-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="32c71-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c71-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="32c71-106">Attributes</span></span>  

 <span data-ttu-id="32c71-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="32c71-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32c71-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="32c71-108">Child Elements</span></span>  
  
|<span data-ttu-id="32c71-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="32c71-109">Element</span></span>|<span data-ttu-id="32c71-110">Описание</span><span class="sxs-lookup"><span data-stu-id="32c71-110">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c71-111">\<add> из \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="32c71-111">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="32c71-112">Конечная точка связи по умолчанию, которую прослушивает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="32c71-112">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32c71-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="32c71-113">Parent Elements</span></span>  
  
|<span data-ttu-id="32c71-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="32c71-114">Element</span></span>|<span data-ttu-id="32c71-115">Описание</span><span class="sxs-lookup"><span data-stu-id="32c71-115">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="32c71-116">Список портов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="32c71-116">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32c71-117">См. также</span><span class="sxs-lookup"><span data-stu-id="32c71-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
