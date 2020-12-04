---
title: Практическое руководство. Установка политики кэша для приложения на основе расположения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 7331845c391265d72d3025fd9bf7856d83c783e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253496"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="8872d-102">Практическое руководство. Установка политики кэша для приложения на основе расположения</span><span class="sxs-lookup"><span data-stu-id="8872d-102">How to: Set a Location-Based Cache Policy for an Application</span></span>

<span data-ttu-id="8872d-103">Политики кэша на основе расположения позволяют приложению явным образом определить поведение кэша на основе расположения запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="8872d-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="8872d-104">В этом разделе описана установка политики кэша программным способом.</span><span class="sxs-lookup"><span data-stu-id="8872d-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="8872d-105">Сведения об установке политики для приложения с помощью файлов конфигурации см. в разделе [Элемент \<requestCaching> (сетевые параметры)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8872d-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="8872d-106">Установка политики кэша для приложения на основе расположения</span><span class="sxs-lookup"><span data-stu-id="8872d-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="8872d-107">Создайте объект <xref:System.Net.Cache.RequestCachePolicy> или <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="8872d-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="8872d-108">Установите этот объект политики как объект по умолчанию для домена приложения.</span><span class="sxs-lookup"><span data-stu-id="8872d-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="8872d-109">Установка политики, которая принимает запрошенные ресурсы из кэша</span><span class="sxs-lookup"><span data-stu-id="8872d-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="8872d-110">Создайте политику, которая принимает запрошенные ресурсы из кэша, если они есть в кэше. В противном случае запросы отправляются на сервер с помощью установки уровня кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="8872d-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="8872d-111">Для выполнения запроса может использоваться любой кэш между клиентом и сервером, включая удаленный кэш.</span><span class="sxs-lookup"><span data-stu-id="8872d-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="8872d-112">Установка политики, которая полностью запрещает получение ресурсов из кэша</span><span class="sxs-lookup"><span data-stu-id="8872d-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="8872d-113">Создайте политику, которая полностью запрещает получение запрошенных ресурсов из кэша, установив уровень кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="8872d-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="8872d-114">С этой политикой ресурс удаляется из локального кэша (если он присутствует в локальном кэше), а также из удаленных кэшей.</span><span class="sxs-lookup"><span data-stu-id="8872d-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="8872d-115">Установка политики, которая возвращает запрошенные ресурсы, только если они присутствуют в локальном кэше</span><span class="sxs-lookup"><span data-stu-id="8872d-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="8872d-116">Создайте политику, которая возвращает запрошенные ресурсы только в том случае, если они присутствуют в локальном кэше, установив уровень кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="8872d-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="8872d-117">Если запрошенный ресурс отсутствует в кэше, выдается исключение <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="8872d-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="8872d-118">Установка политики, которая запрещает получение ресурсов из локального кэша</span><span class="sxs-lookup"><span data-stu-id="8872d-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="8872d-119">Создайте политику, которая запрещает получение запрошенных ресурсов из локального кэша, установив уровень кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="8872d-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="8872d-120">Если запрошенный ресурс находится в промежуточном кэше и успешно проверен, ресурс может быть возвращен из промежуточного кэша.</span><span class="sxs-lookup"><span data-stu-id="8872d-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="8872d-121">Установка политики, которая полностью запрещает получение запрошенных ресурсов из кэша</span><span class="sxs-lookup"><span data-stu-id="8872d-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="8872d-122">Создайте политику, которая полностью запрещает получение запрошенных ресурсов из кэша, установив уровень кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="8872d-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="8872d-123">Ресурс, возвращенный сервером, может быть сохранен в кэше.</span><span class="sxs-lookup"><span data-stu-id="8872d-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="8872d-124">Установка политики, которая разрешает получение запрошенных ресурсов из любого кэша, если кэшированная копия не старше ресурса на сервере</span><span class="sxs-lookup"><span data-stu-id="8872d-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="8872d-125">Создайте политику, которая разрешает получение запрошенных ресурсов из любого кэша, если кэшированная копия не старше ресурса на сервере, установив уровень кэширования <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="8872d-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8872d-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8872d-126">See also</span></span>

- [<span data-ttu-id="8872d-127">Управление кэшем для сетевых приложений</span><span class="sxs-lookup"><span data-stu-id="8872d-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="8872d-128">Политика кэша</span><span class="sxs-lookup"><span data-stu-id="8872d-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="8872d-129">Политики кэша на основе расположения</span><span class="sxs-lookup"><span data-stu-id="8872d-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="8872d-130">Политики кэша на основе времени</span><span class="sxs-lookup"><span data-stu-id="8872d-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="8872d-131">Элемент \<requestCaching> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="8872d-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
