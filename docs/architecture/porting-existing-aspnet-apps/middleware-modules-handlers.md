---
title: Сравнение по промежуточного слоя с модулями и обработчиками
description: В этом разделе рассматриваются различия в структуре для приложений ASP.NET, использующих обработчики и модули с ASP.NET Core приложениями, которые определяют по промежуточного слоя для конвейеров обработки запросов.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3bc3c30a1ee988550cca907d7289583161337cb9
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122876"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="de3f7-103">Сравнение по промежуточного слоя с модулями и обработчиками</span><span class="sxs-lookup"><span data-stu-id="de3f7-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="de3f7-104">Если существующее приложение ASP.NET MVC или веб-API использует OWIN/Katana, скорее всего, вы уже знакомы с концепцией по промежуточного слоя и переносом их в ASP.NET Core должны быть довольно простыми.</span><span class="sxs-lookup"><span data-stu-id="de3f7-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="de3f7-105">Однако большинство приложений ASP.NET полагаются на HTTP-модули и обработчики HTTP, а не по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="de3f7-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="de3f7-106">Перенос этих данных в ASP.NET Core требует дополнительных усилий.</span><span class="sxs-lookup"><span data-stu-id="de3f7-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="de3f7-107">Модули и обработчики ASP.NET</span><span class="sxs-lookup"><span data-stu-id="de3f7-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="de3f7-108">[Модули HTTP и обработчики HTTP](/troubleshoot/aspnet/http-modules-handlers) являются неотъемлемой частью архитектуры ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="de3f7-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="de3f7-109">Во время обработки запроса каждый запрос обрабатывается несколькими модулями HTTP (например, модулем проверки подлинности и модулем сеанса) и обрабатывается одним HTTP-обработчиком.</span><span class="sxs-lookup"><span data-stu-id="de3f7-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="de3f7-110">После обработки запроса обработчиком запрос передается обратно через HTTP-модули.</span><span class="sxs-lookup"><span data-stu-id="de3f7-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="de3f7-111">Если приложение использует пользовательские модули HTTP или обработчики HTTP, вам потребуется план для их переноса в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="de3f7-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="de3f7-112">Наиболее вероятной заменой в ASP.NET Core является по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="de3f7-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="de3f7-113">По промежуточного слоя ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="de3f7-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="de3f7-114">ASP.NET Core определяет конвейер запросов в методе каждого приложения `Configure` .</span><span class="sxs-lookup"><span data-stu-id="de3f7-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="de3f7-115">Этот конвейер запросов определяет способ обработки входящего запроса приложением, при этом каждый метод в конвейере вызывает следующий метод до завершения метода, а цепочка по *промежуточного слоя* завершается и возвращает резервную копию стека.</span><span class="sxs-lookup"><span data-stu-id="de3f7-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="de3f7-116">По промежуточного слоя может быть нацелено на все запросы или может быть настроено на соответствие только определенным запросам в зависимости от запрошенного пути или других факторов.</span><span class="sxs-lookup"><span data-stu-id="de3f7-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="de3f7-117">Его можно настроить полностью в `Configure` методе приложения или реализовать в отдельном классе.</span><span class="sxs-lookup"><span data-stu-id="de3f7-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="de3f7-118">Поведение в приложении ASP.NET MVC, использующем модули HTTP, вероятно, лучше всего подходит для [пользовательского по промежуточного слоя](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="de3f7-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="de3f7-119">Пользовательские обработчики HTTP можно заменить пользовательскими маршрутами или конечными точками, которые отвечают на один и тот же путь.</span><span class="sxs-lookup"><span data-stu-id="de3f7-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="accessing-httpcontext"></a><span data-ttu-id="de3f7-120">Доступ к HttpContext</span><span class="sxs-lookup"><span data-stu-id="de3f7-120">Accessing HttpContext</span></span>

<span data-ttu-id="de3f7-121">Многие приложения .NET ссылаются на контекст текущего запроса через `HttpContext.Current` .</span><span class="sxs-lookup"><span data-stu-id="de3f7-121">Many .NET apps reference the current request's context through `HttpContext.Current`.</span></span> <span data-ttu-id="de3f7-122">Этот статический доступ может быть общим источником проблем с тестированием и другим использованием кода за пределами отдельных запросов.</span><span class="sxs-lookup"><span data-stu-id="de3f7-122">This static access can be a common source of problems with testing and other code usage outside of individual requests.</span></span> <span data-ttu-id="de3f7-123">При создании ASP.NET Core приложений доступ к текущему HttpContext должен предоставляться как параметр метода по промежуточного слоя, как показано в этом примере:</span><span class="sxs-lookup"><span data-stu-id="de3f7-123">When building ASP.NET Core apps, access to the current HttpContext should be provided as a method parameter on middleware, as this sample demonstrates:</span></span>

```csharp
public class Middleware
{
    private readonly RequestDelegate _next;

    public Middleware(RequestDelegate next)
    {
        _next = next;
    }

    public Task Invoke(HttpContext httpContext)
    {
        return _next(httpContext);
    }
}
```

<span data-ttu-id="de3f7-124">Аналогичным образом ASP.NET Core фильтры передают аргумент контекста их методам, из которых можно получить доступ к текущему объекту HttpContext:</span><span class="sxs-lookup"><span data-stu-id="de3f7-124">Similarly, ASP.NET Core filters pass a context argument to their methods, from which the current HttpContext can be accessed:</span></span>

```csharp
public class MyActionFilterAttribute : ActionFilterAttribute
{
    public override void OnResultExecuting(ResultExecutingContext context)
    {
        var headers = context.HttpContext.Request.Headers;
        // do something based on a header

        base.OnResultExecuting(context);
    }
}
```

<span data-ttu-id="de3f7-125">Если у вас есть компоненты или службы, которым требуется доступ к HttpContext, вместо использования статического вызова, например `HttpContext.Current` , следует использовать внедрение зависимостей конструктора и интерфейс [ихттпконтекстакцессор](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) :</span><span class="sxs-lookup"><span data-stu-id="de3f7-125">If you have components or services that require access to HttpContext, rather than using a static call like `HttpContext.Current` you should instead use constructor dependency injection and the [IHttpContextAccessor](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) interface:</span></span>

```csharp
public class MyService
{
    private readonly IHttpContextAccessor _httpContextAccessor;

    public MyService(IHttpContextAccessor httpContextAccessor)
    {
        _httpContextAccessor = httpContextAccessor;
    }

    public void DoSomething()
    {
        var currentContext = _httpContextAccessor.HttpContext;
    }
}
```

<span data-ttu-id="de3f7-126">Этот подход исключает статическое связывание метода с текущим контекстом, предоставляя доступ тестируемым способом.</span><span class="sxs-lookup"><span data-stu-id="de3f7-126">This approach eliminates the static coupling of the method to the current context while providing access in a testable fashion.</span></span>

## <a name="references"></a><span data-ttu-id="de3f7-127">Ссылки</span><span class="sxs-lookup"><span data-stu-id="de3f7-127">References</span></span>

- [<span data-ttu-id="de3f7-128">ASP.NET HTTP-модули и обработчики HTTP</span><span class="sxs-lookup"><span data-stu-id="de3f7-128">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="de3f7-129">По промежуточного слоя ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="de3f7-129">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="de3f7-130">[Назад](dependency-injection-differences.md)
>[Вперед](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="de3f7-130">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
