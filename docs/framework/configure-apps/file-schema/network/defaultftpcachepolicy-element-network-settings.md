---
description: 'Дополнительные сведения о <defaultFtpCachePolicy> элементе: Element (параметры сети)'
title: Элемент <defaultFtpCachePolicy> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 77150ce0980e96dd949df4b5ad7e4557ed1b991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740370"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="b3b9d-103">Элемент \<defaultFtpCachePolicy> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="b3b9d-103">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="b3b9d-104">Описывает, активно ли кэширование FTP и описывает политику кэширования по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-104">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="b3b9d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3b9d-105">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3b9d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b3b9d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b3b9d-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3b9d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b3b9d-108">Attributes</span></span>  
  
|<span data-ttu-id="b3b9d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b3b9d-109">Attribute</span></span>|<span data-ttu-id="b3b9d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b3b9d-110">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="b3b9d-111">Указывает политику кэширования FTP.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-111">Specifies the FTP caching policy.</span></span> <span data-ttu-id="b3b9d-112">Значение по умолчанию — `Default`.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-112">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="b3b9d-113">Атрибут Полицилевел</span><span class="sxs-lookup"><span data-stu-id="b3b9d-113">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="b3b9d-114">Значение</span><span class="sxs-lookup"><span data-stu-id="b3b9d-114">Value</span></span>|<span data-ttu-id="b3b9d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b3b9d-115">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="b3b9d-116">Возвращает кэшированный ресурс, если ресурс является актуальным, длина содержимого является точной, а атрибуты срока действия, изменения и длины содержимого существуют.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-116">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="b3b9d-117">Возвращает ресурс с сервера.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-117">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="b3b9d-118">Возвращает кэшированный ресурс, если длина содержимого имеется и соответствует размеру записи.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-118">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="b3b9d-119">Возвращает кэшированный ресурс, если длина содержимого указана и соответствует размеру записи. в противном случае ресурс загружается с сервера и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-119">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="b3b9d-120">Возвращает кэшированный ресурс, если метка времени кэшированного ресурса совпадает с меткой времени ресурса на сервере. в противном случае ресурс загружается с сервера, хранится в кэше и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-120">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="b3b9d-121">Скачивает ресурс с сервера, сохраняет его в кэше и возвращает ресурс вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-121">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="b3b9d-122">Если кэшированный ресурс существует, он удаляется.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-122">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="b3b9d-123">Ресурс загружается с сервера и возвращается вызывающему.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-123">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="b3b9d-124">Выполняет запрос, используя кэшированную копию ресурса, если метка времени ресурса совпадает с меткой времени ресурса на сервере, в противном случае ресурс загружается с сервера, представляется вызывающему объекту и сохраняется в кэше.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-124">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3b9d-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b3b9d-125">Child Elements</span></span>  

 <span data-ttu-id="b3b9d-126">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3b9d-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b3b9d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b3b9d-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="b3b9d-128">Element</span></span>|<span data-ttu-id="b3b9d-129">Описание</span><span class="sxs-lookup"><span data-stu-id="b3b9d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3b9d-130">requestCaching</span><span class="sxs-lookup"><span data-stu-id="b3b9d-130">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="b3b9d-131">Управляет механизмом кэширования для сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="b3b9d-131">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3b9d-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3b9d-132">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3b9d-133">Пример</span><span class="sxs-lookup"><span data-stu-id="b3b9d-133">Example</span></span>  

 <span data-ttu-id="b3b9d-134">В следующем примере показано, как задать политику кэширования FTP для `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="b3b9d-134">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3b9d-135">См. также</span><span class="sxs-lookup"><span data-stu-id="b3b9d-135">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="b3b9d-136">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="b3b9d-136">Network Settings Schema</span></span>](index.md)
