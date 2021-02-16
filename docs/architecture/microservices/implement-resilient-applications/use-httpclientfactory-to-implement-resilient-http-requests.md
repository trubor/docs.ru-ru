---
title: Использование IHttpClientFactory для реализации устойчивых HTTP-запросов
description: Узнайте, как использовать интерфейс IHttpClientFactory, доступный в .NET Core, начиная с версии 2.1, для создания экземпляров `HttpClient`, чтобы облегчить их применение в ваших приложениях.
ms.date: 01/13/2021
ms.openlocfilehash: fc5da088b1ed7573532dff101aff03d39a02a6f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429316"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="c3b5b-103">Использование IHttpClientFactory для реализации устойчивых HTTP-запросов</span><span class="sxs-lookup"><span data-stu-id="c3b5b-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="c3b5b-104"><xref:System.Net.Http.IHttpClientFactory> — это контракт, который реализуется `DefaultHttpClientFactory` и доступен, начиная с версии .NET Core 2.1. С его помощью можно создавать экземпляры <xref:System.Net.Http.HttpClient>, которые используются в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net"></a><span data-ttu-id="c3b5b-105">Проблемы с исходным классом HttpClient, доступным в .NET</span><span class="sxs-lookup"><span data-stu-id="c3b5b-105">Issues with the original HttpClient class available in .NET</span></span>

