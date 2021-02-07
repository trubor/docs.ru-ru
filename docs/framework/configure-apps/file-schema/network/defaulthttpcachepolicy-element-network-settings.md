---
description: 'Дополнительные сведения о <defaultHttpCachePolicy> элементе: Element (параметры сети)'
title: Элемент <defaultHttpCachePolicy> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: d2df27c9b140c9bdb4def49aef7de1a3d80f4a11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740331"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="78add-103">Элемент \<defaultHttpCachePolicy> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="78add-103">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="78add-104">Описывает, активно ли кэширование HTTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="78add-104">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="78add-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78add-105">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78add-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="78add-106">Attributes and Elements</span></span>  

 <span data-ttu-id="78add-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="78add-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78add-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="78add-108">Attributes</span></span>  
  
|<span data-ttu-id="78add-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="78add-109">Attribute</span></span>|<span data-ttu-id="78add-110">Описание</span><span class="sxs-lookup"><span data-stu-id="78add-110">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="78add-111">Указывает максимальный интервал времени, по истечении которого кэшированный объект помечается как истекший.</span><span class="sxs-lookup"><span data-stu-id="78add-111">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="78add-112">Указывает максимальное время после истечения срока действия вычисленного объекта до пометки времени, когда кэшированный объект помечается как истекший.</span><span class="sxs-lookup"><span data-stu-id="78add-112">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="78add-113">Указывает минимальное время, в течение которого кэшированный объект будет считаться актуальным.</span><span class="sxs-lookup"><span data-stu-id="78add-113">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="78add-114">Указывает, является ли политика кэширования автоматическим, или же кэш будет пропущен.</span><span class="sxs-lookup"><span data-stu-id="78add-114">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="78add-115">Значение по умолчанию — `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="78add-115">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78add-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="78add-116">Child Elements</span></span>  

 <span data-ttu-id="78add-117">None</span><span class="sxs-lookup"><span data-stu-id="78add-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78add-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="78add-118">Parent Elements</span></span>  
  
|<span data-ttu-id="78add-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="78add-119">Element</span></span>|<span data-ttu-id="78add-120">Описание</span><span class="sxs-lookup"><span data-stu-id="78add-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78add-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="78add-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="78add-122">Управляет механизмом кэширования для сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="78add-122">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78add-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="78add-123">Remarks</span></span>  

 <span data-ttu-id="78add-124">Значение `policyLevel` атрибута может быть `BypassCache` или `Default` .</span><span class="sxs-lookup"><span data-stu-id="78add-124">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="78add-125">Значения для `maximumAge` элементов, `maximumStale` и `minimumFresh` являются либо явным временным интервалом с форматом *d*.*чч*:*мм*:*СС* (дни, часы, минуты и секунды), константы `minValue` или `maxValue` (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="78add-125">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="78add-126">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="78add-126">Configuration Files</span></span>  

 <span data-ttu-id="78add-127">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="78add-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78add-128">Пример</span><span class="sxs-lookup"><span data-stu-id="78add-128">Example</span></span>  

 <span data-ttu-id="78add-129">В следующем примере показано, как задать минимальное новое время в 6 часов, максимальное время существования, равное двум дням, и максимальное устаревшее время, равное четырем часам.</span><span class="sxs-lookup"><span data-stu-id="78add-129">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78add-130">См. также</span><span class="sxs-lookup"><span data-stu-id="78add-130">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="78add-131">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="78add-131">Network Settings Schema</span></span>](index.md)
