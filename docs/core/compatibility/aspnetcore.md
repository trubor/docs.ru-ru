---
title: Критические изменения ASP.NET Core
titleSuffix: ''
description: В этой статье приведен список критических изменений в ASP.NET Core 3.0 и 3.1.
ms.date: 11/03/2020
ms.author: scaddie
ms.openlocfilehash: 080cd3c34617e932b64806a6aa1268b4e397e410
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497220"
---
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a><span data-ttu-id="c1f15-103">Критические изменения ASP.NET Core для версий 3.0 и 3.1.</span><span class="sxs-lookup"><span data-stu-id="c1f15-103">ASP.NET Core breaking changes for versions 3.0 and 3.1</span></span>

<span data-ttu-id="c1f15-104">ASP.NET Core предоставляет функции разработки веб-приложений, используемые .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1f15-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="c1f15-105">Выберите одну из следующих ссылок для критических изменений в определенной версии.</span><span class="sxs-lookup"><span data-stu-id="c1f15-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="c1f15-106">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c1f15-106">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="c1f15-107">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c1f15-107">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="c1f15-108">На этой странице описаны следующие критические изменения в ASP.NET Core версий 3.0 и 3.1.</span><span class="sxs-lookup"><span data-stu-id="c1f15-108">The following breaking changes in ASP.NET Core 3.0 and 3.1 are documented on this page:</span></span>

