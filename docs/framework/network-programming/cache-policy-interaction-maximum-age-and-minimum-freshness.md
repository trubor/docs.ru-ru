---
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
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287557"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="e3254-102">Взаимодействие с политикой кэша: максимальный возраст и минимальная актуальность</span><span class="sxs-lookup"><span data-stu-id="e3254-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="e3254-103">Чтобы обеспечить возврат клиентскому приложению самого актуального содержимого, в результате взаимодействия политики кэша клиента и требований к повторной проверке сервера всегда применяется наиболее консервативная политика кэша.</span><span class="sxs-lookup"><span data-stu-id="e3254-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="e3254-104">Все примеры в этом разделе иллюстрируют политику кэша для ресурса, который кэшируется 1 января и срок действия которого истекает 4 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="e3254-105">В приведенных ниже примерах показана политика кэша, полученная в результате сочетания значений максимального возраста (`maxAge`) и минимальной актуальности (`minFresh`).</span><span class="sxs-lookup"><span data-stu-id="e3254-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="e3254-106">Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` не указано, содержимое повторно проверяется 3 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="e3254-107">Если политика кэша задает значение `maxAge` равным 2 дням, а значение `minFresh` равным 1 дню, то в соответствии с `maxAge` содержимое будет актуальным до 3 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="e3254-108">Согласно `minFresh` содержимое будет актуально до 3 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="e3254-109">Поэтому его необходимо будет проверить повторно 3 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="e3254-110">Если политика кэша задает значение `maxAge` равным 2 дням и значение `minFresh` равным 2 дням, то в соответствии с `maxAge` содержимое будет актуальным до 3 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="e3254-111">Согласно `minFresh` содержимое будет актуально до 2 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="e3254-112">Поэтому его необходимо будет проверить повторно 2 января.</span><span class="sxs-lookup"><span data-stu-id="e3254-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3254-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e3254-113">See also</span></span>

- [<span data-ttu-id="e3254-114">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="e3254-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="e3254-115">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="e3254-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="e3254-116">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="e3254-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="e3254-117">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="e3254-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="e3254-118">Настройка кэширования в сетевых приложениях</span><span class="sxs-lookup"><span data-stu-id="e3254-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="e3254-119">Взаимодействие с политикой кэша: максимальный возраст и устаревание</span><span class="sxs-lookup"><span data-stu-id="e3254-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
