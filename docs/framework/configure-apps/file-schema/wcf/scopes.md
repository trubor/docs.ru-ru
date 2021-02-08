---
description: 'Дополнительные сведения: <scopes>'
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 2df1101beb5b1bc09c2d98eb89a8200303c5b456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786867"
---
# \<scopes>

<span data-ttu-id="8b963-102">Содержит коллекцию элементов конфигурации, указывающие идентификаторы URI пользовательских областей, которые можно использовать для фильтрации конечных точек службы во время выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="8b963-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="8b963-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8b963-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b963-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8b963-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8b963-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8b963-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b963-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8b963-106">Attributes</span></span>  

 <span data-ttu-id="8b963-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="8b963-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b963-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8b963-108">Child Elements</span></span>  
  
|<span data-ttu-id="8b963-109">attribute</span><span class="sxs-lookup"><span data-stu-id="8b963-109">Attribute</span></span>|<span data-ttu-id="8b963-110">Описание</span><span class="sxs-lookup"><span data-stu-id="8b963-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="8b963-111">Добавляет данные об области для конечной точки, которая может использоваться в критериях соответствия при поиске служб.</span><span class="sxs-lookup"><span data-stu-id="8b963-111">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b963-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8b963-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8b963-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="8b963-113">Element</span></span>|<span data-ttu-id="8b963-114">Описание</span><span class="sxs-lookup"><span data-stu-id="8b963-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="8b963-115">Указывает различные параметры обнаружения для конечной точки, такие как возможность обнаружения, области и любые пользовательские модули для ее метаданных.</span><span class="sxs-lookup"><span data-stu-id="8b963-115">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b963-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8b963-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
