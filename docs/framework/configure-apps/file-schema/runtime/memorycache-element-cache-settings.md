---
description: 'Дополнительные сведения о <memoryCache> элементе: Element (параметры кэша)'
title: Элемент <memoryCache> (параметры кэша)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 1d46a156a222a0dc54e27cf56a5eb06cb1a908be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782342"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="076f5-103">Элемент \<memoryCache> (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="076f5-103">\<memoryCache> Element (Cache Settings)</span></span>

<span data-ttu-id="076f5-104">Определяет элемент, используемый для настройки кэша, который основан на классе <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-104">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="076f5-105">Класс <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> определяет элемент [memoryCache](memorycache-element-cache-settings.md) , который можно использовать для настройки кэша.</span><span class="sxs-lookup"><span data-stu-id="076f5-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="076f5-106">В одном приложении может использоваться несколько экземпляров класса <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-106">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="076f5-107">Каждый элемент `memoryCache` в файле конфигурации может содержать параметры для именованного экземпляра <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-107">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="076f5-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="076f5-108">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="076f5-109">Тип</span><span class="sxs-lookup"><span data-stu-id="076f5-109">Type</span></span>  

 <span data-ttu-id="076f5-110">Класс<xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-110"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="076f5-111">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="076f5-111">Attributes and Elements</span></span>  

 <span data-ttu-id="076f5-112">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="076f5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="076f5-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="076f5-113">Attributes</span></span>  
  
|<span data-ttu-id="076f5-114">Атрибут</span><span class="sxs-lookup"><span data-stu-id="076f5-114">Attribute</span></span>|<span data-ttu-id="076f5-115">Описание</span><span class="sxs-lookup"><span data-stu-id="076f5-115">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="076f5-116">Максимальный объем памяти в мегабайтах, который может занимать экземпляр объекта <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-116">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="076f5-117">Значение по умолчанию — 0. Это означает, что эвристика автомасштабирования класса <xref:System.Runtime.Caching.MemoryCache> используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="076f5-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="076f5-118">Имя конфигурации кэша.</span><span class="sxs-lookup"><span data-stu-id="076f5-118">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="076f5-119">Процент физической памяти, который может использоваться кэшем.</span><span class="sxs-lookup"><span data-stu-id="076f5-119">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="076f5-120">Значение по умолчанию — 0. Это означает, что эвристика автомасштабирования класса <xref:System.Runtime.Caching.MemoryCache> используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="076f5-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="076f5-121">Значение, указывающее интервал, по истечении которого реализация кэша сравнивает текущую загрузку памяти с абсолютными и процентными ограничениями по памяти, заданными для данного экземпляра кэша.</span><span class="sxs-lookup"><span data-stu-id="076f5-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="076f5-122">Значение вводится в формате "ЧЧ:ММ:СС".</span><span class="sxs-lookup"><span data-stu-id="076f5-122">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="076f5-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="076f5-123">Child Elements</span></span>  
  
|<span data-ttu-id="076f5-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="076f5-124">Element</span></span>|<span data-ttu-id="076f5-125">Описание</span><span class="sxs-lookup"><span data-stu-id="076f5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="076f5-126">Содержит коллекцию параметров конфигурации для экземпляра `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="076f5-126">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="076f5-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="076f5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="076f5-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="076f5-128">Element</span></span>|<span data-ttu-id="076f5-129">Описание</span><span class="sxs-lookup"><span data-stu-id="076f5-129">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="076f5-130">Указывает корневой элемент в каждом файле конфигурации, который используется средой CLR и платформа .NET Framework приложениями.</span><span class="sxs-lookup"><span data-stu-id="076f5-130">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="076f5-131">Содержит типы, позволяющие реализовать кэширование вывода в приложениях, встроенных в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="076f5-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="076f5-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="076f5-132">Remarks</span></span>  

 <span data-ttu-id="076f5-133">Класс <xref:System.Runtime.Caching.MemoryCache> — это конкретная реализация абстрактного класса <xref:System.Runtime.Caching.ObjectCache> .</span><span class="sxs-lookup"><span data-stu-id="076f5-133">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="076f5-134">Экземпляры класса <xref:System.Runtime.Caching.MemoryCache> можно снабдить сведениями о конфигурации из файлов конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="076f5-134">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="076f5-135">Раздел конфигурации [MemoryCache](memorycache-element-cache-settings.md) содержит коллекцию конфигураций `namedCaches` .</span><span class="sxs-lookup"><span data-stu-id="076f5-135">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="076f5-136">При инициализации объекта кэша на базе памяти он сначала пытается найти запись `namedCaches` , которая соответствует имени в параметре, передаваемом конструктору кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="076f5-136">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="076f5-137">Если запись `namedCaches` найдена, из файла конфигурации извлекаются сведения об опросах и управлении памятью.</span><span class="sxs-lookup"><span data-stu-id="076f5-137">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="076f5-138">После этого процесс инициализации определяет, были ли переопределены какие-либо записи конфигурации, с помощью дополнительной коллекцию пар имя-значение для сведений о конфигурации в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="076f5-138">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="076f5-139">Если передать в коллекцию пар имя-значение любое из следующих значений, оно переопределит сведения, полученные из файла конфигурации:</span><span class="sxs-lookup"><span data-stu-id="076f5-139">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="076f5-140">Пример</span><span class="sxs-lookup"><span data-stu-id="076f5-140">Example</span></span>  

 <span data-ttu-id="076f5-141">В следующем примере показано, как задать имя <xref:System.Runtime.Caching.MemoryCache> объекта в качестве имени объекта кэша по умолчанию, задав `name` для атрибута значение Default.</span><span class="sxs-lookup"><span data-stu-id="076f5-141">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="076f5-142">Атрибутам `cacheMemoryLimitMegabytes` и `physicalMemoryLimitPercentage` присваивается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="076f5-142">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="076f5-143">Это означает, что эвристика автомасштабирования <xref:System.Runtime.Caching.MemoryCache> используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="076f5-143">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="076f5-144">Реализация кэша должна каждые две минуты сравнивать текущую загрузку памяти с абсолютными и процентными ограничениями по памяти.</span><span class="sxs-lookup"><span data-stu-id="076f5-144">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="076f5-145">См. также</span><span class="sxs-lookup"><span data-stu-id="076f5-145">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="076f5-146">\<system.runtime.caching> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="076f5-146">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="076f5-147">\<namedCaches> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="076f5-147">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
