---
description: 'Дополнительные сведения о: <add> Element для <namedCaches>'
title: Элемент <add> для <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 1485b80fa84268f68759bfb50744133744142d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802428"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="9101f-103">Элемент \<add> для \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="9101f-103">\<add> Element for \<namedCaches></span></span>

<span data-ttu-id="9101f-104">Добавляет `namedCache` запись в `namedCaches` коллекцию для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="9101f-104">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9101f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9101f-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="9101f-106">Тип</span><span class="sxs-lookup"><span data-stu-id="9101f-106">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9101f-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9101f-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9101f-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9101f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9101f-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9101f-109">Attributes</span></span>  
  
|<span data-ttu-id="9101f-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9101f-110">Attribute</span></span>|<span data-ttu-id="9101f-111">Описание</span><span class="sxs-lookup"><span data-stu-id="9101f-111">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="9101f-112">Целочисленное значение, указывающее максимально допустимый размер (в мегабайтах), <xref:System.Runtime.Caching.MemoryCache> до которого может увеличиваться экземпляр.</span><span class="sxs-lookup"><span data-stu-id="9101f-112">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="9101f-113">Значение по умолчанию — 0. Это означает, что <xref:System.Runtime.Caching.MemoryCache> по умолчанию используется эвристика автоопределения размеров класса.</span><span class="sxs-lookup"><span data-stu-id="9101f-113">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="9101f-114">Имя кэша.</span><span class="sxs-lookup"><span data-stu-id="9101f-114">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="9101f-115">Целочисленное значение от 0 до 100, которое указывает максимальный процент физической памяти компьютера, который может потребляться кэшем.</span><span class="sxs-lookup"><span data-stu-id="9101f-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="9101f-116">Значение по умолчанию — 0. Это означает, что <xref:System.Runtime.Caching.MemoryCache> по умолчанию используется эвристика автоопределения размеров класса.</span><span class="sxs-lookup"><span data-stu-id="9101f-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="9101f-117">Значение, указывающее интервал, по истечении которого реализация кэша сравнивает текущую загрузку памяти с абсолютными и процентными ограничениями по памяти, заданными для данного экземпляра кэша.</span><span class="sxs-lookup"><span data-stu-id="9101f-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="9101f-118">Это значение указывается в формате "чч: мм: СС".</span><span class="sxs-lookup"><span data-stu-id="9101f-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9101f-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9101f-119">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="9101f-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9101f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9101f-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="9101f-121">Element</span></span>|<span data-ttu-id="9101f-122">Описание</span><span class="sxs-lookup"><span data-stu-id="9101f-122">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="9101f-123">Содержит коллекцию параметров конфигурации для именованных <xref:System.Runtime.Caching.MemoryCache> экземпляров.</span><span class="sxs-lookup"><span data-stu-id="9101f-123">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9101f-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="9101f-124">Remarks</span></span>  

 <span data-ttu-id="9101f-125">`add`Элемент добавляет запись в `namedCaches` коллекцию для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="9101f-125">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="9101f-126">Элемент [clear](clear-element-for-namedcaches.md) можно использовать перед тем, как использовать `add` элемент, чтобы убедиться в отсутствии других именованных кэшей в коллекции.</span><span class="sxs-lookup"><span data-stu-id="9101f-126">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="9101f-127">Этот элемент можно использовать в файле machine.config и в файле Web.config.</span><span class="sxs-lookup"><span data-stu-id="9101f-127">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9101f-128">Пример</span><span class="sxs-lookup"><span data-stu-id="9101f-128">Example</span></span>  

 <span data-ttu-id="9101f-129">В следующем примере показано, как определить параметры для записи по умолчанию в `namedCache` `namedCaches` коллекцию для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="9101f-129">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9101f-130">См. также</span><span class="sxs-lookup"><span data-stu-id="9101f-130">See also</span></span>

- [<span data-ttu-id="9101f-131">\<namedCaches> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="9101f-131">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
