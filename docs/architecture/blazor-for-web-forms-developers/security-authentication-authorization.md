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
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-blazor"></a><span data-ttu-id="89201-103">Безопасность. Проверка подлинности и авторизация в ASP.NET Web Forms и Blazor </span><span class="sxs-lookup"><span data-stu-id="89201-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="89201-104">Для миграции приложения из ASP.NET Web Forms в Blazor почти наверняка потребуется обновить способ выполнения проверки подлинности и авторизации, если в приложении настроена проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="89201-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization are performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="89201-105">В этой главе рассказывается, как перейти с модели универсального поставщика ASP.NET Web Forms (для членства, ролей и профилей пользователей) и как работать с ASP.NET Core Identity из приложений Blazor.</span><span class="sxs-lookup"><span data-stu-id="89201-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="89201-106">В этой главе будут рассмотрены только общие шаги и аспекты, а подробные шаги и сценарии можно найти в справочной документации.</span><span class="sxs-lookup"><span data-stu-id="89201-106">While this chapter will cover the high-level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="89201-107">Универсальные поставщики ASP.NET</span><span class="sxs-lookup"><span data-stu-id="89201-107">ASP.NET universal providers</span></span>

<span data-ttu-id="89201-108">Начиная с ASP.NET 2.0 платформа ASP.NET Web Forms поддерживает модель поставщика для различных функций, включая членство.</span><span class="sxs-lookup"><span data-stu-id="89201-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="89201-109">С приложениями ASP.NET Web Forms обычно развертывается универсальный поставщик членства наряду с необязательным поставщиком ролей.</span><span class="sxs-lookup"><span data-stu-id="89201-109">The universal membership provider, along with the optional role provider, is commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="89201-110">Он обеспечивает надежный и безопасный способ управления проверкой подлинности и авторизацией, и этот способ отлично работает и сегодня.</span><span class="sxs-lookup"><span data-stu-id="89201-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="89201-111">Последнее предложение этих универсальных поставщиков доступно в виде пакета NuGet [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span><span class="sxs-lookup"><span data-stu-id="89201-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="89201-112">Универсальные поставщики работают со схемой базы данных SQL, которая включает такие таблицы, как `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles` и `aspnet_Users`.</span><span class="sxs-lookup"><span data-stu-id="89201-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="89201-113">При настройке с помощью [команды aspnet_regsql.exe](/previous-versions/ms229862(v=vs.140)) поставщики устанавливают таблицы и хранимые процедуры, которые предоставляют все необходимые запросы и команды для работы с базовыми данными.</span><span class="sxs-lookup"><span data-stu-id="89201-113">When configured by running the [aspnet_regsql.exe command](/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands to work with the underlying data.</span></span> <span data-ttu-id="89201-114">Схема базы данных и эти хранимые процедуры несовместимы с новыми системами идентификации ASP.NET Identity и ASP.NET Core Identity, поэтому существующие данные необходимо перенести в новую систему.</span><span class="sxs-lookup"><span data-stu-id="89201-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="89201-115">На рисунке 1 показан пример схемы таблицы, настроенной для универсальных поставщиков.</span><span class="sxs-lookup"><span data-stu-id="89201-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![Схема универсальных поставщиков](./media/security/membership-tables.png)

<span data-ttu-id="89201-117">Универсальный поставщик обрабатывает пользователей, членство, роли и профили.</span><span class="sxs-lookup"><span data-stu-id="89201-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="89201-118">Пользователям назначаются глобальные уникальные идентификаторы, а основная информация, такая как userId, userName и т. д., хранится в таблице `aspnet_Users`.</span><span class="sxs-lookup"><span data-stu-id="89201-118">Users are assigned globally unique identifiers and basic information like userId, userName etc. are stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="89201-119">Сведения аутентификации, такие как пароль, формат пароля, соль пароля, счетчики и детали блокировки и т. д., хранятся в таблице `aspnet_Membership`.</span><span class="sxs-lookup"><span data-stu-id="89201-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="89201-120">Роли состоят просто из имен и уникальных идентификаторов, которые назначаются пользователям с помощью таблицы связей `aspnet_UsersInRoles`, обеспечивающей отношение "многие ко многим".</span><span class="sxs-lookup"><span data-stu-id="89201-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="89201-121">Если ваша существующая система использует роли в дополнение к членству, вам потребуется перенести в ASP.NET Core Identity учетные записи пользователей, связанные пароли, роли и членство в ролях.</span><span class="sxs-lookup"><span data-stu-id="89201-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="89201-122">Вам также, скорее всего, потребуется обновить свой код, в котором вы в настоящее время выполняете проверки ролей, используя операторы if, чтобы вместо этого использовать декларативные фильтры, атрибуты и (или) вспомогательные функции тегов.</span><span class="sxs-lookup"><span data-stu-id="89201-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="89201-123">Мы более подробно рассмотрим аспекты миграции в конце этой главы.</span><span class="sxs-lookup"><span data-stu-id="89201-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="89201-124">Настройка авторизации в веб-формах</span><span class="sxs-lookup"><span data-stu-id="89201-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="89201-125">Чтобы настроить авторизованный доступ к определенным страницам в приложении ASP.NET Web Forms, обычно вы указываете, что определенные страницы или папки недоступны для анонимных пользователей.</span><span class="sxs-lookup"><span data-stu-id="89201-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="89201-126">Эта настройка выполняется в файле web.config:</span><span class="sxs-lookup"><span data-stu-id="89201-126">This configuration is done in the web.config file:</span></span>

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

<span data-ttu-id="89201-127">Раздел конфигурации `authentication` устанавливает аутентификацию форм для приложения.</span><span class="sxs-lookup"><span data-stu-id="89201-127">The `authentication` configuration section sets up the forms authentication for the application.</span></span> <span data-ttu-id="89201-128">Раздел `authorization` используется для запрета анонимных пользователей во всем приложении.</span><span class="sxs-lookup"><span data-stu-id="89201-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="89201-129">Однако вы можете предоставить более детализированные правила авторизации на основе местоположения, а также применять проверки авторизации на основе ролей.</span><span class="sxs-lookup"><span data-stu-id="89201-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role-based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="89201-130">Приведенная выше конфигурация в сочетании с первой позволит анонимным пользователям получать доступ к странице входа в систему, переопределяя общесайтовое ограничение для пользователей, не прошедших проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="89201-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

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

<span data-ttu-id="89201-131">Приведенная выше конфигурация в сочетании с другими разрешает доступ к папке `/admin` и всем ресурсам в ней только членам роли "Администраторы".</span><span class="sxs-lookup"><span data-stu-id="89201-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="89201-132">Это ограничение также можно применить, поместив отдельный файл `web.config` в корень папки `/admin`.</span><span class="sxs-lookup"><span data-stu-id="89201-132">This restriction could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="89201-133">Код авторизации в веб-формах</span><span class="sxs-lookup"><span data-stu-id="89201-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="89201-134">Помимо настройки доступа с помощью `web.config` вы также можете программными средствами настроить доступ и поведение в своем приложении веб-форм.</span><span class="sxs-lookup"><span data-stu-id="89201-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="89201-135">Например, вы можете ограничивать возможность выполнения определенных операций или просмотра определенных данных в зависимости от роли пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="89201-136">Этот код можно использовать как в логике кода программной части, так и на самой странице:</span><span class="sxs-lookup"><span data-stu-id="89201-136">This code can be used both in code-behind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="89201-137">Помимо проверки членства пользователей в ролях, вы также можете определять, аутентифицированы ли они (хотя часто это лучше делать с помощью конфигурации на основе местоположения, упоминавшейся выше).</span><span class="sxs-lookup"><span data-stu-id="89201-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="89201-138">Ниже приведен пример такого подхода.</span><span class="sxs-lookup"><span data-stu-id="89201-138">Below is an example of this approach.</span></span>

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

<span data-ttu-id="89201-139">В приведенном выше коде управление доступом на основе ролей (RBAC) используется для определения того, видны ли определенные элементы страницы, например `SecretPanel`, в зависимости от роли текущего пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="89201-140">Как правило, в приложениях ASP.NET Web Forms безопасность настраивается в файле `web.config`, а затем добавляются дополнительные проверки, где это необходимо, на страницах `.aspx` и связанных с ними файлах кода программной части `.aspx.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` code-behind files.</span></span> <span data-ttu-id="89201-141">В большинстве приложений используется универсальный поставщик членства, часто с дополнительным поставщиком ролей.</span><span class="sxs-lookup"><span data-stu-id="89201-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="89201-142">Идентификация ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89201-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="89201-143">Хотя система идентификации ASP.NET Core Identity по-прежнему отвечает за проверку подлинности и авторизацию, в ней используется другой набор абстракций и допущений по сравнению с универсальными поставщиками.</span><span class="sxs-lookup"><span data-stu-id="89201-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="89201-144">Например, новая модель идентификации поддерживает стороннюю аутентификацию, разрешая пользователям проходить проверку подлинности с помощью учетной записи в социальной сети или другого надежного поставщика проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="89201-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="89201-145">ASP.NET Core Identity поддерживает пользовательский интерфейс для часто используемых страниц, таких как страницы входа, выхода и регистрации.</span><span class="sxs-lookup"><span data-stu-id="89201-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="89201-146">Эта система применяет EF Core для доступа к данным и использует миграции EF Core для создания необходимой схемы, которая требуется для поддержки ее модели данных.</span><span class="sxs-lookup"><span data-stu-id="89201-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to support its data model.</span></span> <span data-ttu-id="89201-147">В разделе [Общие сведения об идентификации в ASP.NET Core](/aspnet/core/security/authentication/identity) дается хороший обзор того, что входит в ASP.NET Core Identity, и как начать работать с этой системой.</span><span class="sxs-lookup"><span data-stu-id="89201-147">This [introduction to Identity on ASP.NET Core](/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="89201-148">Если вы еще не настроили ASP.NET Core Identity в своем приложении и его базе данных, это поможет вам начать работу.</span><span class="sxs-lookup"><span data-stu-id="89201-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="89201-149">Роли, утверждения и политики</span><span class="sxs-lookup"><span data-stu-id="89201-149">Roles, claims, and policies</span></span>

<span data-ttu-id="89201-150">Как универсальные поставщики, так и ASP.NET Core Identity поддерживают концепцию ролей.</span><span class="sxs-lookup"><span data-stu-id="89201-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="89201-151">Вы можете создавать роли для пользователей и назначать пользователям роли.</span><span class="sxs-lookup"><span data-stu-id="89201-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="89201-152">Пользователи могут принадлежать к любому количеству ролей, и вы можете проверять членство в роли в рамках реализации авторизации.</span><span class="sxs-lookup"><span data-stu-id="89201-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="89201-153">Помимо ролей, ASP.NET Core Identity поддерживает концепции утверждений и политик.</span><span class="sxs-lookup"><span data-stu-id="89201-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="89201-154">Хотя роль должна соответствовать набору ресурсов, к которому должен иметь доступ пользователь в этой роли, утверждение — это просто часть удостоверения пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="89201-155">Утверждение — это пара "имя-значение", которая представляет собой предмет, а не то, что он может делать.</span><span class="sxs-lookup"><span data-stu-id="89201-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="89201-156">Можно напрямую проверять утверждения пользователя и на основе этих значений определять, следует ли предоставить пользователю доступ к ресурсу.</span><span class="sxs-lookup"><span data-stu-id="89201-156">It is possible to directly inspect a user's claims and determine based on these values whether a user should be given access to a resource.</span></span> <span data-ttu-id="89201-157">Однако такие проверки часто повторяются и рассредоточены по всей системе.</span><span class="sxs-lookup"><span data-stu-id="89201-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="89201-158">Лучше всего определить *политику*.</span><span class="sxs-lookup"><span data-stu-id="89201-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="89201-159">Политика авторизации включает одно или несколько требований.</span><span class="sxs-lookup"><span data-stu-id="89201-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="89201-160">Политики регистрируются в рамках настройки службы авторизации в методе `ConfigureServices` файла `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="89201-161">Например, в следующем фрагменте кода настраивается политика с именем "CanadiansOnly", которая требует, чтобы у пользователя было утверждение Country со значением "Canada".</span><span class="sxs-lookup"><span data-stu-id="89201-161">For example, the following code snippet configures a policy called "CanadiansOnly", which has the requirement that the user has the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="89201-162">[Дополнительные сведения о создании пользовательских политик см. в документации](/aspnet/core/security/authorization/policies).</span><span class="sxs-lookup"><span data-stu-id="89201-162">You can [learn more about how to create custom policies in the documentation](/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="89201-163">Независимо от того, используете ли вы политики или роли, вы можете указать, что для конкретной страницы в вашем приложении Blazor требуется определенная роль или политика, с помощью атрибута `[Authorize]`, применяемого с помощью директивы `@attribute`.</span><span class="sxs-lookup"><span data-stu-id="89201-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application requires that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="89201-164">Требование роли:</span><span class="sxs-lookup"><span data-stu-id="89201-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="89201-165">Требование соблюдения политики:</span><span class="sxs-lookup"><span data-stu-id="89201-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="89201-166">Если вам нужен доступ к состоянию проверки подлинности пользователя, ролям или утверждениям в вашем коде, существует два основных способа обеспечения этой функциональности.</span><span class="sxs-lookup"><span data-stu-id="89201-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this functionality.</span></span> <span data-ttu-id="89201-167">Первый — получать состояние проверки подлинности как каскадный параметр.</span><span class="sxs-lookup"><span data-stu-id="89201-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="89201-168">Второй — получать доступ к состоянию с помощью внедренного `AuthenticationStateProvider`.</span><span class="sxs-lookup"><span data-stu-id="89201-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="89201-169">Подробнее эти способы описаны в [документации по безопасности Blazor](/aspnet/core/blazor/security/).</span><span class="sxs-lookup"><span data-stu-id="89201-169">The details of each of these approaches are described in the [Blazor Security documentation](/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="89201-170">В следующем коде показано, как получить `AuthenticationState` в качестве каскадного параметра.</span><span class="sxs-lookup"><span data-stu-id="89201-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="89201-171">Получив этот параметр, вы можете получить пользователя с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="89201-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="89201-172">В следующем коде показано, как внедрить `AuthenticationStateProvider`.</span><span class="sxs-lookup"><span data-stu-id="89201-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="89201-173">Установив поставщика, вы можете получить доступ к пользователю с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="89201-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="89201-174">**Примечание.** Компонент `AuthorizeView`,который описывается далее в этой главе, предоставляет декларативный способ управления тем, что пользователь видит на странице или в компоненте.</span><span class="sxs-lookup"><span data-stu-id="89201-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="89201-175">Для работы с пользователями и утверждениями (в приложениях Blazor Server) вам также может потребоваться внедрить `UserManager<T>` (используйте `IdentityUser` по умолчанию), который можно использовать для перечисления и изменения утверждений для пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="89201-176">Сначала внедрите тип и назначьте его свойству:</span><span class="sxs-lookup"><span data-stu-id="89201-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="89201-177">Затем используйте его для работы с утверждениями пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="89201-178">В следующем примере показано, как добавить и сохранить утверждение для пользователя.</span><span class="sxs-lookup"><span data-stu-id="89201-178">The following sample shows how to add and persist a claim on a user:</span></span>

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

<span data-ttu-id="89201-179">При работе с ролями придерживайтесь того же подхода.</span><span class="sxs-lookup"><span data-stu-id="89201-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="89201-180">Возможно, вам потребуется внедрить `RoleManager<T>` (используйте `IdentityRole` для типа по умолчанию) для составления списка самих ролей и управления ими.</span><span class="sxs-lookup"><span data-stu-id="89201-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="89201-181">**Примечание.** В проектах Blazor WebAssembly вам потребуется предоставить серверные API для выполнения этих операций (вместо прямого использования `UserManager<T>` или `RoleManager<T>`).</span><span class="sxs-lookup"><span data-stu-id="89201-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="89201-182">Клиентское приложение Blazor WebAssembly будет управлять утверждениями и (или) ролями, безопасно вызывая конечные точки API, предоставленные для этой цели.</span><span class="sxs-lookup"><span data-stu-id="89201-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="89201-183">Руководство по миграции</span><span class="sxs-lookup"><span data-stu-id="89201-183">Migration guide</span></span>

<span data-ttu-id="89201-184">Для перехода с ASP.NET Web Forms и универсальных поставщиков на ASP.NET Core Identity необходимо выполнить несколько следующих действий.</span><span class="sxs-lookup"><span data-stu-id="89201-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="89201-185">Создать схему базы данных ASP.NET Core Identity в целевой базе данных.</span><span class="sxs-lookup"><span data-stu-id="89201-185">Create ASP.NET Core Identity database schema in the destination database</span></span>
2. <span data-ttu-id="89201-186">Перенести данные из схемы универсального поставщика в схему ASP.NET Core Identity.</span><span class="sxs-lookup"><span data-stu-id="89201-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="89201-187">Перенести конфигурацию из `web.config` в ПО промежуточного слоя и службы, обычно в `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-187">Migrate configuration from the `web.config` to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="89201-188">Обновить отдельные страницы с помощью элементов управления и условных операторов, чтобы использовать вспомогательные функции тегов и новые API идентификации.</span><span class="sxs-lookup"><span data-stu-id="89201-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="89201-189">В следующих разделах каждый этап рассматривается более подробно.</span><span class="sxs-lookup"><span data-stu-id="89201-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="89201-190">Создание схемы ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="89201-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="89201-191">Существует несколько способов создания необходимой структуры таблиц, используемой для ASP.NET Core Identity.</span><span class="sxs-lookup"><span data-stu-id="89201-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="89201-192">Самый простой — создать новое веб-приложение ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="89201-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="89201-193">Щелкните "Web Application", а затем измените параметры проверки подлинности так, чтобы использовать учетные записи отдельных пользователей.</span><span class="sxs-lookup"><span data-stu-id="89201-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![Новый проект с учетными записями отдельных пользователей](./media/security/individual-user-accounts.png)

<span data-ttu-id="89201-195">То же самое можно сделать в командной строке, запустив `dotnet new webapp -au Individual`.</span><span class="sxs-lookup"><span data-stu-id="89201-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="89201-196">Как только приложение будет создано, запустите его и зарегистрируйтесь на сайте.</span><span class="sxs-lookup"><span data-stu-id="89201-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="89201-197">Вы должны активировать страницу, подобную показанной ниже:</span><span class="sxs-lookup"><span data-stu-id="89201-197">You should trigger a page like the one shown below:</span></span>

![Страница применения миграций](./media/security/apply-migrations-page.png)

<span data-ttu-id="89201-199">Нажмите кнопку "Apply Migrations", и необходимые таблицы базы данных будут для вас созданы.</span><span class="sxs-lookup"><span data-stu-id="89201-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="89201-200">Кроме того, в вашем проекте должны появиться файлы миграции, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="89201-200">In addition, the migration files should appear in your project, as shown:</span></span>

![Файлы миграции](./media/security/migration-files.png)

<span data-ttu-id="89201-202">Вы можете выполнить миграцию самостоятельно, не запуская веб-приложение, с помощью следующего инструмента командной строки:</span><span class="sxs-lookup"><span data-stu-id="89201-202">You can run the migration yourself, without running the web application, using this command-line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="89201-203">Если вы предпочитаете запускать скрипт для применения новой схемы к существующей базе данных, вы можете создать скрипт для этих миграций из командной строки.</span><span class="sxs-lookup"><span data-stu-id="89201-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command-line.</span></span> <span data-ttu-id="89201-204">Выполните эту команду, чтобы создать скрипт:</span><span class="sxs-lookup"><span data-stu-id="89201-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="89201-205">Приведенная выше команда создаст скрипт SQL в выходном файле `auth.sql`, который затем можно будет запустить для любой базы данных, которая вам нужна.</span><span class="sxs-lookup"><span data-stu-id="89201-205">The above command will produce a SQL script in the output file `auth.sql`, which can then be run against whatever database you like.</span></span> <span data-ttu-id="89201-206">Если у вас возникли проблемы с запуском команд `dotnet ef`, [убедитесь, что в вашей системе установлены инструменты EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="89201-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="89201-207">Если у вас есть дополнительные столбцы в исходных таблицах, то необходимо будет определить наиболее подходящее место для этих столбцов в новой схеме.</span><span class="sxs-lookup"><span data-stu-id="89201-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="89201-208">Как правило, столбцы, находящиеся в таблице `aspnet_Membership`, должны быть сопоставлены с таблицей `AspNetUsers`.</span><span class="sxs-lookup"><span data-stu-id="89201-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="89201-209">Столбцы в `aspnet_Roles` должны быть сопоставлены с `AspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="89201-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="89201-210">Все дополнительные столбцы в таблице `aspnet_UsersInRoles` будут добавлены в таблицу `AspNetUserRoles`.</span><span class="sxs-lookup"><span data-stu-id="89201-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="89201-211">Также имеет смысл обдумать размещение дополнительных столбцов в отдельных таблицах.</span><span class="sxs-lookup"><span data-stu-id="89201-211">It's also worth considering putting any additional columns on separate tables.</span></span> <span data-ttu-id="89201-212">Тогда при будущих миграциях не нужно будет учитывать такие настройки схемы удостоверений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="89201-212">So that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="89201-213">Перенос данных из универсальных поставщиков в ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="89201-213">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="89201-214">Следующим шагом после создания целевой схемы таблиц является перенос записей пользователей и ролей в новую схему.</span><span class="sxs-lookup"><span data-stu-id="89201-214">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="89201-215">Полный список различий в схемах, включая соответствие старых и новых столбцов, можно найти [здесь](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="89201-215">A complete list of the schema differences, including which columns map to which new columns, can be found [here](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="89201-216">Чтобы перенести пользователей из членства в новые таблицы идентификаторов, вы должны [выполнить шаги, описанные в документации](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="89201-216">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="89201-217">После того как эти шаги будут выполнены и скрипт предоставлен, ваши пользователи должны будут сменить пароль при следующем входе в систему.</span><span class="sxs-lookup"><span data-stu-id="89201-217">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="89201-218">Перенести пароли пользователей можно, но этот процесс намного сложнее.</span><span class="sxs-lookup"><span data-stu-id="89201-218">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="89201-219">Требование обновления паролей в рамках процесса миграции и поощрение пользователей к использованию новых уникальных паролей повышает общую безопасность приложения.</span><span class="sxs-lookup"><span data-stu-id="89201-219">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="89201-220">Перенос параметров безопасности из web.config в Startup.cs</span><span class="sxs-lookup"><span data-stu-id="89201-220">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="89201-221">Как упоминалось выше, в ASP.NET членство и поставщики ролей настраиваются в файле `web.config` приложения.</span><span class="sxs-lookup"><span data-stu-id="89201-221">As noted above, ASP.NET membership and role providers are configured in the application's `web.config` file.</span></span> <span data-ttu-id="89201-222">Так как приложения ASP.NET Core не привязаны к службам IIS и используют отдельную систему для настройки, эти параметры должны быть настроены в другом месте.</span><span class="sxs-lookup"><span data-stu-id="89201-222">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="89201-223">По большей части ASP.NET Core Identity настраивается в файле `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-223">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="89201-224">Откройте созданный ранее веб-проект (для создания схемы таблицы идентификаторов) и просмотрите его файл `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-224">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="89201-225">Метод ConfigureServices по умолчанию добавляет поддержку EF Core и Identity:</span><span class="sxs-lookup"><span data-stu-id="89201-225">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

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

<span data-ttu-id="89201-226">Метод расширения `AddDefaultIdentity` используется для настройки Identity на использование `ApplicationDbContext` по умолчанию и типа `IdentityUser` платформы.</span><span class="sxs-lookup"><span data-stu-id="89201-226">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="89201-227">Если вы используете настраиваемый `IdentityUser`, обязательно укажите здесь его тип.</span><span class="sxs-lookup"><span data-stu-id="89201-227">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="89201-228">Если эти методы расширения не работают в вашем приложении, убедитесь, что у вас имеются соответствующие операторы using и необходимые ссылки на пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="89201-228">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="89201-229">Например, в вашем проекте должна быть указана ссылка на некоторые версии пакетов `Microsoft.AspNetCore.Identity.EntityFrameworkCore` и `Microsoft.AspNetCore.Identity.UI`.</span><span class="sxs-lookup"><span data-stu-id="89201-229">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="89201-230">Также в `Startup.cs` вы должны видеть необходимое ПО промежуточного слоя, настроенное для сайта.</span><span class="sxs-lookup"><span data-stu-id="89201-230">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="89201-231">В частности, должны быть настроены `UseAuthentication` и `UseAuthorization`, причем в правильном месте.</span><span class="sxs-lookup"><span data-stu-id="89201-231">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

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

<span data-ttu-id="89201-232">ASP.NET Identity не настраивает анонимный доступ или доступ на основе ролей к расположениям из `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="89201-232">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="89201-233">Вам нужно будет перенести все данные конфигурации авторизации для конкретных местоположений в фильтры в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="89201-233">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="89201-234">Запишите, каким папкам и страницам потребуются такие обновления.</span><span class="sxs-lookup"><span data-stu-id="89201-234">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="89201-235">Вы внесете эти изменения в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="89201-235">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="89201-236">Обновление отдельных страниц для использования абстракций ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="89201-236">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="89201-237">Если в вашем приложении ASP.NET Web Forms были настройки `web.config` для запрета анонимным пользователям доступа к определенным страницам или папкам, вы должны перенести эти изменения, добавив атрибут `[Authorize]` для таких страниц:</span><span class="sxs-lookup"><span data-stu-id="89201-237">In your ASP.NET Web Forms application, if you had `web.config` settings to deny access to certain pages or folders to anonymous users, you would migrate these changes by adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="89201-238">Если вы еще сильнее ограничили доступ, разрешив его только пользователям, принадлежащим к определенной роли, то вы также должны перенести это поведение, добавив атрибут, определяющий роль:</span><span class="sxs-lookup"><span data-stu-id="89201-238">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this behavior by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="89201-239">Атрибут `[Authorize]` работает только с компонентами `@page`, доступными через маршрутизатор Blazor.</span><span class="sxs-lookup"><span data-stu-id="89201-239">The `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="89201-240">Этот атрибут не работает с дочерними компонентами, которые вместо этого должны использовать `AuthorizeView`.</span><span class="sxs-lookup"><span data-stu-id="89201-240">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="89201-241">Если в разметке страниц присутствует логика для определения, следует ли отображать какой-либо код конкретному пользователю, вы можете заменить ее компонентом `AuthorizeView`.</span><span class="sxs-lookup"><span data-stu-id="89201-241">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="89201-242">[Компонент AuthorizeView](/aspnet/core/blazor/security#authorizeview-component) избирательно отображает элементы пользовательского интерфейса в зависимости от того, авторизован ли пользователь для их просмотра.</span><span class="sxs-lookup"><span data-stu-id="89201-242">The [AuthorizeView component](/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="89201-243">Он также предоставляет переменную `context`, которая может использоваться для доступа к пользовательским сведениям.</span><span class="sxs-lookup"><span data-stu-id="89201-243">It also exposes a `context` variable that can be used to access user information.</span></span>

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

<span data-ttu-id="89201-244">Вы можете получить доступ к состоянию проверки подлинности в процедурной логике, обратившись к пользователю из `Task<AuthenticationState` настроенного с атрибутом `[CascadingParameter]`.</span><span class="sxs-lookup"><span data-stu-id="89201-244">You can access the authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="89201-245">Эта конфигурация предоставит вам доступ к пользователю, что позволит определять состояние их проверки подлинности и принадлежность их к определенной роли.</span><span class="sxs-lookup"><span data-stu-id="89201-245">This configuration will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="89201-246">Если вам нужно оценить политику процедурным образом, вы можете внедрить экземпляр `IAuthorizationService` и вызвать в нем метод `AuthorizeAsync`.</span><span class="sxs-lookup"><span data-stu-id="89201-246">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="89201-247">В следующем примере кода показано, как получить сведения о пользователе и разрешить авторизованному пользователю выполнять задачу, ограниченную политикой `content-editor`.</span><span class="sxs-lookup"><span data-stu-id="89201-247">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

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

<span data-ttu-id="89201-248">`AuthenticationState` сначала необходимо настроить как каскадное значение, прежде чем его можно будет привязать к такому каскадному параметру, как этот.</span><span class="sxs-lookup"><span data-stu-id="89201-248">The `AuthenticationState` first need to be set up as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="89201-249">Обычно это делается с помощью компонента `CascadingAuthenticationState`.</span><span class="sxs-lookup"><span data-stu-id="89201-249">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="89201-250">Эта конфигурация обычно выполняется в `App.razor`:</span><span class="sxs-lookup"><span data-stu-id="89201-250">This configuration is typically done in `App.razor`:</span></span>

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

## <a name="summary"></a><span data-ttu-id="89201-251">Итоги</span><span class="sxs-lookup"><span data-stu-id="89201-251">Summary</span></span>

<span data-ttu-id="89201-252">Blazor использует ту же модель безопасности, что и ASP.NET Core, то есть ASP.NET Core Identity.</span><span class="sxs-lookup"><span data-stu-id="89201-252">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="89201-253">Миграция из универсальных поставщиков в ASP.NET Core Identity относительно проста, если предположить, что в исходной схеме данных не было сделано слишком много настроек.</span><span class="sxs-lookup"><span data-stu-id="89201-253">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="89201-254">После переноса данных работа с проверкой подлинности и авторизацией в приложениях Blazor хорошо документирована и большинство требований безопасности имеет программную поддержку.</span><span class="sxs-lookup"><span data-stu-id="89201-254">Once the data has been migrated, working with authentication and authorization in Blazor apps is well documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="89201-255">Ссылки</span><span class="sxs-lookup"><span data-stu-id="89201-255">References</span></span>

- [<span data-ttu-id="89201-256">Общие сведения об идентификации в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89201-256">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="89201-257">Миграция из проверки подлинности членства ASP.NET в ASP.NET Core 2.0 Identity</span><span class="sxs-lookup"><span data-stu-id="89201-257">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="89201-258">Миграция проверки подлинности и идентификации в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89201-258">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="89201-259">Проверка подлинности и авторизация в Blazor ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="89201-259">ASP.NET Core Blazor authentication and authorization</span></span>](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="89201-260">[Назад](config.md)
>[Вперед](migration.md)</span><span class="sxs-lookup"><span data-stu-id="89201-260">[Previous](config.md)
[Next](migration.md)</span></span>
