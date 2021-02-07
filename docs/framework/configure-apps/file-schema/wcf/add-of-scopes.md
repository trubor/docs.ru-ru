---
description: 'Дополнительные сведения <add> о: <scopes>'
title: <add> из <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e5582a7599c221e9ac00e03178911290e18ff536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750238"
---
# <a name="add-of-scopes"></a><span data-ttu-id="d6fbb-103">\<add> из \<scopes></span><span class="sxs-lookup"><span data-stu-id="d6fbb-103">\<add> of \<scopes></span></span>

<span data-ttu-id="d6fbb-104">Добавляет URI пользовательский области, который при выполнении запроса можно использовать для фильтрации конечных точек службы.</span><span class="sxs-lookup"><span data-stu-id="d6fbb-104">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d6fbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d6fbb-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6fbb-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d6fbb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d6fbb-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d6fbb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6fbb-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d6fbb-108">Attributes</span></span>  
  
|<span data-ttu-id="d6fbb-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d6fbb-109">Attribute</span></span>|<span data-ttu-id="d6fbb-110">Описание</span><span class="sxs-lookup"><span data-stu-id="d6fbb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6fbb-111">scope</span><span class="sxs-lookup"><span data-stu-id="d6fbb-111">scope</span></span>|<span data-ttu-id="d6fbb-112">URI, содержащий сведения об области для конечной точки, которую можно использовать в критериях соответствия при поиске служб.</span><span class="sxs-lookup"><span data-stu-id="d6fbb-112">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6fbb-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d6fbb-113">Child Elements</span></span>  

 <span data-ttu-id="d6fbb-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d6fbb-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6fbb-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d6fbb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d6fbb-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="d6fbb-116">Element</span></span>|<span data-ttu-id="d6fbb-117">Описание</span><span class="sxs-lookup"><span data-stu-id="d6fbb-117">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="d6fbb-118">Содержит коллекцию элементов конфигурации, указывающие идентификаторы URI пользовательских областей, которые можно использовать для фильтрации конечных точек службы во время выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="d6fbb-118">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6fbb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="d6fbb-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
