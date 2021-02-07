---
description: 'Дополнительные сведения: <routing>'
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 62222b527a14310b66015d4fdc4503e6cff25c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683350"
---
# \<routing>

<span data-ttu-id="5b278-102">Представляет раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений, а также таблицы маршрутизации, определяющие целевые конечные точки для отправки сообщений при совпадении фильтра.</span><span class="sxs-lookup"><span data-stu-id="5b278-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="5b278-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b278-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b278-104">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="5b278-104">Attributes and elements</span></span>

<span data-ttu-id="5b278-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5b278-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b278-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5b278-106">Attributes</span></span>

<span data-ttu-id="5b278-107">None</span><span class="sxs-lookup"><span data-stu-id="5b278-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b278-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5b278-108">Child elements</span></span>

|     | <span data-ttu-id="5b278-109">Описание</span><span class="sxs-lookup"><span data-stu-id="5b278-109">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="5b278-110">Содержит набор фильтров маршрутизации, определяющих тип Windows Communication Foundation (WCF) MessageFilter, которые будут использоваться при оценке входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="5b278-110">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="5b278-111">Содержит сопоставление между фильтрами маршрутизации и целевыми конечными точками для определения того, какие конечные точки будут использоваться при совпадении с критериями фильтра.</span><span class="sxs-lookup"><span data-stu-id="5b278-111">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="5b278-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5b278-112">Parent elements</span></span>

|     | <span data-ttu-id="5b278-113">Описание</span><span class="sxs-lookup"><span data-stu-id="5b278-113">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="5b278-114">Корневой элемент всех элементов конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="5b278-114">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5b278-115">См. также</span><span class="sxs-lookup"><span data-stu-id="5b278-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
