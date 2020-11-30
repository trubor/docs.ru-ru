---
title: политики кэша на основе времени
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 372621ce55891cb87594e6d059c7bbeeb99f6468
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239423"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="9939b-102">политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="9939b-102">Time-Based Cache Policies</span></span>

<span data-ttu-id="9939b-103">Политика кэша на основе времени определяет актуальность записей в кэше на основе времени извлечения ресурса, заголовков, возвращаемых вместе с ним, и текущего времени.</span><span class="sxs-lookup"><span data-stu-id="9939b-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="9939b-104">При задании политики кэша на основе времени можно использовать политику на основе времени <xref:System.Net.Cache.HttpRequestCacheLevel.Default> или создать настраиваемую политику на основе времени.</span><span class="sxs-lookup"><span data-stu-id="9939b-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="9939b-105">При использовании политики на основе времени по умолчанию для ресурсов, полученных по протоколу HTTP, способ кэширования определяется заголовками, включенными в кэшированный ответ, и поведением, описанным в разделах 13 и 14 документа RFC 2616, который доступен на веб-сайте [IETF](https://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="9939b-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="9939b-106">Пример кода, в котором демонстрируется задание политики на основе времени по умолчанию для ресурсов HTTP, см. в разделе [Практическое руководство. Установка политики кэша для приложения на основе времени по умолчанию](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="9939b-106">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="9939b-107">Примеры кода, демонстрирующие создание и использование политик кэша, см. в разделе [Настройка кэширования в сетевых приложениях](configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="9939b-107">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="9939b-108">Критерии для определения актуальности записей в кэше</span><span class="sxs-lookup"><span data-stu-id="9939b-108">Criteria to Determine Freshness of Cached Entries</span></span>  

 <span data-ttu-id="9939b-109">Для настройки политики кэша на основе времени можно настроить один или несколько из следующих критериев актуальности записей в кэше:</span><span class="sxs-lookup"><span data-stu-id="9939b-109">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="9939b-110">максимальный срок действия;</span><span class="sxs-lookup"><span data-stu-id="9939b-110">Maximum age</span></span>  
  
- <span data-ttu-id="9939b-111">максимальный возраст;</span><span class="sxs-lookup"><span data-stu-id="9939b-111">Maximum staleness</span></span>  
  
- <span data-ttu-id="9939b-112">минимальная актуальность;</span><span class="sxs-lookup"><span data-stu-id="9939b-112">Minimum freshness</span></span>  
  
- <span data-ttu-id="9939b-113">дата синхронизации кэша.</span><span class="sxs-lookup"><span data-stu-id="9939b-113">Cache synchronization date</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9939b-114">Использование кэша политики на основе времени по умолчанию не следует путать с заданием политики кэша по умолчанию для приложения.</span><span class="sxs-lookup"><span data-stu-id="9939b-114">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="9939b-115">Политика на основе времени по умолчанию — это конкретная политика, которую можно использовать на уровне приложения или запросов.</span><span class="sxs-lookup"><span data-stu-id="9939b-115">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="9939b-116">Политика кэша по умолчанию для приложения — это политика (на основе расположения или времени), которая вступает в силу, если политика для запроса не задана.</span><span class="sxs-lookup"><span data-stu-id="9939b-116">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="9939b-117">Подробные сведения о задании политики кэша по умолчанию для приложения см. в разделе <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="9939b-117">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="9939b-118">Максимальный срок действия</span><span class="sxs-lookup"><span data-stu-id="9939b-118">Maximum Age</span></span>  

 <span data-ttu-id="9939b-119">Критерий максимального срока действия определяет то, как долго может использоваться кэшированная копия ресурса.</span><span class="sxs-lookup"><span data-stu-id="9939b-119">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="9939b-120">Если указанный срок действия кэшированной копии ресурса истек, ресурс необходимо проверить повторно, сравнив его с содержимым на сервере.</span><span class="sxs-lookup"><span data-stu-id="9939b-120">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="9939b-121">Если использование ресурса по истечении срока действия разрешено, этот критерий не учитывается, если только также не задано значение максимального возраста.</span><span class="sxs-lookup"><span data-stu-id="9939b-121">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="9939b-122">Максимальный возраст</span><span class="sxs-lookup"><span data-stu-id="9939b-122">Maximum Staleness</span></span>  

 <span data-ttu-id="9939b-123">Критерий максимального возраста определяет то, как долго может использоваться кэшированная копия ресурса после истечения срока ее действия.</span><span class="sxs-lookup"><span data-stu-id="9939b-123">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="9939b-124">Это единственный критерий политики кэша, который разрешает использовать ресурсы с истекшим сроком действия.</span><span class="sxs-lookup"><span data-stu-id="9939b-124">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="9939b-125">Минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="9939b-125">Minimum Freshness</span></span>  

 <span data-ttu-id="9939b-126">Критерий минимальной актуальности определяет период времени до истечения срока действия, до которого может использоваться кэшированная копия ресурса.</span><span class="sxs-lookup"><span data-stu-id="9939b-126">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="9939b-127">Вследствие этой политики срок действия записи в кэше истекает до назначенного времени. Таким образом, параметры минимальной актуальности и максимального возраста являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="9939b-127">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="9939b-128">Дата синхронизации кэша</span><span class="sxs-lookup"><span data-stu-id="9939b-128">Cache Synchronization Date</span></span>  

 <span data-ttu-id="9939b-129">Критерий даты синхронизации кэша определяет то, когда необходимо повторно проверить кэшированную копию ресурса, сравнив ее с содержимым на сервере.</span><span class="sxs-lookup"><span data-stu-id="9939b-129">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="9939b-130">Если содержимое изменилось с момента кэширования объекта, он извлекается с сервера, сохраняется в кэше и возвращается приложению.</span><span class="sxs-lookup"><span data-stu-id="9939b-130">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="9939b-131">Если содержимое не изменилось, его метка времени обновляется и приложение получает содержимое из кэша.</span><span class="sxs-lookup"><span data-stu-id="9939b-131">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="9939b-132">С помощью даты синхронизации кэша можно указать абсолютную дату, когда кэшированное содержимое должно быть проверено повторно.</span><span class="sxs-lookup"><span data-stu-id="9939b-132">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="9939b-133">Если актуальная запись в кэше была в последний раз повторно проверена до даты синхронизации кэша, повторная проверка все же выполняется.</span><span class="sxs-lookup"><span data-stu-id="9939b-133">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="9939b-134">Если запись в кэше была повторно проверена после даты синхронизации кэша и нет дополнительных требований к актуальности или повторной проверке на сервере, используется запись из кэша.</span><span class="sxs-lookup"><span data-stu-id="9939b-134">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="9939b-135">Если дата синхронизации кэша — это будущая дата, запись повторно проверяется каждый раз, когда она запрашивается, пока эта дата не пройдет.</span><span class="sxs-lookup"><span data-stu-id="9939b-135">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="9939b-136">В следующих разделах приводятся сведения о том, как действуют различные сочетания критериев для политики кэша на основе времени:</span><span class="sxs-lookup"><span data-stu-id="9939b-136">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="9939b-137">Взаимодействие с политикой кэша: максимальный возраст и устаревание</span><span class="sxs-lookup"><span data-stu-id="9939b-137">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="9939b-138">Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="9939b-138">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="9939b-139">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9939b-139">See also</span></span>

- [<span data-ttu-id="9939b-140">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="9939b-140">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="9939b-141">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="9939b-141">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="9939b-142">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="9939b-142">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="9939b-143">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="9939b-143">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="9939b-144">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="9939b-144">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