<span data-ttu-id="c3b5b-106">Исходный и хорошо известный класс <xref:System.Net.Http.HttpClient> очень просто использовать, но иногда разработчики применяют его неправильно.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="c3b5b-107">Этот класс реализует `IDisposable`, однако объявлять и создавать его экземпляры в инструкции `using` не рекомендуется, поскольку при удалении объекта `HttpClient` не происходит немедленное освобождение базового сокета, в результате чего со временем может возникнуть проблема _нехватки сокетов_.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="c3b5b-108">Дополнительные сведения об этой проблеме см. в [записи блога](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/), посвященной неправильному использованию HttpClient и нарушению стабильной работы программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="c3b5b-109">Таким образом, создается один экземпляр `HttpClient`, которые будет использоваться повторно на протяжении всего жизненного цикла приложения.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="c3b5b-110">Создание экземпляра класса `HttpClient` для каждого запроса будет сокращать количество доступных сокетов при больших нагрузках.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="c3b5b-111">В результате будут возникать ошибки `SocketException`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="c3b5b-112">Возможные способы решения этой проблемы основаны на создании объекта `HttpClient` в виде класса-одиночки или статического класса, как описано в этой [статье Майкрософт об использовании HttpClient](../../../csharp/tutorials/console-webapiclient.md).</span><span class="sxs-lookup"><span data-stu-id="c3b5b-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="c3b5b-113">Это может быть хорошим решением для консольных приложений, которые выполняются непродолжительное время несколько раз в день, а также их аналогов.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="c3b5b-114">Кроме того, разработчики сталкиваются с проблемами при использовании общего экземпляра `HttpClient` в длительно выполняющихся процессах.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="c3b5b-115">Если экземпляр HttpClient создается в единичном виде или как статический объект, он не может обрабатывать изменения DNS, как описывается в этой [проблеме](https://github.com/dotnet/runtime/issues/18348) в репозитории GitHub dotnet/среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="c3b5b-116">Тем не менее эта проблема связана не с самим объектом `HttpClient`, а с [конструктором по умолчанию для HttpClient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), поскольку он создает новый конкретный экземпляр <xref:System.Net.Http.HttpMessageHandler>, который является источником описываемых выше проблем, связанных с *нехваткой сокетов* и изменениями DNS.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="c3b5b-117">Чтобы решить указанные выше проблемы и обеспечить возможность управления экземплярами `HttpClient`, в .NET Core 2.1 был представлен интерфейс <xref:System.Net.Http.IHttpClientFactory>, который можно использовать для настройки и создания экземпляров `HttpClient` в приложении путем внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="c3b5b-118">Также этот интерфейс предоставляет расширения для ПО промежуточного слоя на основе Polly, что позволяет использовать преимущества делегирования обработчиков в HttpClient.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="c3b5b-119">[Polly](https://thepollyproject.azurewebsites.net/) — это библиотека для обеспечения обработки временных сбоев, которая позволяет разработчикам повысить устойчивость своих приложений, используя некоторые стандартные политики более эффективным и потокобезопасным способом.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-119">[Polly](https://thepollyproject.azurewebsites.net/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="c3b5b-120">Преимущества использования IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="c3b5b-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="c3b5b-121">В текущей реализации <xref:System.Net.Http.IHttpClientFactory> также реализуется <xref:System.Net.Http.IHttpMessageHandlerFactory> и предлагаются следующие преимущества.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="c3b5b-122">Центральное расположение для именования и настройки логических объектов `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="c3b5b-123">Например, вы можете настроить клиент (агент службы), который предварительно настроен для доступа к определенной микрослужбе.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="c3b5b-124">Кодификация концепции исходящего ПО промежуточного слоя путем делегирования обработчиков в `HttpClient` и реализация ПО промежуточного слоя на основе Polly для использования политик устойчивости Polly.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="c3b5b-125">В `HttpClient` уже существует концепция делегирования обработчиков, которые можно связать друг с другом для исходящих HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="c3b5b-126">Вы можете регистрировать клиенты HTTP в фабрике, а также использовать обработчик Polly, чтобы использовать политики Polly для повторных попыток, размыкателя цепи и т. д.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="c3b5b-127">Управление временем существования <xref:System.Net.Http.HttpMessageHandler>, чтобы избежать упомянутых проблем, которые могут возникнуть при управлении временем существования `HttpClient` самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="c3b5b-128">Экземпляры `HttpClient`, внедряемые в виде зависимостей, можно безопасно удалять, поскольку связанный с ними обработчик `HttpMessageHandler` управляется фабрикой.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="c3b5b-129">В сущности, внедренные экземпляры `HttpClient` с точки зрения внедрения зависимостей имеют *ограниченную область действия*.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="c3b5b-130">Реализация `IHttpClientFactory` (`DefaultHttpClientFactory`) тесно привязывается к реализации внедрения зависимостей в пакете NuGet `Microsoft.Extensions.DependencyInjection`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="c3b5b-131">См. сведения об использовании других контейнеров внедрения зависимостей в этом [обсуждении GitHub](https://github.com/dotnet/extensions/issues/1345).</span><span class="sxs-lookup"><span data-stu-id="c3b5b-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="c3b5b-132">Способы применения IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="c3b5b-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="c3b5b-133">Есть несколько способов использования `IHttpClientFactory` в вашем приложении:</span><span class="sxs-lookup"><span data-stu-id="c3b5b-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="c3b5b-134">Основное использование</span><span class="sxs-lookup"><span data-stu-id="c3b5b-134">Basic usage</span></span>
- <span data-ttu-id="c3b5b-135">Использование именованных клиентов</span><span class="sxs-lookup"><span data-stu-id="c3b5b-135">Use Named Clients</span></span>
- <span data-ttu-id="c3b5b-136">Использование типизированных клиентов</span><span class="sxs-lookup"><span data-stu-id="c3b5b-136">Use Typed Clients</span></span>
- <span data-ttu-id="c3b5b-137">Использование созданных клиентов</span><span class="sxs-lookup"><span data-stu-id="c3b5b-137">Use Generated Clients</span></span>

<span data-ttu-id="c3b5b-138">Для краткости в этом руководстве показан наиболее структурированный способ использования `IHttpClientFactory`, а именно — с помощью типизированных клиентов (шаблон агента службы).</span><span class="sxs-lookup"><span data-stu-id="c3b5b-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="c3b5b-139">Все параметры описаны и перечислены в [этой статье](/aspnet/core/fundamentals/http-requests#consumption-patterns), посвященной использованию `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="c3b5b-140">Как использовать типизированные клиенты с IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="c3b5b-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="c3b5b-141">Так что же такое типизированный клиент?</span><span class="sxs-lookup"><span data-stu-id="c3b5b-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="c3b5b-142">Это просто объект `HttpClient`, предварительно настроенный для конкретной цели.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="c3b5b-143">Эта конфигурация может включать заданные значения, например базовый сервер, заголовки HTTP или величины времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="c3b5b-144">На следующей схеме показано, как использовать типизированные клиенты с `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![На схеме показано, как использовать типизированные клиенты с IHttpClientFactory.](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="c3b5b-146">**Рис. 8-4**.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-146">**Figure 8-4**.</span></span> <span data-ttu-id="c3b5b-147">Использование `IHttpClientFactory` с классами типизированных клиентов.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="c3b5b-148">На изображении выше `ClientService` (используется контроллером или в коде клиента) использует объект `HttpClient`, созданный зарегистрированной фабрикой `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="c3b5b-149">Эта фабрика назначает `HttpMessageHandler` из пула объекту `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="c3b5b-150">`HttpClient` можно настроить с помощью политик Polly при регистрации фабрики `IHttpClientFactory` в контейнере внедрения зависимостей, используя метод расширения <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A>.</span></span>

<span data-ttu-id="c3b5b-151">Чтобы настроить такую структуру, добавьте <xref:System.Net.Http.IHttpClientFactory> в приложение, установив пакет NuGet `Microsoft.Extensions.Http`, который содержит метод расширения <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> для <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="c3b5b-152">Этот метод расширения регистрирует внутренний класс `DefaultHttpClientFactory`, который будет использоваться как класс-одиночка для интерфейса `IHttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="c3b5b-153">Он определяет временную конфигурацию для <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="c3b5b-154">Этот обработчик сообщений (объект <xref:System.Net.Http.HttpMessageHandler>), взятый из пула, используется классом `HttpClient`, который возвращается фабрикой.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="c3b5b-155">В приведенном далее коде показано, как `AddHttpClient()` может использоваться для регистрации типизированных клиентов (агентов службы), которым нужно использовать `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="c3b5b-156">Как показано в предыдущем примере кода, регистрация клиентских служб позволяет `DefaultClientFactory` создать объект `HttpClient` для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="c3b5b-157">В регистрацию можно также добавить настройки конкретного экземпляра, например, настроить базовый адрес и добавить некоторые политики устойчивости, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="c3b5b-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="c3b5b-158">В следующем коде для примера показана одна из приведенных выше политик.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="c3b5b-159">Дополнительные сведения об использовании Polly можно найти в [следующей статье](implement-http-call-retries-exponential-backoff-polly.md).</span><span class="sxs-lookup"><span data-stu-id="c3b5b-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="c3b5b-160">Время существования HttpClient</span><span class="sxs-lookup"><span data-stu-id="c3b5b-160">HttpClient lifetimes</span></span>

<span data-ttu-id="c3b5b-161">Каждый раз, когда вы получаете объект `HttpClient` из `IHttpClientFactory`, возвращается новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="c3b5b-162">Но чтобы уменьшить потребление ресурсов, каждый объект `HttpClient` использует из пула экземпляр `HttpMessageHandler`, который также применяется фабрикой `IHttpClientFactory`, если время существования `HttpMessageHandler` еще не истекло.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="c3b5b-163">Создание пулов обработчиков желательно, поскольку каждый обработчик обычно управляет собственными базовыми HTTP-подключениями. Создание лишних обработчиков может привести к задержке подключения.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="c3b5b-164">Некоторые обработчики поддерживают подключения открытыми в течение неопределенного периода, что может помешать обработчику отреагировать на изменения DNS.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="c3b5b-165">Время существования объектов `HttpMessageHandler`это период, в течение которого экземпляр `HttpMessageHandler` в пуле может использоваться повторно.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="c3b5b-166">Значение по умолчанию — две минуты, но его можно переопределить для отдельных типизированных клиентов.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="c3b5b-167">Чтобы переопределить это значение, вызовите `SetHandlerLifetime()` в экземпляре <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder>, который возвращается при создании клиента, как показано в следующем примере кода:</span><span class="sxs-lookup"><span data-stu-id="c3b5b-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="c3b5b-168">Для каждого типизированного клиента можно указать свое значение времени существования настроенного обработчика.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="c3b5b-169">Установите значение `InfiniteTimeSpan`, чтобы отключить срок действия обработчика.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="c3b5b-170">Реализация классов типизированных клиентов, использующих внедренный и настроенный HttpClient</span><span class="sxs-lookup"><span data-stu-id="c3b5b-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="c3b5b-171">Вы уже должны были определить классы типизированных клиентов, например классы в примере кода, такие как BasketService, CatalogService, OrderingService и т. д. Типизированный клиент — это класс, который принимает объект `HttpClient` (внедренный через конструктор) и использует его для вызова удаленной службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="c3b5b-172">Пример:</span><span class="sxs-lookup"><span data-stu-id="c3b5b-172">For example:</span></span>

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take,
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl,
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

<span data-ttu-id="c3b5b-173">Типизированный клиент (в нашем примере это `CatalogService`) активируется путем внедрения зависимостей, то есть он может принять любую зарегистрированную службу в свой конструктор в дополнение к `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="c3b5b-174">Типизированный клиент фактически является временным объектом, что означает, что новый экземпляр создается каждый раз, когда требуется один.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="c3b5b-175">Он получает новый экземпляр `HttpClient` каждый раз, когда он создается.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="c3b5b-176">Тем не менее объекты `HttpMessageHandler` в пуле используются повторно множеством экземпляров `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="c3b5b-177">Использование классов типизированных клиентов</span><span class="sxs-lookup"><span data-stu-id="c3b5b-177">Use your Typed Client classes</span></span>

<span data-ttu-id="c3b5b-178">Наконец, когда вы реализуете классы типов, а также зарегистрируете и настроите их в `AddHttpClient()`.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="c3b5b-179">После этого их можно будет использовать везде, где можно внедрить службы с помощью внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="c3b5b-180">Например, в любом коде страницы Razor или любом контроллере веб-приложения MVC, как в следующем коде из eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

<span data-ttu-id="c3b5b-181">До этого момента в приведенном выше фрагменте кода показан только пример выполнения обычных HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="c3b5b-182">Но "волшебство" начинается в следующих разделах, в которых показано, как все HTTP-запросы, выполняемые `HttpClient`, могут иметь устойчивые политики, такие как повторные попытки с экспоненциальной задержкой, выключателями, функциями безопасности с помощью маркеров проверки подлинности или даже любым другим пользовательским компонентом.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="c3b5b-183">Все это можно сделать, добавив политики и делегировав обработчики зарегистрированным типизированным клиентам.</span><span class="sxs-lookup"><span data-stu-id="c3b5b-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c3b5b-184">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="c3b5b-184">Additional resources</span></span>

- <span data-ttu-id="c3b5b-185">**Использование HttpClientFactory в .NET**</span><span class="sxs-lookup"><span data-stu-id="c3b5b-185">**Using HttpClientFactory in .NET**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="c3b5b-186">**Исходный код HttpClientFactory в репозитории GitHub `dotnet/extensions`**</span><span class="sxs-lookup"><span data-stu-id="c3b5b-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/v3.1.8/src/HttpClientFactory>

- <span data-ttu-id="c3b5b-187">**Polly (библиотека для обеспечения отказоустойчивости .NET и обработки временных сбоев)**</span><span class="sxs-lookup"><span data-stu-id="c3b5b-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://thepollyproject.azurewebsites.net/>
  
- <span data-ttu-id="c3b5b-188">**Использование IHttpClientFactory без внедрения зависимостей (проблема GitHub)**</span><span class="sxs-lookup"><span data-stu-id="c3b5b-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="c3b5b-189">[Назад](implement-resilient-entity-framework-core-sql-connections.md)
>[Вперед](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="c3b5b-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
