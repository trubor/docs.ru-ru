---
title: Различия маршрутизации между ASP.NET MVC и ASP.NET Core
description: Как определяется Маршрутизация и как она работает в среде выполнения в ASP.NET MVC? Чем маршрутизация отличается в ASP.NET Coreных приложениях?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d5c18948248f03a19c97461efe3df38a5be9360b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401715"
---
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="b3211-104">Различия маршрутизации между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3211-104">Routing differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="b3211-105">Маршрутизация отвечает за сопоставление входящих запросов браузера с определенными действиями контроллера (или обработчиками Razor Pages).</span><span class="sxs-lookup"><span data-stu-id="b3211-105">Routing is responsible for mapping incoming browser requests to particular controller actions (or Razor Pages handlers).</span></span> <span data-ttu-id="b3211-106">В этом разделе описывается различие маршрутизации между ASP.NET MVC (и веб-API) и ASP.NET Core (MVC, Razor Pages и иным способом).</span><span class="sxs-lookup"><span data-stu-id="b3211-106">This section covers how routing differs between ASP.NET MVC (and Web API) and ASP.NET Core (MVC, Razor Pages, and otherwise).</span></span>

## <a name="routing-in-aspnet-mvc-and-web-api"></a><span data-ttu-id="b3211-107">Маршрутизация в ASP.NET MVC и веб-API</span><span class="sxs-lookup"><span data-stu-id="b3211-107">Routing in ASP.NET MVC and Web API</span></span>

<span data-ttu-id="b3211-108">ASP.NET MVC предлагает два подхода к маршрутизации:</span><span class="sxs-lookup"><span data-stu-id="b3211-108">ASP.NET MVC offers two approaches to routing:</span></span>

1. <span data-ttu-id="b3211-109">Таблица маршрутов, которая представляет собой коллекцию маршрутов, которые можно использовать для сопоставления входящих запросов с действиями контроллера.</span><span class="sxs-lookup"><span data-stu-id="b3211-109">The route table, which is a collection of routes that can be used to match incoming requests to controller actions.</span></span>
1. <span data-ttu-id="b3211-110">Маршрутизация атрибутов, которая выполняет ту же функцию, но достигается путем оформления самих действий, вместо изменения глобальной таблицы маршрутов.</span><span class="sxs-lookup"><span data-stu-id="b3211-110">Attribute routing, which performs the same function but is achieved by decorating the actions themselves, rather than editing a global route table.</span></span>

## <a name="route-table"></a><span data-ttu-id="b3211-111">Таблица маршрутов</span><span class="sxs-lookup"><span data-stu-id="b3211-111">Route table</span></span>

<span data-ttu-id="b3211-112">Таблица маршрутов настраивается при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="b3211-112">The route table is configured when the app starts up.</span></span> <span data-ttu-id="b3211-113">Как правило, вызов статического метода используется для настройки коллекции глобальных маршрутов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b3211-113">Typically, a static method call is used to configure the global route collection, like so:</span></span>

```csharp
public class MvcApplication : System.Web.HttpApplication
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
        routes.MapRoute(
            name: "Default",
            url: "{controller}/{action}/{id}",
            defaults: new { controller = "Home", action = "Index", id = "" },
            constraints: new { id = "\\d+" }
        );
    }

    protected void Application_Start()
    {
        RegisterRoutes(RouteTable.Routes);
    }
}
```

<span data-ttu-id="b3211-114">В приведенном выше коде Управление таблицей маршрута осуществляется с помощью `RouteCollection` типа, который используется для добавления новых маршрутов с помощью `MapRoute` .</span><span class="sxs-lookup"><span data-stu-id="b3211-114">In the preceding code, the route table is managed by the `RouteCollection` type, which is used to add new routes with `MapRoute`.</span></span> <span data-ttu-id="b3211-115">Маршруты именуются и включают строку маршрута, которая может включать параметры для контроллеров, действий, областей и других заполнителей.</span><span class="sxs-lookup"><span data-stu-id="b3211-115">Routes are named and include a route string, which can include parameters for controllers, actions, areas, and other placeholders.</span></span> <span data-ttu-id="b3211-116">Если приложение соответствует стандартному соглашению, большинство его действий может обрабатываться этим отдельным маршрутом по умолчанию, за исключением того, что это соглашение настроено с использованием дополнительных маршрутов.</span><span class="sxs-lookup"><span data-stu-id="b3211-116">If an app follows a standard convention, most of its actions can be handled by this single default route, with any exceptions to this convention configured using additional routes.</span></span>

