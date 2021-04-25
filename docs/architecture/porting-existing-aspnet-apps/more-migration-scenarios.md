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
# <a name="more-migration-scenarios"></a><span data-ttu-id="f385f-103">Дополнительные сценарии миграции</span><span class="sxs-lookup"><span data-stu-id="f385f-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f385f-104">В этом разделе описываются несколько различных сценариев приложений ASP.NET и приводятся конкретные методы решения каждого из них.</span><span class="sxs-lookup"><span data-stu-id="f385f-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="f385f-105">С помощью этого раздела можно определить сценарии, применимые к приложению, и оценить, какие методы будут работать для приложения и его среды размещения.</span><span class="sxs-lookup"><span data-stu-id="f385f-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="f385f-106">Миграция ASP.NET MVC 5 и WebApi 2 на ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="f385f-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="f385f-107">Распространенным сценарием для приложений ASP.NET MVC 5 и Web API 2 было установка обоих продуктов в одном и том же приложении.</span><span class="sxs-lookup"><span data-stu-id="f385f-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="f385f-108">Это поддерживаемый и относительно распространенный подход, используемый многими группами, но поскольку эти два продукта используют разные абстракции, требуются некоторые избыточные усилия.</span><span class="sxs-lookup"><span data-stu-id="f385f-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="f385f-109">Например, Настройка маршрутов для ASP.NET MVC выполняется с помощью методов в `RouteCollection` , таких как `MapMvcAttributeRoutes()` и `MapRoute()` .</span><span class="sxs-lookup"><span data-stu-id="f385f-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="f385f-110">Но веб-API ASP.NET 2 маршрутизация управляется с помощью `HttpConfiguration` методов и, таких как `MapHttpAttributeRoutes()` и `MapHttpRoute()` .</span><span class="sxs-lookup"><span data-stu-id="f385f-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="f385f-111">`eShopLegacyMVC`Приложение включает в себя ASP.NET MVC и веб-API, а также методы в своей `App_Start` папке для настройки маршрутов для обоих.</span><span class="sxs-lookup"><span data-stu-id="f385f-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="f385f-112">Он также поддерживает внедрение зависимостей с помощью Autofac, что также требует двух наборов аналогичной работы для настройки:</span><span class="sxs-lookup"><span data-stu-id="f385f-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="f385f-113">При обновлении этих приложений для использования ASP.NET Core эти дублирующие усилия и путаница, которые иногда прилагается к ней, устраняются.</span><span class="sxs-lookup"><span data-stu-id="f385f-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="f385f-114">ASP.NET Core MVC — это единая платформа с одним набором правил для маршрутизации, фильтров и многого другого.</span><span class="sxs-lookup"><span data-stu-id="f385f-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="f385f-115">Внедрение зависимостей встроено в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f385f-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="f385f-116">Все это можно настроить в `Startup.cs` , как показано в `eShopPorted` приложении в примере.</span><span class="sxs-lookup"><span data-stu-id="f385f-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="f385f-117">Миграция HttpResponseMessage в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="f385f-118">Некоторые веб-API ASP.NET приложения могут иметь методы действий, возвращающие `HttpResponseMessage` .</span><span class="sxs-lookup"><span data-stu-id="f385f-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="f385f-119">Этот тип не существует в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f385f-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="f385f-120">Ниже приведен пример использования в `Delete` методе действия с помощью `ResponseMessage` вспомогательного метода в базе `ApiController` :</span><span class="sxs-lookup"><span data-stu-id="f385f-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="f385f-121">В ASP.NET Core MVC доступны вспомогательные методы для всех распространенных кодов состояния ответа HTTP, поэтому приведенный выше метод будет перенесен в следующий код:</span><span class="sxs-lookup"><span data-stu-id="f385f-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="f385f-122">Если вы обнаружите, что вам нужно вернуть пользовательский код состояния, для которого не существует вспомогательного приложения, всегда можно использовать `return StatusCode(int statusCode)` для возврата любого числового кода.</span><span class="sxs-lookup"><span data-stu-id="f385f-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="f385f-123">Перенос согласования содержимого из веб-API ASP.NET в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="f385f-124">Веб-API ASP.NET 2 поддерживает [Согласование содержимого](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) изначально.</span><span class="sxs-lookup"><span data-stu-id="f385f-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="f385f-125">Пример приложения включает в себя `BrandsController` , который демонстрирует эту поддержку путем перечисления результатов в формате XML или JSON.</span><span class="sxs-lookup"><span data-stu-id="f385f-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="f385f-126">Он основан на `Accept` заголовке запроса и изменяется, когда он включает `application/xml` или `application/json` .</span><span class="sxs-lookup"><span data-stu-id="f385f-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="f385f-127">В приложениях ASP.NET MVC 5 не встроена поддержка согласования содержимого.</span><span class="sxs-lookup"><span data-stu-id="f385f-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="f385f-128">Согласование содержимого предпочтительнее, чем возврат определенного типа кодирования, так как он является более гибким и делает API доступным для большего числа клиентов.</span><span class="sxs-lookup"><span data-stu-id="f385f-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="f385f-129">Если в данный момент у вас есть методы действий, возвращающие конкретный формат, рекомендуется изменить их, чтобы возвратить тип результата, поддерживающий согласование содержимого при переносе кода в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f385f-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="f385f-130">Следующий код возвращает данные в формате JSON независимо от `Accept` содержимого заголовка клиента:</span><span class="sxs-lookup"><span data-stu-id="f385f-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="f385f-131">[ASP.NET Core MVC поддерживает согласование содержимого в собственном](/aspnet/core/web-api/advanced/formatting)режиме, при условии, что используется соответствующий [тип возвращаемого](/aspnet/core/web-api/action-return-types) значения.</span><span class="sxs-lookup"><span data-stu-id="f385f-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="f385f-132">Согласование содержимого реализуется с помощью [Обжектресулт], который возвращается результатами действий, связанными с кодом состояния, возвращаемыми вспомогательными методами контроллера.</span><span class="sxs-lookup"><span data-stu-id="f385f-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="f385f-133">Предыдущий метод действия, реализованный в ASP.NET Core MVC с использованием согласования содержимого, будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f385f-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="f385f-134">Это по умолчанию будет возвращать данные в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="f385f-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="f385f-135">XML и другие форматы будут использоваться, [Если приложение настроено с использованием соответствующего модуля форматирования](/aspnet/core/web-api/advanced/formatting).</span><span class="sxs-lookup"><span data-stu-id="f385f-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="custom-model-binding"></a><span data-ttu-id="f385f-136">Пользовательская привязка модели</span><span class="sxs-lookup"><span data-stu-id="f385f-136">Custom model binding</span></span>

