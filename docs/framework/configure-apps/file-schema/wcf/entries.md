---
description: 'Дополнительные сведения: <entries>'
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: e5aefce4328c341b6d132765c8e726910241aae1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782108"
---
# \<entries>

<span data-ttu-id="90bff-102">Запись маршрутизации, содержащая сопоставление между фильтрами маршрутизации и целевыми конечными точками (которые будут использованы при отправке сообщений при условии совпадения с критериями фильтров).</span><span class="sxs-lookup"><span data-stu-id="90bff-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="90bff-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90bff-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90bff-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="90bff-104">Attributes and Elements</span></span>  

 <span data-ttu-id="90bff-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="90bff-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90bff-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="90bff-106">Attributes</span></span>  

 <span data-ttu-id="90bff-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="90bff-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90bff-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="90bff-108">Child Elements</span></span>  
  
|<span data-ttu-id="90bff-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="90bff-109">Element</span></span>|<span data-ttu-id="90bff-110">Описание</span><span class="sxs-lookup"><span data-stu-id="90bff-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="90bff-111">Сопоставляет фильтр с ранее определенной конечной точкой клиента.</span><span class="sxs-lookup"><span data-stu-id="90bff-111">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="90bff-112">Сообщения, соответствующие этому фильтру, будут отправлены по данному назначению.</span><span class="sxs-lookup"><span data-stu-id="90bff-112">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90bff-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="90bff-113">Parent Elements</span></span>  
  
|<span data-ttu-id="90bff-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="90bff-114">Element</span></span>|<span data-ttu-id="90bff-115">Описание</span><span class="sxs-lookup"><span data-stu-id="90bff-115">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="90bff-116">Раздел конфигурации, содержащий таблицу маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="90bff-116">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90bff-117">См. также</span><span class="sxs-lookup"><span data-stu-id="90bff-117">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
