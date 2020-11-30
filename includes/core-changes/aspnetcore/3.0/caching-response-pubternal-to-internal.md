---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032710"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="4ccf9-101">Кэширование. Типы ResponseCaching pubternal теперь стали внутренними</span><span class="sxs-lookup"><span data-stu-id="4ccf9-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="4ccf9-102">В ASP.NET Core 3.0 типы pubternal в `ResponseCaching` были изменены на `internal`.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="4ccf9-103">Кроме того, реализации по умолчанию `IResponseCachingPolicyProvider` и `IResponseCachingKeyProvider` больше не добавляются в службы в рамках метода `AddResponseCaching`.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4ccf9-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="4ccf9-104">Change description</span></span>

<span data-ttu-id="4ccf9-105">В ASP.NET Core типы pubternal объявляются как `public`, но они находятся в пространстве имен с суффиксом `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="4ccf9-106">Хотя это типы являются общедоступными, для них отсутствует политика поддержки и они подвержены критическим изменениям.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="4ccf9-107">К сожалению, довольно часто эти типы использовались случайно, что приводило к критическим изменениям в таких проектах и ограничивало возможности, связанные с обслуживанием платформы.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4ccf9-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="4ccf9-108">Version introduced</span></span>

<span data-ttu-id="4ccf9-109">3.0</span><span class="sxs-lookup"><span data-stu-id="4ccf9-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4ccf9-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="4ccf9-110">Old behavior</span></span>

<span data-ttu-id="4ccf9-111">Эти типы были видны всем пользователям, но не поддерживаемыми.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4ccf9-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="4ccf9-112">New behavior</span></span>

<span data-ttu-id="4ccf9-113">Теперь эти типы являются `internal`.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4ccf9-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="4ccf9-114">Reason for change</span></span>

<span data-ttu-id="4ccf9-115">Область `internal` лучше соответствует неподдерживаемой политике.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4ccf9-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="4ccf9-116">Recommended action</span></span>

<span data-ttu-id="4ccf9-117">Копируйте типы, используемые приложением или библиотекой.</span><span class="sxs-lookup"><span data-stu-id="4ccf9-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="4ccf9-118">Категория</span><span class="sxs-lookup"><span data-stu-id="4ccf9-118">Category</span></span>

<span data-ttu-id="4ccf9-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ccf9-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ccf9-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="4ccf9-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
