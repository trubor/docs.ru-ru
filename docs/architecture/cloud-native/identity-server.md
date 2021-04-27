---
title: IdentityServer для облачных приложений в машинном код
description: Создание архитектуры облачных приложений .NET для Azure | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: 2578f39d19911e9c6d952f62e139329a7a6274fb
ms.sourcegitcommit: 381b773c9962aca5f8d0b973d0653c0f4edcc4d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2021
ms.locfileid: "108013636"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="03cc0-103">IdentityServer для собственных приложений в облаке</span><span class="sxs-lookup"><span data-stu-id="03cc0-103">IdentityServer for cloud-native applications</span></span>

<span data-ttu-id="03cc0-104">IdentityServer — это сервер проверки подлинности, который реализует стандарты OpenID Connect Connect (OIDC) и OAuth 2,0 для ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cc0-104">IdentityServer is an authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="03cc0-105">Он предназначен для предоставления общего способа проверки подлинности запросов ко всем приложениям независимо от того, являются ли они веб-приложениями, собственными, мобильными или интерфейсными конечными точками API.</span><span class="sxs-lookup"><span data-stu-id="03cc0-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="03cc0-106">IdentityServer можно использовать для реализации единого Sign-On (единого входа) для нескольких приложений и типов приложений.</span><span class="sxs-lookup"><span data-stu-id="03cc0-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="03cc0-107">Его можно использовать для проверки подлинности реальных пользователей с помощью форм входа и аналогичных пользовательских интерфейсов, а также для проверки подлинности на основе служб, которая обычно включает выдачу, проверку и обновление маркеров без какого-либо пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="03cc0-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="03cc0-108">IdentityServer разработана как настраиваемое решение.</span><span class="sxs-lookup"><span data-stu-id="03cc0-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="03cc0-109">Каждый экземпляр обычно настраивается в соответствии с потребностями конкретной организации и/или набора приложений.</span><span class="sxs-lookup"><span data-stu-id="03cc0-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="03cc0-110">Распространенные сценарии веб-приложений</span><span class="sxs-lookup"><span data-stu-id="03cc0-110">Common web app scenarios</span></span>

<span data-ttu-id="03cc0-111">Как правило, приложения должны поддерживать некоторые или все из следующих сценариев:</span><span class="sxs-lookup"><span data-stu-id="03cc0-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="03cc0-112">Пользователи, обращающиеся к веб-приложениям с помощью браузера.</span><span class="sxs-lookup"><span data-stu-id="03cc0-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="03cc0-113">Пользователи, обращающиеся к внутренним веб-API из приложений на основе браузера.</span><span class="sxs-lookup"><span data-stu-id="03cc0-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="03cc0-114">Пользователи мобильных и собственных клиентов, обращающихся к серверным веб-API.</span><span class="sxs-lookup"><span data-stu-id="03cc0-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="03cc0-115">Другие приложения, обращающиеся к серверным веб-API (без активного пользователя или пользовательского интерфейса).</span><span class="sxs-lookup"><span data-stu-id="03cc0-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="03cc0-116">Любому приложению может потребоваться взаимодействовать с другими веб-API, используя собственное удостоверение или делегируя идентификатору пользователя.</span><span class="sxs-lookup"><span data-stu-id="03cc0-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

![Типы приложений и сценариев](./media/application-types.png)

<span data-ttu-id="03cc0-118">**Рис. 8-1**.</span><span class="sxs-lookup"><span data-stu-id="03cc0-118">**Figure 8-1**.</span></span> <span data-ttu-id="03cc0-119">Типы приложений и сценарии.</span><span class="sxs-lookup"><span data-stu-id="03cc0-119">Application types and scenarios.</span></span>

