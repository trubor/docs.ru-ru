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
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a>Критические изменения ASP.NET Core для версий 3.0 и 3.1.

ASP.NET Core предоставляет функции разработки веб-приложений, используемые .NET Core.

Выберите одну из следующих ссылок для критических изменений в определенной версии.

* [ASP.NET Core 3.1](#aspnet-core-31)
* [ASP.NET Core 3.0](#aspnet-core-30)

На этой странице описаны следующие критические изменения в ASP.NET Core версий 3.0 и 3.1.

- [Удалены устаревшие API в областях борьбы с фальсификацией, CORS, диагностики, MVC и маршрутизации](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Проверка подлинности. Использование Google + прекращено](#authentication-google-deprecated-and-replaced)
- [Проверка подлинности. Удалено свойство HttpContext.Authentication](#authentication-httpcontextauthentication-property-removed)
- [Проверка подлинности. Заменены типы Newtonsoft.Json](#authentication-newtonsoftjson-types-replaced)
- [Проверка подлинности. Изменена подпись ExchangeCodeAsync OAuthHandler](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Авторизация. Перегрузка AddAuthorization перемещена в другую сборку](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Авторизация. IAllowAnonymous удален из AuthorizationFilterContext.Filters](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Авторизация. Для реализаций IAuthorizationPolicyProvider требуется новый метод](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Кэширование. Удалено свойство CompactOnMemoryPressure](#caching-compactonmemorypressure-property-removed)
- [Кэширование. Microsoft.Extensions.Caching.SqlServer использует новый пакет SqlClient](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Защита данных. DataProtection.Blobs использует новые API службы хранилища Azure](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [Размещение. Модуль AspNetCoreModule версии 1 удален из пакета размещения Windows](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Размещение. Универсальный узел ограничивает внедрение через конструктор Startup](#hosting-generic-host-restricts-startup-constructor-injection)
- [Размещение. Для приложений IIS вне процесса включено перенаправление HTTPS](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Размещение. Удалены типы IHostingEnvironment и IApplicationLifetime](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Размещение. ObjectPoolProvider удален из зависимостей WebHostBuilder](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP. Изменения SameSite в браузере влияют на проверку подлинности](#http-browser-samesite-changes-impact-authentication)
- [HTTP. Удалена расширяемость DefaultHttpContext](#http-defaulthttpcontext-extensibility-removed)
- [HTTP. Поля HeaderNames изменены на статические только для чтения](#http-headernames-constants-changed-to-static-readonly)
- [HTTP. Изменения в инфраструктуре текста ответа](#http-response-body-infrastructure-changes)
- [HTTP. Внесены изменения в некоторые значения по умолчанию для параметра SameSite для файлов cookie](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP. Синхронный ввод-вывода отключен по умолчанию](#http-synchronous-io-disabled-in-all-servers)
- [Удостоверение. Удалена перегрузка метода AddDefaultUI](#identity-adddefaultui-method-overload-removed)
- [Удостоверение. Изменена версия начальной загрузки пользовательского интерфейса](#identity-default-bootstrap-version-of-ui-changed)
- [Удостоверение. SignInAsync создает исключение для удостоверения, не прошедшего проверку подлинности](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Удостоверение. Конструктор SignInManager принимает новый параметр](#identity-signinmanager-constructor-accepts-new-parameter)
- [Удостоверение. Пользовательский интерфейс использует функцию статических веб-ресурсов](#identity-ui-uses-static-web-assets-feature)
- [Kestrel. Удалены адаптеры подключений](#kestrel-connection-adapters-removed)
- [Kestrel. Удалена пустая сборка HTTPS](#kestrel-empty-https-assembly-removed)
- [Kestrel. Заголовки трейлеров запросов перемещены в новую коллекцию](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel. Внесены изменения в слой абстракции транспорта](#kestrel-transport-abstractions-removed-and-made-public)
- [Локализация. Интерфейсы API отмечены как устаревшие](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Ведение журнала. Класс DebugLogger стал внутренним](#logging-debuglogger-class-made-internal)
- [MVC. Удален асинхронный суффикс действия контроллера](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC. JsonResult перемещен в Microsoft.AspNetCore.Mvc.Core](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC. Использование средства предварительной компиляции прекращено](#mvc-precompilation-tool-deprecated)
- [MVC. Типы теперь стали внутренними](#mvc-pubternal-types-changed-to-internal)
- [MVC. Удалена оболочка совместимости веб-интерфейса API](#mvc-web-api-compatibility-shim-removed)
- [Razor. Удален API RazorTemplateEngine](#razor-razortemplateengine-api-removed)
- [Razor. Компиляция среды выполнения перемещена в пакет](#razor-runtime-compilation-moved-to-a-package)
- [Состояние сеанса. Удалены устаревшие API](#session-state-obsolete-apis-removed)
- [Общая платформа. Из Microsoft.AspNetCore.App удалена сборка](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Общая платформа. Удален Microsoft.AspNetCore.All](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR. Заменен HandshakeProtocol.SuccessHandshakeData](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR. Удалены методы HubConnection](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR. Изменены конструкторы HubConnectionContext](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR. Изменено имя пакета клиента JavaScript](#signalr-javascript-client-package-name-changed)
- [SignalR. Устаревшие API](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [Одностраничные приложения. Изменено поведение по умолчанию при переключении на средство ведения журнала консоли SpaServices и NodeServices](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Одностраничные приложения. SpaServices и NodeServices отмечены как устаревшие](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Целевая платформа: прекращена поддержка .NET Framework](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a>ASP.NET Core 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3.0

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
