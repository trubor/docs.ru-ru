---
title: Дополнительные сценарии миграции
description: В этом разделе описываются дополнительные сценарии и методы миграции платформа .NET Framework приложений в .NET Core и .NET 5.
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: da710644c5c17c3d701cc8d492481a076a691eeb
ms.sourcegitcommit: 5cad087ed0cfc4cf632b6d8270ed311e4d8b5217
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2021
ms.locfileid: "107928596"
---
# <a name="more-migration-scenarios"></a>Дополнительные сценарии миграции

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

В этом разделе описываются несколько различных сценариев приложений ASP.NET и приводятся конкретные методы решения каждого из них. С помощью этого раздела можно определить сценарии, применимые к приложению, и оценить, какие методы будут работать для приложения и его среды размещения.

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a>Миграция ASP.NET MVC 5 и WebApi 2 на ASP.NET Core MVC

Распространенным сценарием для приложений ASP.NET MVC 5 и Web API 2 было установка обоих продуктов в одном и том же приложении. Это поддерживаемый и относительно распространенный подход, используемый многими группами, но поскольку эти два продукта используют разные абстракции, требуются некоторые избыточные усилия. Например, Настройка маршрутов для ASP.NET MVC выполняется с помощью методов в `RouteCollection` , таких как `MapMvcAttributeRoutes()` и `MapRoute()` . Но веб-API ASP.NET 2 маршрутизация управляется с помощью `HttpConfiguration` методов и, таких как `MapHttpAttributeRoutes()` и `MapHttpRoute()` .

`eShopLegacyMVC`Приложение включает в себя ASP.NET MVC и веб-API, а также методы в своей `App_Start` папке для настройки маршрутов для обоих. Он также поддерживает внедрение зависимостей с помощью Autofac, что также требует двух наборов аналогичной работы для настройки:

```csharp
protected IContainer RegisterContainer()
{
    var builder = new ContainerBuilder();

    var thisAssembly = Assembly.GetExecutingAssembly();
    builder.RegisterControllers(thisAssembly);      // MVC controllers
    builder.RegisterApiControllers(thisAssembly);   // Web API controllers

    var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
    builder.RegisterModule(new ApplicationModule(mockData));

    var container = builder.Build();

    // set mvc resolver
    DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

    // set webapi resolver
    var resolver = new AutofacWebApiDependencyResolver(container);
    GlobalConfiguration.Configuration.DependencyResolver = resolver;

    return container;
}
```

При обновлении этих приложений для использования ASP.NET Core эти дублирующие усилия и путаница, которые иногда прилагается к ней, устраняются. ASP.NET Core MVC — это единая платформа с одним набором правил для маршрутизации, фильтров и многого другого. Внедрение зависимостей встроено в .NET Core. Все это можно настроить в `Startup.cs` , как показано в `eShopPorted` приложении в примере.

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a>Миграция HttpResponseMessage в ASP.NET Core

Некоторые веб-API ASP.NET приложения могут иметь методы действий, возвращающие `HttpResponseMessage` . Этот тип не существует в ASP.NET Core. Ниже приведен пример использования в `Delete` методе действия с помощью `ResponseMessage` вспомогательного метода в базе `ApiController` :

```csharp
// DELETE api/<controller>/5
[HttpDelete]
public IHttpActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return ResponseMessage(new HttpResponseMessage(HttpStatusCode.NotFound));
    }

    // demo only - don't actually delete
    return ResponseMessage(new HttpResponseMessage(HttpStatusCode.OK));
}
```

В ASP.NET Core MVC доступны вспомогательные методы для всех распространенных кодов состояния ответа HTTP, поэтому приведенный выше метод будет перенесен в следующий код:

```csharp
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return NotFound();
    }

    // demo only - don't actually delete
    return Ok();
}
```

Если вы обнаружите, что вам нужно вернуть пользовательский код состояния, для которого не существует вспомогательного приложения, всегда можно использовать `return StatusCode(int statusCode)` для возврата любого числового кода.

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a>Перенос согласования содержимого из веб-API ASP.NET в ASP.NET Core

