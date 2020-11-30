---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032702"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="ce199-101">Аутентификация. Механизм Google+ устарел и заменяется</span><span class="sxs-lookup"><span data-stu-id="ce199-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="ce199-102">Google постепенно [отключает](https://developers.google.com/+/api-shutdown) механизм входа через Google+ для приложений, начиная с 28 января 2019 г.</span><span class="sxs-lookup"><span data-stu-id="ce199-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ce199-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="ce199-103">Change description</span></span>

<span data-ttu-id="ce199-104">Платформы ASP.NET 4.x и ASP.NET Core использовали API для входа, предоставленные Google+, для проверки подлинности пользователей с учетной записью Google в веб-приложениях.</span><span class="sxs-lookup"><span data-stu-id="ce199-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="ce199-105">Это изменение затронет такие пакеты NuGet, как [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) для ASP.NET Core и [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) для `Microsoft.Owin` с ASP.NET Web Forms и MVC.</span><span class="sxs-lookup"><span data-stu-id="ce199-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="ce199-106">В API-интерфейсах, которые Google предоставил в качестве замены, используется другой источник данных и другой формат.</span><span class="sxs-lookup"><span data-stu-id="ce199-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="ce199-107">Ниже описаны методы и решения, которые позволят учесть эти структурные изменения.</span><span class="sxs-lookup"><span data-stu-id="ce199-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="ce199-108">Приложения должны проверять, соответствуют ли данные требованиям.</span><span class="sxs-lookup"><span data-stu-id="ce199-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="ce199-109">Например, имена, адреса электронной почты, ссылки на профили и фотографии профилей могут возвращать немного другие значения, чем раньше.</span><span class="sxs-lookup"><span data-stu-id="ce199-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce199-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ce199-110">Version introduced</span></span>

<span data-ttu-id="ce199-111">Все версии.</span><span class="sxs-lookup"><span data-stu-id="ce199-111">All versions.</span></span> <span data-ttu-id="ce199-112">Это изменение является внешним по отношению к ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce199-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce199-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ce199-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="ce199-114">Owin с ASP.NET Web Forms и MVC</span><span class="sxs-lookup"><span data-stu-id="ce199-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="ce199-115">Для `Microsoft.Owin` версии 3.1.0 и более поздних [здесь](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635) описаны меры для временного устранения рисков.</span><span class="sxs-lookup"><span data-stu-id="ce199-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="ce199-116">Приложения должны по этой процедуре проверить наличие изменений в формате данных.</span><span class="sxs-lookup"><span data-stu-id="ce199-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="ce199-117">Планируется выпуск версии `Microsoft.Owin` 4.0.1 с исправлением.</span><span class="sxs-lookup"><span data-stu-id="ce199-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="ce199-118">Все приложения, которые используют любую из предыдущих версий, нужно обновить до версии 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="ce199-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="ce199-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ce199-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="ce199-120">Устранение рисков, описанное в инструкции для [Owin с ASP.NET Web Forms и MVC](#owin-with-aspnet-web-forms-and-mvc), можно адаптировать для ASP.NET Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="ce199-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="ce199-121">Исправления пакетов NuGet не планируются, так как версия 1.x уже достигла [завершения жизненного цикла](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="ce199-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="ce199-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ce199-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="ce199-123">Для `Microsoft.AspNetCore.Authentication.Google` версии 2.x замените существующий вызов `AddGoogle` в `Startup.ConfigureServices` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="ce199-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="ce199-124">В февральские обновления 2.1 и 2.2 описанное выше изменение конфигурации включено как новый вариант по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ce199-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="ce199-125">Обновления для ASP.NET Core 2.0 не планируются, так как эта версия достигла [завершения жизненного цикла](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="ce199-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="ce199-126">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ce199-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="ce199-127">Метод устранения рисков, предложенный для ASP.NET Core 2.x, также можно использовать и для ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce199-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="ce199-128">В будущих предварительных версиях для 3.0 пакет `Microsoft.AspNetCore.Authentication.Google` может быть удален.</span><span class="sxs-lookup"><span data-stu-id="ce199-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="ce199-129">Вместо него пользователям будет предоставляться `Microsoft.AspNetCore.Authentication.OpenIdConnect`.</span><span class="sxs-lookup"><span data-stu-id="ce199-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="ce199-130">В следующем примере кода показано, как заменить `AddGoogle` на `AddOpenIdConnect` в `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="ce199-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="ce199-131">Эту замену можно использовать для ASP.NET Core 2.0 и более поздних версий, а также адаптировать для ASP.NET Core 1.x по необходимости.</span><span class="sxs-lookup"><span data-stu-id="ce199-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="ce199-132">Категория</span><span class="sxs-lookup"><span data-stu-id="ce199-132">Category</span></span>

<span data-ttu-id="ce199-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce199-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce199-134">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ce199-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
