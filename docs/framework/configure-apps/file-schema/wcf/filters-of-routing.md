---
description: 'Дополнительные сведения <filters> о: <routing>'
title: <filters> из <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 41b51453f53fca042f53ca1ee8372413b8478ecd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782056"
---
# <a name="filters-of-routing"></a><span data-ttu-id="ffe70-103">\<filters> из \<routing></span><span class="sxs-lookup"><span data-stu-id="ffe70-103">\<filters> of \<routing></span></span>

<span data-ttu-id="ffe70-104">Представляет раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="ffe70-104">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="ffe70-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ffe70-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffe70-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="ffe70-106">Attributes and elements</span></span>

<span data-ttu-id="ffe70-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ffe70-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ffe70-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ffe70-108">Attributes</span></span>

<span data-ttu-id="ffe70-109">None</span><span class="sxs-lookup"><span data-stu-id="ffe70-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ffe70-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ffe70-110">Child elements</span></span>

|     | <span data-ttu-id="ffe70-111">Описание</span><span class="sxs-lookup"><span data-stu-id="ffe70-111">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="ffe70-112">Содержит фильтр маршрутизации, определяющий тип Windows Communication Foundation (WCF), который <xref:System.ServiceModel.Dispatcher.MessageFilter> будет использоваться при оценке входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="ffe70-112">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ffe70-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ffe70-113">Parent elements</span></span>

|     | <span data-ttu-id="ffe70-114">Описание</span><span class="sxs-lookup"><span data-stu-id="ffe70-114">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="ffe70-115">Представляет раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений, а также таблицы маршрутизации, определяющие целевые конечные точки для отправки сообщений при совпадении фильтра.</span><span class="sxs-lookup"><span data-stu-id="ffe70-115">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ffe70-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ffe70-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