<span data-ttu-id="03cc0-120">В каждом из этих сценариев предоставленная функциональность должна быть защищена от несанкционированного использования.</span><span class="sxs-lookup"><span data-stu-id="03cc0-120">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="03cc0-121">Как минимум, обычно требуется проверка подлинности пользователя или участника, выполняющего запрос ресурса.</span><span class="sxs-lookup"><span data-stu-id="03cc0-121">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="03cc0-122">Эта проверка подлинности может использовать один из нескольких распространенных протоколов, таких как SAML2p, WS-подача или OpenID Connect Connect.</span><span class="sxs-lookup"><span data-stu-id="03cc0-122">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="03cc0-123">Взаимодействие с API обычно использует протокол OAuth2 и его поддержку для маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="03cc0-123">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="03cc0-124">Отделение этих критических проблем безопасности и их реализация от самих приложений обеспечивает согласованность и повышает безопасность и удобство обслуживания.</span><span class="sxs-lookup"><span data-stu-id="03cc0-124">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="03cc0-125">Аутсорсинг этих задач на выделенный продукт, такой как IdentityServer, позволяет каждому приложению решить эти проблемы самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="03cc0-125">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="03cc0-126">IdentityServer предоставляет по промежуточного слоя, которое выполняется в приложении ASP.NET Core и добавляет поддержку OpenID Connect Connect и OAuth2 (см. [Поддерживаемые спецификации](https://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="03cc0-126">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](https://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="03cc0-127">Организации создают собственное ASP.NET Core приложение с помощью по промежуточного слоя IdentityServer, которое действует как STS для всех своих протоколов безопасности на основе маркеров.</span><span class="sxs-lookup"><span data-stu-id="03cc0-127">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="03cc0-128">По промежуточного слоя IdentityServer предоставляет конечные точки для поддержки стандартных функций, в том числе:</span><span class="sxs-lookup"><span data-stu-id="03cc0-128">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="03cc0-129">Авторизация (проверка подлинности конечного пользователя)</span><span class="sxs-lookup"><span data-stu-id="03cc0-129">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="03cc0-130">Токен (запрос маркера программным путем)</span><span class="sxs-lookup"><span data-stu-id="03cc0-130">Token (request a token programmatically)</span></span>
- <span data-ttu-id="03cc0-131">Обнаружение (метаданные о сервере)</span><span class="sxs-lookup"><span data-stu-id="03cc0-131">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="03cc0-132">Сведения о пользователе (получение сведений о пользователе с действительным маркером доступа)</span><span class="sxs-lookup"><span data-stu-id="03cc0-132">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="03cc0-133">Авторизация устройства (используется для запуска авторизации потока устройства)</span><span class="sxs-lookup"><span data-stu-id="03cc0-133">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="03cc0-134">Самоанализ (проверка маркера)</span><span class="sxs-lookup"><span data-stu-id="03cc0-134">Introspection (token validation)</span></span>
- <span data-ttu-id="03cc0-135">Отзыв (отзыв маркера)</span><span class="sxs-lookup"><span data-stu-id="03cc0-135">Revocation (token revocation)</span></span>
- <span data-ttu-id="03cc0-136">Завершение сеанса (активация единого выхода для всех приложений)</span><span class="sxs-lookup"><span data-stu-id="03cc0-136">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="03cc0-137">Начало работы</span><span class="sxs-lookup"><span data-stu-id="03cc0-137">Getting started</span></span>

<span data-ttu-id="03cc0-138">IdentityServer4 доступен по двум лицензиям:</span><span class="sxs-lookup"><span data-stu-id="03cc0-138">IdentityServer4 is available under dual license:</span></span>  

* <span data-ttu-id="03cc0-139">RPL — позволяет использовать IdentityServer4 Free, если используется в работе с открытым исходным кодом</span><span class="sxs-lookup"><span data-stu-id="03cc0-139">RPL - let's you use the IdentityServer4 free if used in open source work</span></span>
* <span data-ttu-id="03cc0-140">Оплачено — давайте будем использовать IdentityServer4 в коммерческом сценарии.</span><span class="sxs-lookup"><span data-stu-id="03cc0-140">Paid - let's you use the IdentityServer4 in a commercial scenario</span></span>

<span data-ttu-id="03cc0-141">Обратитесь к официальной странице [цен на продукт](https://duendesoftware.com/products/identityserver) .</span><span class="sxs-lookup"><span data-stu-id="03cc0-141">Please reach out to official [Product's pricing](https://duendesoftware.com/products/identityserver) page.</span></span>

<span data-ttu-id="03cc0-142">Его можно добавить в приложения с помощью пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="03cc0-142">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="03cc0-143">Основной пакет — [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) , который был загружен более 4 000 000 раз.</span><span class="sxs-lookup"><span data-stu-id="03cc0-143">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="03cc0-144">Базовый пакет не включает код пользовательского интерфейса и поддерживает только в конфигурации памяти.</span><span class="sxs-lookup"><span data-stu-id="03cc0-144">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="03cc0-145">Чтобы использовать ее с базой данных, вам также понадобится поставщик данных, такой как [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , который использует Entity Framework Core для хранения конфигурации и рабочих данных для IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="03cc0-145">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="03cc0-146">Для пользовательского интерфейса можно скопировать файлы из [репозитория пользовательского интерфейса](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) быстрого запуска в приложение ASP.NET Core MVC, чтобы добавить поддержку входа и выхода с помощью по промежуточного слоя IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="03cc0-146">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="03cc0-147">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="03cc0-147">Configuration</span></span>

<span data-ttu-id="03cc0-148">IdentityServer поддерживает различные типы протоколов и поставщиков проверки подлинности, которые можно настроить в рамках каждой выборочной установки.</span><span class="sxs-lookup"><span data-stu-id="03cc0-148">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="03cc0-149">Обычно это делается в классе ASP.NET Core приложения `Startup` в `ConfigureServices` методе.</span><span class="sxs-lookup"><span data-stu-id="03cc0-149">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="03cc0-150">Конфигурация включает в себя указание поддерживаемых протоколов и пути к серверам и конечным точкам, которые будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="03cc0-150">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="03cc0-151">На рис. 8-2 показан пример конфигурации, взятой из проекта пользовательского интерфейса быстрого запуска IdentityServer4:</span><span class="sxs-lookup"><span data-stu-id="03cc0-151">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="03cc0-152">**Рис. 8-2**.</span><span class="sxs-lookup"><span data-stu-id="03cc0-152">**Figure 8-2**.</span></span> <span data-ttu-id="03cc0-153">Настройка IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="03cc0-153">Configuring IdentityServer.</span></span>

<span data-ttu-id="03cc0-154">IdentityServer также содержит общедоступный демонстрационный сайт, который можно использовать для тестирования различных протоколов и конфигураций.</span><span class="sxs-lookup"><span data-stu-id="03cc0-154">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="03cc0-155">Он расположен по адресу [https://demo.identityserver.io/](https://demo.identityserver.io/) и содержит сведения о том, как настроить его поведение на основе `client_id` предоставленного ему поведения.</span><span class="sxs-lookup"><span data-stu-id="03cc0-155">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="03cc0-156">Клиенты JavaScript</span><span class="sxs-lookup"><span data-stu-id="03cc0-156">JavaScript clients</span></span>

<span data-ttu-id="03cc0-157">Многие облачные приложения используют API на стороне сервера и полнофункциональные клиентские приложения с одними страницами (одностраничные приложения) на внешнем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="03cc0-157">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="03cc0-158">IdentityServer поставляется с [клиентом JavaScript](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) через NPM, который можно добавить в одностраничные приложения, чтобы использовать IdentityServer для входа, выхода и проверки подлинности на основе маркеров для веб-API.</span><span class="sxs-lookup"><span data-stu-id="03cc0-158">IdentityServer ships a [JavaScript client](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="03cc0-159">Ссылки</span><span class="sxs-lookup"><span data-stu-id="03cc0-159">References</span></span>

- [<span data-ttu-id="03cc0-160">Документация по IdentityServer</span><span class="sxs-lookup"><span data-stu-id="03cc0-160">IdentityServer documentation</span></span>](https://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="03cc0-161">Типы приложений</span><span class="sxs-lookup"><span data-stu-id="03cc0-161">Application types</span></span>](/azure/active-directory/develop/app-types)
- [<span data-ttu-id="03cc0-162">Клиент OIDC JavaScript</span><span class="sxs-lookup"><span data-stu-id="03cc0-162">JavaScript OIDC client</span></span>](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="03cc0-163">[Назад](azure-active-directory.md)
>[Вперед](security.md)</span><span class="sxs-lookup"><span data-stu-id="03cc0-163">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
