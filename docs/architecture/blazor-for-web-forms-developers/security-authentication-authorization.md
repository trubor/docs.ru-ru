---
title: Безопасность. Проверка подлинности и авторизация в ASP.NET Web Forms и Blazor
description: Узнайте, как обрабатывать проверку подлинности и авторизацию в ASP.NET Web Forms и Blazor.
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 0344960237a5d9da61eb0d85987c44e136f1be48
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509849"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-blazor"></a>Безопасность. Проверка подлинности и авторизация в ASP.NET Web Forms и Blazor 

Для миграции приложения из ASP.NET Web Forms в Blazor почти наверняка потребуется обновить способ выполнения проверки подлинности и авторизации, если в приложении настроена проверка подлинности. В этой главе рассказывается, как перейти с модели универсального поставщика ASP.NET Web Forms (для членства, ролей и профилей пользователей) и как работать с ASP.NET Core Identity из приложений Blazor. В этой главе будут рассмотрены только общие шаги и аспекты, а подробные шаги и сценарии можно найти в справочной документации.

## <a name="aspnet-universal-providers"></a>Универсальные поставщики ASP.NET

Начиная с ASP.NET 2.0 платформа ASP.NET Web Forms поддерживает модель поставщика для различных функций, включая членство. С приложениями ASP.NET Web Forms обычно развертывается универсальный поставщик членства наряду с необязательным поставщиком ролей. Он обеспечивает надежный и безопасный способ управления проверкой подлинности и авторизацией, и этот способ отлично работает и сегодня. Последнее предложение этих универсальных поставщиков доступно в виде пакета NuGet [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).

Универсальные поставщики работают со схемой базы данных SQL, которая включает такие таблицы, как `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles` и `aspnet_Users`. При настройке с помощью [команды aspnet_regsql.exe](/previous-versions/ms229862(v=vs.140)) поставщики устанавливают таблицы и хранимые процедуры, которые предоставляют все необходимые запросы и команды для работы с базовыми данными. Схема базы данных и эти хранимые процедуры несовместимы с новыми системами идентификации ASP.NET Identity и ASP.NET Core Identity, поэтому существующие данные необходимо перенести в новую систему. На рисунке 1 показан пример схемы таблицы, настроенной для универсальных поставщиков.

![Схема универсальных поставщиков](./media/security/membership-tables.png)

Универсальный поставщик обрабатывает пользователей, членство, роли и профили. Пользователям назначаются глобальные уникальные идентификаторы, а основная информация, такая как userId, userName и т. д., хранится в таблице `aspnet_Users`. Сведения аутентификации, такие как пароль, формат пароля, соль пароля, счетчики и детали блокировки и т. д., хранятся в таблице `aspnet_Membership`. Роли состоят просто из имен и уникальных идентификаторов, которые назначаются пользователям с помощью таблицы связей `aspnet_UsersInRoles`, обеспечивающей отношение "многие ко многим".

Если ваша существующая система использует роли в дополнение к членству, вам потребуется перенести в ASP.NET Core Identity учетные записи пользователей, связанные пароли, роли и членство в ролях. Вам также, скорее всего, потребуется обновить свой код, в котором вы в настоящее время выполняете проверки ролей, используя операторы if, чтобы вместо этого использовать декларативные фильтры, атрибуты и (или) вспомогательные функции тегов. Мы более подробно рассмотрим аспекты миграции в конце этой главы.

### <a name="authorization-configuration-in-web-forms"></a>Настройка авторизации в веб-формах

Чтобы настроить авторизованный доступ к определенным страницам в приложении ASP.NET Web Forms, обычно вы указываете, что определенные страницы или папки недоступны для анонимных пользователей. Эта настройка выполняется в файле web.config:

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

Раздел конфигурации `authentication` устанавливает аутентификацию форм для приложения. Раздел `authorization` используется для запрета анонимных пользователей во всем приложении. Однако вы можете предоставить более детализированные правила авторизации на основе местоположения, а также применять проверки авторизации на основе ролей.

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

Приведенная выше конфигурация в сочетании с первой позволит анонимным пользователям получать доступ к странице входа в систему, переопределяя общесайтовое ограничение для пользователей, не прошедших проверку подлинности.

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

Приведенная выше конфигурация в сочетании с другими разрешает доступ к папке `/admin` и всем ресурсам в ней только членам роли "Администраторы". Это ограничение также можно применить, поместив отдельный файл `web.config` в корень папки `/admin`.

### <a name="authorization-code-in-web-forms"></a>Код авторизации в веб-формах

Помимо настройки доступа с помощью `web.config` вы также можете программными средствами настроить доступ и поведение в своем приложении веб-форм. Например, вы можете ограничивать возможность выполнения определенных операций или просмотра определенных данных в зависимости от роли пользователя.

