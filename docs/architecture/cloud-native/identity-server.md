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
# <a name="identityserver-for-cloud-native-applications"></a>IdentityServer для собственных приложений в облаке

IdentityServer — это сервер проверки подлинности, который реализует стандарты OpenID Connect Connect (OIDC) и OAuth 2,0 для ASP.NET Core. Он предназначен для предоставления общего способа проверки подлинности запросов ко всем приложениям независимо от того, являются ли они веб-приложениями, собственными, мобильными или интерфейсными конечными точками API. IdentityServer можно использовать для реализации единого Sign-On (единого входа) для нескольких приложений и типов приложений. Его можно использовать для проверки подлинности реальных пользователей с помощью форм входа и аналогичных пользовательских интерфейсов, а также для проверки подлинности на основе служб, которая обычно включает выдачу, проверку и обновление маркеров без какого-либо пользовательского интерфейса. IdentityServer разработана как настраиваемое решение. Каждый экземпляр обычно настраивается в соответствии с потребностями конкретной организации и/или набора приложений.

## <a name="common-web-app-scenarios"></a>Распространенные сценарии веб-приложений

Как правило, приложения должны поддерживать некоторые или все из следующих сценариев:

- Пользователи, обращающиеся к веб-приложениям с помощью браузера.
- Пользователи, обращающиеся к внутренним веб-API из приложений на основе браузера.
- Пользователи мобильных и собственных клиентов, обращающихся к серверным веб-API.
- Другие приложения, обращающиеся к серверным веб-API (без активного пользователя или пользовательского интерфейса).
- Любому приложению может потребоваться взаимодействовать с другими веб-API, используя собственное удостоверение или делегируя идентификатору пользователя.

![Типы приложений и сценариев](./media/application-types.png)

**Рис. 8-1**. Типы приложений и сценарии.

В каждом из этих сценариев предоставленная функциональность должна быть защищена от несанкционированного использования. Как минимум, обычно требуется проверка подлинности пользователя или участника, выполняющего запрос ресурса. Эта проверка подлинности может использовать один из нескольких распространенных протоколов, таких как SAML2p, WS-подача или OpenID Connect Connect. Взаимодействие с API обычно использует протокол OAuth2 и его поддержку для маркеров безопасности. Отделение этих критических проблем безопасности и их реализация от самих приложений обеспечивает согласованность и повышает безопасность и удобство обслуживания. Аутсорсинг этих задач на выделенный продукт, такой как IdentityServer, позволяет каждому приложению решить эти проблемы самостоятельно.

IdentityServer предоставляет по промежуточного слоя, которое выполняется в приложении ASP.NET Core и добавляет поддержку OpenID Connect Connect и OAuth2 (см. [Поддерживаемые спецификации](https://docs.identityserver.io/en/latest/intro/specs.html)). Организации создают собственное ASP.NET Core приложение с помощью по промежуточного слоя IdentityServer, которое действует как STS для всех своих протоколов безопасности на основе маркеров. По промежуточного слоя IdentityServer предоставляет конечные точки для поддержки стандартных функций, в том числе:

- Авторизация (проверка подлинности конечного пользователя)
- Токен (запрос маркера программным путем)
- Обнаружение (метаданные о сервере)
- Сведения о пользователе (получение сведений о пользователе с действительным маркером доступа)
- Авторизация устройства (используется для запуска авторизации потока устройства)
- Самоанализ (проверка маркера)
- Отзыв (отзыв маркера)
- Завершение сеанса (активация единого выхода для всех приложений)

## <a name="getting-started"></a>Начало работы

IdentityServer4 доступен по двум лицензиям:  

* RPL — позволяет использовать IdentityServer4 Free, если используется в работе с открытым исходным кодом
* Оплачено — давайте будем использовать IdentityServer4 в коммерческом сценарии.

Обратитесь к официальной странице [цен на продукт](https://duendesoftware.com/products/identityserver) .

Его можно добавить в приложения с помощью пакетов NuGet. Основной пакет — [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) , который был загружен более 4 000 000 раз. Базовый пакет не включает код пользовательского интерфейса и поддерживает только в конфигурации памяти. Чтобы использовать ее с базой данных, вам также понадобится поставщик данных, такой как [IdentityServer4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , который использует Entity Framework Core для хранения конфигурации и рабочих данных для IdentityServer. Для пользовательского интерфейса можно скопировать файлы из [репозитория пользовательского интерфейса](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) быстрого запуска в приложение ASP.NET Core MVC, чтобы добавить поддержку входа и выхода с помощью по промежуточного слоя IdentityServer.

## <a name="configuration"></a>Конфигурация

IdentityServer поддерживает различные типы протоколов и поставщиков проверки подлинности, которые можно настроить в рамках каждой выборочной установки. Обычно это делается в классе ASP.NET Core приложения `Startup` в `ConfigureServices` методе. Конфигурация включает в себя указание поддерживаемых протоколов и пути к серверам и конечным точкам, которые будут использоваться. На рис. 8-2 показан пример конфигурации, взятой из проекта пользовательского интерфейса быстрого запуска IdentityServer4:

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

**Рис. 8-2**. Настройка IdentityServer.

IdentityServer также содержит общедоступный демонстрационный сайт, который можно использовать для тестирования различных протоколов и конфигураций. Он расположен по адресу [https://demo.identityserver.io/](https://demo.identityserver.io/) и содержит сведения о том, как настроить его поведение на основе `client_id` предоставленного ему поведения.

## <a name="javascript-clients"></a>Клиенты JavaScript

Многие облачные приложения используют API на стороне сервера и полнофункциональные клиентские приложения с одними страницами (одностраничные приложения) на внешнем интерфейсе. IdentityServer поставляется с [клиентом JavaScript](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) ( `oidc-client.js` ) через NPM, который можно добавить в одностраничные приложения, чтобы использовать IdentityServer для входа, выхода и проверки подлинности на основе маркеров для веб-API.

## <a name="references"></a>Ссылки

- [Документация по IdentityServer](https://docs.identityserver.io/en/latest/)
- [Типы приложений](/azure/active-directory/develop/app-types)
- [Клиент OIDC JavaScript](https://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
>[Назад](azure-active-directory.md)
>[Вперед](security.md)
