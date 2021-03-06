---
title: Дополнительные сценарии миграции
description: В этом разделе описываются дополнительные сценарии и методы миграции платформа .NET Framework приложений в .NET Core и .NET 5.
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: fa1b756d8852854e50127ae3e7443e2949cceaa8
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401726"
---
# <a name="more-migration-scenarios"></a><span data-ttu-id="d9e9a-103">Дополнительные сценарии миграции</span><span class="sxs-lookup"><span data-stu-id="d9e9a-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d9e9a-104">В этом разделе описываются несколько различных сценариев приложений ASP.NET и приводятся конкретные методы решения каждого из них.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="d9e9a-105">С помощью этого раздела можно определить сценарии, применимые к приложению, и оценить, какие методы будут работать для приложения и его среды размещения.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="d9e9a-106">Миграция ASP.NET MVC 5 и WebApi 2 на ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="d9e9a-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="d9e9a-107">Распространенным сценарием для приложений ASP.NET MVC 5 и Web API 2 было установка обоих продуктов в одном и том же приложении.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="d9e9a-108">Это поддерживаемый и относительно распространенный подход, используемый многими группами, но поскольку эти два продукта используют разные абстракции, требуются некоторые избыточные усилия.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="d9e9a-109">Например, Настройка маршрутов для ASP.NET MVC выполняется с помощью методов в `RouteCollection` , таких как `MapMvcAttributeRoutes()` и `MapRoute()` .</span><span class="sxs-lookup"><span data-stu-id="d9e9a-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="d9e9a-110">Но веб-API ASP.NET 2 маршрутизация управляется с помощью `HttpConfiguration` методов и, таких как `MapHttpAttributeRoutes()` и `MapHttpRoute()` .</span><span class="sxs-lookup"><span data-stu-id="d9e9a-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="d9e9a-111">`eShopLegacyMVC`Приложение включает в себя ASP.NET MVC и веб-API, а также методы в своей `App_Start` папке для настройки маршрутов для обоих.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="d9e9a-112">Он также поддерживает внедрение зависимостей с помощью Autofac, что также требует двух наборов аналогичной работы для настройки:</span><span class="sxs-lookup"><span data-stu-id="d9e9a-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="d9e9a-113">При обновлении этих приложений для использования ASP.NET Core эти дублирующие усилия и путаница, которые иногда прилагается к ней, устраняются.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="d9e9a-114">ASP.NET Core MVC — это единая платформа с одним набором правил для маршрутизации, фильтров и многого другого.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="d9e9a-115">Внедрение зависимостей встроено в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="d9e9a-116">Все это можно настроить в `Startup.cs` , как показано в `eShopPorted` приложении в примере.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="d9e9a-117">Миграция HttpResponseMessage в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e9a-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="d9e9a-118">Некоторые веб-API ASP.NET приложения могут иметь методы действий, возвращающие `HttpResponseMessage` .</span><span class="sxs-lookup"><span data-stu-id="d9e9a-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="d9e9a-119">Этот тип не существует в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="d9e9a-120">Ниже приведен пример использования в `Delete` методе действия с помощью `ResponseMessage` вспомогательного метода в базе `ApiController` :</span><span class="sxs-lookup"><span data-stu-id="d9e9a-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="d9e9a-121">В ASP.NET Core MVC доступны вспомогательные методы для всех распространенных кодов состояния ответа HTTP, поэтому приведенный выше метод будет перенесен в следующий код:</span><span class="sxs-lookup"><span data-stu-id="d9e9a-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="d9e9a-122">Если вы обнаружите, что вам нужно вернуть пользовательский код состояния, для которого не существует вспомогательного приложения, всегда можно использовать `return StatusCode(int statusCode)` для возврата любого числового кода.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="d9e9a-123">Перенос согласования содержимого из веб-API ASP.NET в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e9a-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="d9e9a-124">Веб-API ASP.NET 2 поддерживает [Согласование содержимого](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) изначально.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="d9e9a-125">Пример приложения включает в себя `BrandsController` , который демонстрирует эту поддержку путем перечисления результатов в формате XML или JSON.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="d9e9a-126">Он основан на `Accept` заголовке запроса и изменяется, когда он включает `application/xml` или `application/json` .</span><span class="sxs-lookup"><span data-stu-id="d9e9a-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="d9e9a-127">В приложениях ASP.NET MVC 5 не встроена поддержка согласования содержимого.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="d9e9a-128">Согласование содержимого предпочтительнее, чем возврат определенного типа кодирования, так как он является более гибким и делает API доступным для большего числа клиентов.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="d9e9a-129">Если в данный момент у вас есть методы действий, возвращающие конкретный формат, рекомендуется изменить их, чтобы возвратить тип результата, поддерживающий согласование содержимого при переносе кода в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="d9e9a-130">Следующий код возвращает данные в формате JSON независимо от `Accept` содержимого заголовка клиента:</span><span class="sxs-lookup"><span data-stu-id="d9e9a-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="d9e9a-131">[ASP.NET Core MVC поддерживает согласование содержимого в собственном](/aspnet/core/web-api/advanced/formatting)режиме, при условии, что используется соответствующий [тип возвращаемого](/aspnet/core/web-api/action-return-types) значения.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="d9e9a-132">Согласование содержимого реализуется с помощью [Обжектресулт], который возвращается результатами действий, связанными с кодом состояния, возвращаемыми вспомогательными методами контроллера.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="d9e9a-133">Предыдущий метод действия, реализованный в ASP.NET Core MVC с использованием согласования содержимого, будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d9e9a-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="d9e9a-134">Это по умолчанию будет возвращать данные в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="d9e9a-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="d9e9a-135">XML и другие форматы будут использоваться, [Если приложение настроено с использованием соответствующего модуля форматирования](/aspnet/core/web-api/advanced/formatting).</span><span class="sxs-lookup"><span data-stu-id="d9e9a-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="references"></a><span data-ttu-id="d9e9a-136">Ссылки</span><span class="sxs-lookup"><span data-stu-id="d9e9a-136">References</span></span>

- [<span data-ttu-id="d9e9a-137">Согласование содержимого веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d9e9a-137">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="d9e9a-138">Форматирование данных отклика в веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d9e9a-138">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
><span data-ttu-id="d9e9a-139">[Назад](example-migration-eshop.md)
>[Вперед](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="d9e9a-139">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
