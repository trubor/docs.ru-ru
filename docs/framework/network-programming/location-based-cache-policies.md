---
description: 'Узнайте подробнее о: политики кэша на основе расположения'
title: политики кэша на основе расположения
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: ef770b45f173fee66c80d721766a0be6244bbeb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662719"
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="dfa3a-103">политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="dfa3a-103">Location-Based Cache Policies</span></span>

<span data-ttu-id="dfa3a-104">Политики кэша на основе расположения определяют актуальность действительных записей в кэше на основе расположения, в котором может быть получен запрашиваемый ресурс.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-104">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="dfa3a-105">Кэшируемый ресурс является действительным, если он не нарушает требований сервера по повторной проверке.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-105">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="dfa3a-106">Политика кэша на основе расположения создается программным способом с помощью конструктора класса <xref:System.Net.Cache.RequestCachePolicy> или <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-106">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="dfa3a-107">Тип политики на основе расположения передается в конструктор с помощью значения перечисления <xref:System.Net.Cache.RequestCacheLevel> или <xref:System.Net.Cache.HttpRequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-107">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="dfa3a-108">Примеры кода с созданием политик на основе расположения см. в разделе [Практическое руководство. Установка политики кэша на основе расположения для приложения](how-to-set-a-location-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-108">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="dfa3a-109">В следующих разделах приводится описание каждого типа политики кэша на основе расположения для ресурсов HTTP и HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-109">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="dfa3a-110">Политика "Из кэша при наличии"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-110">Cache If Available Policy</span></span>  

 <span data-ttu-id="dfa3a-111">Если действительный запрошенный ресурс есть в локальном кэше, используется кэшированный ресурс; в противном случае запрос к ресурсу отправляется на сервер.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-111">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="dfa3a-112">Если запрошенный ресурс доступен в любом кэше между клиентом и сервером, запрос будет выполнен промежуточным кэшем.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-112">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="dfa3a-113">Политика "Только из кэша"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-113">Cache Only Policy</span></span>  

 <span data-ttu-id="dfa3a-114">Если действительный запрошенный ресурс есть в локальном кэше, используется кэшированный ресурс.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-114">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="dfa3a-115">При указании этого уровня политики кэша исключение <xref:System.Net.WebException> выдается, если элемент не существует в локальном кэше.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-115">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="dfa3a-116">Политика "Только из локального кэша"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-116">Cache Or Next Cache Only Policy</span></span>  

 <span data-ttu-id="dfa3a-117">Если действительный запрошенный ресурс есть в локальном кэше или в промежуточном кэше в локальной сети, используется кэшированный ресурс.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-117">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="dfa3a-118">В противном случае возникнет исключение <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-118">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="dfa3a-119">В протоколе кэширования HTTP для этого используется директива управления кэшем "Только если содержится в кэше" (only-if-cached).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-119">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="dfa3a-120">Политика "Не использовать кэш"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-120">No Cache No Store Policy</span></span>  

 <span data-ttu-id="dfa3a-121">В этой политике запрошенные ресурсы из кэша никогда не используются, а ресурсы никогда не помещаются в кэш.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-121">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="dfa3a-122">Если запрошенный ресурс присутствует в локальном кэше, он удаляется.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-122">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="dfa3a-123">При использовании этого уровня политики также удаляется ресурс в промежуточном кэше.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-123">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="dfa3a-124">В протоколе кэширования HTTP для этого используется директива управления кэшем "Не сохранять в кэше" (no-store).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-124">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="dfa3a-125">Политика "Обновление"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-125">Refresh Policy</span></span>  

 <span data-ttu-id="dfa3a-126">Запрошенный ресурс может использоваться, если он получен с сервера или найден в кэше (за исключением локального кэша).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-126">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="dfa3a-127">Перед использованием результата из промежуточного кэша в качестве ответа на запрос кэш должен повторно проверить кэшированную запись для этого результата, обратившись к серверу.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-127">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="dfa3a-128">В протоколе кэширования HTTP для этого используются директива управления кэшем "Максимальный возраст — 0" (max-age = 0) и заголовок Pragma "Без кэширования" (no-cache).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-128">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="dfa3a-129">политика повторной загрузки</span><span class="sxs-lookup"><span data-stu-id="dfa3a-129">Reload Policy</span></span>  

 <span data-ttu-id="dfa3a-130">Запрошенные ресурсы необходимо получать от сервера.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-130">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="dfa3a-131">Ответ может быть сохранен в локальном кэше.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-131">The response might be saved in the local cache.</span></span> <span data-ttu-id="dfa3a-132">В протоколе кэширования HTTP для этого используются директива управления кэшем "Не сохранять в кэше" (no-store) и заголовок Pragma "Без кэширования" (no-cache).</span><span class="sxs-lookup"><span data-stu-id="dfa3a-132">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="dfa3a-133">Политика "Повторная проверка"</span><span class="sxs-lookup"><span data-stu-id="dfa3a-133">Revalidate Policy</span></span>  

 <span data-ttu-id="dfa3a-134">Сравнивает копию ресурса в кэше с копией на сервере.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-134">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="dfa3a-135">Если копия на сервере более свежая, эта копия возвращается в ответ на запрос и записывается в кэш.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-135">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="dfa3a-136">Если копия в кэше аналогична копии на сервере, возвращается копия из кэша.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-136">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="dfa3a-137">В протоколе кэширования HTTP для этого используется условный запрос.</span><span class="sxs-lookup"><span data-stu-id="dfa3a-137">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa3a-138">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dfa3a-138">See also</span></span>

- [<span data-ttu-id="dfa3a-139">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="dfa3a-139">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="dfa3a-140">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="dfa3a-140">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="dfa3a-141">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="dfa3a-141">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="dfa3a-142">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="dfa3a-142">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="dfa3a-143">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="dfa3a-143">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
