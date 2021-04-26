---
title: Обеспечение безопасности веб-приложений и микрослужб .NET
description: Безопасность микрослужб и веб-приложений .NET — узнайте о способах проверки подлинности в веб-приложениях ASP.NET Core.
author: mjrousos
ms.date: 01/13/2021
ms.openlocfilehash: 9e564b7c53933d7259f18e2c328325432b4383ed
ms.sourcegitcommit: 178ccefa8c454bfae844ce12ed222a54913df157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2021
ms.locfileid: "107883232"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Обеспечение безопасности микрослужб и веб-приложений .NET

Безопасность микрослужб и веб-приложений — это очень обширная тема, для полного рассмотрения которой может потребоваться несколько книг, подобной этой. Поэтому в этом разделе мы уделим основное внимание аутентификации, авторизации и секретам приложений.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Внедрение проверки подлинности в микрослужбы и веб-приложения .NET

Доступ к ресурсам и API-интерфейсам, публикуемым службой, часто требуется ограничить определенным кругом надежных пользователей или клиентов. Первый этап принятия подобных решений о доверии на уровне API — проверка подлинности. Проверка подлинности — это процесс достоверного установления личности пользователя.

При использовании микрослужб управление проверкой подлинности обычно осуществляется централизованно. Если имеется шлюз API, проверку подлинности целесообразно проводить в нем, как показано на рис. 9-1. При таком подходе отдельные микрослужбы не должны быть доступны напрямую (в обход шлюза API), если только не реализованы дополнительные средства безопасности для проверки того, поступают ли сообщения из шлюза или нет.

![Схема взаимодействия клиентского мобильного приложения с серверной частью.](./media/index/api-gateway-centralized-authentication.png)

**Рис. 9-1**. Централизованная проверка подлинности с помощью шлюза API

Когда шлюз API централизует проверку подлинности, он добавляет сведения о пользователе при переадресации запросов в микрослужбы. Если службы доступны напрямую, для проверки подлинности пользователей можно применять службу проверки подлинности, например Azure Active Directory или выделенную микрослужбу проверки подлинности, выступающую в роли службы токенов безопасности (STS). Сведения о доверии передаются между службами с помощью токенов безопасности или файлов cookie. (При необходимости эти токены могут передаваться между приложениями ASP.NET Core путем реализации [совместного использования файлов cookie](/aspnet/core/security/cookie-sharing).) Такая схема проиллюстрирована на рис. 9-2.

![Схема, показывающая проверку подлинности с помощью серверных микрослужб.](./media/index/identity-microservice-authentication.png)

**Рис. 9-2**. Проверка подлинности с помощью микрослужбы удостоверений; сведения о доверии передаются посредством токена авторизации

При прямом доступе к микрослужбам доверие, включающее проверку подлинности и авторизацию, обрабатывается общим для всех токеном безопасности, который выдает специализированная микрослужба.

### <a name="authenticate-with-aspnet-core-identity"></a>Проверка подлинности с помощью ASP.NET Core Identity

Основным механизмом для идентификации пользователей приложения в ASP.NET Core является система членства на основе [удостоверений ASP.NET Core](/aspnet/core/security/authentication/identity). В удостоверении ASP.NET Core хранятся сведения о пользователе (в том числе данные для входа, роли и утверждения). Само удостоверение находится в хранилище данных, которое настраивает разработчик. Как правило, хранилище данных ASP.NET Core Identity представляет собой хранилище Entity Framework, входящее в пакет `Microsoft.AspNetCore.Identity.EntityFrameworkCore`. Однако вы также можете использовать настраиваемые хранилища или пакеты сторонних поставщиков для хранения сведений удостоверений в Хранилище таблиц Azure, CosmosDB или других местах.

> [!TIP]
> В ASP.NET Core 2.1 и более поздних версиях предоставляется [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) в виде [библиотеки классов Razor](/aspnet/core/razor-pages/ui-class), поэтому в проекте не будет отображаться большая часть необходимого кода, как в предыдущих версиях. Дополнительные сведения о том, как настроить код Identity в соответствии со своими требованиями, см. в статье [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity) (Шаблоны для использования Identity в проектах ASP.NET Core).