### <a name="attribute-routing-in-aspnet-mvc"></a><span data-ttu-id="b3211-117">Маршрутизация атрибутов в ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="b3211-117">Attribute routing in ASP.NET MVC</span></span>

<span data-ttu-id="b3211-118">Маршруты, определенные с помощью их действий, могут быть проще в обнаружении и причинах, чем маршруты, определенные во внешнем расположении.</span><span class="sxs-lookup"><span data-stu-id="b3211-118">Routes that are defined with their actions may be easier to discover and reason about than routes defined in an external location.</span></span> <span data-ttu-id="b3211-119">При использовании маршрутизации атрибутов отдельный метод действия может иметь свой маршрут, определенный с помощью `[Route]` атрибута:</span><span class="sxs-lookup"><span data-stu-id="b3211-119">Using attribute routing, an individual action method can have its route defined with a `[Route]` attribute:</span></span>

```csharp
public class ProductsController
{
    [Route("products")]
    public ActionResult Index()
    {
        return View();
    }

    [Route("products/{id}")]
    public ActionResult Details(int id)
    {
        return View();
    }
}
```

<span data-ttu-id="b3211-120">[Маршрутизация атрибутов в ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) также поддерживает значения по умолчанию и префиксы, которые могут быть добавлены на уровне контроллера (и применяются ко всем действиям в этом контроллере).</span><span class="sxs-lookup"><span data-stu-id="b3211-120">[Attribute routing in ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) also supports defaults and prefixes, which can be added at the controller level (and which are applied to all actions within that controller).</span></span> <span data-ttu-id="b3211-121">Дополнительные сведения см. в документации.</span><span class="sxs-lookup"><span data-stu-id="b3211-121">Refer to the documentation for details.</span></span>

<span data-ttu-id="b3211-122">Для настройки маршрутизации атрибутов необходимо добавить одну строку в конфигурацию таблицы маршрутов по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="b3211-122">Setting up attribute routing requires adding one line to the default route table configuration:</span></span>

```csharp
routes.MapMvcAttributeRoutes();
```

<span data-ttu-id="b3211-123">Маршрутизация атрибутов может воспользоваться преимуществами ограничений маршрута, встроенных и пользовательских, и поддерживает именованные маршруты и области с помощью `[RouteArea]` атрибута.</span><span class="sxs-lookup"><span data-stu-id="b3211-123">Attribute routing can take advantage of route constraints, both built-in and custom, and supports named routes and areas using the `[RouteArea]` attribute.</span></span> <span data-ttu-id="b3211-124">Если приложение использует области, необходимо настроить поддержку для них в коде регистрации маршрута, добавив еще одну строку:</span><span class="sxs-lookup"><span data-stu-id="b3211-124">If your app uses areas, you'll need to configure support for them in your route registration code by adding one more line:</span></span>

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a><span data-ttu-id="b3211-125">Маршрутизация атрибутов в веб-API ASP.NET 2</span><span class="sxs-lookup"><span data-stu-id="b3211-125">Attribute routing in ASP.NET Web API 2</span></span>

