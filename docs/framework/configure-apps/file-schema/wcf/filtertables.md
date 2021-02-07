---
description: 'Дополнительные сведения: <filterTables>'
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 932d0e162c3fdeba8b166d3adaaa73cc3b5293a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664591"
---
# \<filterTables>

<span data-ttu-id="1e5ed-102">Представляет раздел конфигурации, в котором определены таблицы маршрутизации, содержащие сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при совпадении с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="1e5ed-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="1e5ed-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e5ed-103">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e5ed-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1e5ed-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1e5ed-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1e5ed-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e5ed-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1e5ed-106">Attributes</span></span>  

 <span data-ttu-id="1e5ed-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1e5ed-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e5ed-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1e5ed-108">Child Elements</span></span>  
  
|<span data-ttu-id="1e5ed-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="1e5ed-109">Element</span></span>|<span data-ttu-id="1e5ed-110">Описание</span><span class="sxs-lookup"><span data-stu-id="1e5ed-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="1e5ed-111">Таблица маршрутизации, содержащая сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при условии совпадения с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="1e5ed-111">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e5ed-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1e5ed-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1e5ed-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="1e5ed-113">Element</span></span>|<span data-ttu-id="1e5ed-114">Описание</span><span class="sxs-lookup"><span data-stu-id="1e5ed-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="1e5ed-115">Раздел конфигурации, содержащий фильтры и таблицы маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="1e5ed-115">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e5ed-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1e5ed-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
