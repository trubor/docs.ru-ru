---
description: 'Дополнительные сведения <add> о: <entries>'
title: <add> из <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 0be24fb9d2327d411368dd05afc21156dfaf3d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803975"
---
# <a name="add-of-entries"></a><span data-ttu-id="5ea10-103">\<add> из \<entries></span><span class="sxs-lookup"><span data-stu-id="5ea10-103">\<add> of \<entries></span></span>

<span data-ttu-id="5ea10-104">Представляет запись маршрутизации, которая сопоставляет фильтр с ранее определенной конечной точкой клиента.</span><span class="sxs-lookup"><span data-stu-id="5ea10-104">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="5ea10-105">Сообщения, соответствующие этому фильтру, будут отправлены по данному назначению.</span><span class="sxs-lookup"><span data-stu-id="5ea10-105">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5ea10-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ea10-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea10-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5ea10-107">Attributes and Elements</span></span>  

 <span data-ttu-id="5ea10-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5ea10-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea10-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5ea10-109">Attributes</span></span>  
  
|<span data-ttu-id="5ea10-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5ea10-110">Attribute</span></span>|<span data-ttu-id="5ea10-111">Описание</span><span class="sxs-lookup"><span data-stu-id="5ea10-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ea10-112">backupList</span><span class="sxs-lookup"><span data-stu-id="5ea10-112">backupList</span></span>|<span data-ttu-id="5ea10-113">Строка, указывающая ссылку на резервный список конечных точек.</span><span class="sxs-lookup"><span data-stu-id="5ea10-113">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="5ea10-114">endpoint</span><span class="sxs-lookup"><span data-stu-id="5ea10-114">endpoint</span></span>|<span data-ttu-id="5ea10-115">Строка, в которой указана ссылка на конечную точку клиента, получающую сообщения, которые соответствуют критериям фильтра, указанного в атрибуте `filterName`.</span><span class="sxs-lookup"><span data-stu-id="5ea10-115">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="5ea10-116">filterName</span><span class="sxs-lookup"><span data-stu-id="5ea10-116">filterName</span></span>|<span data-ttu-id="5ea10-117">Строка, в которой указана ссылка на элемент фильтра.</span><span class="sxs-lookup"><span data-stu-id="5ea10-117">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="5ea10-118">priority</span><span class="sxs-lookup"><span data-stu-id="5ea10-118">priority</span></span>|<span data-ttu-id="5ea10-119">Целое число, задающее приоритет этой записи.</span><span class="sxs-lookup"><span data-stu-id="5ea10-119">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="5ea10-120">Записи в таблице маршрутизации обрабатываются исходя из приоритета, причем 0 является самым низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="5ea10-120">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="5ea10-121">Все записи определенного приоритета обрабатываются одновременно, и, если для текущего приоритета не находится совпадающая запись, вычисляется следующий уровень приоритета.</span><span class="sxs-lookup"><span data-stu-id="5ea10-121">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="5ea10-122">Это необязательное значение.</span><span class="sxs-lookup"><span data-stu-id="5ea10-122">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea10-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5ea10-123">Child Elements</span></span>  

 <span data-ttu-id="5ea10-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5ea10-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea10-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5ea10-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea10-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="5ea10-126">Element</span></span>|<span data-ttu-id="5ea10-127">Описание</span><span class="sxs-lookup"><span data-stu-id="5ea10-127">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="5ea10-128">Раздел конфигурации, в котором содержатся записи сопоставления маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="5ea10-128">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ea10-129">См. также</span><span class="sxs-lookup"><span data-stu-id="5ea10-129">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