<span data-ttu-id="f385f-137">Большинство приложений ASP.NET MVC и веб-API используют привязку модели.</span><span class="sxs-lookup"><span data-stu-id="f385f-137">Most ASP.NET MVC and Web API apps make use of model binding.</span></span> <span data-ttu-id="f385f-138">Синтаксис привязки модели по умолчанию довольно легко переносится между этими приложениями и ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="f385f-138">The default model binding syntax migrates fairly seamlessly between these apps and ASP.NET Core MVC.</span></span> <span data-ttu-id="f385f-139">Однако в некоторых случаях клиенты записали [пользовательские связыватели модели](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) для поддержки определенных типов моделей или сценариев использования.</span><span class="sxs-lookup"><span data-stu-id="f385f-139">However, in some cases customers have written [custom model binders](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) to support specific model types or usage scenarios.</span></span> <span data-ttu-id="f385f-140">Пользовательские связыватели модели в ASP.NET MVC и проектах веб-API используют отдельные `IModelBinder` интерфейсы, определенные в `System.Web.Mvc` `System.Web.Http` пространствах имен и соответственно.</span><span class="sxs-lookup"><span data-stu-id="f385f-140">Custom model binders in ASP.NET MVC and Web API projects use separate `IModelBinder` interfaces defined in `System.Web.Mvc` and `System.Web.Http` namespaces, respectively.</span></span> <span data-ttu-id="f385f-141">В обоих случаях пользовательский связыватель предоставляет `Bind` метод, принимающий контекст контроллера или действия и контекст привязки модели в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="f385f-141">In both cases, the custom binder exposes a `Bind` method that accepts a controller or action context and a model binding context as arguments.</span></span>

<span data-ttu-id="f385f-142">После создания пользовательского связывателя его необходимо зарегистрировать в приложении.</span><span class="sxs-lookup"><span data-stu-id="f385f-142">Once the custom binder is created, it must be registered with the app.</span></span> <span data-ttu-id="f385f-143">Для этого шага требуется создать другой тип, `ModelBinderProvider` который выступает в качестве фабрики и создает связыватель модели во время запроса.</span><span class="sxs-lookup"><span data-stu-id="f385f-143">This step requires creating another type, a `ModelBinderProvider`, which acts as a factory and creates the model binder during a request.</span></span> <span data-ttu-id="f385f-144">В приложениях MVC можно добавлять привязки `ApplicationStart` , как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="f385f-144">Binders can be added during `ApplicationStart` in MVC apps as shown:</span></span>

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

<span data-ttu-id="f385f-145">В приложениях веб-API настраиваемые связыватели можно ссылаться с помощью атрибутов.</span><span class="sxs-lookup"><span data-stu-id="f385f-145">In Web API apps, custom binders can be referenced using attributes.</span></span> <span data-ttu-id="f385f-146">`ModelBinder`Атрибут можно добавить к параметрам метода действия или к определению типа параметра, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="f385f-146">The `ModelBinder` attribute can be added to action method parameters or to the parameter's type definition, as shown:</span></span>

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

<span data-ttu-id="f385f-147">Чтобы зарегистрировать связыватель модели глобально в веб-API ASP.NET, его поставщик необходимо добавить во время запуска приложения:</span><span class="sxs-lookup"><span data-stu-id="f385f-147">To register a model binder globally in ASP.NET Web API, its provider must be added during app startup:</span></span>

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

<span data-ttu-id="f385f-148">При переносе [поставщиков пользовательских моделей на ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)шаблон веб-API ближе к ASP.NET Core подходу, чем ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="f385f-148">When migrating [custom model providers to ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample), the Web API pattern is closer to the ASP.NET Core approach than the ASP.NET MVC 5.</span></span> <span data-ttu-id="f385f-149">Главным различием между `IModelBinder` интерфейсом ASP.NET Core и веб-API является то, что метод ASP.NET Core является async ( `BindModelAsync` ), а `BindingModelContext` вместо двух параметров, таких как требуемая версия веб-API, требуется только один параметр.</span><span class="sxs-lookup"><span data-stu-id="f385f-149">The main differences between ASP.NET Core's `IModelBinder` interface and Web API's is that the ASP.NET Core method is async (`BindModelAsync`) and it only requires a single `BindingModelContext` parameter instead of two parameters like Web API's version required.</span></span> <span data-ttu-id="f385f-150">В ASP.NET Core можно использовать `[ModelBinder]` атрибут для отдельных параметров метода действия или связанных с ними типов.</span><span class="sxs-lookup"><span data-stu-id="f385f-150">In ASP.NET Core, you can use a `[ModelBinder]` attribute on individual action method parameters or their associated types.</span></span> <span data-ttu-id="f385f-151">Вы также можете создать `ModelBinderProvider` , который будет использоваться глобально в приложении, где это необходимо.</span><span class="sxs-lookup"><span data-stu-id="f385f-151">You can also create a `ModelBinderProvider` that will be used globally within the app where appropriate.</span></span> <span data-ttu-id="f385f-152">Чтобы настроить такой поставщик, добавьте код `Startup` в `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="f385f-152">To configure such a provider, you would add code to `Startup` in `ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a><span data-ttu-id="f385f-153">Модули форматирования мультимедиа</span><span class="sxs-lookup"><span data-stu-id="f385f-153">Media formatters</span></span>

<span data-ttu-id="f385f-154">Веб-API ASP.NET поддерживает несколько форматов мультимедиа и может быть расширен с помощью пользовательских модулей форматирования мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="f385f-154">ASP.NET Web API supports multiple media formats and can be extended by using custom media formatters.</span></span> <span data-ttu-id="f385f-155">Документация описывает [Пример модуля форматирования мультимедиа CSV](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) , который можно использовать для отправки данных в формате значений с разделителями-запятыми.</span><span class="sxs-lookup"><span data-stu-id="f385f-155">The docs describe an [example CSV Media Formatter](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) that can be used to send data in a comma-separated value format.</span></span> <span data-ttu-id="f385f-156">Если приложение веб-API использует пользовательские модули форматирования мультимедиа, их необходимо преобразовать в [ASP.NET Core пользовательские модули форматирования](/aspnet/core/web-api/advanced/custom-formatters).</span><span class="sxs-lookup"><span data-stu-id="f385f-156">If your Web API app uses custom media formatters, you'll need to convert them to [ASP.NET Core custom formatters](/aspnet/core/web-api/advanced/custom-formatters).</span></span>

