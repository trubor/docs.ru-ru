---
description: 'Дополнительные сведения: <namespaceTable>'
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 73bfac93fba3247c02c2d86d1482af2563015a76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684091"
---
# \<namespaceTable>

<span data-ttu-id="db4b5-102">Представляет секцию конфигурации для определения набора элементов, содержащих пространство имен для использования в качестве префиксов сопоставлений, которые в дальнейшем могут быть использованы в фильтрах XPath для маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="db4b5-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="db4b5-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db4b5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db4b5-104">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="db4b5-104">Attributes and elements</span></span>

<span data-ttu-id="db4b5-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="db4b5-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="db4b5-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="db4b5-106">Attributes</span></span>

<span data-ttu-id="db4b5-107">None</span><span class="sxs-lookup"><span data-stu-id="db4b5-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="db4b5-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="db4b5-108">Child elements</span></span>

|     | <span data-ttu-id="db4b5-109">Описание</span><span class="sxs-lookup"><span data-stu-id="db4b5-109">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="db4b5-110">Определяет сопоставление префикса пространства имен, используемого в выражениях XPath.</span><span class="sxs-lookup"><span data-stu-id="db4b5-110">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="db4b5-111">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="db4b5-111">Parent elements</span></span>

|     | <span data-ttu-id="db4b5-112">Описание</span><span class="sxs-lookup"><span data-stu-id="db4b5-112">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="db4b5-113">Представляет раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений, а также таблицы маршрутизации, определяющие целевые конечные точки для отправки сообщений при совпадении фильтра.</span><span class="sxs-lookup"><span data-stu-id="db4b5-113">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="db4b5-114">См. также</span><span class="sxs-lookup"><span data-stu-id="db4b5-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