Веб-API ASP.NET 2 поддерживает [Согласование содержимого](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) изначально. Пример приложения включает в себя `BrandsController` , который демонстрирует эту поддержку путем перечисления результатов в формате XML или JSON. Он основан на `Accept` заголовке запроса и изменяется, когда он включает `application/xml` или `application/json` .

В приложениях ASP.NET MVC 5 не встроена поддержка согласования содержимого.

Согласование содержимого предпочтительнее, чем возврат определенного типа кодирования, так как он является более гибким и делает API доступным для большего числа клиентов. Если в данный момент у вас есть методы действий, возвращающие конкретный формат, рекомендуется изменить их, чтобы возвратить тип результата, поддерживающий согласование содержимого при переносе кода в ASP.NET Core.

Следующий код возвращает данные в формате JSON независимо от `Accept` содержимого заголовка клиента:

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

[ASP.NET Core MVC поддерживает согласование содержимого в собственном](/aspnet/core/web-api/advanced/formatting)режиме, при условии, что используется соответствующий [тип возвращаемого](/aspnet/core/web-api/action-return-types) значения. Согласование содержимого реализуется с помощью [Обжектресулт], который возвращается результатами действий, связанными с кодом состояния, возвращаемыми вспомогательными методами контроллера. Предыдущий метод действия, реализованный в ASP.NET Core MVC с использованием согласования содержимого, будет выглядеть следующим образом:

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

Это по умолчанию будет возвращать данные в формате JSON. XML и другие форматы будут использоваться, [Если приложение настроено с использованием соответствующего модуля форматирования](/aspnet/core/web-api/advanced/formatting).

## <a name="custom-model-binding"></a>Пользовательская привязка модели

Большинство приложений ASP.NET MVC и веб-API используют привязку модели. Синтаксис привязки модели по умолчанию довольно легко переносится между этими приложениями и ASP.NET Core MVC. Однако в некоторых случаях клиенты записали [пользовательские связыватели модели](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) для поддержки определенных типов моделей или сценариев использования. Пользовательские связыватели модели в ASP.NET MVC и проектах веб-API используют отдельные `IModelBinder` интерфейсы, определенные в `System.Web.Mvc` `System.Web.Http` пространствах имен и соответственно. В обоих случаях пользовательский связыватель предоставляет `Bind` метод, принимающий контекст контроллера или действия и контекст привязки модели в качестве аргументов.

После создания пользовательского связывателя его необходимо зарегистрировать в приложении. Для этого шага требуется создать другой тип, `ModelBinderProvider` который выступает в качестве фабрики и создает связыватель модели во время запроса. В приложениях MVC можно добавлять привязки `ApplicationStart` , как показано ниже.

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

В приложениях веб-API настраиваемые связыватели можно ссылаться с помощью атрибутов. `ModelBinder`Атрибут можно добавить к параметрам метода действия или к определению типа параметра, как показано ниже.

```csharp
// attribute on action method parameter
public HttpResponseMessage([ModelBinder(typeof(MyCustomBinder))] CustomDTO custom)
{
}

// attribute on type
[ModelBinder(typeof(MyCustomBinder))]
public class CustomDTO
{
}
```

Чтобы зарегистрировать связыватель модели глобально в веб-API ASP.NET, его поставщик необходимо добавить во время запуска приложения:

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var provider = new CustomModelBinderProvider(
            typeof(CustomDTO), new CustomModelBinder());
        config.Services.Insert(typeof(ModelBinderProvider), 0, provider);

        // ...
    }
}
```

При переносе [поставщиков пользовательских моделей на ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)шаблон веб-API ближе к ASP.NET Core подходу, чем ASP.NET MVC 5. Главным различием между `IModelBinder` интерфейсом ASP.NET Core и веб-API является то, что метод ASP.NET Core является async ( `BindModelAsync` ), а `BindingModelContext` вместо двух параметров, таких как требуемая версия веб-API, требуется только один параметр. В ASP.NET Core можно использовать `[ModelBinder]` атрибут для отдельных параметров метода действия или связанных с ними типов. Вы также можете создать `ModelBinderProvider` , который будет использоваться глобально в приложении, где это необходимо. Чтобы настроить такой поставщик, добавьте код `Startup` в `ConfigureServices` :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a>Модули форматирования мультимедиа

Веб-API ASP.NET поддерживает несколько форматов мультимедиа и может быть расширен с помощью пользовательских модулей форматирования мультимедиа. Документация описывает [Пример модуля форматирования мультимедиа CSV](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) , который можно использовать для отправки данных в формате значений с разделителями-запятыми. Если приложение веб-API использует пользовательские модули форматирования мультимедиа, их необходимо преобразовать в [ASP.NET Core пользовательские модули форматирования](/aspnet/core/web-api/advanced/custom-formatters).

Чтобы создать пользовательский модуль форматирования в веб-API 2, вы наследуете от соответствующего базового класса, а затем добавили модуль форматирования в конвейер веб-API с помощью `HttpConfiguration` объекта:

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter());
}
```