Этот код можно использовать как в логике кода программной части, так и на самой странице:

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

Помимо проверки членства пользователей в ролях, вы также можете определять, аутентифицированы ли они (хотя часто это лучше делать с помощью конфигурации на основе местоположения, упоминавшейся выше). Ниже приведен пример такого подхода.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

В приведенном выше коде управление доступом на основе ролей (RBAC) используется для определения того, видны ли определенные элементы страницы, например `SecretPanel`, в зависимости от роли текущего пользователя.

Как правило, в приложениях ASP.NET Web Forms безопасность настраивается в файле `web.config`, а затем добавляются дополнительные проверки, где это необходимо, на страницах `.aspx` и связанных с ними файлах кода программной части `.aspx.cs`. В большинстве приложений используется универсальный поставщик членства, часто с дополнительным поставщиком ролей.

## <a name="aspnet-core-identity"></a>Идентификация ASP.NET Core

Хотя система идентификации ASP.NET Core Identity по-прежнему отвечает за проверку подлинности и авторизацию, в ней используется другой набор абстракций и допущений по сравнению с универсальными поставщиками. Например, новая модель идентификации поддерживает стороннюю аутентификацию, разрешая пользователям проходить проверку подлинности с помощью учетной записи в социальной сети или другого надежного поставщика проверки подлинности. ASP.NET Core Identity поддерживает пользовательский интерфейс для часто используемых страниц, таких как страницы входа, выхода и регистрации. Эта система применяет EF Core для доступа к данным и использует миграции EF Core для создания необходимой схемы, которая требуется для поддержки ее модели данных. В разделе [Общие сведения об идентификации в ASP.NET Core](/aspnet/core/security/authentication/identity) дается хороший обзор того, что входит в ASP.NET Core Identity, и как начать работать с этой системой. Если вы еще не настроили ASP.NET Core Identity в своем приложении и его базе данных, это поможет вам начать работу.

### <a name="roles-claims-and-policies"></a>Роли, утверждения и политики

Как универсальные поставщики, так и ASP.NET Core Identity поддерживают концепцию ролей. Вы можете создавать роли для пользователей и назначать пользователям роли. Пользователи могут принадлежать к любому количеству ролей, и вы можете проверять членство в роли в рамках реализации авторизации.

Помимо ролей, ASP.NET Core Identity поддерживает концепции утверждений и политик. Хотя роль должна соответствовать набору ресурсов, к которому должен иметь доступ пользователь в этой роли, утверждение — это просто часть удостоверения пользователя. Утверждение — это пара "имя-значение", которая представляет собой предмет, а не то, что он может делать.

Можно напрямую проверять утверждения пользователя и на основе этих значений определять, следует ли предоставить пользователю доступ к ресурсу. Однако такие проверки часто повторяются и рассредоточены по всей системе. Лучше всего определить *политику*.

Политика авторизации включает одно или несколько требований. Политики регистрируются в рамках настройки службы авторизации в методе `ConfigureServices` файла `Startup.cs`. Например, в следующем фрагменте кода настраивается политика с именем "CanadiansOnly", которая требует, чтобы у пользователя было утверждение Country со значением "Canada".

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

[Дополнительные сведения о создании пользовательских политик см. в документации](/aspnet/core/security/authorization/policies).

Независимо от того, используете ли вы политики или роли, вы можете указать, что для конкретной страницы в вашем приложении Blazor требуется определенная роль или политика, с помощью атрибута `[Authorize]`, применяемого с помощью директивы `@attribute`.

Требование роли:

```csharp
@attribute [Authorize(Roles ="administrators")]
```

Требование соблюдения политики:

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

Если вам нужен доступ к состоянию проверки подлинности пользователя, ролям или утверждениям в вашем коде, существует два основных способа обеспечения этой функциональности. Первый — получать состояние проверки подлинности как каскадный параметр. Второй — получать доступ к состоянию с помощью внедренного `AuthenticationStateProvider`. Подробнее эти способы описаны в [документации по безопасности Blazor](/aspnet/core/blazor/security/).

В следующем коде показано, как получить `AuthenticationState` в качестве каскадного параметра.

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

Получив этот параметр, вы можете получить пользователя с помощью следующего кода.

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

В следующем коде показано, как внедрить `AuthenticationStateProvider`.

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

Установив поставщика, вы можете получить доступ к пользователю с помощью следующего кода:

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**Примечание.** Компонент `AuthorizeView`,который описывается далее в этой главе, предоставляет декларативный способ управления тем, что пользователь видит на странице или в компоненте.

Для работы с пользователями и утверждениями (в приложениях Blazor Server) вам также может потребоваться внедрить `UserManager<T>` (используйте `IdentityUser` по умолчанию), который можно использовать для перечисления и изменения утверждений для пользователя. Сначала внедрите тип и назначьте его свойству:

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