<span data-ttu-id="f385f-157">Чтобы создать пользовательский модуль форматирования в веб-API 2, вы наследуете от соответствующего базового класса, а затем добавили модуль форматирования в конвейер веб-API с помощью `HttpConfiguration` объекта:</span><span class="sxs-lookup"><span data-stu-id="f385f-157">To create a custom formatter in Web API 2, you inherited from an appropriate base class and then added the formatter to the Web API pipeline using the `HttpConfiguration` object:</span></span>

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter());
}
```

<span data-ttu-id="f385f-158">В ASP.NET Core процесс аналогичен.</span><span class="sxs-lookup"><span data-stu-id="f385f-158">In ASP.NET Core, the process is similar.</span></span> <span data-ttu-id="f385f-159">ASP.NET Core поддерживает модули форматирования ввода (используемые привязкой модели) и модули форматирования выходных данных (используются для форматирования ответов).</span><span class="sxs-lookup"><span data-stu-id="f385f-159">ASP.NET Core supports both input formatters (used by model binding) and output formatters (used to format responses).</span></span> <span data-ttu-id="f385f-160">Добавление пользовательского модуля форматирования для вывода ответов с особым способом включает наследование от соответствующего базового класса и Добавление модуля форматирования в MVC в `Startup` :</span><span class="sxs-lookup"><span data-stu-id="f385f-160">Adding a custom formatter to output responses in a specific way involves inheriting from an appropriate base class and adding the formatter to MVC in `Startup`:</span></span>

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

<span data-ttu-id="f385f-161">Полный список базовых классов можно найти в пространстве имен [Microsoft. AspNetCore. MVC. Formatter](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) .</span><span class="sxs-lookup"><span data-stu-id="f385f-161">You'll find a complete list of base classes in the [Microsoft.AspNetCore.Mvc.Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) namespace.</span></span>

<span data-ttu-id="f385f-162">Шаги для миграции из модуля форматирования веб-API в ASP.NET Core модуль форматирования MVC:</span><span class="sxs-lookup"><span data-stu-id="f385f-162">The steps to migrate from a Web API formatter to an ASP.NET Core MVC formatter are:</span></span>

1. <span data-ttu-id="f385f-163">Найдите соответствующий базовый класс для нового модуля форматирования.</span><span class="sxs-lookup"><span data-stu-id="f385f-163">Identify an appropriate base class for the new formatter.</span></span>
1. <span data-ttu-id="f385f-164">Создайте новый экземпляр базового класса и реализуйте его необходимые методы.</span><span class="sxs-lookup"><span data-stu-id="f385f-164">Create a new instance of the base class and implement its required methods.</span></span>
1. <span data-ttu-id="f385f-165">Скопируйте функции из модуля форматирования веб-API в новую реализацию.</span><span class="sxs-lookup"><span data-stu-id="f385f-165">Copy over the functionality from the Web API formatter to the new implementation.</span></span>
1. <span data-ttu-id="f385f-166">Настройте MVC в методе приложения ASP.NET Core, `ConfigureServices` чтобы использовать новый модуль форматирования.</span><span class="sxs-lookup"><span data-stu-id="f385f-166">Configure MVC in the ASP.NET Core App's `ConfigureServices` method to use the new formatter.</span></span>

## <a name="custom-filters"></a><span data-ttu-id="f385f-167">Настраиваемые фильтры</span><span class="sxs-lookup"><span data-stu-id="f385f-167">Custom filters</span></span>

<span data-ttu-id="f385f-168">Фильтры используются в ASP.NET Core приложениях для выполнения кода до и (или) после определенных этапов в конвейере обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="f385f-168">Filters are used in ASP.NET Core apps to execute code before and/or after certain stages in the request processing pipeline.</span></span> <span data-ttu-id="f385f-169">ASP.NET MVC и веб-API также используют фильтры во многом так же, но сведения различаются.</span><span class="sxs-lookup"><span data-stu-id="f385f-169">ASP.NET MVC and Web API also use filters in much the same way, but the details vary.</span></span> <span data-ttu-id="f385f-170">Например, [ASP.NET MVC поддерживает четыре типа фильтров](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters).</span><span class="sxs-lookup"><span data-stu-id="f385f-170">For instance, [ASP.NET MVC supports four kinds of filters](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters).</span></span> <span data-ttu-id="f385f-171">Веб-API ASP.NET 2 поддерживает аналогичные фильтры, а как MVC, так и веб-API включали атрибуты для [переопределения фильтров](/dotnet/api/system.web.mvc.filters.ioverridefilter).</span><span class="sxs-lookup"><span data-stu-id="f385f-171">ASP.NET Web API 2 supports similar filters, and both MVC and Web API included attributes to [override filters](/dotnet/api/system.web.mvc.filters.ioverridefilter).</span></span>

<span data-ttu-id="f385f-172">Наиболее распространенным фильтром, используемым в приложениях ASP.NET MVC и веб-API, является фильтр действий, определяемый [интерфейсом иактионфилтер](/dotnet/api/system.web.mvc.iactionfilter).</span><span class="sxs-lookup"><span data-stu-id="f385f-172">The most common filter used in ASP.NET MVC and Web API apps is the action filter, which is defined by an [IActionFilter interface](/dotnet/api/system.web.mvc.iactionfilter).</span></span> <span data-ttu-id="f385f-173">Этот интерфейс предоставляет методы для Before ( `OnActionExecuting` ) и After ( `OnActionExecuted` ), которые можно использовать для выполнения кода до и (или) после выполнения действия, как указано для каждого метода.</span><span class="sxs-lookup"><span data-stu-id="f385f-173">This interface provides methods for before (`OnActionExecuting`) and after (`OnActionExecuted`) which can be used to execute code before and/or after an action executes, as noted for each method.</span></span>

<span data-ttu-id="f385f-174">ASP.NET Core поддерживает фильтры, а его унификация MVC и веб-API означает, что существует только один подход к их реализации.</span><span class="sxs-lookup"><span data-stu-id="f385f-174">ASP.NET Core continues to support filters, and its unification of MVC and Web API means there is only one approach to their implementation.</span></span> <span data-ttu-id="f385f-175">[Документация включает подробное описание пяти (5) видов фильтров, встроенных в ASP.NET Core MVC](/aspnet/core/mvc/controllers/filters#filter-types).</span><span class="sxs-lookup"><span data-stu-id="f385f-175">The [docs include detailed coverage of the five (5) kinds of filters built into ASP.NET Core MVC](/aspnet/core/mvc/controllers/filters#filter-types).</span></span> <span data-ttu-id="f385f-176">Все варианты фильтров, поддерживаемые в ASP.NET MVC и веб-API ASP.NET имеют связанные версии в ASP.NET Core, поэтому миграция, как правило, заключается в определении соответствующего интерфейса и (или) базового класса и переносе кода.</span><span class="sxs-lookup"><span data-stu-id="f385f-176">All of the filter variants supported in ASP.NET MVC and ASP.NET Web API have associated versions in ASP.NET Core, so migration is generally just a matter of identifying the appropriate interface and/or base class and migrating the code over.</span></span>

<span data-ttu-id="f385f-177">Помимо синхронных интерфейсов ASP.NET Core также предоставляет асинхронные интерфейсы, такие как, которые `IAsyncActionFilter` предоставляют один асинхронный метод, который можно использовать для включения кода для выполнения как до, так и после действия, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="f385f-177">In addition to the synchronous interfaces, ASP.NET Core also provides async interfaces like `IAsyncActionFilter` which provide a single async method that can be used to incorporate code to run both before and after the action, as shown:</span></span>

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

<span data-ttu-id="f385f-178">При переносе асинхронного кода (или кода, который должен быть асинхронным) командам следует рассмотреть возможность использования встроенных асинхронных типов, предоставляемых для этой цели.</span><span class="sxs-lookup"><span data-stu-id="f385f-178">When migrating async code (or code that should be async), teams should consider leveraging the built in async types that are provided for this purpose.</span></span>

<span data-ttu-id="f385f-179">Большинство приложений ASP.NET MVC и веб-API не используют большое количество настраиваемых фильтров.</span><span class="sxs-lookup"><span data-stu-id="f385f-179">Most ASP.NET MVC and Web API apps do not use a large number of custom filters.</span></span> <span data-ttu-id="f385f-180">Поскольку подход к фильтрам в ASP.NET Core MVC тесно согласуется с фильтрами в ASP.NET MVC и веб-API, миграция пользовательских фильтров обычно довольно проста.</span><span class="sxs-lookup"><span data-stu-id="f385f-180">Since the approach to filters in ASP.NET Core MVC is closely aligned with filters in ASP.NET MVC and Web API, the migration of custom filters is generally fairly straightforward.</span></span> <span data-ttu-id="f385f-181">Не забудьте прочитать подробную документацию по фильтрам в документации по ASP.NET Core и, убедившись, что вы хорошо понимаете их, переносите логику из старой системы в фильтры новой системы.</span><span class="sxs-lookup"><span data-stu-id="f385f-181">Be sure to read the detailed documentation on filters in ASP.NET Core's docs, and once you're sure you have a good understanding of them, port the logic from the old system to the new system's filters.</span></span>

## <a name="route-constraints"></a><span data-ttu-id="f385f-182">Ограничения маршрута</span><span class="sxs-lookup"><span data-stu-id="f385f-182">Route constraints</span></span>

<span data-ttu-id="f385f-183">ASP.NET Core использует ограничения маршрута, чтобы обеспечить правильную маршрутизацию запросов для маршрутизации запроса.</span><span class="sxs-lookup"><span data-stu-id="f385f-183">ASP.NET Core uses route constraints to help ensure requests are routed properly to route a request.</span></span> <span data-ttu-id="f385f-184">[ASP.NET Core поддерживает большое количество различных ограничений маршрута для этой цели]/АСПнет/коре/фундаменталс/раутинг # Route-Constraint-Reference).</span><span class="sxs-lookup"><span data-stu-id="f385f-184">[ASP.NET Core supports a large number of different route constraints for this purpose]/aspnet/core/fundamentals/routing#route-constraint-reference).</span></span> <span data-ttu-id="f385f-185">Ограничения маршрутов могут применяться в таблице маршрутов, но большинство приложений, созданных с помощью ASP.NET MVC 5 и/или [веб-API ASP.NET 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) , используют встроенные ограничения маршрута, применяемые к маршрутам атрибутов.</span><span class="sxs-lookup"><span data-stu-id="f385f-185">Route constraints can be applied in the route table, but most apps built with ASP.NET MVC 5 and/or [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) use inline route constraints applied to attribute routes.</span></span> <span data-ttu-id="f385f-186">Встроенные ограничения маршрутов используют следующий формат:</span><span class="sxs-lookup"><span data-stu-id="f385f-186">Inline route constraints use a format like this one:</span></span>

```csharp
[Route("/customer/{id:int}")]
```

<span data-ttu-id="f385f-187">`:int` `id` Параметр после параметра Route ограничивает значение в соответствии с `int` типом.</span><span class="sxs-lookup"><span data-stu-id="f385f-187">The `:int` after the `id` route parameter constrains the value to match the the `int` type.</span></span> <span data-ttu-id="f385f-188">Одно из преимуществ использования ограничений маршрутов заключается в том, что они позволяют использовать два одинаковых маршрута, где параметры отличаются только их типом.</span><span class="sxs-lookup"><span data-stu-id="f385f-188">One benefit of using route constraints is that they allow for two otherwise-identical routes to exist where the parameters differ only by their type.</span></span> <span data-ttu-id="f385f-189">Это позволяет аналогично [перегружать методы](../../standard/design-guidelines/member-overloading.md) маршрутов на основе только типа параметра.</span><span class="sxs-lookup"><span data-stu-id="f385f-189">This allows for the equivalent of [method overloading](../../standard/design-guidelines/member-overloading.md) of routes based solely on parameter type.</span></span>

<span data-ttu-id="f385f-190">Набор ограничений маршрута, их синтаксис и использование очень схожи между всеми тремя подходами.</span><span class="sxs-lookup"><span data-stu-id="f385f-190">The set of route constraints, their syntax, and usage is very similar between all three approaches.</span></span> <span data-ttu-id="f385f-191">Пользовательские ограничения маршрута довольно редки в клиентских приложениях.</span><span class="sxs-lookup"><span data-stu-id="f385f-191">Custom route constraints are fairly rare in customer applications.</span></span> <span data-ttu-id="f385f-192">Если приложение использует настраиваемое ограничение маршрута и необходимо перенести в ASP.NET Core, в документацию включены примеры, демонстрирующие [Создание настраиваемых ограничений маршрута в ASP.NET Core](/aspnet/core/fundamentals/routing#custom-route-constraints).</span><span class="sxs-lookup"><span data-stu-id="f385f-192">If your app uses a custom route constraint and needs to port to ASP.NET Core, the docs include examples showing [how to create custom route constraints in ASP.NET Core](/aspnet/core/fundamentals/routing#custom-route-constraints).</span></span> <span data-ttu-id="f385f-193">По сути, все, что необходимо, это реализовать `IRouteConstraint` и его `Match` метод, а затем добавить пользовательское ограничение при настройке маршрутизации для приложения:</span><span class="sxs-lookup"><span data-stu-id="f385f-193">Essentially all that's required is to implement `IRouteConstraint` and its `Match` method, and then add the custom constraint when configuring routing for the app:</span></span>

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

<span data-ttu-id="f385f-194">Это очень похоже на то, как пользовательские ограничения используются в веб-API ASP.NET, который использует `IHttpRouteConstraint` и настраивает его с помощью распознавателя и вызова `HttpConfiguration.MapHttpAttributeRoutes` :</span><span class="sxs-lookup"><span data-stu-id="f385f-194">This is very similar to how custom constraints are used in ASP.NET Web API, which uses `IHttpRouteConstraint` and configures it using a resolver and a call to `HttpConfiguration.MapHttpAttributeRoutes`:</span></span>

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

<span data-ttu-id="f385f-195">ASP.NET MVC 5 следует очень похожим подходом, используя `IRouteConstraint` для его имени интерфейса и настроив ограничение как часть конфигурации маршрута:</span><span class="sxs-lookup"><span data-stu-id="f385f-195">ASP.NET MVC 5 follows a very similar approach, using `IRouteConstraint` for its interface name and configuring the constraint as part of route configuration:</span></span>

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

<span data-ttu-id="f385f-196">Миграция использования ограничения маршрута, а также пользовательских ограничений маршрута к ASP.NET Core обычно очень проста.</span><span class="sxs-lookup"><span data-stu-id="f385f-196">Migrating route constraint usage as well as custom route constraints to ASP.NET Core is typically very straightforward.</span></span>

## <a name="custom-route-handlers"></a><span data-ttu-id="f385f-197">Пользовательские обработчики маршрутов</span><span class="sxs-lookup"><span data-stu-id="f385f-197">Custom route handlers</span></span>

<span data-ttu-id="f385f-198">Еще одна довольно сложная функция ASP.NET MVC 5 — это обработчики маршрутов.</span><span class="sxs-lookup"><span data-stu-id="f385f-198">Another fairly advanced feature of ASP.NET MVC 5 is route handlers.</span></span> <span data-ttu-id="f385f-199">Пользовательские обработчики маршрутов реализуют `IRouteHandler` , в том числе один метод, возвращающий `IHttpHandler` для запроса на предоставление.</span><span class="sxs-lookup"><span data-stu-id="f385f-199">Custom route handlers implement `IRouteHandler`, which includes a single method that returns an `IHttpHandler` for a give request.</span></span> <span data-ttu-id="f385f-200">`IHttpHandler`, В свою очередь, предоставляет `IsReusable` свойство и единственный `ProcessRequest` метод.</span><span class="sxs-lookup"><span data-stu-id="f385f-200">The `IHttpHandler`, in turn, exposes an `IsReusable` property and a single `ProcessRequest` method.</span></span> <span data-ttu-id="f385f-201">В ASP.NET MVC 5 можно настроить определенный маршрут в таблице маршрутов для использования настраиваемого обработчика:</span><span class="sxs-lookup"><span data-stu-id="f385f-201">In ASP.NET MVC 5, you can configure a particular route in the route table to use your custom handler:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

<span data-ttu-id="f385f-202">Чтобы перенести пользовательские обработчики маршрутов из ASP.NET MVC 5 в ASP.NET Core, можно либо использовать фильтр (например, фильтр действий), либо пользовательский [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) .</span><span class="sxs-lookup"><span data-stu-id="f385f-202">To migrate custom route handlers from ASP.NET MVC 5 to ASP.NET Core, you can either use a filter (such as an action filter) or a custom [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter).</span></span> <span data-ttu-id="f385f-203">Подход фильтра относительно прост, и его можно добавить в качестве глобального фильтра при добавлении MVC `ConfigureServices` в в *Startup. CS*.</span><span class="sxs-lookup"><span data-stu-id="f385f-203">The filter approach is relatively straightforward, and can be added as a global filter when MVC is added to `ConfigureServices` in *Startup.cs*.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

<span data-ttu-id="f385f-204">`IRouter`Параметр требует реализации `RouteAsync` методов интерфейса и `GetVirtualPath` .</span><span class="sxs-lookup"><span data-stu-id="f385f-204">The `IRouter` option requires implementing the interface's `RouteAsync` and `GetVirtualPath` methods.</span></span> <span data-ttu-id="f385f-205">Пользовательский маршрутизатор добавляется в конвейер запросов в `Configure` методе в *Startup. CS*.</span><span class="sxs-lookup"><span data-stu-id="f385f-205">The custom router is added to the request pipeline in the `Configure` method in *Startup.cs*.</span></span>

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

<span data-ttu-id="f385f-206">В веб-API ASP.NET эти обработчики называются [пользовательскими обработчиками сообщений](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers), а не *обработчиками маршрутов*.</span><span class="sxs-lookup"><span data-stu-id="f385f-206">In ASP.NET Web API, these handlers are referred to as [custom message handlers](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers), rather than *route handlers*.</span></span> <span data-ttu-id="f385f-207">Обработчики сообщений должны быть производными от класса `DelegatingHandler` и переопределять его `SendAsync` метод.</span><span class="sxs-lookup"><span data-stu-id="f385f-207">Message handlers must derive from `DelegatingHandler` and override its `SendAsync` method.</span></span> <span data-ttu-id="f385f-208">Обработчики сообщений можно объединить в цепочки, чтобы сформировать конвейер так, что очень похоже на ASP.NET Core по промежуточного слоя и его конвейер запросов.</span><span class="sxs-lookup"><span data-stu-id="f385f-208">Message handlers can be chained together to form a pipeline in a fashion that is very similar to ASP.NET Core middleware and its request pipeline.</span></span>

<span data-ttu-id="f385f-209">ASP.NET Core не имеет `DelegatingHandler` типа или отдельного конвейера обработчика сообщений.</span><span class="sxs-lookup"><span data-stu-id="f385f-209">ASP.NET Core has no `DelegatingHandler` type or separate message handler pipeline.</span></span> <span data-ttu-id="f385f-210">Вместо этого такие обработчики следует перенести с помощью глобальных фильтров, пользовательских `IRouter` экземпляров (см. выше) или пользовательского по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="f385f-210">Instead, such handlers should be migrated using global filters, custom `IRouter` instances (see above), or custom middleware.</span></span> <span data-ttu-id="f385f-211">ASP.NET Core фильтры и `IRouter` типы MVC имеют преимущество встроенного доступа к конструкциям MVC, таким как контроллеры и действия, в то время как по промежуточного слоя не имеет связей с MVC.</span><span class="sxs-lookup"><span data-stu-id="f385f-211">ASP.NET Core MVC filters and `IRouter` types have the advantage of having built-in access to MVC constructs like controllers and actions, while middleware is a lower level approach that has no ties to MVC.</span></span> <span data-ttu-id="f385f-212">Это делает его более гибким, но также требует дополнительных усилий, если требуется доступ к компонентам MVC.</span><span class="sxs-lookup"><span data-stu-id="f385f-212">This makes it more flexible but also requires more effort if you need to access MVC components.</span></span>

## <a name="cors-support"></a><span data-ttu-id="f385f-213">Поддержка CORS</span><span class="sxs-lookup"><span data-stu-id="f385f-213">CORS support</span></span>

<span data-ttu-id="f385f-214">CORS или совместное использование ресурсов в разных источниках — это стандарт W3C, позволяющий серверам принимать запросы, которые не поступают от ответов, которые они обслуживают.</span><span class="sxs-lookup"><span data-stu-id="f385f-214">CORS, or Cross-Origin Resource Sharing, is a W3C standard that allows servers to accept requests that don't originate from responses they've served.</span></span> <span data-ttu-id="f385f-215">ASP.NET MVC 5 и веб-API ASP.NET 2 поддерживают CORS различными способами.</span><span class="sxs-lookup"><span data-stu-id="f385f-215">ASP.NET MVC 5 and ASP.NET Web API 2 support CORS in different ways.</span></span> <span data-ttu-id="f385f-216">Самый простой способ включить поддержку CORS в ASP.NET MVC 5 — это фильтр действий, подобный этому:</span><span class="sxs-lookup"><span data-stu-id="f385f-216">The simplest way to enable CORS support in ASP.NET MVC 5 is with an action filter like this one:</span></span>

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

<span data-ttu-id="f385f-217">Веб-API ASP.NET также может использовать такой фильтр, но он имеет [встроенную поддержку включения CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) :</span><span class="sxs-lookup"><span data-stu-id="f385f-217">ASP.NET Web API can also use such a filter, but it has [built-in support for enabling CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) as well:</span></span>

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

<span data-ttu-id="f385f-218">После добавления можно настроить разрешенные источники, заголовки и методы с помощью `EnableCors` атрибута следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f385f-218">Once this is added, you can configure allowed origins, headers, and methods using the `EnableCors` attribute, like so:</span></span>

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

<span data-ttu-id="f385f-219">Прежде чем переносить реализацию CORS из ASP.NET MVC 5 или веб-API ASP.NET 2, ознакомьтесь с принципами [работы CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) и создайте некоторые автоматические тесты, демонстрирующие, что CORS работает должным образом в текущей системе.</span><span class="sxs-lookup"><span data-stu-id="f385f-219">Before migrating your CORS implementation from ASP.NET MVC 5 or ASP.NET Web API 2, be sure to review [how CORS works](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) and create some automated tests that demonstrate CORS is working as expected in your current system.</span></span>

<span data-ttu-id="f385f-220">В ASP.NET Core существует три встроенных способа включения CORS:</span><span class="sxs-lookup"><span data-stu-id="f385f-220">In ASP.NET Core, there are three built-in ways to enable CORS:</span></span>

- <span data-ttu-id="f385f-221">[Настроено с помощью политики](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware) в `ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="f385f-221">[Configured via policy](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware) in `ConfigureServices`</span></span>
- <span data-ttu-id="f385f-222">Включено с [маршрутизацией конечных точек](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)</span><span class="sxs-lookup"><span data-stu-id="f385f-222">Enabled with [endpoint routing](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)</span></span>
- <span data-ttu-id="f385f-223">Включено с [ `EnableCors` атрибутом](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)</span><span class="sxs-lookup"><span data-stu-id="f385f-223">Enabled with the [`EnableCors` attribute](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)</span></span>