<span data-ttu-id="b3211-126">[Маршрутизация атрибутов в веб-API ASP.NET 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) аналогична маршрутизации в ASP.NET MVC 5 с незначительными различиями.</span><span class="sxs-lookup"><span data-stu-id="b3211-126">[Attribute routing in ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) is similar to routing in ASP.NET MVC 5, with minor differences.</span></span> <span data-ttu-id="b3211-127">Настройка веб-API 2 обычно выполняется в собственном классе, который вызывается во время запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b3211-127">Configuring Web API 2 is typically done in its own class, which is called during app startup.</span></span> <span data-ttu-id="b3211-128">Конфигурация маршрутизации атрибутов обрабатывается в этом классе:</span><span class="sxs-lookup"><span data-stu-id="b3211-128">Attribute routing configuration is handled in this class:</span></span>

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        // Attribute routing.
        config.MapHttpAttributeRoutes();

        // Convention-based routing.
        config.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "api/{controller}/{id}",
            defaults: new { id = RouteParameter.Optional }
        );
    }
}
```

<span data-ttu-id="b3211-129">Как показано в приведенном выше коде, маршрутизация атрибутов может сочетаться с маршрутизацией на основе соглашений в приложениях веб-API.</span><span class="sxs-lookup"><span data-stu-id="b3211-129">As shown in the preceding code, attribute routing may be combined with convention-based routing in Web API apps.</span></span>

<span data-ttu-id="b3211-130">Помимо маршрутизации атрибутов, [веб-API ASP.NET выбирает, какое действие следует вызвать](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) на основе метода HTTP (например, Get или POST), `{action}` заполнителя в маршруте (если есть) и параметры действия.</span><span class="sxs-lookup"><span data-stu-id="b3211-130">In addition to attribute routing, [ASP.NET Web API chooses which action to call](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) based on the HTTP method (for example, GET or POST), the `{action}` placeholder in a route (if any), and parameters of the action.</span></span> <span data-ttu-id="b3211-131">Во многих случаях имя действия поможет определить, соответствует ли оно, так как префикс имени действия "Get" или "Post" используется для сопоставления соответствующего метода HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3211-131">In many cases, the name of the action will help determine whether it's matched, since prefixing the action name with "Get" or "Post" is used to match the appropriate HTTP method to it.</span></span> <span data-ttu-id="b3211-132">Кроме того, действия можно снабдить соответствующим атрибутом метода HTTP, например `[HttpGet]` , допуская использование имен действий, которые не имеют префикса с помощью метода HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3211-132">Alternatively, actions can be decorated with an appropriate HTTP method attribute, like `[HttpGet]`, allowing the use of action names that aren't prefixed with an HTTP method.</span></span>

```csharp
public class ProductsController : ApiController
{
    // matched by name and (lack of) parameters
    public IEnumerable<Product> GetAll() { }

    // matched by GET and string parameter
    [HttpGet]
    public IEnumerable<Product> FindProductsByName(string name) { }
}
```

<span data-ttu-id="b3211-133">В соответствии с указанным выше контроллером HTTP-запрос GET `localhost:123/products/` соответствует `GetAll` действию.</span><span class="sxs-lookup"><span data-stu-id="b3211-133">Given the above controller, an HTTP GET request to `localhost:123/products/` matches the `GetAll` action.</span></span> <span data-ttu-id="b3211-134">Запрос HTTP GET, `localhost:123/products?name=ardalis` соответствующий `FindProductsByName` действию.</span><span class="sxs-lookup"><span data-stu-id="b3211-134">An HTTP GET request to `localhost:123/products?name=ardalis` matches the `FindProductsByName` action.</span></span>

## <a name="routing-in-aspnet-core-31"></a><span data-ttu-id="b3211-135">Маршрутизация в ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b3211-135">Routing in ASP.NET Core 3.1</span></span>

<span data-ttu-id="b3211-136">В ASP.NET Core маршрутизация обрабатывается по промежуточного слоя маршрутизации, который соответствует URL-адресам входящих запросов на действия или другие конечные точки.</span><span class="sxs-lookup"><span data-stu-id="b3211-136">In ASP.NET Core, routing is handled by routing middleware, which matches the URLs of incoming requests to actions or other endpoints.</span></span> <span data-ttu-id="b3211-137">Действия контроллера либо маршрутизируются, либо направляются с помощью атрибутов.</span><span class="sxs-lookup"><span data-stu-id="b3211-137">Controller actions are either conventionally routed or attribute-routed.</span></span> <span data-ttu-id="b3211-138">Стандартная маршрутизация аналогична подходу таблицы маршрутов, используемому в ASP.NET MVC и веб-API.</span><span class="sxs-lookup"><span data-stu-id="b3211-138">Conventional routing is similar to the route table approach used in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="b3211-139">Независимо от того, используете ли вы стандартный, атрибут или оба, необходимо настроить приложение для использования по промежуточного слоя маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="b3211-139">Whether you're using conventional, attribute, or both, you need to configure your app to use the routing middleware.</span></span> <span data-ttu-id="b3211-140">Чтобы использовать по промежуточного слоя, добавьте в метод следующий код `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="b3211-140">To use the middleware, add the following code to your `Startup.Configure` method:</span></span>

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a><span data-ttu-id="b3211-141">Маршрутизация на основе соглашений</span><span class="sxs-lookup"><span data-stu-id="b3211-141">Conventional routing</span></span>