В ASP.NET Core процесс аналогичен. ASP.NET Core поддерживает модули форматирования ввода (используемые привязкой модели) и модули форматирования выходных данных (используются для форматирования ответов). Добавление пользовательского модуля форматирования для вывода ответов с особым способом включает наследование от соответствующего базового класса и Добавление модуля форматирования в MVC в `Startup` :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.InputFormatters.Insert(0, new CustomInputFormatter());
        options.OutputFormatters.Insert(0, new CustomOutputFormatter());
    });
}
```

Полный список базовых классов можно найти в пространстве имен [Microsoft. AspNetCore. MVC. Formatter](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) .

Шаги для миграции из модуля форматирования веб-API в ASP.NET Core модуль форматирования MVC:

1. Найдите соответствующий базовый класс для нового модуля форматирования.
1. Создайте новый экземпляр базового класса и реализуйте его необходимые методы.
1. Скопируйте функции из модуля форматирования веб-API в новую реализацию.
1. Настройте MVC в методе приложения ASP.NET Core, `ConfigureServices` чтобы использовать новый модуль форматирования.

## <a name="custom-filters"></a>Настраиваемые фильтры

Фильтры используются в ASP.NET Core приложениях для выполнения кода до и (или) после определенных этапов в конвейере обработки запросов. ASP.NET MVC и веб-API также используют фильтры во многом так же, но сведения различаются. Например, [ASP.NET MVC поддерживает четыре типа фильтров](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters). Веб-API ASP.NET 2 поддерживает аналогичные фильтры, а как MVC, так и веб-API включали атрибуты для [переопределения фильтров](/dotnet/api/system.web.mvc.filters.ioverridefilter).

Наиболее распространенным фильтром, используемым в приложениях ASP.NET MVC и веб-API, является фильтр действий, определяемый [интерфейсом иактионфилтер](/dotnet/api/system.web.mvc.iactionfilter). Этот интерфейс предоставляет методы для Before ( `OnActionExecuting` ) и After ( `OnActionExecuted` ), которые можно использовать для выполнения кода до и (или) после выполнения действия, как указано для каждого метода.

ASP.NET Core поддерживает фильтры, а его унификация MVC и веб-API означает, что существует только один подход к их реализации. [Документация включает подробное описание пяти (5) видов фильтров, встроенных в ASP.NET Core MVC](/aspnet/core/mvc/controllers/filters#filter-types). Все варианты фильтров, поддерживаемые в ASP.NET MVC и веб-API ASP.NET имеют связанные версии в ASP.NET Core, поэтому миграция, как правило, заключается в определении соответствующего интерфейса и (или) базового класса и переносе кода.

Помимо синхронных интерфейсов ASP.NET Core также предоставляет асинхронные интерфейсы, такие как, которые `IAsyncActionFilter` предоставляют один асинхронный метод, который можно использовать для включения кода для выполнения как до, так и после действия, как показано ниже.

```csharp
public class SampleAsyncActionFilter : IAsyncActionFilter
{
    public async Task OnActionExecutionAsync(
        ActionExecutingContext context,
        ActionExecutionDelegate next)
    {
        // Do something before the action executes.

        // next() calls the action method.
        var resultContext = await next();
        // resultContext.Result is set.
        // Do something after the action executes.
    }
}
```

При переносе асинхронного кода (или кода, который должен быть асинхронным) командам следует рассмотреть возможность использования встроенных асинхронных типов, предоставляемых для этой цели.

Большинство приложений ASP.NET MVC и веб-API не используют большое количество настраиваемых фильтров. Поскольку подход к фильтрам в ASP.NET Core MVC тесно согласуется с фильтрами в ASP.NET MVC и веб-API, миграция пользовательских фильтров обычно довольно проста. Не забудьте прочитать подробную документацию по фильтрам в документации по ASP.NET Core и, убедившись, что вы хорошо понимаете их, переносите логику из старой системы в фильтры новой системы.

## <a name="route-constraints"></a>Ограничения маршрута

ASP.NET Core использует ограничения маршрута, чтобы обеспечить правильную маршрутизацию запросов для маршрутизации запроса. [ASP.NET Core поддерживает большое количество различных ограничений маршрута для этой цели]/АСПнет/коре/фундаменталс/раутинг # Route-Constraint-Reference). Ограничения маршрутов могут применяться в таблице маршрутов, но большинство приложений, созданных с помощью ASP.NET MVC 5 и/или [веб-API ASP.NET 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) , используют встроенные ограничения маршрута, применяемые к маршрутам атрибутов. Встроенные ограничения маршрутов используют следующий формат:

```csharp
[Route("/customer/{id:int}")]
```

`:int` `id` Параметр после параметра Route ограничивает значение в соответствии с `int` типом. Одно из преимуществ использования ограничений маршрутов заключается в том, что они позволяют использовать два одинаковых маршрута, где параметры отличаются только их типом. Это позволяет аналогично [перегружать методы](../../standard/design-guidelines/member-overloading.md) маршрутов на основе только типа параметра.

Набор ограничений маршрута, их синтаксис и использование очень схожи между всеми тремя подходами. Пользовательские ограничения маршрута довольно редки в клиентских приложениях. Если приложение использует настраиваемое ограничение маршрута и необходимо перенести в ASP.NET Core, в документацию включены примеры, демонстрирующие [Создание настраиваемых ограничений маршрута в ASP.NET Core](/aspnet/core/fundamentals/routing#custom-route-constraints). По сути, все, что необходимо, это реализовать `IRouteConstraint` и его `Match` метод, а затем добавить пользовательское ограничение при настройке маршрутизации для приложения:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers();

    services.AddRouting(options =>
    {
        options.ConstraintMap.Add("customName", typeof(MyCustomConstraint));
    });
}
```

