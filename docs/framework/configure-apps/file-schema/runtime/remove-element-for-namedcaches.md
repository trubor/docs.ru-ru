---
description: 'Дополнительные сведения о: <remove> Element для <namedCaches>'
title: Элемент <remove> для <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 5b39fc596735d746c52cdb5623962f5b9952fa3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802466"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="66b3d-103">Элемент \<remove> для \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="66b3d-103">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="66b3d-104">Удаляет элемент именованного кэша из коллекции `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="66b3d-104">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="66b3d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66b3d-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="66b3d-106">Тип</span><span class="sxs-lookup"><span data-stu-id="66b3d-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66b3d-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="66b3d-107">Attributes and Elements</span></span>  

 <span data-ttu-id="66b3d-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="66b3d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66b3d-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="66b3d-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="66b3d-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="66b3d-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="66b3d-111">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="66b3d-111">Parent Elements</span></span>  
  
|<span data-ttu-id="66b3d-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="66b3d-112">Element</span></span>|<span data-ttu-id="66b3d-113">Описание</span><span class="sxs-lookup"><span data-stu-id="66b3d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="66b3d-114">Содержит коллекцию параметров конфигурации для именованных <xref:System.Runtime.Caching.MemoryCache> экземпляров.</span><span class="sxs-lookup"><span data-stu-id="66b3d-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66b3d-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="66b3d-115">Remarks</span></span>  

 <span data-ttu-id="66b3d-116">`remove`Элемент удаляет `namedCache` запись из именованной коллекции кэша для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="66b3d-116">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b3d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="66b3d-117">See also</span></span>

- [<span data-ttu-id="66b3d-118">\<namedCaches> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="66b3d-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
