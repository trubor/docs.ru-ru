---
description: 'Дополнительные сведения: <System. Runtime. Caching> элемент (параметры кэша)'
title: Элемент <system.runtime.caching> (параметры кэша)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 602d863caedef5c1334948b25b0caa2b0e35f685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652735"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="075ff-103">Элемент \<system.runtime.caching> (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="075ff-103">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="075ff-104">Обеспечивает настройку реализации <xref:System.Runtime.Caching.ObjectCache> в памяти по умолчанию посредством записи `memoryCache` в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="075ff-104">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="075ff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="075ff-105">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="075ff-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="075ff-106">Attributes and Elements</span></span>

<span data-ttu-id="075ff-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="075ff-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="075ff-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="075ff-108">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="075ff-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="075ff-109">Child Elements</span></span>

|<span data-ttu-id="075ff-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="075ff-110">Element</span></span>|<span data-ttu-id="075ff-111">Описание</span><span class="sxs-lookup"><span data-stu-id="075ff-111">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="075ff-112">Определяет элемент, используемый для настройки кэша, который основан на классе <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="075ff-112">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="075ff-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="075ff-113">Parent Elements</span></span>  
  
|<span data-ttu-id="075ff-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="075ff-114">Element</span></span>|<span data-ttu-id="075ff-115">Описание</span><span class="sxs-lookup"><span data-stu-id="075ff-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="075ff-116">Указывает корневой элемент в каждом файле конфигурации, который используется средой CLR и платформа .NET Framework приложениями.</span><span class="sxs-lookup"><span data-stu-id="075ff-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="075ff-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="075ff-117">Remarks</span></span>

<span data-ttu-id="075ff-118">Классы в этом пространстве имен предоставляют способ использования средств кэширования, например таких, которые имеются в ASP.NET, но без зависимости от сборки `System.Web` .</span><span class="sxs-lookup"><span data-stu-id="075ff-118">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="075ff-119">Для получения дополнительной информации см. [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="075ff-119">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="075ff-120">Функции кэширования вывода и типы в <xref:System.Runtime.Caching> пространстве имен являются новыми в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="075ff-120">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="075ff-121">Пример</span><span class="sxs-lookup"><span data-stu-id="075ff-121">Example</span></span>

<span data-ttu-id="075ff-122">В следующем примере кода показано, как настроить кэш, основанный на классе <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="075ff-122">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="075ff-123">В примере показано, как построить экземпляр записи `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="075ff-123">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="075ff-124">Для имени кэша задается имя записи кэша по умолчанию, присвоенное `name` атрибуту значения "default".</span><span class="sxs-lookup"><span data-stu-id="075ff-124">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="075ff-125">Атрибутам `cacheMemoryLimitMegabytes` и `physicalMemoryPercentage` присваивается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="075ff-125">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="075ff-126">Это означает, что эвристика автомасштабирования <xref:System.Runtime.Caching.MemoryCache> используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="075ff-126">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="075ff-127">Реализация кэша должна каждые две минуты сравнивать текущую загрузку памяти с абсолютными и процентными ограничениями по памяти.</span><span class="sxs-lookup"><span data-stu-id="075ff-127">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="075ff-128">См. также</span><span class="sxs-lookup"><span data-stu-id="075ff-128">See also</span></span>

- [<span data-ttu-id="075ff-129">\<memoryCache> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="075ff-129">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
