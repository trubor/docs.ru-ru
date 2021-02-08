---
description: 'Дополнительные сведения: <filterTable>'
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 2051bb0e778e5676f39d91b7d7ba415fd7e523af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782043"
---
# \<filterTable>

<span data-ttu-id="5c3ae-102">Представляет таблицу маршрутизации, которая содержит список фильтров, с помощью которых вычисляются сообщения, а также клиентскую конечную точку, которой будут направляться сообщения, если фильтр возвратит значение true.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="5c3ae-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c3ae-103">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c3ae-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5c3ae-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5c3ae-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c3ae-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5c3ae-106">Attributes</span></span>  
  
|<span data-ttu-id="5c3ae-107">Элемент</span><span class="sxs-lookup"><span data-stu-id="5c3ae-107">Element</span></span>|<span data-ttu-id="5c3ae-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5c3ae-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c3ae-109">name</span><span class="sxs-lookup"><span data-stu-id="5c3ae-109">name</span></span>|<span data-ttu-id="5c3ae-110">Строка, содержащая уникальное имя этого элемента конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-110">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c3ae-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5c3ae-111">Child Elements</span></span>  
  
|<span data-ttu-id="5c3ae-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="5c3ae-112">Element</span></span>|<span data-ttu-id="5c3ae-113">Описание</span><span class="sxs-lookup"><span data-stu-id="5c3ae-113">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="5c3ae-114">Сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при условии совпадения с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="5c3ae-114">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c3ae-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5c3ae-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5c3ae-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="5c3ae-116">Element</span></span>|<span data-ttu-id="5c3ae-117">Описание</span><span class="sxs-lookup"><span data-stu-id="5c3ae-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="5c3ae-118">Раздел конфигурации, содержащий таблицы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="5c3ae-118">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c3ae-119">См. также</span><span class="sxs-lookup"><span data-stu-id="5c3ae-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
