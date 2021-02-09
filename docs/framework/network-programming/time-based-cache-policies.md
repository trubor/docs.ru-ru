---
description: 'Узнайте подробнее о: политики кэша на основе времени'
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
ms.openlocfilehash: 42a76be0da664899295a583d72477de0698cc39e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712302"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="8bd18-103">политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="8bd18-103">Time-Based Cache Policies</span></span>

<span data-ttu-id="8bd18-104">Политика кэша на основе времени определяет актуальность записей в кэше на основе времени извлечения ресурса, заголовков, возвращаемых вместе с ним, и текущего времени.</span><span class="sxs-lookup"><span data-stu-id="8bd18-104">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="8bd18-105">При задании политики кэша на основе времени можно использовать политику на основе времени <xref:System.Net.Cache.HttpRequestCacheLevel.Default> или создать настраиваемую политику на основе времени.</span><span class="sxs-lookup"><span data-stu-id="8bd18-105">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="8bd18-106">При использовании политики на основе времени по умолчанию для ресурсов, полученных по протоколу HTTP, способ кэширования определяется заголовками, включенными в кэшированный ответ, и поведением, описанным в разделах 13 и 14 документа RFC 2616, который доступен на веб-сайте [IETF](https://www.ietf.org/).</span><span class="sxs-lookup"><span data-stu-id="8bd18-106">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="8bd18-107">Пример кода, в котором демонстрируется задание политики на основе времени по умолчанию для ресурсов HTTP, см. в разделе [Практическое руководство. Установка политики кэша для приложения на основе времени по умолчанию](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="8bd18-107">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="8bd18-108">Примеры кода, демонстрирующие создание и использование политик кэша, см. в разделе [Настройка кэширования в сетевых приложениях](configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="8bd18-108">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="8bd18-109">Критерии для определения актуальности записей в кэше</span><span class="sxs-lookup"><span data-stu-id="8bd18-109">Criteria to Determine Freshness of Cached Entries</span></span>  

 <span data-ttu-id="8bd18-110">Для настройки политики кэша на основе времени можно настроить один или несколько из следующих критериев актуальности записей в кэше:</span><span class="sxs-lookup"><span data-stu-id="8bd18-110">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="8bd18-111">максимальный срок действия;</span><span class="sxs-lookup"><span data-stu-id="8bd18-111">Maximum age</span></span>  
  
- <span data-ttu-id="8bd18-112">максимальный возраст;</span><span class="sxs-lookup"><span data-stu-id="8bd18-112">Maximum staleness</span></span>  
  
- <span data-ttu-id="8bd18-113">минимальная актуальность;</span><span class="sxs-lookup"><span data-stu-id="8bd18-113">Minimum freshness</span></span>  
  
- <span data-ttu-id="8bd18-114">дата синхронизации кэша.</span><span class="sxs-lookup"><span data-stu-id="8bd18-114">Cache synchronization date</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bd18-115">Использование кэша политики на основе времени по умолчанию не следует путать с заданием политики кэша по умолчанию для приложения.</span><span class="sxs-lookup"><span data-stu-id="8bd18-115">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="8bd18-116">Политика на основе времени по умолчанию — это конкретная политика, которую можно использовать на уровне приложения или запросов.</span><span class="sxs-lookup"><span data-stu-id="8bd18-116">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="8bd18-117">Политика кэша по умолчанию для приложения — это политика (на основе расположения или времени), которая вступает в силу, если политика для запроса не задана.</span><span class="sxs-lookup"><span data-stu-id="8bd18-117">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="8bd18-118">Подробные сведения о задании политики кэша по умолчанию для приложения см. в разделе <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="8bd18-118">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="8bd18-119">Maximum Age</span><span class="sxs-lookup"><span data-stu-id="8bd18-119">Maximum Age</span></span>  

 <span data-ttu-id="8bd18-120">Критерий максимального срока действия определяет то, как долго может использоваться кэшированная копия ресурса.</span><span class="sxs-lookup"><span data-stu-id="8bd18-120">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="8bd18-121">Если указанный срок действия кэшированной копии ресурса истек, ресурс необходимо проверить повторно, сравнив его с содержимым на сервере.</span><span class="sxs-lookup"><span data-stu-id="8bd18-121">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="8bd18-122">Если использование ресурса по истечении срока действия разрешено, этот критерий не учитывается, если только также не задано значение максимального возраста.</span><span class="sxs-lookup"><span data-stu-id="8bd18-122">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="8bd18-123">Максимальный возраст</span><span class="sxs-lookup"><span data-stu-id="8bd18-123">Maximum Staleness</span></span>  

 <span data-ttu-id="8bd18-124">Критерий максимального возраста определяет то, как долго может использоваться кэшированная копия ресурса после истечения срока ее действия.</span><span class="sxs-lookup"><span data-stu-id="8bd18-124">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="8bd18-125">Это единственный критерий политики кэша, который разрешает использовать ресурсы с истекшим сроком действия.</span><span class="sxs-lookup"><span data-stu-id="8bd18-125">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="8bd18-126">Минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="8bd18-126">Minimum Freshness</span></span>  

 <span data-ttu-id="8bd18-127">Критерий минимальной актуальности определяет период времени до истечения срока действия, до которого может использоваться кэшированная копия ресурса.</span><span class="sxs-lookup"><span data-stu-id="8bd18-127">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="8bd18-128">Вследствие этой политики срок действия записи в кэше истекает до назначенного времени. Таким образом, параметры минимальной актуальности и максимального возраста являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="8bd18-128">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="8bd18-129">Дата синхронизации кэша</span><span class="sxs-lookup"><span data-stu-id="8bd18-129">Cache Synchronization Date</span></span>  

 <span data-ttu-id="8bd18-130">Критерий даты синхронизации кэша определяет то, когда необходимо повторно проверить кэшированную копию ресурса, сравнив ее с содержимым на сервере.</span><span class="sxs-lookup"><span data-stu-id="8bd18-130">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="8bd18-131">Если содержимое изменилось с момента кэширования объекта, он извлекается с сервера, сохраняется в кэше и возвращается приложению.</span><span class="sxs-lookup"><span data-stu-id="8bd18-131">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="8bd18-132">Если содержимое не изменилось, его метка времени обновляется и приложение получает содержимое из кэша.</span><span class="sxs-lookup"><span data-stu-id="8bd18-132">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="8bd18-133">С помощью даты синхронизации кэша можно указать абсолютную дату, когда кэшированное содержимое должно быть проверено повторно.</span><span class="sxs-lookup"><span data-stu-id="8bd18-133">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="8bd18-134">Если актуальная запись в кэше была в последний раз повторно проверена до даты синхронизации кэша, повторная проверка все же выполняется.</span><span class="sxs-lookup"><span data-stu-id="8bd18-134">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="8bd18-135">Если запись в кэше была повторно проверена после даты синхронизации кэша и нет дополнительных требований к актуальности или повторной проверке на сервере, используется запись из кэша.</span><span class="sxs-lookup"><span data-stu-id="8bd18-135">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="8bd18-136">Если дата синхронизации кэша — это будущая дата, запись повторно проверяется каждый раз, когда она запрашивается, пока эта дата не пройдет.</span><span class="sxs-lookup"><span data-stu-id="8bd18-136">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="8bd18-137">В следующих разделах приводятся сведения о том, как действуют различные сочетания критериев для политики кэша на основе времени:</span><span class="sxs-lookup"><span data-stu-id="8bd18-137">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="8bd18-138">Взаимодействие с политикой кэша: максимальный возраст и устаревание</span><span class="sxs-lookup"><span data-stu-id="8bd18-138">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="8bd18-139">Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="8bd18-139">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="8bd18-140">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8bd18-140">See also</span></span>

- [<span data-ttu-id="8bd18-141">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="8bd18-141">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="8bd18-142">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="8bd18-142">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="8bd18-143">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="8bd18-143">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="8bd18-144">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="8bd18-144">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="8bd18-145">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="8bd18-145">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