- [<span data-ttu-id="c1f15-109">Удалены устаревшие API в областях борьбы с фальсификацией, CORS, диагностики, MVC и маршрутизации</span><span class="sxs-lookup"><span data-stu-id="c1f15-109">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="c1f15-110">Проверка подлинности. Использование Google + прекращено</span><span class="sxs-lookup"><span data-stu-id="c1f15-110">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="c1f15-111">Проверка подлинности. Удалено свойство HttpContext.Authentication</span><span class="sxs-lookup"><span data-stu-id="c1f15-111">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="c1f15-112">Проверка подлинности. Заменены типы Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="c1f15-112">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="c1f15-113">Проверка подлинности. Изменена подпись ExchangeCodeAsync OAuthHandler</span><span class="sxs-lookup"><span data-stu-id="c1f15-113">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="c1f15-114">Авторизация. Перегрузка AddAuthorization перемещена в другую сборку</span><span class="sxs-lookup"><span data-stu-id="c1f15-114">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="c1f15-115">Авторизация. IAllowAnonymous удален из AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="c1f15-115">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="c1f15-116">Авторизация. Для реализаций IAuthorizationPolicyProvider требуется новый метод</span><span class="sxs-lookup"><span data-stu-id="c1f15-116">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="c1f15-117">Кэширование. Удалено свойство CompactOnMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="c1f15-117">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="c1f15-118">Кэширование. Microsoft.Extensions.Caching.SqlServer использует новый пакет SqlClient</span><span class="sxs-lookup"><span data-stu-id="c1f15-118">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="c1f15-119">Защита данных. DataProtection.Blobs использует новые API службы хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="c1f15-119">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [<span data-ttu-id="c1f15-120">Размещение. Модуль AspNetCoreModule версии 1 удален из пакета размещения Windows</span><span class="sxs-lookup"><span data-stu-id="c1f15-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="c1f15-121">Размещение. Универсальный узел ограничивает внедрение через конструктор Startup</span><span class="sxs-lookup"><span data-stu-id="c1f15-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="c1f15-122">Размещение. Для приложений IIS вне процесса включено перенаправление HTTPS</span><span class="sxs-lookup"><span data-stu-id="c1f15-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="c1f15-123">Размещение. Удалены типы IHostingEnvironment и IApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="c1f15-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="c1f15-124">Размещение. ObjectPoolProvider удален из зависимостей WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="c1f15-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="c1f15-125">HTTP. Изменения SameSite в браузере влияют на проверку подлинности</span><span class="sxs-lookup"><span data-stu-id="c1f15-125">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="c1f15-126">HTTP. Удалена расширяемость DefaultHttpContext</span><span class="sxs-lookup"><span data-stu-id="c1f15-126">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="c1f15-127">HTTP. Поля HeaderNames изменены на статические только для чтения</span><span class="sxs-lookup"><span data-stu-id="c1f15-127">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="c1f15-128">HTTP. Изменения в инфраструктуре текста ответа</span><span class="sxs-lookup"><span data-stu-id="c1f15-128">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="c1f15-129">HTTP. Внесены изменения в некоторые значения по умолчанию для параметра SameSite для файлов cookie</span><span class="sxs-lookup"><span data-stu-id="c1f15-129">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="c1f15-130">HTTP. Синхронный ввод-вывода отключен по умолчанию</span><span class="sxs-lookup"><span data-stu-id="c1f15-130">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="c1f15-131">Удостоверение. Удалена перегрузка метода AddDefaultUI</span><span class="sxs-lookup"><span data-stu-id="c1f15-131">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="c1f15-132">Удостоверение. Изменена версия начальной загрузки пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="c1f15-132">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="c1f15-133">Удостоверение. SignInAsync создает исключение для удостоверения, не прошедшего проверку подлинности</span><span class="sxs-lookup"><span data-stu-id="c1f15-133">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="c1f15-134">Удостоверение. Конструктор SignInManager принимает новый параметр</span><span class="sxs-lookup"><span data-stu-id="c1f15-134">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="c1f15-135">Удостоверение. Пользовательский интерфейс использует функцию статических веб-ресурсов</span><span class="sxs-lookup"><span data-stu-id="c1f15-135">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="c1f15-136">Kestrel. Удалены адаптеры подключений</span><span class="sxs-lookup"><span data-stu-id="c1f15-136">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="c1f15-137">Kestrel. Удалена пустая сборка HTTPS</span><span class="sxs-lookup"><span data-stu-id="c1f15-137">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="c1f15-138">Kestrel. Заголовки трейлеров запросов перемещены в новую коллекцию</span><span class="sxs-lookup"><span data-stu-id="c1f15-138">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="c1f15-139">Kestrel. Внесены изменения в слой абстракции транспорта</span><span class="sxs-lookup"><span data-stu-id="c1f15-139">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="c1f15-140">Локализация. Интерфейсы API отмечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="c1f15-140">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="c1f15-141">Ведение журнала. Класс DebugLogger стал внутренним</span><span class="sxs-lookup"><span data-stu-id="c1f15-141">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="c1f15-142">MVC. Удален асинхронный суффикс действия контроллера</span><span class="sxs-lookup"><span data-stu-id="c1f15-142">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="c1f15-143">MVC. JsonResult перемещен в Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="c1f15-143">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="c1f15-144">MVC. Использование средства предварительной компиляции прекращено</span><span class="sxs-lookup"><span data-stu-id="c1f15-144">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="c1f15-145">MVC. Типы теперь стали внутренними</span><span class="sxs-lookup"><span data-stu-id="c1f15-145">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="c1f15-146">MVC. Удалена оболочка совместимости веб-интерфейса API</span><span class="sxs-lookup"><span data-stu-id="c1f15-146">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="c1f15-147">Razor. Удален API RazorTemplateEngine</span><span class="sxs-lookup"><span data-stu-id="c1f15-147">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="c1f15-148">Razor. Компиляция среды выполнения перемещена в пакет</span><span class="sxs-lookup"><span data-stu-id="c1f15-148">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="c1f15-149">Состояние сеанса. Удалены устаревшие API</span><span class="sxs-lookup"><span data-stu-id="c1f15-149">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="c1f15-150">Общая платформа. Из Microsoft.AspNetCore.App удалена сборка</span><span class="sxs-lookup"><span data-stu-id="c1f15-150">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="c1f15-151">Общая платформа. Удален Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="c1f15-151">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="c1f15-152">SignalR. Заменен HandshakeProtocol.SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="c1f15-152">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="c1f15-153">SignalR. Удалены методы HubConnection</span><span class="sxs-lookup"><span data-stu-id="c1f15-153">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="c1f15-154">SignalR. Изменены конструкторы HubConnectionContext</span><span class="sxs-lookup"><span data-stu-id="c1f15-154">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="c1f15-155">SignalR. Изменено имя пакета клиента JavaScript</span><span class="sxs-lookup"><span data-stu-id="c1f15-155">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="c1f15-156">SignalR. Устаревшие API</span><span class="sxs-lookup"><span data-stu-id="c1f15-156">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="c1f15-157">Одностраничные приложения. Изменено поведение по умолчанию при переключении на средство ведения журнала консоли SpaServices и NodeServices</span><span class="sxs-lookup"><span data-stu-id="c1f15-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="c1f15-158">Одностраничные приложения. SpaServices и NodeServices отмечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="c1f15-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="c1f15-159">Целевая платформа: прекращена поддержка .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1f15-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="c1f15-160">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c1f15-160">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="c1f15-161">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c1f15-161">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
