---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032782"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="931f8-101">Удостоверение. Создание исключения SignInAsync для удостоверения, не прошедшего проверку подлинности</span><span class="sxs-lookup"><span data-stu-id="931f8-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="931f8-102">По умолчанию `SignInAsync` создает исключение для субъектов и удостоверений, в которых `IsAuthenticated` является `false`.</span><span class="sxs-lookup"><span data-stu-id="931f8-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="931f8-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="931f8-103">Version introduced</span></span>

<span data-ttu-id="931f8-104">3.0</span><span class="sxs-lookup"><span data-stu-id="931f8-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="931f8-105">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="931f8-105">Old behavior</span></span>

<span data-ttu-id="931f8-106">`SignInAsync` принимает все субъекты и удостоверения, включая удостоверения, в которых `IsAuthenticated` является `false`.</span><span class="sxs-lookup"><span data-stu-id="931f8-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="931f8-107">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="931f8-107">New behavior</span></span>

<span data-ttu-id="931f8-108">По умолчанию `SignInAsync` создает исключение для субъектов и удостоверений, в которых `IsAuthenticated` является `false`.</span><span class="sxs-lookup"><span data-stu-id="931f8-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="931f8-109">Есть новый флаг, который подавляет это поведение, но поведение по умолчанию изменилось.</span><span class="sxs-lookup"><span data-stu-id="931f8-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="931f8-110">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="931f8-110">Reason for change</span></span>

<span data-ttu-id="931f8-111">Старое поведение было проблематичным, так как по умолчанию эти участники отклонялись `[Authorize]` / `RequireAuthenticatedUser()`.</span><span class="sxs-lookup"><span data-stu-id="931f8-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="931f8-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="931f8-112">Recommended action</span></span>

<span data-ttu-id="931f8-113">В ASP.NET Core 3.0 (предварительная версия 6) есть флаг `RequireAuthenticatedSignIn` в `AuthenticationOptions`, который является `true` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="931f8-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="931f8-114">Установите для этого флага значение `false`, чтобы восстановить старое поведение.</span><span class="sxs-lookup"><span data-stu-id="931f8-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="931f8-115">Категория</span><span class="sxs-lookup"><span data-stu-id="931f8-115">Category</span></span>

<span data-ttu-id="931f8-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="931f8-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="931f8-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="931f8-117">Affected APIs</span></span>

<span data-ttu-id="931f8-118">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="931f8-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