Затем используйте его для работы с утверждениями пользователя. В следующем примере показано, как добавить и сохранить утверждение для пользователя.

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

При работе с ролями придерживайтесь того же подхода. Возможно, вам потребуется внедрить `RoleManager<T>` (используйте `IdentityRole` для типа по умолчанию) для составления списка самих ролей и управления ими.

**Примечание.** В проектах Blazor WebAssembly вам потребуется предоставить серверные API для выполнения этих операций (вместо прямого использования `UserManager<T>` или `RoleManager<T>`). Клиентское приложение Blazor WebAssembly будет управлять утверждениями и (или) ролями, безопасно вызывая конечные точки API, предоставленные для этой цели.

### <a name="migration-guide"></a>Руководство по миграции

Для перехода с ASP.NET Web Forms и универсальных поставщиков на ASP.NET Core Identity необходимо выполнить несколько следующих действий.

1. Создать схему базы данных ASP.NET Core Identity в целевой базе данных.
2. Перенести данные из схемы универсального поставщика в схему ASP.NET Core Identity.
3. Перенести конфигурацию из `web.config` в ПО промежуточного слоя и службы, обычно в `Startup.cs`.
4. Обновить отдельные страницы с помощью элементов управления и условных операторов, чтобы использовать вспомогательные функции тегов и новые API идентификации.

В следующих разделах каждый этап рассматривается более подробно.

### <a name="creating-the-aspnet-core-identity-schema"></a>Создание схемы ASP.NET Core Identity

Существует несколько способов создания необходимой структуры таблиц, используемой для ASP.NET Core Identity. Самый простой — создать новое веб-приложение ASP.NET Core. Щелкните "Web Application", а затем измените параметры проверки подлинности так, чтобы использовать учетные записи отдельных пользователей.

![Новый проект с учетными записями отдельных пользователей](./media/security/individual-user-accounts.png)

То же самое можно сделать в командной строке, запустив `dotnet new webapp -au Individual`. Как только приложение будет создано, запустите его и зарегистрируйтесь на сайте. Вы должны активировать страницу, подобную показанной ниже:

![Страница применения миграций](./media/security/apply-migrations-page.png)

Нажмите кнопку "Apply Migrations", и необходимые таблицы базы данных будут для вас созданы. Кроме того, в вашем проекте должны появиться файлы миграции, как показано ниже:

![Файлы миграции](./media/security/migration-files.png)

Вы можете выполнить миграцию самостоятельно, не запуская веб-приложение, с помощью следующего инструмента командной строки:

```powershell
dotnet ef database update
```

Если вы предпочитаете запускать скрипт для применения новой схемы к существующей базе данных, вы можете создать скрипт для этих миграций из командной строки. Выполните эту команду, чтобы создать скрипт:

```powershell
dotnet ef migrations script -o auth.sql
```

Приведенная выше команда создаст скрипт SQL в выходном файле `auth.sql`, который затем можно будет запустить для любой базы данных, которая вам нужна. Если у вас возникли проблемы с запуском команд `dotnet ef`, [убедитесь, что в вашей системе установлены инструменты EF Core](/ef/core/miscellaneous/cli/dotnet).

Если у вас есть дополнительные столбцы в исходных таблицах, то необходимо будет определить наиболее подходящее место для этих столбцов в новой схеме. Как правило, столбцы, находящиеся в таблице `aspnet_Membership`, должны быть сопоставлены с таблицей `AspNetUsers`. Столбцы в `aspnet_Roles` должны быть сопоставлены с `AspNetRoles`. Все дополнительные столбцы в таблице `aspnet_UsersInRoles` будут добавлены в таблицу `AspNetUserRoles`.

Также имеет смысл обдумать размещение дополнительных столбцов в отдельных таблицах. Тогда при будущих миграциях не нужно будет учитывать такие настройки схемы удостоверений по умолчанию.

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>Перенос данных из универсальных поставщиков в ASP.NET Core Identity

Следующим шагом после создания целевой схемы таблиц является перенос записей пользователей и ролей в новую схему. Полный список различий в схемах, включая соответствие старых и новых столбцов, можно найти [здесь](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).

Чтобы перенести пользователей из членства в новые таблицы идентификаторов, вы должны [выполнить шаги, описанные в документации](/aspnet/core/migration/proper-to-2x/membership-to-core-identity). После того как эти шаги будут выполнены и скрипт предоставлен, ваши пользователи должны будут сменить пароль при следующем входе в систему.

Перенести пароли пользователей можно, но этот процесс намного сложнее. Требование обновления паролей в рамках процесса миграции и поощрение пользователей к использованию новых уникальных паролей повышает общую безопасность приложения.

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>Перенос параметров безопасности из web.config в Startup.cs