<span data-ttu-id="b3211-142">При использовании обычной маршрутизации вы настраиваете одно или несколько соглашений, которые будут использоваться для сопоставления входящих URL-адресов с *конечными точками* в приложении.</span><span class="sxs-lookup"><span data-stu-id="b3211-142">With conventional routing, you set up one or more conventions that will be used to match incoming URLs to *endpoints* in the app.</span></span> <span data-ttu-id="b3211-143">В ASP.NET Core эти конечные точки могут быть действиями контроллера, как в ASP.NET MVC или веб-API.</span><span class="sxs-lookup"><span data-stu-id="b3211-143">In ASP.NET Core, these endpoints may be controller actions, like in ASP.NET MVC or Web API.</span></span> <span data-ttu-id="b3211-144">Конечные точки также могут быть Razor Pages, проверки работоспособности или концентраторы SignalR.</span><span class="sxs-lookup"><span data-stu-id="b3211-144">The endpoints could also be Razor Pages, Health Checks, or SignalR hubs.</span></span> <span data-ttu-id="b3211-145">Все эти маршрутизируемые функции настраиваются аналогичным образом с помощью конечных точек:</span><span class="sxs-lookup"><span data-stu-id="b3211-145">All of these routable features are configured in a similar fashion using endpoints:</span></span>

