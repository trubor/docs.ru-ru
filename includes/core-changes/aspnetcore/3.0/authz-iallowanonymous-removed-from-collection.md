---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032713"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="91410-101">Авторизация. IAllowAnonymous удален из AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="91410-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="91410-102">Начиная с ASP.NET Core 3.0, MVC не добавляет [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) для атрибутов [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute), обнаруженных на контроллерах и методах действий.</span><span class="sxs-lookup"><span data-stu-id="91410-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="91410-103">Это изменение локально адресовано для производных <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, но является критическим изменением для реализаций <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> и <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter>.</span><span class="sxs-lookup"><span data-stu-id="91410-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="91410-104">Такие реализации, заключенные в атрибут [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute), представляют собой [популярный](https://stackoverflow.com/a/41348219/608220) и поддерживаемый способ обеспечения строго типизированной авторизации на основе атрибутов, когда требуется настройка или внедрение зависимостей.</span><span class="sxs-lookup"><span data-stu-id="91410-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="91410-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="91410-105">Version introduced</span></span>

<span data-ttu-id="91410-106">3.0</span><span class="sxs-lookup"><span data-stu-id="91410-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="91410-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="91410-107">Old behavior</span></span>

<span data-ttu-id="91410-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> отображался в коллекции [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A).</span><span class="sxs-lookup"><span data-stu-id="91410-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="91410-109">Тестирование наличия интерфейса было правильным подходом к переопределению или отключению фильтра на отдельных методах контроллера.</span><span class="sxs-lookup"><span data-stu-id="91410-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="91410-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="91410-110">New behavior</span></span>

<span data-ttu-id="91410-111">`IAllowAnonymous` больше не отображается в коллекции `AuthorizationFilterContext.Filters`.</span><span class="sxs-lookup"><span data-stu-id="91410-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="91410-112">Реализации `IAsyncAuthorizationFilter`, зависящие от прежнего поведения, обычно приводят к периодическим ответам HTTP "401: не санкционировано" или HTTP "403: запрещено".</span><span class="sxs-lookup"><span data-stu-id="91410-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="91410-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="91410-113">Reason for change</span></span>

<span data-ttu-id="91410-114">В ASP.NET Core 3.0 введена новая стратегия маршрутизации конечных точек.</span><span class="sxs-lookup"><span data-stu-id="91410-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="91410-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="91410-115">Recommended action</span></span>

<span data-ttu-id="91410-116">Поиск метаданных конечной точки для `IAllowAnonymous`.</span><span class="sxs-lookup"><span data-stu-id="91410-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="91410-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="91410-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="91410-118">Пример этой техники можно увидеть в [этом методе HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="91410-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="91410-119">Категория</span><span class="sxs-lookup"><span data-stu-id="91410-119">Category</span></span>

<span data-ttu-id="91410-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91410-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="91410-121">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="91410-121">Affected APIs</span></span>

<span data-ttu-id="91410-122">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="91410-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
