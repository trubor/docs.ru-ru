---
description: 'Дополнительные сведения: <useRequestHeadersForMetadataAddress>'
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 53636b5890eb54095737e2ed62a75e9b81c1c1f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664435"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="a3a8b-102">Включает получение сведений об адресе метаданных из заголовков сообщений запросов.</span><span class="sxs-lookup"><span data-stu-id="a3a8b-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="a3a8b-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3a8b-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3a8b-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a3a8b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a3a8b-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a3a8b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3a8b-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a3a8b-106">Attributes</span></span>  

 <span data-ttu-id="a3a8b-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a3a8b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3a8b-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a3a8b-108">Child Elements</span></span>  
  
|<span data-ttu-id="a3a8b-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="a3a8b-109">Element</span></span>|<span data-ttu-id="a3a8b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a3a8b-110">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="a3a8b-111">Коллекция портов по умолчанию со списком конечных точек связи по умолчанию, которые прослушивает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="a3a8b-111">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3a8b-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a3a8b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a3a8b-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="a3a8b-113">Element</span></span>|<span data-ttu-id="a3a8b-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a3a8b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a3a8b-115">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="a3a8b-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3a8b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a3a8b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