Приведенный ниже код взят из шаблона проекта веб-приложения ASP.NET Core MVC 3.1 с выбранной проверкой подлинности отдельной учетной записи пользователя. В нем показано, как настроить ASP.NET Core Identity с помощью Entity Framework Core в методе `Startup.ConfigureServices`.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

После настройки системы ASP.NET Core Identity ее необходимо включить, добавив `app.UseAuthentication()` и `endpoints.MapRazorPages()` как показано в следующем коде в методе `Startup.Configure` службы.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> Для правильной работы Identity строки в приведенном выше коде **должны находиться в таком же порядке**.

Использование удостоверения ASP.NET Core обеспечивает несколько сценариев.

- Создание сведений о пользователе с помощью типа UserManager (userManager.CreateAsync).

- Проверка подлинности пользователей с помощью типа SignInManager. Вы можете использовать `signInManager.SignInAsync` для входа напрямую или `signInManager.PasswordSignInAsync` для проверки пользовательского пароля и последующего входа.

- Идентификация пользователя в соответствии со сведениями в файле cookie (которые считываются с помощью ПО промежуточного слоя удостоверения ASP.NET Core). Это позволяет включать в последующие запросы из браузера удостоверение и утверждения вошедшего в систему пользователя.

Удостоверение ASP.NET Core также поддерживает [двухфакторную проверку подлинности](/aspnet/core/security/authentication/2fa).

Для сценариев проверки подлинности, в которых используется локальное хранилище данных пользователей и удостоверения сохраняются между запросами с помощью файлов cookie (как обычно бывает в случае с веб-приложениями MVC), удостоверение ASP.NET Core является рекомендуемым решением.

### <a name="authenticate-with-external-providers"></a>Проверка подлинности с помощью внешних поставщиков

ASP.NET Core также поддерживает использование [внешних поставщиков проверки подлинности](/aspnet/core/security/authentication/social/) для обеспечения входа пользователей посредством рабочих процессов [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2). Это означает, что пользователи могут выполнять вход с помощью существующих процедур проверки подлинности, предоставляемых такими поставщиками, как Майкрософт, Google, Facebook или Twitter, и связывать свои удостоверения с удостоверением ASP.NET Core в вашем приложении.

Чтобы использовать внешнюю проверку подлинности (помимо промежуточного ПО для проверки подлинности), упомянутую ранее, с помощью метода `app.UseAuthentication()`, потребуется также зарегистрировать внешний поставщик в `Startup`, как показано в следующем примере:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

В следующей таблице показаны популярные внешние поставщики проверки подлинности и связанные с ними пакеты NuGet:

| **Поставщик**  | **Пакет**                                          |
| ------------- | ---------------------------------------------------- |
| **Майкрософт** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Во всех случаях необходимо выполнить процедуру регистрации приложения, которая зависит от поставщика и обычно включает в себя такие задачи:

1. Получение идентификатора клиентского приложения.
2. Получение секрета клиентского приложения.
3. Настройка URL-адреса перенаправления, осуществляемая ПО промежуточного слоя для авторизации и зарегистрированным поставщиком.
4. (Необязательно) Настройка URL-адреса выхода для правильной обработки выхода в сценарии с использованием единого входа.

Дополнительные сведения о настройке приложения для внешнего поставщика см. в документации ASP.NET Core по [внешнему поставщику проверки подлинности](/aspnet/core/security/authentication/social/).

> [!TIP]
> Все данные обрабатываются с помощью ПО промежуточного слоя авторизации и ранее упомянутых служб. Поэтому при создании в Visual Studio проекта веб-приложения ASP.NET Core нужно лишь выбрать вариант проверки подлинности **Учетная запись отдельного пользователя** (помимо регистрации поставщиков, упомянутых ранее), как показано на рис. 9-3.