Это очень похоже на то, как пользовательские ограничения используются в веб-API ASP.NET, который использует `IHttpRouteConstraint` и настраивает его с помощью распознавателя и вызова `HttpConfiguration.MapHttpAttributeRoutes` :

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var constraintResolver = new DefaultInlineConstraintResolver();
        constraintResolver.ConstraintMap.Add("nonzero", typeof(CustomConstraint));

        config.MapHttpAttributeRoutes(constraintResolver);
    }
}
```

ASP.NET MVC 5 следует очень похожим подходом, используя `IRouteConstraint` для его имени интерфейса и настроив ограничение как часть конфигурации маршрута:

```csharp
public class RouteConfig
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

        var constraintsResolver = new DefaultInlineConstraintResolver();
        constraintsResolver.ConstraintMap.Add("values", typeof(ValuesConstraint));
        routes.MapMvcAttributeRoutes(constraintsResolver);
    }
}
```

Миграция использования ограничения маршрута, а также пользовательских ограничений маршрута к ASP.NET Core обычно очень проста.

## <a name="custom-route-handlers"></a>Пользовательские обработчики маршрутов

Еще одна довольно сложная функция ASP.NET MVC 5 — это обработчики маршрутов. Пользовательские обработчики маршрутов реализуют `IRouteHandler` , в том числе один метод, возвращающий `IHttpHandler` для запроса на предоставление. `IHttpHandler`, В свою очередь, предоставляет `IsReusable` свойство и единственный `ProcessRequest` метод. В ASP.NET MVC 5 можно настроить определенный маршрут в таблице маршрутов для использования настраиваемого обработчика:

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

Чтобы перенести пользовательские обработчики маршрутов из ASP.NET MVC 5 в ASP.NET Core, можно либо использовать фильтр (например, фильтр действий), либо пользовательский [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) . Подход фильтра относительно прост, и его можно добавить в качестве глобального фильтра при добавлении MVC `ConfigureServices` в в *Startup. CS*.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

`IRouter`Параметр требует реализации `RouteAsync` методов интерфейса и `GetVirtualPath` . Пользовательский маршрутизатор добавляется в конвейер запросов в `Configure` методе в *Startup. CS*.

```csharp
public void Configure(IApplicationBuilder app)
{
    // ...
    app.UseMvc(routes =>
    {
        routes.Routes.Add(new CustomRouter(routes.DefaultHandler));
    });
}
```

В веб-API ASP.NET эти обработчики называются [пользовательскими обработчиками сообщений](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers), а не *обработчиками маршрутов*. Обработчики сообщений должны быть производными от класса `DelegatingHandler` и переопределять его `SendAsync` метод. Обработчики сообщений можно объединить в цепочки, чтобы сформировать конвейер так, что очень похоже на ASP.NET Core по промежуточного слоя и его конвейер запросов.

ASP.NET Core не имеет `DelegatingHandler` типа или отдельного конвейера обработчика сообщений. Вместо этого такие обработчики следует перенести с помощью глобальных фильтров, пользовательских `IRouter` экземпляров (см. выше) или пользовательского по промежуточного слоя. ASP.NET Core фильтры и `IRouter` типы MVC имеют преимущество встроенного доступа к конструкциям MVC, таким как контроллеры и действия, в то время как по промежуточного слоя не имеет связей с MVC. Это делает его более гибким, но также требует дополнительных усилий, если требуется доступ к компонентам MVC.

## <a name="cors-support"></a>Поддержка CORS

CORS или совместное использование ресурсов в разных источниках — это стандарт W3C, позволяющий серверам принимать запросы, которые не поступают от ответов, которые они обслуживают. ASP.NET MVC 5 и веб-API ASP.NET 2 поддерживают CORS различными способами. Самый простой способ включить поддержку CORS в ASP.NET MVC 5 — это фильтр действий, подобный этому:

```csharp
public class AllowCrossSiteAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext filterContext)
    {
        filterContext.RequestContext.HttpContext.Response.AddHeader(
            "Access-Control-Allow-Origin", "example.com");
        base.OnActionExecuting(filterContext);
    }
}
```

Веб-API ASP.NET также может использовать такой фильтр, но он имеет [встроенную поддержку включения CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) :

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        config.EnableCors();
        // ...
    }
}
```