Как упоминалось выше, в ASP.NET членство и поставщики ролей настраиваются в файле `web.config` приложения. Так как приложения ASP.NET Core не привязаны к службам IIS и используют отдельную систему для настройки, эти параметры должны быть настроены в другом месте. По большей части ASP.NET Core Identity настраивается в файле `Startup.cs`. Откройте созданный ранее веб-проект (для создания схемы таблицы идентификаторов) и просмотрите его файл `Startup.cs`.

Метод ConfigureServices по умолчанию добавляет поддержку EF Core и Identity:

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

Метод расширения `AddDefaultIdentity` используется для настройки Identity на использование `ApplicationDbContext` по умолчанию и типа `IdentityUser` платформы. Если вы используете настраиваемый `IdentityUser`, обязательно укажите здесь его тип. Если эти методы расширения не работают в вашем приложении, убедитесь, что у вас имеются соответствующие операторы using и необходимые ссылки на пакеты NuGet. Например, в вашем проекте должна быть указана ссылка на некоторые версии пакетов `Microsoft.AspNetCore.Identity.EntityFrameworkCore` и `Microsoft.AspNetCore.Identity.UI`.

Также в `Startup.cs` вы должны видеть необходимое ПО промежуточного слоя, настроенное для сайта. В частности, должны быть настроены `UseAuthentication` и `UseAuthorization`, причем в правильном месте.

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity не настраивает анонимный доступ или доступ на основе ролей к расположениям из `Startup.cs`. Вам нужно будет перенести все данные конфигурации авторизации для конкретных местоположений в фильтры в ASP.NET Core. Запишите, каким папкам и страницам потребуются такие обновления. Вы внесете эти изменения в следующем разделе.

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>Обновление отдельных страниц для использования абстракций ASP.NET Core Identity

Если в вашем приложении ASP.NET Web Forms были настройки `web.config` для запрета анонимным пользователям доступа к определенным страницам или папкам, вы должны перенести эти изменения, добавив атрибут `[Authorize]` для таких страниц:

```razor
@attribute [Authorize]
```

Если вы еще сильнее ограничили доступ, разрешив его только пользователям, принадлежащим к определенной роли, то вы также должны перенести это поведение, добавив атрибут, определяющий роль:

```razor
@attribute [Authorize(Roles ="administrators")]
```

Атрибут `[Authorize]` работает только с компонентами `@page`, доступными через маршрутизатор Blazor. Этот атрибут не работает с дочерними компонентами, которые вместо этого должны использовать `AuthorizeView`.

Если в разметке страниц присутствует логика для определения, следует ли отображать какой-либо код конкретному пользователю, вы можете заменить ее компонентом `AuthorizeView`. [Компонент AuthorizeView](/aspnet/core/blazor/security#authorizeview-component) избирательно отображает элементы пользовательского интерфейса в зависимости от того, авторизован ли пользователь для их просмотра. Он также предоставляет переменную `context`, которая может использоваться для доступа к пользовательским сведениям.

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

Вы можете получить доступ к состоянию проверки подлинности в процедурной логике, обратившись к пользователю из `Task<AuthenticationState` настроенного с атрибутом `[CascadingParameter]`. Эта конфигурация предоставит вам доступ к пользователю, что позволит определять состояние их проверки подлинности и принадлежность их к определенной роли. Если вам нужно оценить политику процедурным образом, вы можете внедрить экземпляр `IAuthorizationService` и вызвать в нем метод `AuthorizeAsync`. В следующем примере кода показано, как получить сведения о пользователе и разрешить авторизованному пользователю выполнять задачу, ограниченную политикой `content-editor`.

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

`AuthenticationState` сначала необходимо настроить как каскадное значение, прежде чем его можно будет привязать к такому каскадному параметру, как этот. Обычно это делается с помощью компонента `CascadingAuthenticationState`. Эта конфигурация обычно выполняется в `App.razor`:

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>Итоги

Blazor использует ту же модель безопасности, что и ASP.NET Core, то есть ASP.NET Core Identity. Миграция из универсальных поставщиков в ASP.NET Core Identity относительно проста, если предположить, что в исходной схеме данных не было сделано слишком много настроек. После переноса данных работа с проверкой подлинности и авторизацией в приложениях Blazor хорошо документирована и большинство требований безопасности имеет программную поддержку.

## <a name="references"></a>Ссылки

- [Общие сведения об идентификации в ASP.NET Core](/aspnet/core/security/authentication/identity)
- [Миграция из проверки подлинности членства ASP.NET в ASP.NET Core 2.0 Identity](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [Миграция проверки подлинности и идентификации в ASP.NET Core](/aspnet/core/migration/identity)
- [Проверка подлинности и авторизация в Blazor ASP.NET Core](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[Назад](config.md)
>[Вперед](migration.md)