```csharp
// in Startup.Configure()
app.UseEndpoints(endpoints =>
{
    endpoints.MapHealthChecks("/healthz").RequireAuthorization();
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

<span data-ttu-id="b3211-146">Приведенный выше код используется (в дополнение к `UseRouting` ) для настройки различных конечных точек, включая проверки работоспособности, контроллеры и Razor Pages.</span><span class="sxs-lookup"><span data-stu-id="b3211-146">The preceding code is used (in addition to `UseRouting`) to configure various endpoints, including Health Checks, controllers, and Razor Pages.</span></span> <span data-ttu-id="b3211-147">Для контроллеров в приведенной выше конфигурации задано соглашение о маршрутизации по умолчанию. это довольно стандартный `{controller}/{action}/{id?}` шаблон, который рекомендуется использовать с первой версии ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="b3211-147">For controllers, the above configuration specifies a default routing convention, which is the fairly standard `{controller}/{action}/{id?}` pattern that's been recommended since the first versions of ASP.NET MVC.</span></span>

### <a name="attribute-routing"></a><span data-ttu-id="b3211-148">Маршрутизация с помощью атрибутов</span><span class="sxs-lookup"><span data-stu-id="b3211-148">Attribute routing</span></span>

<span data-ttu-id="b3211-149">Маршрутизация атрибутов в ASP.NET Core является предпочтительным подходом для настройки маршрутизации в контроллерах.</span><span class="sxs-lookup"><span data-stu-id="b3211-149">Attribute routing in ASP.NET Core is the preferred approach for configuring routing in controllers.</span></span> <span data-ttu-id="b3211-150">Если вы создаете API, `[ApiController]` атрибут должен применяться к контроллерам.</span><span class="sxs-lookup"><span data-stu-id="b3211-150">If you're building APIs, the `[ApiController]` attribute should be applied to your controllers.</span></span> <span data-ttu-id="b3211-151">Помимо прочего, этот атрибут требует использования маршрутизации атрибутов для действий в таких классах контроллеров.</span><span class="sxs-lookup"><span data-stu-id="b3211-151">Among other things, this attribute requires the use of attribute routing for actions in such controller classes.</span></span>

<span data-ttu-id="b3211-152">Маршрутизация атрибутов в ASP.NET Core ведет себя аналогично в ASP.NET MVC и веб-API.</span><span class="sxs-lookup"><span data-stu-id="b3211-152">Attribute routing in ASP.NET Core behaves similarly in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="b3211-153">Однако в дополнение к поддержке `[Route]` атрибута сведения о маршрутах также можно указать как часть атрибута метода HTTP:</span><span class="sxs-lookup"><span data-stu-id="b3211-153">In addition to supporting the `[Route]` attribute, however, route information can also be specified as part of the HTTP method attribute:</span></span>

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

<span data-ttu-id="b3211-154">Как и в предыдущих версиях, можно указать маршрут по умолчанию с заполнителями и добавить его на уровне класса контроллера или даже в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="b3211-154">As with previous versions, you can specify a default route with placeholders, and add this at the controller class level or even on a base class.</span></span> <span data-ttu-id="b3211-155">Для всех этих вариантов используется один и тот же `[Route]` атрибут.</span><span class="sxs-lookup"><span data-stu-id="b3211-155">You use the same `[Route]` attribute for all of these cases.</span></span> <span data-ttu-id="b3211-156">Например, базовый класс контроллера API может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b3211-156">For example, a base API controller class might look like this:</span></span>

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

<span data-ttu-id="b3211-157">С помощью этого атрибута классы, наследующие от этого типа, будут маршрутизировать URL-адреса к действиям на основе имени контроллера, имени действия и необязательного целочисленного `id` параметра.</span><span class="sxs-lookup"><span data-stu-id="b3211-157">Using this attribute, classes inheriting from this type would route URLs to actions based on the controller name, action name, and an optional integer `id` parameter.</span></span>

## <a name="references"></a><span data-ttu-id="b3211-158">Ссылки</span><span class="sxs-lookup"><span data-stu-id="b3211-158">References</span></span>

- [<span data-ttu-id="b3211-159">Общие сведения о маршрутизации в ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="b3211-159">ASP.NET MVC Routing Overview</span></span>](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [<span data-ttu-id="b3211-160">Маршрутизация атрибутов в ASP.NET MVC 5</span><span class="sxs-lookup"><span data-stu-id="b3211-160">Attribute Routing in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [<span data-ttu-id="b3211-161">Маршрутизация атрибутов в веб-API ASP.NET 2</span><span class="sxs-lookup"><span data-stu-id="b3211-161">Attribute routing in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [<span data-ttu-id="b3211-162">Выбор маршрутизации и действий в веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b3211-162">Routing and Action Selection in ASP.NET Web API</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [<span data-ttu-id="b3211-163">Маршрутизация в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3211-163">Routing in ASP.NET Core</span></span>](/aspnet/core/fundamentals/routing)
- [<span data-ttu-id="b3211-164">Маршрутизация к действиям контроллера в ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="b3211-164">Routing to controller actions in ASP.NET Core MVC</span></span>](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
><span data-ttu-id="b3211-165">[Назад](configuration-differences.md)
>[Вперед](comparing-razor-pages-aspnet-mvc.md)</span><span class="sxs-lookup"><span data-stu-id="b3211-165">[Previous](configuration-differences.md)
[Next](comparing-razor-pages-aspnet-mvc.md)</span></span>
