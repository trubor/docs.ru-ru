---
description: 'Дополнительные сведения о <requestCaching> элементе: Element (параметры сети)'
title: Элемент <requestCaching> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: d09da8ad7a38ac363aaa740cca4de25e33fa8c56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698561"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="037c0-103">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="037c0-103">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="037c0-104">Управляет механизмом кэширования для сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="037c0-104">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="037c0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="037c0-105">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="037c0-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="037c0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="037c0-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="037c0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="037c0-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="037c0-108">Attributes</span></span>  
  
|<span data-ttu-id="037c0-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="037c0-109">Attribute</span></span>|<span data-ttu-id="037c0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="037c0-110">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="037c0-111">Указывает, обеспечивает ли кэш изоляцию между данными разных пользователей.</span><span class="sxs-lookup"><span data-stu-id="037c0-111">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="037c0-112">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="037c0-112">The default value is `true`.</span></span> <span data-ttu-id="037c0-113">Это значение должно быть `false` для приложений среднего уровня.</span><span class="sxs-lookup"><span data-stu-id="037c0-113">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="037c0-114">Указывает, что кэширование отключено для всех веб-ответов и не может быть переопределено программным способом.</span><span class="sxs-lookup"><span data-stu-id="037c0-114">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="037c0-115">Одно из значений в перечислении <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="037c0-115">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="037c0-116">Значение по умолчанию — `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="037c0-116">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="037c0-117">Задает время по умолчанию, по истечении которого содержимое помечается как просроченное.</span><span class="sxs-lookup"><span data-stu-id="037c0-117">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="037c0-118">Атрибут Полицилевел</span><span class="sxs-lookup"><span data-stu-id="037c0-118">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="037c0-119">Значение</span><span class="sxs-lookup"><span data-stu-id="037c0-119">Value</span></span>|<span data-ttu-id="037c0-120">Описание</span><span class="sxs-lookup"><span data-stu-id="037c0-120">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="037c0-121">Возвращает кэшированный ресурс, если ресурс является актуальным, длина содержимого является точной, а атрибуты срока действия, изменения и длины содержимого существуют.</span><span class="sxs-lookup"><span data-stu-id="037c0-121">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="037c0-122">Возвращает ресурс с сервера.</span><span class="sxs-lookup"><span data-stu-id="037c0-122">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="037c0-123">Возвращает кэшированный ресурс, если длина содержимого имеется и соответствует размеру записи.</span><span class="sxs-lookup"><span data-stu-id="037c0-123">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="037c0-124">Возвращает кэшированный ресурс, если длина содержимого указана и соответствует размеру записи. в противном случае ресурс загружается с сервера и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="037c0-124">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="037c0-125">Возвращает кэшированный ресурс, если метка времени кэшированного ресурса совпадает с меткой времени ресурса на сервере. в противном случае ресурс загружается с сервера, хранится в кэше, и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="037c0-125">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="037c0-126">Скачивает ресурс с сервера, сохраняет его в кэше и возвращает ресурс вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="037c0-126">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="037c0-127">Если кэшированный ресурс существует, он удаляется.</span><span class="sxs-lookup"><span data-stu-id="037c0-127">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="037c0-128">Ресурс загружается с сервера и возвращается вызывающему.</span><span class="sxs-lookup"><span data-stu-id="037c0-128">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="037c0-129">Удовлетворяет запросу, используя кэшированную копию ресурса, если отметка времени совпадает с меткой времени ресурса на сервере. в противном случае ресурс загружается с сервера, представленного вызывающему объекту, и хранится в кэше.</span><span class="sxs-lookup"><span data-stu-id="037c0-129">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="037c0-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="037c0-130">Child Elements</span></span>  
  
|<span data-ttu-id="037c0-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="037c0-131">Element</span></span>|<span data-ttu-id="037c0-132">Описание</span><span class="sxs-lookup"><span data-stu-id="037c0-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="037c0-133">дефаулсттпкачеполици</span><span class="sxs-lookup"><span data-stu-id="037c0-133">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="037c0-134">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="037c0-134">Optional element.</span></span><br /><br /> <span data-ttu-id="037c0-135">Описывает, активно ли кэширование HTTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="037c0-135">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="037c0-136">Элемент \<defaultFtpCachePolicy> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="037c0-136">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="037c0-137">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="037c0-137">Optional element.</span></span><br /><br /> <span data-ttu-id="037c0-138">Описывает, активно ли кэширование FTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="037c0-138">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="037c0-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="037c0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="037c0-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="037c0-140">Element</span></span>|<span data-ttu-id="037c0-141">Описание</span><span class="sxs-lookup"><span data-stu-id="037c0-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="037c0-142">system.net</span><span class="sxs-lookup"><span data-stu-id="037c0-142">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="037c0-143">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="037c0-143">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="037c0-144">Пример</span><span class="sxs-lookup"><span data-stu-id="037c0-144">Example</span></span>  

 <span data-ttu-id="037c0-145">В следующем примере показано, как отключить все кэширование.</span><span class="sxs-lookup"><span data-stu-id="037c0-145">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="037c0-146">См. также</span><span class="sxs-lookup"><span data-stu-id="037c0-146">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="037c0-147">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="037c0-147">Network Settings Schema</span></span>](index.md)
