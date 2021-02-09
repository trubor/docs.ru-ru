---
description: 'Узнайте подробнее о: Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность'
title: 'Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность'
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 882df93d44c0d745fcf30a7d9be3152797df4844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791651"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="6826a-103">Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="6826a-103">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="6826a-104">Чтобы обеспечить возврат клиентскому приложению самого актуального содержимого, в результате взаимодействия политики кэша клиента и требований к повторной проверке сервера всегда применяется наиболее консервативная политика кэша.</span><span class="sxs-lookup"><span data-stu-id="6826a-104">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="6826a-105">Все примеры в этом разделе иллюстрируют политику кэша для ресурса, который кэшируется 1 января и срок действия которого истекает 4 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-105">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="6826a-106">В приведенных ниже примерах показана политика кэша, полученная в результате сочетания значений максимального возраста (`maxAge`) и минимальной актуальности (`minFresh`).</span><span class="sxs-lookup"><span data-stu-id="6826a-106">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="6826a-107">Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` не указано, содержимое повторно проверяется 3 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-107">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="6826a-108">Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` равным 1 дню, то в соответствии с `maxAge` содержимое будет актуальным до 3 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-108">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="6826a-109">Согласно `minFresh` содержимое будет актуально до 3 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-109">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="6826a-110">Поэтому его необходимо будет проверить повторно 3 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-110">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="6826a-111">Если политика кэша задает значение `maxAge` равным 2 дням и значение `minFresh` равным 2 дням, то в соответствии с `maxAge` содержимое будет актуальным до 3 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-111">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="6826a-112">Согласно `minFresh` содержимое будет актуально до 2 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-112">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="6826a-113">Поэтому его необходимо будет проверить повторно 2 января.</span><span class="sxs-lookup"><span data-stu-id="6826a-113">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6826a-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6826a-114">See also</span></span>

- [<span data-ttu-id="6826a-115">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="6826a-115">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="6826a-116">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="6826a-116">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="6826a-117">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="6826a-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="6826a-118">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="6826a-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="6826a-119">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="6826a-119">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="6826a-120">Взаимодействие с политикой кэша: максимальный возраст и устаревание</span><span class="sxs-lookup"><span data-stu-id="6826a-120">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
