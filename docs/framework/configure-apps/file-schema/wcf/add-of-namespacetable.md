---
description: 'Дополнительные сведения <add> о: <namespaceTable>'
title: <add> из <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: b7804bdec4a1fb2199c81ba0dde031b80b451d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750264"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="49cbc-103">\<add> из \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="49cbc-103">\<add> of \<namespaceTable></span></span>

<span data-ttu-id="49cbc-104">Представляет элемент конфигурации, содержащий пространство имен, используемое в качестве префикса сопоставления, которое затем можно использовать в фильтрах XPath для маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="49cbc-104">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="49cbc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49cbc-105">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49cbc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="49cbc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="49cbc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="49cbc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49cbc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="49cbc-108">Attributes</span></span>  
  
|<span data-ttu-id="49cbc-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="49cbc-109">Attribute</span></span>|<span data-ttu-id="49cbc-110">Описание</span><span class="sxs-lookup"><span data-stu-id="49cbc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49cbc-111">пространство имен</span><span class="sxs-lookup"><span data-stu-id="49cbc-111">namespace</span></span>|<span data-ttu-id="49cbc-112">Строка, содержащая пространство имен.</span><span class="sxs-lookup"><span data-stu-id="49cbc-112">A string containing the namespace.</span></span>|  
|<span data-ttu-id="49cbc-113">prefix</span><span class="sxs-lookup"><span data-stu-id="49cbc-113">prefix</span></span>|<span data-ttu-id="49cbc-114">Строка, содержащая префикс этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="49cbc-114">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49cbc-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="49cbc-115">Child Elements</span></span>  

 <span data-ttu-id="49cbc-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="49cbc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49cbc-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="49cbc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="49cbc-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="49cbc-118">Element</span></span>|<span data-ttu-id="49cbc-119">Описание</span><span class="sxs-lookup"><span data-stu-id="49cbc-119">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="49cbc-120">Представляет секцию конфигурации для определения набора элементов, содержащих пространство имен для использования в качестве префиксов сопоставлений, которые в дальнейшем могут быть использованы в фильтрах XPath для маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="49cbc-120">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49cbc-121">См. также</span><span class="sxs-lookup"><span data-stu-id="49cbc-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