![Снимок экрана: диалоговое окно "Создать веб-приложение ASP.NET Core".](./media/index/select-individual-user-account-authentication-option.png)

**Рис. 9-3**. Выбор варианта "Отдельная учетная запись пользователя" для использования внешней проверки подлинности при создании проекта веб-приложения в Visual Studio 2019.

Помимо перечисленных выше внешних поставщиков проверки подлинности, доступны пакеты сторонних производителей, предоставляющие ПО промежуточного слоя для использования множества других внешних поставщиков проверки подлинности. Список см. в репозитории [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) на сайте GitHub.

Вы также можете создать собственное ПО промежуточного слоя для внешней проверки подлинности, позволяющее решать какие-то особые задачи.

### <a name="authenticate-with-bearer-tokens"></a>Проверка подлинности с помощью токенов носителя

Проверка подлинности посредством удостоверения ASP.NET Core (или посредством удостоверения и внешних поставщиков проверки подлинности) подходит для многих веб-приложений, позволяющих хранить сведения о пользователе в файле cookie. Но в других ситуациях хранить и передавать данные в файлах cookie нецелесообразно.

Например, в веб-API ASP.NET Core, предоставляющем конечные точки с поддержкой REST, к которым могут обращаться одностраничные приложения, собственные клиенты или даже другие веб-интерфейсы API, как правило, желательно использовать проверку подлинности посредством токена носителя. Такие приложения не работают с файлами cookie, но могут легко извлекать токен носителя и включать его в заголовок авторизации последующих запросов. Для проверки подлинности на основе токенов ASP.NET Core поддерживает несколько способов использования [OAuth 2.0](https://oauth.net/2/) и [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Проверка подлинности с помощью поставщика удостоверений OpenID Connect или OAuth 2.0

Если сведения о пользователе хранятся в Azure Active Directory или другом решении для управления удостоверениями, поддерживающем OpenID Connect или OAuth 2.0, вы можете использовать пакет **Microsoft.AspNetCore.Authentication.OpenIdConnect** для проверки подлинности с помощью рабочего процесса OpenID Connect. Например, для проверки подлинности в микрослужбе Identity.Api из eShopOnContainers веб-приложение ASP.NET Core может использовать ПО промежуточного слоя из этого пакета, как показано в следующем упрощенном примере `Startup.cs`:

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = Configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

При использовании этого рабочего процесса ПО промежуточного слоя ASP.NET Core Identity не требуется, так как служба Identity берет на себя хранение всех пользовательских сведений и проверку подлинности.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Выпуск токенов безопасности службой ASP.NET Core

Если вы предпочитаете выпускать токены безопасности для локальных пользователей удостоверения ASP.NET Core, а не использовать внешний поставщик удостоверений, то вы можете прибегнуть к ряду полезных библиотек сторонних разработчиков.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) и [OpenIddict](https://github.com/openiddict/openiddict-core) — это поставщики OpenID Connect, которые легко интегрируются с удостоверением ASP.NET Core и позволяют выпускать токены безопасности из службы ASP.NET Core. В [документации по IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) приведены подробные инструкции по работе с этой библиотекой. Ниже описываются основные действия по использованию IdentityServer4 для выпуска токенов.

1. Вызовите app.UseIdentityServer в методе Startup.Configure, чтобы добавить IdentityServer4 в конвейер обработки HTTP-запросов приложения. Это позволит библиотеке обрабатывать запросы к конечным точкам OpenID Connect и OAuth2 как /connect/token.

2. Настройте IdentityServer4 в методе Startup.ConfigureServices, выполнив вызов services.AddIdentityServer.

3. Чтобы настроить сервер удостоверений, нужно задать следующие данные:

   - [учетные данные](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) для входа;

   - [ресурсы удостоверений и API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html), к которым пользователи могут запрашивать доступ:

      - ресурсы API представляют защищенные данные или функциональные возможности, к которым пользователь может получать доступ с помощью токена доступа; примером ресурса API может служить веб-API (или набор веб-API), требующий авторизации;

      - ресурсы удостоверений представляют сведения (утверждения), которые предоставляются клиенту для идентификации пользователя; утверждения могут включать имя пользователя, адрес электронной почты и другие данные;

   - [клиенты](https://identityserver4.readthedocs.io/en/latest/topics/clients.html), которые будут подключаться для запроса токенов;

   - механизм хранения сведений о пользователях, например [удостоверение ASP.NET Core](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) или иной.

При указании клиентов и ресурсов, используемых IdentityServer4, вы можете передать коллекцию <xref:System.Collections.Generic.IEnumerable%601> соответствующего типа в методы, которые принимают хранилища клиентов или ресурсов в памяти. В более сложных сценариях типы клиентов или поставщиков ресурсов можно предоставлять с помощью внедрения зависимостей.

Ниже приведен пример конфигурации для IdentityServer4, которая предполагает использование клиентов и ресурсов в памяти, предоставляемых пользовательским типом IClientStore.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a>Использование токенов безопасности

Проверка подлинности в конечной точке OpenID Connect или выпуск собственных токенов безопасности подходят для некоторых ситуаций. Но что если службе нужно просто предоставлять доступ только тем пользователям, у которых есть действительные токены безопасности, предоставленные другой службой?

Для такого случая в пакете **Microsoft.AspNetCore.Authentication.JwtBearer** доступно ПО промежуточного слоя, обрабатывающее токены JWT. JWT расшифровывается как [JSON Web Token](https://tools.ietf.org/html/rfc7519) (веб-токен JSON). Это распространенный формат токенов безопасности (определенный в документе RFC 7519) для передачи утверждений безопасности. Упрощенный пример использования ПО промежуточного слоя для применения таких токенов показан в следующем фрагменте кода, взятом из микрослужбы Ordering.Api в eShopOnContainers.

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

В примере используются следующие параметры.

- `Audience` представляет получателя входящего токена или ресурса, к которому токен предоставляет доступ. Если значение этого параметра не совпадает со значением параметра в токене, токен будет отклонен.

- `Authority` — это адрес сервера проверки подлинности, выпускающего токен. ПО промежуточного слоя для проверки подлинности носителя JWT использует этот универсальный код ресурса (URI) для получения открытого ключа, с помощью которого можно проверить подпись токена. ПО промежуточного слоя также проверяет, совпадает ли значение параметра `iss` в токене с этим кодом URI.

Другой параметр, `RequireHttpsMetadata`, полезен для тестирования. Присвоив ему значение false (ложь), можно проводить тестирование в средах, где у вас нет сертификатов. В реальных развертываниях токены носителя JWT следует передавать только по протоколу HTTPS.

При наличии этого ПО промежуточного слоя токены JWT автоматически извлекаются из заголовков авторизации. Затем они десериализируются, проверяются (на основе значений параметров `Audience` и `Authority`) и сохраняются как сведения о пользователе для последующего применения в действиях MVC или фильтрах авторизации.

ПО промежуточного слоя для проверки подлинности носителя JWT может поддерживать и более сложные сценарии, например проверку токена с помощью локального сертификата, если центр сертификации недоступен. В этом сценарии вы можете указать объект `TokenValidationParameters` в объекте `JwtBearerOptions`.

## <a name="additional-resources"></a>Дополнительные ресурсы

- **Совместное использование файлов cookie в приложениях** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Общие сведения об Identity** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Рик Андерсон (Rick Anderson). Двухфакторная проверка подлинности с помощью SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Проверка подлинности Facebook, Google и других внешних поставщиков** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Мичелл Аникас (Michell Anicas). An Introduction to OAuth 2 (Введение в OAuth 2)**  \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **репозиторий GitHub для поставщиков OAuth в ASP.NET**\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Официальная документация** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Назад](../implement-resilient-applications/monitor-app-health.md)
>[Вперед](authorization-net-microservices-web-applications.md)