После добавления можно настроить разрешенные источники, заголовки и методы с помощью `EnableCors` атрибута следующим образом:

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

Прежде чем переносить реализацию CORS из ASP.NET MVC 5 или веб-API ASP.NET 2, ознакомьтесь с принципами [работы CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) и создайте некоторые автоматические тесты, демонстрирующие, что CORS работает должным образом в текущей системе.

В ASP.NET Core существует три встроенных способа включения CORS:

- [Настроено с помощью политики](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware) в `ConfigureServices`
- Включено с [маршрутизацией конечных точек](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)
- Включено с [ `EnableCors` атрибутом](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)

Каждый из этих подходов подробно описан в документах, которые связаны с приведенными выше параметрами. Выбор одного из них во многом зависит от того, как существующее приложение поддерживает CORS. Если приложение использует атрибуты, вы, вероятно, можете выполнить миграцию, чтобы использовать `EnableCors` атрибут наиболее просто. Если приложение использует фильтры, можно продолжать использовать этот подход (хотя это не стандартный подход, используемый в ASP.NET Core), или выполнить миграцию для использования атрибутов или политик. Маршрутизация конечных точек — это относительно новая функция, появившаяся в ASP.NET Core 3 и не имеющая близкого аналога в приложениях ASP.NET MVC 5 или веб-API ASP.NET 2.

## <a name="custom-areas"></a>Пользовательские области

Многие приложения ASP.NET MVC используют области для организации проекта. Области обычно находятся в корне проекта в папке *областей* и должны быть зарегистрированы при запуске приложения, обычно в `Application_Start()` :

```csharp
AreaRegistration.RegisterAllAreas();
```

Альтернативой регистрации всех областей при запуске является использование `RouteArea` атрибута на отдельных контроллерах:

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

При использовании областей дополнительные аргументы передаются в вспомогательные методы HTML для создания ссылок на действия в различных областях:

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

