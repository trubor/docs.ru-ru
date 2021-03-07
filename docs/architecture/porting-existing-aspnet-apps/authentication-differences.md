---
title: Сравнение проверки подлинности и авторизации между ASP.NET MVC и ASP.NET Core
description: Сводка различий проверки подлинности и авторизации между ASP.NET MVC и ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c8f3314186b7408e40d3a79cbc922a29eb75c5d2
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401817"
---
# <a name="compare-authentication-and-authorization-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="8dbd5-103">Сравнение проверки подлинности и авторизации между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8dbd5-103">Compare authentication and authorization between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="8dbd5-104">В ASP.NET MVC 5 Проверка подлинности настраивается в *Startup.auth.CS* в папке *App_Start* .</span><span class="sxs-lookup"><span data-stu-id="8dbd5-104">In ASP.NET MVC 5, authentication is configured in *Startup.Auth.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="8dbd5-105">В ASP.NET Core MVC эта конфигурация происходит в `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="8dbd5-105">In ASP.NET Core MVC, this configuration occurs in `Startup.cs`.</span></span> <span data-ttu-id="8dbd5-106">Проверка подлинности и авторизация выполняются с помощью по промежуточного слоя, добавленного в конвейер запросов в `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="8dbd5-106">Authentication and authorization are performed using middleware added to the request pipeline in `ConfigureServices`:</span></span>

```csharp
// inside Startup.ConfigureServices

app.UseRouting();

app.UseAuthentication();
app.UseAuthorization();

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

<span data-ttu-id="8dbd5-107">Важно добавить по промежуточного слоя проверки подлинности в соответствующем порядке в конвейере по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-107">It's important to add the auth middleware in the appropriate order in the middleware pipeline.</span></span> <span data-ttu-id="8dbd5-108">Только запросы, которые делают его по промежуточного слоя, будут затронуты.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-108">Only requests that make it to the middleware will be impacted by it.</span></span> <span data-ttu-id="8dbd5-109">Например, если вызов метода `UseStaticFiles()` был помещен выше показанного здесь кода, он не будет защищен проверкой подлинности и авторизацией.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-109">For instance, if a call to `UseStaticFiles()` was placed above the code shown here, it wouldn't be protected by authentication and authorization.</span></span>

<span data-ttu-id="8dbd5-110">В ASP.NET MVC и веб-API приложения часто обращаются к текущему пользователю с помощью `ClaimsPrincipal.Current` Свойства.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-110">In ASP.NET MVC and Web API, apps often refer to the current user using the `ClaimsPrincipal.Current` property.</span></span> <span data-ttu-id="8dbd5-111">Это свойство не задано в ASP.NET Core, и любое поведение в приложении, которое зависит от него, должно быть [перенесено из ClaimsPrincipal. Current](/aspnet/core/migration/claimsprincipal-current) с помощью `User` свойства в `ControllerBase` или получения доступа к текущему `HttpContext` свойству и ссылки на его `User` свойство.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-111">This property isn't set in ASP.NET Core, and any behavior in your app that depends on it will need to [migrate from ClaimsPrincipal.Current](/aspnet/core/migration/claimsprincipal-current) by using the `User` property on `ControllerBase` or getting access to the current `HttpContext` and referencing its `User` property.</span></span> <span data-ttu-id="8dbd5-112">Если ни одно из этих решений не является параметром, службы могут запросить пользователя в качестве аргумента, в этом случае он должен быть указан в любом расположении в приложении, а также `IHttpContextAccessor` может быть запрошен и использован для получения `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="8dbd5-112">If neither of these solutions is an option, services can request the User as an argument, in which case it must be supplied from elsewhere in the app, or the `IHttpContextAccessor` can be requested and used to get the `HttpContext`.</span></span>

## <a name="authorization"></a><span data-ttu-id="8dbd5-113">Авторизация</span><span class="sxs-lookup"><span data-stu-id="8dbd5-113">Authorization</span></span>

<span data-ttu-id="8dbd5-114">Авторизация определяет, что может делать данный пользователь в приложении.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-114">Authorization defines what a given user can do within the app.</span></span> <span data-ttu-id="8dbd5-115">Это отдельно от проверки подлинности, что очень важно для идентификации пользователя.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-115">It's separate from authentication, which is concerned merely with identifying who the user is.</span></span> <span data-ttu-id="8dbd5-116">ASP.NET Core предоставляет простую, декларативную роль и многофункциональную модель на основе политик для авторизации.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-116">ASP.NET Core provides a simple, declarative role and a rich, policy-based model for authorization.</span></span> <span data-ttu-id="8dbd5-117">Чтобы указать, что ресурсу требуется авторизация, часто достаточно просто добавить `[Authorize]` атрибут к действию или контроллеру.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-117">Specifying that a resource requires authorization is often as simple as adding the `[Authorize]` attribute to the action or controller.</span></span> <span data-ttu-id="8dbd5-118">Если выполняется миграция на Razor Pages из представлений MVC, необходимо [указать соглашения для авторизации при настройке Razor Pages при запуске](/aspnet/core/security/authorization/razor-pages-authorization).</span><span class="sxs-lookup"><span data-stu-id="8dbd5-118">If you're migrating to Razor Pages from MVC views, you should [specify conventions for authorization when you configure Razor Pages in Startup](/aspnet/core/security/authorization/razor-pages-authorization).</span></span>

<span data-ttu-id="8dbd5-119">Авторизация в ASP.NET Core может быть такой же простой, как запрет анонимных пользователей, разрешая пользователям, прошедшим проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-119">Authorization in ASP.NET Core may be as simple as prohibiting anonymous users while allowing authenticated users.</span></span> <span data-ttu-id="8dbd5-120">Кроме того, можно увеличить масштаб для поддержки подходов авторизации на основе ролей, основанных на утверждениях или политик.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-120">Or it can scale up to support role-based, claims-based, or policy-based authorization approaches.</span></span> <span data-ttu-id="8dbd5-121">Дополнительные сведения об этих подходах см. в документации по [авторизации в ASP.NET Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="8dbd5-121">For more information on these approaches, see the documentation on [authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span> <span data-ttu-id="8dbd5-122">Скорее всего, вы обнаружите, что один из них тесно соответствует текущему подходу авторизации.</span><span class="sxs-lookup"><span data-stu-id="8dbd5-122">You'll likely find that one of them is closely aligned with your current authorization approach.</span></span>

## <a name="references"></a><span data-ttu-id="8dbd5-123">Ссылки</span><span class="sxs-lookup"><span data-stu-id="8dbd5-123">References</span></span>

- [<span data-ttu-id="8dbd5-124">Безопасность, проверка подлинности и авторизация с помощью ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="8dbd5-124">Security, Authentication, and Authorization with ASP.NET MVC</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="8dbd5-125">Перенесите проверку подлинности и удостоверение в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8dbd5-125">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="8dbd5-126">Миграция из ClaimsPrincipal. Current</span><span class="sxs-lookup"><span data-stu-id="8dbd5-126">Migrate from ClaimsPrincipal.Current</span></span>](/aspnet/core/migration/claimsprincipal-current)
- [<span data-ttu-id="8dbd5-127">Общие сведения об авторизации в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8dbd5-127">Introduction to Authorization in ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)

>[!div class="step-by-step"]
><span data-ttu-id="8dbd5-128">[Назад](webapi-differences.md)
>[Вперед](identity-differences.md)</span><span class="sxs-lookup"><span data-stu-id="8dbd5-128">[Previous](webapi-differences.md)
[Next](identity-differences.md)</span></span>