<span data-ttu-id="f385f-224">Каждый из этих подходов подробно описан в документах, которые связаны с приведенными выше параметрами.</span><span class="sxs-lookup"><span data-stu-id="f385f-224">Each of these approaches is covered in detail in the docs, which are linked from the above options.</span></span> <span data-ttu-id="f385f-225">Выбор одного из них во многом зависит от того, как существующее приложение поддерживает CORS.</span><span class="sxs-lookup"><span data-stu-id="f385f-225">Which one you choose will largely depend on how your existing app supports CORS.</span></span> <span data-ttu-id="f385f-226">Если приложение использует атрибуты, вы, вероятно, можете выполнить миграцию, чтобы использовать `EnableCors` атрибут наиболее просто.</span><span class="sxs-lookup"><span data-stu-id="f385f-226">If the app uses attributes, you can probably migrate to use the `EnableCors` attribute most easily.</span></span> <span data-ttu-id="f385f-227">Если приложение использует фильтры, можно продолжать использовать этот подход (хотя это не стандартный подход, используемый в ASP.NET Core), или выполнить миграцию для использования атрибутов или политик.</span><span class="sxs-lookup"><span data-stu-id="f385f-227">If your app uses filters, you could continue using that approach (though it's not the typical approach used in ASP.NET Core), or migrate to use attributes or policies.</span></span> <span data-ttu-id="f385f-228">Маршрутизация конечных точек — это относительно новая функция, появившаяся в ASP.NET Core 3 и не имеющая близкого аналога в приложениях ASP.NET MVC 5 или веб-API ASP.NET 2.</span><span class="sxs-lookup"><span data-stu-id="f385f-228">Endpoint routing is a relatively new feature introduced with ASP.NET Core 3 and as such it doesn't have a close analog in ASP.NET MVC 5 or ASP.NET Web API 2 apps.</span></span>

## <a name="custom-areas"></a><span data-ttu-id="f385f-229">Пользовательские области</span><span class="sxs-lookup"><span data-stu-id="f385f-229">Custom areas</span></span>

<span data-ttu-id="f385f-230">Многие приложения ASP.NET MVC используют области для организации проекта.</span><span class="sxs-lookup"><span data-stu-id="f385f-230">Many ASP.NET MVC apps use Areas to organize the project.</span></span> <span data-ttu-id="f385f-231">Области обычно находятся в корне проекта в папке *областей* и должны быть зарегистрированы при запуске приложения, обычно в `Application_Start()` :</span><span class="sxs-lookup"><span data-stu-id="f385f-231">Areas typically reside in the root of the project in an *Areas* folder, and must be registered when the application starts, typically in `Application_Start()`:</span></span>

```csharp
AreaRegistration.RegisterAllAreas();
```

<span data-ttu-id="f385f-232">Альтернативой регистрации всех областей при запуске является использование `RouteArea` атрибута на отдельных контроллерах:</span><span class="sxs-lookup"><span data-stu-id="f385f-232">An alternative to registering all areas in startup is to use the `RouteArea` attribute on individual controllers:</span></span>

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

<span data-ttu-id="f385f-233">При использовании областей дополнительные аргументы передаются в вспомогательные методы HTML для создания ссылок на действия в различных областях:</span><span class="sxs-lookup"><span data-stu-id="f385f-233">When using Areas, additional arguments are passed into HTML helper methods to generate links to actions in different areas:</span></span>

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

<span data-ttu-id="f385f-234">Веб-API ASP.NET приложения обычно не используют области явным образом, так как их контроллеры можно поместить в любую папку в проекте.</span><span class="sxs-lookup"><span data-stu-id="f385f-234">ASP.NET Web API apps don't typically use areas explicitly, since their controllers can be placed in any folder in the project.</span></span> <span data-ttu-id="f385f-235">Команды могут использовать любую структуру папок для Организации контроллеров API.</span><span class="sxs-lookup"><span data-stu-id="f385f-235">Teams can use any folder structure they like to organize their API controllers.</span></span>

<span data-ttu-id="f385f-236">[Области](/aspnet/core/mvc/controllers/areas) поддерживаются в ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="f385f-236">[Areas](/aspnet/core/mvc/controllers/areas) are supported in ASP.NET Core MVC.</span></span> <span data-ttu-id="f385f-237">Используемый подход практически идентичен использованию областей в ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="f385f-237">The approach used is nearly identical to the use of areas in ASP.NET MVC 5.</span></span> <span data-ttu-id="f385f-238">Разработчики, выполняющие миграцию кода с помощью областей, должны учитывать следующие отличия.</span><span class="sxs-lookup"><span data-stu-id="f385f-238">Developers migrating code using areas should keep in mind the following differences:</span></span>

- <span data-ttu-id="f385f-239">`AreaRegistration.RegisterAllAreas` не используется в ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="f385f-239">`AreaRegistration.RegisterAllAreas` is not used in ASP.NET Core MVC</span></span>
- <span data-ttu-id="f385f-240">Области применяются с помощью `[Area("name")]` атрибута (не `RouteArea` как в ASP.NET MVC 5).</span><span class="sxs-lookup"><span data-stu-id="f385f-240">Areas are applied using the `[Area("name")]` attribute (not `RouteArea` as in ASP.NET MVC 5)</span></span>
- <span data-ttu-id="f385f-241">При необходимости области можно добавить в шаблоны таблицы маршрутов (или же они могут использовать маршрутизацию атрибутов).</span><span class="sxs-lookup"><span data-stu-id="f385f-241">Areas can be added to the route table templates, if desired (or they can use attribute routing)</span></span>

<span data-ttu-id="f385f-242">Чтобы добавить поддержку областей в таблицу маршрутов в ASP.NET Core MVC, в `Configure` разделе *Startup. CS* необходимо добавить следующее:</span><span class="sxs-lookup"><span data-stu-id="f385f-242">To add area support to the route table in ASP.NET Core MVC, you would add the following in `Configure` in *Startup.cs*:</span></span>

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

<span data-ttu-id="f385f-243">Области можно также использовать с маршрутизацией атрибутов, используя `{area}` ключевое слово в определении маршрута (это одно из нескольких [зарезервированных имен маршрутизации](/aspnet/core/mvc/controllers/routing#reserved-routing-names) , которые можно использовать с шаблонами маршрутов).</span><span class="sxs-lookup"><span data-stu-id="f385f-243">Areas can also be used with attribute routing, using the `{area}` keyword in the route definition (it's one of several [reserved routing names](/aspnet/core/mvc/controllers/routing#reserved-routing-names) that can be used with route templates).</span></span>

<span data-ttu-id="f385f-244">Вспомогательные функции тегов поддерживают области с `asp-area` атрибутом, который можно использовать для создания ссылок в представлениях и страницах Razor.</span><span class="sxs-lookup"><span data-stu-id="f385f-244">Tag helpers support areas with the `asp-area` attribute, which can be used to generate links in Razor views and pages:</span></span>

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

<span data-ttu-id="f385f-245">Если выполняется миграция на Razor Pages необходимо использовать папку *областей* в папке *pages* .</span><span class="sxs-lookup"><span data-stu-id="f385f-245">If you're migrating to Razor Pages you will need to use an *Areas* folder in your *Pages* folder.</span></span> <span data-ttu-id="f385f-246">Дополнительные сведения см. [в разделе области с Razor Pages](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages).</span><span class="sxs-lookup"><span data-stu-id="f385f-246">For more information, see [Areas with Razor Pages](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages).</span></span>

<span data-ttu-id="f385f-247">Помимо приведенных выше рекомендаций, команды должны проанализировать, [как маршрутизация в ASP.NET Core работает с областями](/aspnet/core/mvc/controllers/routing#areas) в рамках процесса планирования миграции.</span><span class="sxs-lookup"><span data-stu-id="f385f-247">In addition to the above guidance, teams should review [how routing in ASP.NET Core works with areas](/aspnet/core/mvc/controllers/routing#areas) as part of their migration planning process.</span></span>

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a><span data-ttu-id="f385f-248">Интеграционные тесты для ASP.NET MVC и веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f385f-248">Integration tests for ASP.NET MVC and ASP.NET Web API</span></span>

<span data-ttu-id="f385f-249">Тесты интеграции — это автоматические тесты, которые проверяют, правильно ли работают несколько различных частей приложения.</span><span class="sxs-lookup"><span data-stu-id="f385f-249">Integration tests are automated tests that verify several different parts of an app work together correctly.</span></span> <span data-ttu-id="f385f-250">Написание интеграционных тестов для ASP.NET MVC и веб-API ASP.NET обычно включало развертывание приложения на реальном веб-сервере, например локальный экземпляр IIS или IIS Express, а затем запросы к этому размещенному приложению с помощью HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="f385f-250">Writing integration tests for ASP.NET MVC and ASP.NET Web API usually involved deploying the app to a real web server, such as a local instance of IIS or IIS Express, and then making requests to this hosted application using an HTTP client.</span></span> <span data-ttu-id="f385f-251">Некоторые из этих тестов могут взаимодействовать с пользовательским интерфейсом на стороне клиента с помощью средств автоматизации браузера, таких как [Selenium](https://www.selenium.dev/), хотя часто эти тесты называются *тестами пользовательского интерфейса* , а не тестами интеграции.</span><span class="sxs-lookup"><span data-stu-id="f385f-251">Some of these tests may interact with the client-side user interface using browser automation tools like [Selenium](https://www.selenium.dev/), though often these are referred to as *UI tests* rather than integration tests.</span></span>

<span data-ttu-id="f385f-252">Если перенесенное приложение использует то же поведение, что и исходная версия, любая существующая технология, используемая группой для выполнения тестов интеграции (и тестов пользовательского интерфейса), должна продолжать работать точно так же, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="f385f-252">If your migrated app shares the same behavior as its original version, whatever existing technology the team is using to perform integration tests (and UI tests) should continue to work just as it did before.</span></span> <span data-ttu-id="f385f-253">Обычно эти тесты не отличаются от базовой технологии, используемой для размещения тестируемого приложения, и взаимодействуют с ним только через HTTP-запросы.</span><span class="sxs-lookup"><span data-stu-id="f385f-253">These tests are usually indifferent to the underlying technology used to host the app they're testing, and interact with it only through HTTP requests.</span></span> <span data-ttu-id="f385f-254">То, что может стать более сложной задачей, заключается в том, как тесты взаимодействуют с приложением для получения известного хорошего состояния перед каждым тестом.</span><span class="sxs-lookup"><span data-stu-id="f385f-254">Where things may get more challenging is with how the tests interact with the app to get it into a known good state prior to each test.</span></span> <span data-ttu-id="f385f-255">Это может потребовать некоторых усилий при миграции, так как настройка и запуск значительно отличаются в ASP.NET Core по сравнению с ASP.NET MVC или веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f385f-255">This may require some migration effort, since configuration and startup are significantly different in ASP.NET Core compared to ASP.NET MVC or ASP.NET Web API.</span></span>

<span data-ttu-id="f385f-256">Группы должны строго рассмотреть миграцию своих интеграционных тестов для использования [встроенной поддержки тестирования интеграции ASP.NET Core](/aspnet/core/test/integration-tests) .</span><span class="sxs-lookup"><span data-stu-id="f385f-256">Teams should strongly consider migrating their integration tests to use [ASP.NET Core's built-in integration testing](/aspnet/core/test/integration-tests) support.</span></span> <span data-ttu-id="f385f-257">В ASP.NET Core приложения можно протестировать, развернув их в `TestHost` , который настраивается с помощью `WebApplicationFactory` .</span><span class="sxs-lookup"><span data-stu-id="f385f-257">In ASP.NET Core, apps can be tested by deploying them to a `TestHost`, which is configured using a `WebApplicationFactory`.</span></span> <span data-ttu-id="f385f-258">Для размещения приложения на тестирование требуется небольшое количество настроек, но после этого создание отдельных тестов интеграции очень просто.</span><span class="sxs-lookup"><span data-stu-id="f385f-258">There's a little bit of setup required to host the app for testing, but once this is in place, creating individual integration tests is very straightforward.</span></span>

<span data-ttu-id="f385f-259">Одной из лучших функций поддержки тестирования интеграции ASP.NET Core является то, что приложение размещается в памяти.</span><span class="sxs-lookup"><span data-stu-id="f385f-259">One of the best features of ASP.NET Core's integration testing support is that the app is hosted in memory.</span></span> <span data-ttu-id="f385f-260">Нет необходимости настраивать реальный сервер для размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="f385f-260">There's no need to configure a real webserver to host the app.</span></span> <span data-ttu-id="f385f-261">Нет необходимости использовать средство автоматизации браузера (если вы тестируете только ASP.NET Core и не поведение на стороне клиента).</span><span class="sxs-lookup"><span data-stu-id="f385f-261">There's no need to use a browser automation tool (if you're only testing ASP.NET Core and not client-side behavior).</span></span> <span data-ttu-id="f385f-262">Многие проблемы, которые могут возникнуть при попытке использовать реальный веб-сервер для автоматизированных тестов интеграции, например проблемы с брандмауэром или проблемы запуска и прекращения процесса, устраняются при таком подходе.</span><span class="sxs-lookup"><span data-stu-id="f385f-262">Many of the problems that can be encountered when trying to use a real web server for automated integration tests, such as firewall issues or process start/stop issues, are eliminated with this approach.</span></span> <span data-ttu-id="f385f-263">Поскольку все запросы выполняются в памяти без требования к сети, тесты также выполняются гораздо быстрее, чем тесты, которые должны настроить отдельный сервер и взаимодействовать с ним по сети (даже если он работает на том же компьютере).</span><span class="sxs-lookup"><span data-stu-id="f385f-263">Since the requests are all made in memory with no network requirement, the tests also tend to run much faster than tests that must set up a separate webserver and communicate with it over the network (even if it's running on the same machine).</span></span>

<span data-ttu-id="f385f-264">Ниже приведен пример ASP.NET Core интеграционный тест (иногда называемый *функциональными тестами* , который отличает их от тестов интеграции более низкого уровня) из [эталонного приложения eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb):</span><span class="sxs-lookup"><span data-stu-id="f385f-264">Below you can see an example ASP.NET Core integration test (sometimes referred to as *functional tests* to distinguish them from lower-level integration tests) from the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb):</span></span>

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

<span data-ttu-id="f385f-265">Если переносимое приложение не содержит тестов интеграции, процесс миграции может быть отличной возможностью добавить некоторые.</span><span class="sxs-lookup"><span data-stu-id="f385f-265">If the app being migrated has no integration tests, the migration process can be a great opportunity to add some.</span></span> <span data-ttu-id="f385f-266">Эти тесты могут проверить, что перенесенное приложение ведет себя по мере ожидания команды.</span><span class="sxs-lookup"><span data-stu-id="f385f-266">These tests can verify that the migrated app behaves as the team expects.</span></span> <span data-ttu-id="f385f-267">При выполнении таких тестов на раннем этапе миграции они могут гарантировать, что последующие действия по переносу не нарушат ранее перенесенные части приложения.</span><span class="sxs-lookup"><span data-stu-id="f385f-267">When such tests are in place early in a migration, they can ensure that later migration efforts do not break previously migrated portions of the app.</span></span> <span data-ttu-id="f385f-268">Учитывая, насколько просто настраивать и выполнять интеграционные тесты в ASP.NET Core, возврат на инвестиции, потраченный на настройку таких тестов, обычно довольно высок.</span><span class="sxs-lookup"><span data-stu-id="f385f-268">Given how easy it is to set up and run integration tests in ASP.NET Core, the return on the investment spent setting up such tests is usually pretty high.</span></span>

## <a name="wcf-client-configuration"></a><span data-ttu-id="f385f-269">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="f385f-269">WCF client configuration</span></span>

<span data-ttu-id="f385f-270">Если приложение в настоящее время использует службы WCF в качестве клиента, этот сценарий поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f385f-270">If your app currently relies on WCF services as a client, this scenario is supported.</span></span> <span data-ttu-id="f385f-271">Однако необходимо [перенести конфигурацию](/aspnet/core/migration/configuration) из *web.config* , чтобы использовать новую *appsettings.jsв* файле.</span><span class="sxs-lookup"><span data-stu-id="f385f-271">However, you will need to [migrate your configuration](/aspnet/core/migration/configuration) from *web.config* to use the new *appsettings.json* file.</span></span> <span data-ttu-id="f385f-272">Другой вариант — добавить любую необходимую конфигурацию к клиентам программным способом при их создании.</span><span class="sxs-lookup"><span data-stu-id="f385f-272">Another option is to add any necessary configuration to your clients programmatically when you create them.</span></span> <span data-ttu-id="f385f-273">Пример:</span><span class="sxs-lookup"><span data-stu-id="f385f-273">For example:</span></span>

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

<span data-ttu-id="f385f-274">Если в вашей организации есть обширные службы, созданные с помощью WCF, которые использует приложение, рассмотрите возможность переноса для использования gRPC.</span><span class="sxs-lookup"><span data-stu-id="f385f-274">If your organization has extensive services built using WCF that your app relies on, consider migrating them to use gRPC instead.</span></span> <span data-ttu-id="f385f-275">Дополнительные сведения о gRPC, о том, зачем вам нужно выполнить миграцию, и подробном руководству по миграции, см. в книге [gRPC for WCF Developers](/dotnet/architecture/grpc-for-wcf-developers/) .</span><span class="sxs-lookup"><span data-stu-id="f385f-275">For more details on gRPC, why you may wish to migrate, and a detailed migration guide, consult the [gRPC for WCF Developers](/dotnet/architecture/grpc-for-wcf-developers/) eBook.</span></span>

## <a name="references"></a><span data-ttu-id="f385f-276">Ссылки</span><span class="sxs-lookup"><span data-stu-id="f385f-276">References</span></span>

- [<span data-ttu-id="f385f-277">Согласование содержимого веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f385f-277">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="f385f-278">Форматирование данных отклика в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-278">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)
- [<span data-ttu-id="f385f-279">Пользовательские связыватели модели в веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f385f-279">Custom Model Binders in ASP.NET Web API</span></span>](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [<span data-ttu-id="f385f-280">Пользовательские связыватели модели в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-280">Custom Model Binders in ASP.NET Core</span></span>](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- <span data-ttu-id="f385f-281">[Модули форматирования мультимедиа в веб-API ASP.NET 2](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span><span class="sxs-lookup"><span data-stu-id="f385f-281">[Media Formatters in ASP.NET Web API 2](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span></span>\
- [<span data-ttu-id="f385f-282">Пользовательские модули форматирования для веб-API в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-282">Custom formatters in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/custom-formatters)
- [<span data-ttu-id="f385f-283">Фильтры в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-283">Filters in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/filters)
- [<span data-ttu-id="f385f-284">Ограничения маршрутов в веб-API ASP.NET 2</span><span class="sxs-lookup"><span data-stu-id="f385f-284">Route constraints in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [<span data-ttu-id="f385f-285">Ограничения маршрутов в ASP.NET MVC 5</span><span class="sxs-lookup"><span data-stu-id="f385f-285">Route constraints in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [<span data-ttu-id="f385f-286">Ссылка на ограничение маршрута ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-286">ASP.NET Core Route Constraint Reference</span></span>](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [<span data-ttu-id="f385f-287">Пользовательские обработчики сообщений в веб-API ASP.NET 2</span><span class="sxs-lookup"><span data-stu-id="f385f-287">Custom message handlers in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [<span data-ttu-id="f385f-288">Простой элемент управления CORS в MVC 5 и Web API 2</span><span class="sxs-lookup"><span data-stu-id="f385f-288">Simple CORS control in MVC 5 and Web API 2</span></span>](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [<span data-ttu-id="f385f-289">Включение запросов между источниками в веб-API</span><span class="sxs-lookup"><span data-stu-id="f385f-289">Enabling Cross-Origin Requests in Web API</span></span>](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [<span data-ttu-id="f385f-290">Включение запросов между источниками (CORS) в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-290">Enable Cross-Origin Requests (CORS) in ASP.NET Core</span></span>](/aspnet/core/security/cors)
- [<span data-ttu-id="f385f-291">Области в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-291">Areas in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/areas)
- [<span data-ttu-id="f385f-292">Интеграционные тесты на платформе ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f385f-292">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
><span data-ttu-id="f385f-293">[Назад](example-migration-eshop.md)
>[Вперед](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f385f-293">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
