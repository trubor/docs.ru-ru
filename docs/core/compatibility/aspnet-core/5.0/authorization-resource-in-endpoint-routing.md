---
title: Критическое изменение. Авторизация. Для маршрутизации конечных точек используется ресурс HttpContext
description: Сведения о критическом изменении в ASP.NET Core 5.0 — аутентификация. Для маршрутизации конечных точек используется ресурс HttpContext
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 90f15bcbc1fb05e67b1c6d7494938eebac7718fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497887"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="02ee1-103">Авторизация. Для маршрутизации конечных точек используется ресурс HttpContext</span><span class="sxs-lookup"><span data-stu-id="02ee1-103">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="02ee1-104">При маршрутизации конечных точек в ASP.NET Core 3.1 в качестве ресурса для авторизации используется конечная точка.</span><span class="sxs-lookup"><span data-stu-id="02ee1-104">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="02ee1-105">Такой подход не обеспечивал доступ к данным маршрута (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span><span class="sxs-lookup"><span data-stu-id="02ee1-105">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="02ee1-106">Ранее в MVC передавался ресурс <xref:Microsoft.AspNetCore.Http.HttpContext>, который обеспечивал доступ одновременно к конечной точке (<xref:Microsoft.AspNetCore.Http.Endpoint>) и данным маршрута.</span><span class="sxs-lookup"><span data-stu-id="02ee1-106">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="02ee1-107">Это изменение гарантирует, что в качестве ресурса для авторизации всегда будет передаваться `HttpContext`.</span><span class="sxs-lookup"><span data-stu-id="02ee1-107">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="02ee1-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="02ee1-108">Version introduced</span></span>

<span data-ttu-id="02ee1-109">5.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="02ee1-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="02ee1-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="02ee1-110">Old behavior</span></span>

<span data-ttu-id="02ee1-111">При использовании маршрутизации конечной точки и ПО промежуточного слоя авторизации (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) или атрибутов [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) в качестве ресурса для авторизации передается соответствующая конечная точка.</span><span class="sxs-lookup"><span data-stu-id="02ee1-111">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="02ee1-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="02ee1-112">New behavior</span></span>

<span data-ttu-id="02ee1-113">При маршрутизации конечной точки для авторизации передается `HttpContext`.</span><span class="sxs-lookup"><span data-stu-id="02ee1-113">Endpoint routing passes the `HttpContext` to authorization.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="02ee1-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="02ee1-114">Reason for change</span></span>

<span data-ttu-id="02ee1-115">Существует возможность перейти к конечной точке из `HttpContext`.</span><span class="sxs-lookup"><span data-stu-id="02ee1-115">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="02ee1-116">Тем не менее, из конечной точки было невозможно получить информацию, например данные маршрута.</span><span class="sxs-lookup"><span data-stu-id="02ee1-116">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="02ee1-117">Таким образом, утрачивались функциональные возможности из-за маршрутизации без конечной точки.</span><span class="sxs-lookup"><span data-stu-id="02ee1-117">There was a loss in functionality from non-endpoint routing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="02ee1-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="02ee1-118">Recommended action</span></span>

<span data-ttu-id="02ee1-119">Если в вашем приложении используется ресурс конечной точки вызовите <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> для `HttpContext`, чтобы сохранить доступ к конечной точке.</span><span class="sxs-lookup"><span data-stu-id="02ee1-119">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="02ee1-120">В ASP.NET Core 5.0 предварительной версии 8 и более поздних вы можете восстановить поведение предыдущих версий с использованием <xref:System.AppContext.SetSwitch%2A>.</span><span class="sxs-lookup"><span data-stu-id="02ee1-120">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="02ee1-121">Пример:</span><span class="sxs-lookup"><span data-stu-id="02ee1-121">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a><span data-ttu-id="02ee1-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="02ee1-122">Affected APIs</span></span>

<span data-ttu-id="02ee1-123">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="02ee1-123">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
