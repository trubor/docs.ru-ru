---
description: 'Дополнительные сведения: <filter>'
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 993d2265ac3a714475e8cbe9e8a2c3f93c46bde2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664682"
---
# \<filter>

<span data-ttu-id="f1162-102">Определяет фильтр маршрутизации, определяющий тип Windows Communication Foundation (WCF), который <xref:System.ServiceModel.Dispatcher.MessageFilter> будет использоваться при оценке входящих сообщений, а также любые вспомогательные данные или параметры, необходимые для фильтра.</span><span class="sxs-lookup"><span data-stu-id="f1162-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="f1162-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1162-103">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1162-104">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="f1162-104">Attributes and elements</span></span>

<span data-ttu-id="f1162-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f1162-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1162-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f1162-106">Attributes</span></span>

| <span data-ttu-id="f1162-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f1162-107">Attribute</span></span>  | <span data-ttu-id="f1162-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f1162-108">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f1162-109">customType</span><span class="sxs-lookup"><span data-stu-id="f1162-109">customType</span></span> | <span data-ttu-id="f1162-110">Строка, содержащая полное имя для пользовательского типа, используемого в качестве фильтра.</span><span class="sxs-lookup"><span data-stu-id="f1162-110">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f1162-111">Если параметр `filterType` имеет значение `custom` , этот атрибут содержит полное имя типа создаваемого класса.</span><span class="sxs-lookup"><span data-stu-id="f1162-111">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f1162-112">`filterData` может также содержать значения, используемые при вычислении настраиваемого фильтра типов.</span><span class="sxs-lookup"><span data-stu-id="f1162-112">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f1162-113">filterData</span><span class="sxs-lookup"><span data-stu-id="f1162-113">filterData</span></span> | <span data-ttu-id="f1162-114">Строка, содержащая данные фильтра.</span><span class="sxs-lookup"><span data-stu-id="f1162-114">A string containing the filter data.</span></span> <span data-ttu-id="f1162-115">Дополнительные сведения об указании этого атрибута см. в разделе <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1162-115">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f1162-116">filterType</span><span class="sxs-lookup"><span data-stu-id="f1162-116">filterType</span></span> | <span data-ttu-id="f1162-117">Строка, содержащая тип фильтра.</span><span class="sxs-lookup"><span data-stu-id="f1162-117">A string containing the filter type.</span></span> <span data-ttu-id="f1162-118">Этот атрибут имеет тип <xref:System.ServiceModel.Routing.Configuration.FilterType>.</span><span class="sxs-lookup"><span data-stu-id="f1162-118">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f1162-119">Дополнительные сведения о том, как это работает с атрибутом `filterData`, см. в разделе <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1162-119">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f1162-120">name</span><span class="sxs-lookup"><span data-stu-id="f1162-120">name</span></span>       | <span data-ttu-id="f1162-121">Строка, содержащая уникальное имя этого элемента фильтра.</span><span class="sxs-lookup"><span data-stu-id="f1162-121">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f1162-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f1162-122">Child elements</span></span>

<span data-ttu-id="f1162-123">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f1162-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1162-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f1162-124">Parent elements</span></span>

| <span data-ttu-id="f1162-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="f1162-125">Element</span></span> | <span data-ttu-id="f1162-126">Описание</span><span class="sxs-lookup"><span data-stu-id="f1162-126">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="f1162-127">Раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений.</span><span class="sxs-lookup"><span data-stu-id="f1162-127">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f1162-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f1162-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
