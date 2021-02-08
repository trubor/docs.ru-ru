---
description: 'Дополнительные сведения о <namedCaches> элементе: Element (параметры кэша)'
title: Элемент <namedCaches> (параметры кэша)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 543650513270c0cee24d965b8efe98a75d7b8f9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782329"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="aee14-103">Элемент \<namedCaches> (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="aee14-103">\<namedCaches> Element (Cache Settings)</span></span>

<span data-ttu-id="aee14-104">Задает коллекцию параметров конфигурации для именованных <xref:System.Runtime.Caching.MemoryCache> экземпляров.</span><span class="sxs-lookup"><span data-stu-id="aee14-104">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="aee14-105"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Свойство ссылается на коллекцию параметров конфигурации из одного или нескольких `namedCaches` элементов файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="aee14-105">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="aee14-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aee14-106">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="aee14-107">Тип</span><span class="sxs-lookup"><span data-stu-id="aee14-107">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aee14-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="aee14-108">Attributes and Elements</span></span>  

 <span data-ttu-id="aee14-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="aee14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aee14-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="aee14-110">Attributes</span></span>  
  
|<span data-ttu-id="aee14-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="aee14-111">Attribute</span></span>|<span data-ttu-id="aee14-112">Описание</span><span class="sxs-lookup"><span data-stu-id="aee14-112">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="aee14-113">Целочисленное значение, указывающее максимально допустимый размер (в мегабайтах), <xref:System.Runtime.Caching.MemoryCache> до которого может увеличиваться экземпляр.</span><span class="sxs-lookup"><span data-stu-id="aee14-113">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="aee14-114">Значение по умолчанию — 0. Это означает, что по умолчанию используется эвристика автоподбора размера <xref:System.Runtime.Caching.MemoryCache> класса.</span><span class="sxs-lookup"><span data-stu-id="aee14-114">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="aee14-115">Имя кэша.</span><span class="sxs-lookup"><span data-stu-id="aee14-115">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="aee14-116">Целочисленное значение от 0 до 100, которое указывает максимальный процент физической памяти компьютера, который может потребляться кэшем.</span><span class="sxs-lookup"><span data-stu-id="aee14-116">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="aee14-117">Значение по умолчанию — 0. Это означает, что по умолчанию используется эвристика автоподбора размера <xref:System.Runtime.Caching.MemoryCache> класса.</span><span class="sxs-lookup"><span data-stu-id="aee14-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="aee14-118">Значение, указывающее интервал, по истечении которого реализация кэша сравнивает текущую загрузку памяти с абсолютными и процентными ограничениями по памяти, заданными для данного экземпляра кэша.</span><span class="sxs-lookup"><span data-stu-id="aee14-118">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="aee14-119">Это значение указывается в формате "чч: мм: СС".</span><span class="sxs-lookup"><span data-stu-id="aee14-119">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aee14-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="aee14-120">Child Elements</span></span>  
  
|<span data-ttu-id="aee14-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="aee14-121">Element</span></span>|<span data-ttu-id="aee14-122">Описание</span><span class="sxs-lookup"><span data-stu-id="aee14-122">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="aee14-123">Добавляет именованный кэш к коллекции `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="aee14-123">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="aee14-124">Очищает коллекцию `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="aee14-124">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="aee14-125">Удаляет элемент именованного кэша из коллекции `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="aee14-125">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aee14-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="aee14-126">Parent Elements</span></span>  
  
|<span data-ttu-id="aee14-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="aee14-127">Element</span></span>|<span data-ttu-id="aee14-128">Описание</span><span class="sxs-lookup"><span data-stu-id="aee14-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="aee14-129">Указывает корневой элемент в каждом файле конфигурации, который используется средой CLR и платформа .NET Framework приложениями.</span><span class="sxs-lookup"><span data-stu-id="aee14-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="aee14-130">Определяет элемент, используемый для настройки кэша, который основан на классе <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="aee14-130">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="aee14-131">Содержит типы, позволяющие реализовать кэширование вывода в приложениях, встроенных в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aee14-131">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aee14-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="aee14-132">Remarks</span></span>  

 <span data-ttu-id="aee14-133">Раздел конфигурации кэша памяти файла Web.config может содержать `add` `remove` атрибуты, и `clear` для `namedCaches` коллекции.</span><span class="sxs-lookup"><span data-stu-id="aee14-133">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="aee14-134">Каждая `namedCaches` запись уникально идентифицируется `name` атрибутом.</span><span class="sxs-lookup"><span data-stu-id="aee14-134">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="aee14-135">Экземпляры записей кэша памяти можно получить, обратившись к сведениям в файлах конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="aee14-135">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="aee14-136">По умолчанию в файле конфигурации содержится запись только для экземпляра кэша по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aee14-136">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="aee14-137">Экземпляром кэша по умолчанию является экземпляр, который возвращается из <xref:System.Runtime.Caching.MemoryCache.Default%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="aee14-137">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="aee14-138">Если для атрибута name задано значение Default, то элемент использует экземпляр кэша памяти по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aee14-138">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aee14-139">Пример</span><span class="sxs-lookup"><span data-stu-id="aee14-139">Example</span></span>  

 <span data-ttu-id="aee14-140">В следующем примере показано, как задать имя кэша в качестве имени записи кэша по умолчанию, задав `name` для атрибута значение Default.</span><span class="sxs-lookup"><span data-stu-id="aee14-140">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="aee14-141">Атрибутам `cacheMemoryLimitMegabytes` и `physicalMemoryPercentage` присваивается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="aee14-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="aee14-142">Установка этих атрибутов равным нулю означает, что используется эвристический подход автоподбора размера <xref:System.Runtime.Caching.MemoryCache> класса.</span><span class="sxs-lookup"><span data-stu-id="aee14-142">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="aee14-143">Реализация кэша сравнивает текущую загрузку памяти с абсолютными и процентными ограничениями памяти каждые две минуты.</span><span class="sxs-lookup"><span data-stu-id="aee14-143">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aee14-144">См. также</span><span class="sxs-lookup"><span data-stu-id="aee14-144">See also</span></span>

- [<span data-ttu-id="aee14-145">\<memoryCache> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="aee14-145">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