Веб-API ASP.NET приложения обычно не используют области явным образом, так как их контроллеры можно поместить в любую папку в проекте. Команды могут использовать любую структуру папок для Организации контроллеров API.

[Области](/aspnet/core/mvc/controllers/areas) поддерживаются в ASP.NET Core MVC. Используемый подход практически идентичен использованию областей в ASP.NET MVC 5. Разработчики, выполняющие миграцию кода с помощью областей, должны учитывать следующие отличия.

- `AreaRegistration.RegisterAllAreas` не используется в ASP.NET Core MVC
- Области применяются с помощью `[Area("name")]` атрибута (не `RouteArea` как в ASP.NET MVC 5).
- При необходимости области можно добавить в шаблоны таблицы маршрутов (или же они могут использовать маршрутизацию атрибутов).

Чтобы добавить поддержку областей в таблицу маршрутов в ASP.NET Core MVC, в `Configure` разделе *Startup. CS* необходимо добавить следующее:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "MyArea",
        pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");

    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Области можно также использовать с маршрутизацией атрибутов, используя `{area}` ключевое слово в определении маршрута (это одно из нескольких [зарезервированных имен маршрутизации](/aspnet/core/mvc/controllers/routing#reserved-routing-names) , которые можно использовать с шаблонами маршрутов).

Вспомогательные функции тегов поддерживают области с `asp-area` атрибутом, который можно использовать для создания ссылок в представлениях и страницах Razor.

```razor
<ul>
    <li>
        <a asp-area="Products" asp-controller="Home" asp-action="About">
            Products/Home/About
        </a>
    </li>
    <li>
        <a asp-area="Services" asp-controller="Home" asp-action="About">
            Services About
        </a>
    </li>
    <li>
        <a asp-area="" asp-controller="Home" asp-action="About">
            /Home/About
        </a>
    </li>
</ul>
```

Если выполняется миграция на Razor Pages необходимо использовать папку *областей* в папке *pages* . Дополнительные сведения см. [в разделе области с Razor Pages](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages).

Помимо приведенных выше рекомендаций, команды должны проанализировать, [как маршрутизация в ASP.NET Core работает с областями](/aspnet/core/mvc/controllers/routing#areas) в рамках процесса планирования миграции.

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a>Интеграционные тесты для ASP.NET MVC и веб-API ASP.NET

Тесты интеграции — это автоматические тесты, которые проверяют, правильно ли работают несколько различных частей приложения. Написание интеграционных тестов для ASP.NET MVC и веб-API ASP.NET обычно включало развертывание приложения на реальном веб-сервере, например локальный экземпляр IIS или IIS Express, а затем запросы к этому размещенному приложению с помощью HTTP-клиента. Некоторые из этих тестов могут взаимодействовать с пользовательским интерфейсом на стороне клиента с помощью средств автоматизации браузера, таких как [Selenium](https://www.selenium.dev/), хотя часто эти тесты называются *тестами пользовательского интерфейса* , а не тестами интеграции.

Если перенесенное приложение использует то же поведение, что и исходная версия, любая существующая технология, используемая группой для выполнения тестов интеграции (и тестов пользовательского интерфейса), должна продолжать работать точно так же, как и раньше. Обычно эти тесты не отличаются от базовой технологии, используемой для размещения тестируемого приложения, и взаимодействуют с ним только через HTTP-запросы. То, что может стать более сложной задачей, заключается в том, как тесты взаимодействуют с приложением для получения известного хорошего состояния перед каждым тестом. Это может потребовать некоторых усилий при миграции, так как настройка и запуск значительно отличаются в ASP.NET Core по сравнению с ASP.NET MVC или веб-API ASP.NET.

Группы должны строго рассмотреть миграцию своих интеграционных тестов для использования [встроенной поддержки тестирования интеграции ASP.NET Core](/aspnet/core/test/integration-tests) . В ASP.NET Core приложения можно протестировать, развернув их в `TestHost` , который настраивается с помощью `WebApplicationFactory` . Для размещения приложения на тестирование требуется небольшое количество настроек, но после этого создание отдельных тестов интеграции очень просто.

Одной из лучших функций поддержки тестирования интеграции ASP.NET Core является то, что приложение размещается в памяти. Нет необходимости настраивать реальный сервер для размещения приложения. Нет необходимости использовать средство автоматизации браузера (если вы тестируете только ASP.NET Core и не поведение на стороне клиента). Многие проблемы, которые могут возникнуть при попытке использовать реальный веб-сервер для автоматизированных тестов интеграции, например проблемы с брандмауэром или проблемы запуска и прекращения процесса, устраняются при таком подходе. Поскольку все запросы выполняются в памяти без требования к сети, тесты также выполняются гораздо быстрее, чем тесты, которые должны настроить отдельный сервер и взаимодействовать с ним по сети (даже если он работает на том же компьютере).

Ниже приведен пример ASP.NET Core интеграционный тест (иногда называемый *функциональными тестами* , который отличает их от тестов интеграции более низкого уровня) из [эталонного приложения eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb):

```csharp
public class GetByIdEndpoint : IClassFixture<ApiTestFixture>
{
    JsonSerializerOptions _jsonOptions = new JsonSerializerOptions { PropertyNameCaseInsensitive = true };

    public GetByIdEndpoint(ApiTestFixture factory)
    {
        Client = factory.CreateClient();
    }

    public HttpClient Client { get; }

    [Fact]
    public async Task ReturnsItemGivenValidId()
    {
        var response = await Client.GetAsync("api/catalog-items/5");
        response.EnsureSuccessStatusCode();
        var stringResponse = await response.Content.ReadAsStringAsync();
        var model = stringResponse.FromJson<GetByIdCatalogItemResponse>();

        Assert.Equal(5, model.CatalogItem.Id);
        Assert.Equal("Roslyn Red Sheet", model.CatalogItem.Name);
    }
}
```

Если переносимое приложение не содержит тестов интеграции, процесс миграции может быть отличной возможностью добавить некоторые. Эти тесты могут проверить, что перенесенное приложение ведет себя по мере ожидания команды. При выполнении таких тестов на раннем этапе миграции они могут гарантировать, что последующие действия по переносу не нарушат ранее перенесенные части приложения. Учитывая, насколько просто настраивать и выполнять интеграционные тесты в ASP.NET Core, возврат на инвестиции, потраченный на настройку таких тестов, обычно довольно высок.

## <a name="wcf-client-configuration"></a>Конфигурация клиента WCF

Если приложение в настоящее время использует службы WCF в качестве клиента, этот сценарий поддерживается. Однако необходимо [перенести конфигурацию](/aspnet/core/migration/configuration) из *web.config* , чтобы использовать новую *appsettings.jsв* файле. Другой вариант — добавить любую необходимую конфигурацию к клиентам программным способом при их создании. Пример:

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

Если в вашей организации есть обширные службы, созданные с помощью WCF, которые использует приложение, рассмотрите возможность переноса для использования gRPC. Дополнительные сведения о gRPC, о том, зачем вам нужно выполнить миграцию, и подробном руководству по миграции, см. в книге [gRPC for WCF Developers](/dotnet/architecture/grpc-for-wcf-developers/) .

## <a name="references"></a>Ссылки

- [Согласование содержимого веб-API ASP.NET](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [Форматирование данных отклика в веб-API ASP.NET Core](/aspnet/core/web-api/advanced/formatting)
- [Пользовательские связыватели модели в веб-API ASP.NET](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [Пользовательские связыватели модели в ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- [Модули форматирования мультимедиа в веб-API ASP.NET 2](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)\
- [Пользовательские модули форматирования для веб-API в ASP.NET Core](/aspnet/core/web-api/advanced/custom-formatters)
- [Фильтры в ASP.NET Core](/aspnet/core/mvc/controllers/filters)
- [Ограничения маршрутов в веб-API ASP.NET 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [Ограничения маршрутов в ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [Ссылка на ограничение маршрута ASP.NET Core](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [Пользовательские обработчики сообщений в веб-API ASP.NET 2](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [Простой элемент управления CORS в MVC 5 и Web API 2](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [Включение запросов между источниками в веб-API](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [Включение запросов между источниками (CORS) в ASP.NET Core](/aspnet/core/security/cors)
- [Области в ASP.NET Core](/aspnet/core/mvc/controllers/areas)
- [Интеграционные тесты на платформе ASP.NET Core](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[Назад](example-migration-eshop.md)
>[Вперед](deployment-scenarios.md)
