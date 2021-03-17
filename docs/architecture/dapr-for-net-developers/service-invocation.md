---
title: Стандартный блок вызова службы ДАПР
description: Описание стандартного блока вызова службы, его функций, преимуществ и способов его применения
author: amolenk
ms.date: 02/17/2021
ms.openlocfilehash: f6d5f10ae476d85a9925c4fa387a16d575cacf6a
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624101"
---
# <a name="the-dapr-service-invocation-building-block"></a><span data-ttu-id="1b23a-103">Стандартный блок вызова службы ДАПР</span><span class="sxs-lookup"><span data-stu-id="1b23a-103">The Dapr service invocation building block</span></span>

<span data-ttu-id="1b23a-104">В распределенной системе одной службе часто требуется взаимодействовать с другой службой для выполнения бизнес-операций.</span><span class="sxs-lookup"><span data-stu-id="1b23a-104">Across a distributed system, one service often needs to communicate with another to complete a business operation.</span></span> <span data-ttu-id="1b23a-105">[Стандартный блок вызова службы ДАПР](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) помогает упростить обмен данными между службами.</span><span class="sxs-lookup"><span data-stu-id="1b23a-105">The [Dapr service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) can help streamline the communication between services.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="1b23a-106">Решение</span><span class="sxs-lookup"><span data-stu-id="1b23a-106">What it solves</span></span>

<span data-ttu-id="1b23a-107">Выполнение вызовов между службами в распределенном приложении может показаться непростым, но существует множество проблем.</span><span class="sxs-lookup"><span data-stu-id="1b23a-107">Making calls between services in a distributed application may appear easy, but there are many challenges involved.</span></span> <span data-ttu-id="1b23a-108">Например:</span><span class="sxs-lookup"><span data-stu-id="1b23a-108">For example:</span></span>

- <span data-ttu-id="1b23a-109">Где расположены другие службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-109">Where the other services are located.</span></span>
- <span data-ttu-id="1b23a-110">Как безопасно вызывать службу с учетом адреса службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-110">How to call a service securely, given the service address.</span></span>
- <span data-ttu-id="1b23a-111">Как выполнять повторные попытки при возникновении кратковременных [временных ошибок](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) .</span><span class="sxs-lookup"><span data-stu-id="1b23a-111">How to handle retries when short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) occur.</span></span>

<span data-ttu-id="1b23a-112">Наконец, поскольку распределенные приложения состоят из множества различных служб, сбор аналитических сведений между графами вызовов служб очень важен для диагностики проблем в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="1b23a-112">Lastly, as distributed applications compose many different services, capturing insights across service call graphs are critical to diagnosing production issues.</span></span>

<span data-ttu-id="1b23a-113">Стандартный блок вызова службы решает эти проблемы, используя ДАПР расширения в качестве [обратных прокси-серверов](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) для службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-113">The service invocation building block addresses these challenges by using a Dapr sidecar as a [reverse proxy](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) for your service.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="1b23a-114">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="1b23a-114">How it works</span></span>

<span data-ttu-id="1b23a-115">Начнем с примера.</span><span class="sxs-lookup"><span data-stu-id="1b23a-115">Let's start with an example.</span></span> <span data-ttu-id="1b23a-116">Рассмотрим две службы: "Service A" и "Service B".</span><span class="sxs-lookup"><span data-stu-id="1b23a-116">Consider two services, "Service A" and "Service B".</span></span> <span data-ttu-id="1b23a-117">Службе A необходимо вызвать `catalog/items` API для службы б. Хотя служба A может взять зависимость от службы б и выполнить прямой вызов, служба а вместо этого вызывает API вызова службы на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-117">Service A needs to call the `catalog/items` API on Service B. While Service A could take a dependency on Service B and make a direct call to it, Service A instead invokes the service invocation API on the Dapr sidecar.</span></span> <span data-ttu-id="1b23a-118">На рис. 6-1 показана операция.</span><span class="sxs-lookup"><span data-stu-id="1b23a-118">Figure 6-1 shows the operation.</span></span>

![Как работает вызов службы ДАПР](./media/service-invocation/service-invocation-flow.png)

<span data-ttu-id="1b23a-120">**Рис. 6-1**.</span><span class="sxs-lookup"><span data-stu-id="1b23a-120">**Figure 6-1**.</span></span> <span data-ttu-id="1b23a-121">Как работает вызов службы ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-121">How Dapr service invocation works.</span></span>

<span data-ttu-id="1b23a-122">Обратите внимание на шаги, приведенные на предыдущем рисунке.</span><span class="sxs-lookup"><span data-stu-id="1b23a-122">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="1b23a-123">Служба A вызывает `catalog/items` конечную точку в службе B, вызывая API вызова службы в службе A расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-123">Service A makes a call to the `catalog/items` endpoint in Service B by invoking the service invocation API on the Service A sidecar.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1b23a-124">Расширения использует подключаемый механизм разрешения имен для разрешения адреса службы б. В режиме с автономным размещением ДАПР использует [MDN](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) для его поиска.</span><span class="sxs-lookup"><span data-stu-id="1b23a-124">The sidecar uses a pluggable name resolution mechanism to resolve the address of Service B. In self-hosted mode, Dapr uses [mDNS](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) to find it.</span></span> <span data-ttu-id="1b23a-125">При работе в режиме Kubernetes служба DNS Kubernetes определяет адрес.</span><span class="sxs-lookup"><span data-stu-id="1b23a-125">When running in Kubernetes mode, the Kubernetes DNS service determines the address.</span></span>  

1. <span data-ttu-id="1b23a-126">Служба A расширения перенаправляет запрос к службе B расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-126">The Service A sidecar forwards the request to the Service B sidecar.</span></span>

1. <span data-ttu-id="1b23a-127">Служба B расширения выполняет фактический `catalog/items` запрос к API-интерфейсу Service b.</span><span class="sxs-lookup"><span data-stu-id="1b23a-127">The Service B sidecar makes the actual `catalog/items` request against the Service B API.</span></span>

1. <span data-ttu-id="1b23a-128">Служба б выполняет запрос и возвращает ответ обратно в его расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-128">Service B executes the request and returns a response back to its sidecar.</span></span>

1. <span data-ttu-id="1b23a-129">Служба б расширения перенаправляет ответ обратно в службу A расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-129">The Service B sidecar forwards the response back to the Service A sidecar.</span></span>

1. <span data-ttu-id="1b23a-130">Служба A расширения возвращает ответ обратно службе.</span><span class="sxs-lookup"><span data-stu-id="1b23a-130">The Service A sidecar returns the response back to Service A.</span></span>

<span data-ttu-id="1b23a-131">Так как вызовы проходят через сидекарс, ДАПР может внедрить некоторые полезные перекрестные поведения:</span><span class="sxs-lookup"><span data-stu-id="1b23a-131">Because the calls flow through sidecars, Dapr can inject some useful cross-cutting behaviors:</span></span>

- <span data-ttu-id="1b23a-132">Автоматически повторять вызовы при сбое.</span><span class="sxs-lookup"><span data-stu-id="1b23a-132">Automatically retry calls upon failure.</span></span>
- <span data-ttu-id="1b23a-133">Обеспечьте безопасность вызовов между службами с помощью взаимной проверки подлинности (mTLS), включая автоматическую смену сертификатов.</span><span class="sxs-lookup"><span data-stu-id="1b23a-133">Make calls between services secure with mutual (mTLS) authentication, including automatic certificate rollover.</span></span>
- <span data-ttu-id="1b23a-134">Контролируйте, какие операции клиенты могут выполнять с помощью политик управления доступом.</span><span class="sxs-lookup"><span data-stu-id="1b23a-134">Control what operations clients can do using access control policies.</span></span>
- <span data-ttu-id="1b23a-135">Сбор трассировок и метрик для всех вызовов между службами для получения ценной информации и диагностики.</span><span class="sxs-lookup"><span data-stu-id="1b23a-135">Capture traces and metrics for all calls between services to provide insights and diagnostics.</span></span>

<span data-ttu-id="1b23a-136">Любое приложение может вызвать расширения ДАПР с помощью собственного API **вызова** , встроенного в ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-136">Any application can invoke a Dapr sidecar by using the native **invoke** API built into Dapr.</span></span> <span data-ttu-id="1b23a-137">API можно вызывать с помощью HTTP или gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-137">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="1b23a-138">Используйте следующий URL-адрес для вызова API HTTP:</span><span class="sxs-lookup"><span data-stu-id="1b23a-138">Use the following URL to call the HTTP API:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- <span data-ttu-id="1b23a-139">`<dapr-port>` HTTP-порт, прослушиваемый ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-139">`<dapr-port>` the HTTP port that Dapr is listening on.</span></span>
- <span data-ttu-id="1b23a-140">`<application-id>` Идентификатор приложения для вызова.</span><span class="sxs-lookup"><span data-stu-id="1b23a-140">`<application-id>` application ID of the service to call.</span></span>
- <span data-ttu-id="1b23a-141">`<method-name>` имя метода, вызываемого в удаленной службе.</span><span class="sxs-lookup"><span data-stu-id="1b23a-141">`<method-name>` name of the method to invoke on the remote service.</span></span>

<span data-ttu-id="1b23a-142">В следующем примере *выполняется вызов с помощью* приведения к `catalog/items` конечной точке Get `Service B` :</span><span class="sxs-lookup"><span data-stu-id="1b23a-142">In the following example, a *curl* call is made to the `catalog/items` 'GET' endpoint of `Service B`:</span></span>

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> <span data-ttu-id="1b23a-143">Интерфейсы API ДАПР позволяют любому стеку приложений, поддерживающему HTTP или gRPC, использовать стандартные блоки ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-143">The Dapr APIs enable any application stack that supports HTTP or gRPC to use Dapr building blocks.</span></span> <span data-ttu-id="1b23a-144">Таким образом, Стандартный блок вызова службы может действовать как мост между протоколами.</span><span class="sxs-lookup"><span data-stu-id="1b23a-144">Therefore, the service invocation building block can act as a bridge between protocols.</span></span> <span data-ttu-id="1b23a-145">Службы могут взаимодействовать друг с другом с помощью протокола HTTP, gRPC или их комбинации.</span><span class="sxs-lookup"><span data-stu-id="1b23a-145">Services can communicate with each other using HTTP, gRPC or a combination of both.</span></span>

<span data-ttu-id="1b23a-146">В следующем разделе вы узнаете, как использовать пакет SDK для .NET, чтобы упростить вызовы вызова служб.</span><span class="sxs-lookup"><span data-stu-id="1b23a-146">In the next section, you'll learn how to use the .NET SDK to simplify service invocation calls.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="1b23a-147">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="1b23a-147">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="1b23a-148">[Пакет SDK](https://github.com/dapr/dotnet-sdk) для ДАПР .net предоставляет разработчикам .NET интуитивно понятный и языковый способ взаимодействия с ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-148">The Dapr [.NET SDK](https://github.com/dapr/dotnet-sdk) provides .NET developers with an intuitive and language-specific way to interact with Dapr.</span></span> <span data-ttu-id="1b23a-149">Пакет SDK предоставляет разработчикам три способа выполнения вызовов удаленного вызова службы:</span><span class="sxs-lookup"><span data-stu-id="1b23a-149">The SDK offers developers three ways of making remote service invocation calls:</span></span>

1. <span data-ttu-id="1b23a-150">Вызов служб HTTP с помощью HttpClient</span><span class="sxs-lookup"><span data-stu-id="1b23a-150">Invoke HTTP services using HttpClient</span></span>
1. <span data-ttu-id="1b23a-151">Вызов служб HTTP с помощью Дапрклиент</span><span class="sxs-lookup"><span data-stu-id="1b23a-151">Invoke HTTP services using DaprClient</span></span>
1. <span data-ttu-id="1b23a-152">Вызов служб gRPC с помощью Дапрклиент</span><span class="sxs-lookup"><span data-stu-id="1b23a-152">Invoke gRPC services using DaprClient</span></span>

### <a name="invoke-http-services-using-httpclient"></a><span data-ttu-id="1b23a-153">Вызов служб HTTP с помощью HttpClient</span><span class="sxs-lookup"><span data-stu-id="1b23a-153">Invoke HTTP services using HttpClient</span></span>

<span data-ttu-id="1b23a-154">Предпочтительным способом вызова конечной точки HTTP является использование расширенной интеграции ДАПР с `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="1b23a-154">The preferred way to call an HTTP endpoint is to use Dapr's rich integration with `HttpClient`.</span></span> <span data-ttu-id="1b23a-155">В следующем примере заказ отправляется путем вызова `submit` метода `orderservice` приложения:</span><span class="sxs-lookup"><span data-stu-id="1b23a-155">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

<span data-ttu-id="1b23a-156">В этом примере `DaprClient.CreateHttpClient` возвращает `HttpClient` экземпляр, который используется для выполнения вызова службы ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-156">In the example, `DaprClient.CreateHttpClient` returns an `HttpClient` instance that is used to perform Dapr service invocation.</span></span> <span data-ttu-id="1b23a-157">Возвращаемый объект `HttpClient` использует специальный обработчик сообщений ДАПР, который перезаписывает URI исходящих запросов.</span><span class="sxs-lookup"><span data-stu-id="1b23a-157">The returned `HttpClient` uses a special Dapr message handler that rewrites URIs of outgoing requests.</span></span> <span data-ttu-id="1b23a-158">Имя узла интерпретируется как идентификатор приложения для вызова.</span><span class="sxs-lookup"><span data-stu-id="1b23a-158">The host name is interpreted as the application ID of the service to call.</span></span> <span data-ttu-id="1b23a-159">Фактически вызывается перезаписанный запрос:</span><span class="sxs-lookup"><span data-stu-id="1b23a-159">The rewritten request that's actually being called is:</span></span>

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

<span data-ttu-id="1b23a-160">В этом примере используется значение по умолчанию для конечной точки HTTP ДАПР, то есть `http://127.0.0.1:<dapr-http-port>/` .</span><span class="sxs-lookup"><span data-stu-id="1b23a-160">This example uses the default value for the Dapr HTTP endpoint, which is `http://127.0.0.1:<dapr-http-port>/`.</span></span> <span data-ttu-id="1b23a-161">Значение `dapr-http-port` берется из `DAPR_HTTP_PORT` переменной среды.</span><span class="sxs-lookup"><span data-stu-id="1b23a-161">The value of `dapr-http-port` is taken from the `DAPR_HTTP_PORT` environment variable.</span></span> <span data-ttu-id="1b23a-162">Если он не задан, используется номер порта по умолчанию `3500` .</span><span class="sxs-lookup"><span data-stu-id="1b23a-162">If it's not set, the default port number `3500` is used.</span></span>

<span data-ttu-id="1b23a-163">Кроме того, можно настроить пользовательскую конечную точку в вызове `DaprClient.CreateHttpClient` :</span><span class="sxs-lookup"><span data-stu-id="1b23a-163">Alternatively, you can configure a custom endpoint in the call to `DaprClient.CreateHttpClient`:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

<span data-ttu-id="1b23a-164">Можно также напрямую задать базовый адрес, указав идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-164">You can also directly set the base address by specifying the application ID.</span></span> <span data-ttu-id="1b23a-165">Это позволяет использовать относительные URI при совершении вызова:</span><span class="sxs-lookup"><span data-stu-id="1b23a-165">This makes it possible to use relative URIs when making a call:</span></span>

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

<span data-ttu-id="1b23a-166">`HttpClient`Объект должен быть длительным.</span><span class="sxs-lookup"><span data-stu-id="1b23a-166">The `HttpClient` object is intended to be long-lived.</span></span> <span data-ttu-id="1b23a-167">Один `HttpClient` экземпляр можно повторно использовать в течение времени существования приложения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-167">A single `HttpClient` instance can be reused for the lifetime of the application.</span></span> <span data-ttu-id="1b23a-168">В следующем сценарии показано, как `OrderServiceClient` класс повторно использует экземпляр ДАПР `HttpClient` :</span><span class="sxs-lookup"><span data-stu-id="1b23a-168">The next scenario demonstrates how an `OrderServiceClient` class reuses a Dapr `HttpClient` instance:</span></span>  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

<span data-ttu-id="1b23a-169">В приведенном выше фрагменте объект `OrderServiceClient` регистрируется как одноэлементный с системой внедрения зависимостей ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1b23a-169">In the snippet above, the `OrderServiceClient` is registered as a singleton with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="1b23a-170">Фабрика реализации создает новый `HttpClient` экземпляр путем вызова метода `DaprClient.CreateInvokeHttpClient` .</span><span class="sxs-lookup"><span data-stu-id="1b23a-170">An implementation factory creates a new `HttpClient` instance by calling `DaprClient.CreateInvokeHttpClient`.</span></span> <span data-ttu-id="1b23a-171">Затем он использует только что созданный `HttpClient` объект для создания экземпляра `OrderServiceClient` объекта.</span><span class="sxs-lookup"><span data-stu-id="1b23a-171">It then uses the newly created `HttpClient` to instantiate the `OrderServiceClient` object.</span></span> <span data-ttu-id="1b23a-172">Регистрация в `OrderServiceClient` качестве одноэлементного экземпляра будет повторно использоваться в течение времени существования приложения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-172">By registering the `OrderServiceClient` as a singleton, it will be reused for the lifetime of the application.</span></span>

<span data-ttu-id="1b23a-173">`OrderServiceClient`Сам по себе не имеет кода, зависящего от ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-173">The `OrderServiceClient` itself has no Dapr-specific code.</span></span> <span data-ttu-id="1b23a-174">Несмотря на то, что вызов службы ДАПР используется внутри, можно считать ДАПР HttpClient, как и любые другие HttpClient:</span><span class="sxs-lookup"><span data-stu-id="1b23a-174">Even though Dapr service invocation is used under the hood, you can treat the Dapr HttpClient like any other HttpClient:</span></span>

```csharp
public class OrderServiceClient : IOrderServiceClient
{
    private readonly HttpClient _httpClient;

    public OrderServiceClient(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public async Task SubmitOrder(Order order)
    {
        var response = await _httpClient.PostAsJsonAsync("submit", order);
        response.EnsureSuccessStatusCode();
    }
}
```

<span data-ttu-id="1b23a-175">Использование класса HttpClient с вызовом службы ДАПР имеет много преимуществ:</span><span class="sxs-lookup"><span data-stu-id="1b23a-175">Using the HttpClient class with Dapr service invocation has many benefits:</span></span>

- <span data-ttu-id="1b23a-176">HttpClient — хорошо известный класс, который многие разработчики уже используют в своем коде.</span><span class="sxs-lookup"><span data-stu-id="1b23a-176">HttpClient is a well-known class that many developers already use in their code.</span></span> <span data-ttu-id="1b23a-177">Использование HttpClient для вызова службы ДАПР позволяет разработчикам повторно использовать имеющиеся навыки.</span><span class="sxs-lookup"><span data-stu-id="1b23a-177">Using HttpClient for Dapr service invocation allows developers to reuse their existing skills.</span></span>
- <span data-ttu-id="1b23a-178">HttpClient поддерживает расширенные сценарии, такие как пользовательские заголовки, и полный контроль над сообщениями запросов и ответов.</span><span class="sxs-lookup"><span data-stu-id="1b23a-178">HttpClient supports advanced scenarios, such as custom headers, and full control over request and response messages.</span></span>
- <span data-ttu-id="1b23a-179">В .NET 5 HttpClient поддерживает автоматическую сериализацию и десериализацию с помощью System.Text.Jsв.</span><span class="sxs-lookup"><span data-stu-id="1b23a-179">In .NET 5, HttpClient supports automatic serialization and deserialization using System.Text.Json.</span></span>
- <span data-ttu-id="1b23a-180">HttpClient интегрируется с множеством существующих платформ и библиотек, таких как [refit](https://github.com/reactiveui/refit), [рестшарп](https://restsharp.dev/getting-started/getting-started.html#basic-usage)и [Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="1b23a-180">HttpClient integrates with many existing frameworks and libraries, such as [Refit](https://github.com/reactiveui/refit), [RestSharp](https://restsharp.dev/getting-started/getting-started.html#basic-usage), and [Polly](https://github.com/App-vNext/Polly).</span></span>

### <a name="invoke-http-services-using-daprclient"></a><span data-ttu-id="1b23a-181">Вызов служб HTTP с помощью Дапрклиент</span><span class="sxs-lookup"><span data-stu-id="1b23a-181">Invoke HTTP services using DaprClient</span></span>

<span data-ttu-id="1b23a-182">Хотя HttpClient является предпочтительным способом вызова служб с использованием семантики HTTP, можно также использовать `DaprClient.InvokeMethodAsync` семейство методов.</span><span class="sxs-lookup"><span data-stu-id="1b23a-182">While HttpClient is the preferred way to invoke services using HTTP semantics, you can also use the `DaprClient.InvokeMethodAsync` family of methods.</span></span> <span data-ttu-id="1b23a-183">В следующем примере заказ отправляется путем вызова `submit` метода `orderservice` приложения:</span><span class="sxs-lookup"><span data-stu-id="1b23a-183">The following example submits an order by calling the `submit` method of the `orderservice` application:</span></span>

``` csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation =
        await daprClient.InvokeMethodAsync<Order, OrderConfirmation>(
            "orderservice", "submit", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="1b23a-184">Третий аргумент, `order` объект, сериализуется внутренне (с `System.Text.JsonSerializer` ) и отправляется в качестве полезных данных запроса.</span><span class="sxs-lookup"><span data-stu-id="1b23a-184">The third argument, an `order` object, is serialized internally (with `System.Text.JsonSerializer`) and sent as the request payload.</span></span> <span data-ttu-id="1b23a-185">Пакет SDK для .NET позаботится о вызове расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-185">The .NET SDK takes care of the call to the sidecar.</span></span> <span data-ttu-id="1b23a-186">Он также Десериализует ответ на `OrderConfirmation` объект.</span><span class="sxs-lookup"><span data-stu-id="1b23a-186">It also deserializes the response to an `OrderConfirmation` object.</span></span> <span data-ttu-id="1b23a-187">Поскольку метод HTTP не указан, запрос выполняется как HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="1b23a-187">Because no HTTP method is specified, the request is executed as an HTTP POST.</span></span>

<span data-ttu-id="1b23a-188">В следующем примере показано, как можно выполнить HTTP-запрос GET, указав `HttpMethod` :</span><span class="sxs-lookup"><span data-stu-id="1b23a-188">The next example demonstrates how you can make an HTTP GET request by specifying the `HttpMethod`:</span></span>

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

<span data-ttu-id="1b23a-189">В некоторых сценариях может потребоваться больший контроль над сообщением запроса.</span><span class="sxs-lookup"><span data-stu-id="1b23a-189">For some scenarios, you may require more control over the request message.</span></span> <span data-ttu-id="1b23a-190">Например, если необходимо указать заголовки запроса или вы хотите использовать пользовательский сериализатор для полезных данных.</span><span class="sxs-lookup"><span data-stu-id="1b23a-190">For example, when you need to specify request headers, or you want to use a custom serializer for the payload.</span></span> <span data-ttu-id="1b23a-191">`DaprClient.CreateInvokeMethodRequest` создает `HttpRequestMessage` .</span><span class="sxs-lookup"><span data-stu-id="1b23a-191">`DaprClient.CreateInvokeMethodRequest` creates an `HttpRequestMessage`.</span></span> <span data-ttu-id="1b23a-192">В следующем примере показано, как добавить заголовок авторизации HTTP к сообщению запроса:</span><span class="sxs-lookup"><span data-stu-id="1b23a-192">The following example demonstrates how to add an HTTP authorization header to a request message:</span></span>

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

<span data-ttu-id="1b23a-193">`HttpRequestMessage`Теперь установлены следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="1b23a-193">The `HttpRequestMessage` now has the following properties set:</span></span>

- <span data-ttu-id="1b23a-194">URL-адрес = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span><span class="sxs-lookup"><span data-stu-id="1b23a-194">Url = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`</span></span>
- <span data-ttu-id="1b23a-195">HttpMethod = POST</span><span class="sxs-lookup"><span data-stu-id="1b23a-195">HttpMethod = POST</span></span>
- <span data-ttu-id="1b23a-196">Content =  `JsonContent` объект, содержащий сериализованный JSON `order`</span><span class="sxs-lookup"><span data-stu-id="1b23a-196">Content =  `JsonContent` object containing the JSON-serialized `order`</span></span>
- <span data-ttu-id="1b23a-197">Headers. Authorization = "Bearer \<token> "</span><span class="sxs-lookup"><span data-stu-id="1b23a-197">Headers.Authorization = "bearer \<token>"</span></span>

<span data-ttu-id="1b23a-198">Когда запрос будет настроен так, как вам нужно, используйте `DaprClient.InvokeMethodAsync` для его отправки:</span><span class="sxs-lookup"><span data-stu-id="1b23a-198">Once you've got the request set up the way you want, use `DaprClient.InvokeMethodAsync` to send it:</span></span>

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

<span data-ttu-id="1b23a-199">`DaprClient.InvokeMethodAsync` Десериализует ответ на `OrderConfirmation` объект, если запрос выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="1b23a-199">`DaprClient.InvokeMethodAsync` deserializes the response to an `OrderConfirmation` object if the request is successful.</span></span> <span data-ttu-id="1b23a-200">Кроме того, можно использовать `DaprClient.InvokeMethodWithResponseAsync` для получения полного доступа к базовому `HttpResponseMessage` :</span><span class="sxs-lookup"><span data-stu-id="1b23a-200">Alternatively, you can use `DaprClient.InvokeMethodWithResponseAsync` to get full access to the underlying `HttpResponseMessage`:</span></span>

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> <span data-ttu-id="1b23a-201">Для вызовов вызова служб по протоколу HTTP стоит рассмотреть использование интеграции ДАПР HttpClient, представленной в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="1b23a-201">For service invocation calls using HTTP, it's worth considering using the Dapr HttpClient integration presented in the previous section.</span></span> <span data-ttu-id="1b23a-202">Использование HttpClient предоставляет дополнительные преимущества, такие как интеграция с существующими платформами и библиотеками.</span><span class="sxs-lookup"><span data-stu-id="1b23a-202">Using HttpClient gives you additional benefits such as integration with existing frameworks and libraries.</span></span>

### <a name="invoke-grpc-services-using-daprclient"></a><span data-ttu-id="1b23a-203">Вызов служб gRPC с помощью Дапрклиент</span><span class="sxs-lookup"><span data-stu-id="1b23a-203">Invoke gRPC services using DaprClient</span></span>

<span data-ttu-id="1b23a-204">Дапрклиент предоставляет семейство `InvokeMethodGrpcAsync` методов для вызова конечных точек gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-204">DaprClient provides a family of `InvokeMethodGrpcAsync` methods for calling gRPC endpoints.</span></span> <span data-ttu-id="1b23a-205">Основное отличие от методов HTTP заключается в использовании сериализатора protobuf, а не JSON.</span><span class="sxs-lookup"><span data-stu-id="1b23a-205">The main difference with the HTTP methods is the use of a Protobuf serializer instead of JSON.</span></span> <span data-ttu-id="1b23a-206">В следующем примере вызывается `submitOrder` метод класса `orderservice` over gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-206">The following example invokes the `submitOrder` method of the `orderservice` over gRPC.</span></span>

```csharp
var daprClient = new DaprClientBuilder().Build();
try
{
    var confirmation = await daprClient.InvokeMethodGrpcAsync<Order, OrderConfirmation>("orderservice", "submitOrder", order);
}
catch (InvocationException ex)
{
    // Handle error
}
```

<span data-ttu-id="1b23a-207">В приведенном выше примере Дапрклиент Сериализует данный `order` объект с помощью [protobuf](https://developers.google.com/protocol-buffers) и использует результат в качестве тела запроса gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-207">In the example above, DaprClient serializes the given `order` object using [Protobuf](https://developers.google.com/protocol-buffers) and uses the result as the gRPC request body.</span></span> <span data-ttu-id="1b23a-208">Аналогичным образом, текст ответа protobuf десериализуется и возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="1b23a-208">Likewise, the response body is Protobuf deserialized and returned to the caller.</span></span> <span data-ttu-id="1b23a-209">Protobuf обычно обеспечивает лучшую производительность, чем полезные данные JSON, используемые в вызове службы HTTP.</span><span class="sxs-lookup"><span data-stu-id="1b23a-209">Protobuf typically provides better performance than the JSON payloads used in HTTP service invocation.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="1b23a-210">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="1b23a-210">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="1b23a-211">Исходная Эталонная архитектура микрослужбы [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) от корпорации Майкрософт использует сочетание служб HTTP/RESTful и gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="1b23a-211">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) microservice reference architecture from Microsoft used a mix of HTTP/REST and gRPC services.</span></span> <span data-ttu-id="1b23a-212">Использование gRPC было ограничено обменом данными между [службой агрегатора](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) и основными серверными службами.</span><span class="sxs-lookup"><span data-stu-id="1b23a-212">The use of gRPC was limited to communication between an [aggregator service](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) and core back-end services.</span></span> <span data-ttu-id="1b23a-213">На рис. 6-2 показана архитектура:</span><span class="sxs-lookup"><span data-stu-id="1b23a-213">Figure 6-2 show the architecture:</span></span>

![вызовы gRPC и HTTP/RESTFUL в eShopOnContainers](./media/service-invocation/eshop-on-containers.png)

<span data-ttu-id="1b23a-215">**Рис. 6-2**.</span><span class="sxs-lookup"><span data-stu-id="1b23a-215">**Figure 6-2**.</span></span> <span data-ttu-id="1b23a-216">вызовы gRPC и HTTP/RESTFUL в eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1b23a-216">gRPC and HTTP/REST calls in eShopOnContainers.</span></span>

<span data-ttu-id="1b23a-217">Обратите внимание на шаги, приведенные на предыдущем рисунке.</span><span class="sxs-lookup"><span data-stu-id="1b23a-217">Note the steps from the previous figure:</span></span>

1. <span data-ttu-id="1b23a-218">Внешний интерфейс вызывает [шлюз API](/azure/architecture/microservices/design/gateway) с помощью протокола HTTP/RESTful.</span><span class="sxs-lookup"><span data-stu-id="1b23a-218">The front end calls the [API gateway](/azure/architecture/microservices/design/gateway) using HTTP/REST.</span></span>

1. <span data-ttu-id="1b23a-219">Шлюз API перенаправляет простые запросы [CRUD](https://www.sumologic.com/glossary/crud/) (создание, чтение, обновление и удаление) непосредственно в основную серверную службу с помощью протокола HTTP/RESTful.</span><span class="sxs-lookup"><span data-stu-id="1b23a-219">The API gateway forwards simple [CRUD](https://www.sumologic.com/glossary/crud/) (Create, Read, Update, Delete) requests directly to a core back-end service using HTTP/REST.</span></span>

1. <span data-ttu-id="1b23a-220">Шлюз API перенаправляет сложные запросы, которые подразумевают координированные вызовы к нескольким внутренним службам, в службу агрегатора веб-покупок.</span><span class="sxs-lookup"><span data-stu-id="1b23a-220">The API gateway forwards complex requests that involve coordinated calls to multiple back-end services to the web shopping aggregator service.</span></span>

1. <span data-ttu-id="1b23a-221">Служба агрегатора использует gRPC для вызова основных серверных служб.</span><span class="sxs-lookup"><span data-stu-id="1b23a-221">The aggregator service uses gRPC to call core back-end services.</span></span>

<span data-ttu-id="1b23a-222">В недавно обновленной реализации Ешопондапр в службы и шлюз API добавляются ДАПР сидекарс.</span><span class="sxs-lookup"><span data-stu-id="1b23a-222">In the recently updated eShopOnDapr implementation, Dapr sidecars are added to the services and API gateway.</span></span> <span data-ttu-id="1b23a-223">На рис. 6-3 показана Обновленная архитектура:</span><span class="sxs-lookup"><span data-stu-id="1b23a-223">Figure 6-3 show the updated architecture:</span></span>

![вызовы gRPC и HTTP/RESTFUL с сидекарс в eShopOnContainers](./media/service-invocation/eshop-on-dapr.png)

<span data-ttu-id="1b23a-225">**Рис. 6-3.**</span><span class="sxs-lookup"><span data-stu-id="1b23a-225">**Figure 6-3**.</span></span> <span data-ttu-id="1b23a-226">Обновлена архитектура Ешоп с помощью ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-226">Updated eShop architecture using Dapr.</span></span>

<span data-ttu-id="1b23a-227">Обратите внимание на обновленные шаги, приведенные на предыдущем рисунке.</span><span class="sxs-lookup"><span data-stu-id="1b23a-227">Note the updated steps from the previous figure:</span></span>

1. <span data-ttu-id="1b23a-228">Внешний интерфейс по-прежнему использует протокол HTTP/RESTFUL для вызова шлюза API.</span><span class="sxs-lookup"><span data-stu-id="1b23a-228">The front end still uses HTTP/REST to call the API gateway.</span></span>

1. <span data-ttu-id="1b23a-229">Шлюз API перенаправляет HTTP-запросы к своему ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-229">The API gateway forwards HTTP requests to its Dapr sidecar.</span></span>

1. <span data-ttu-id="1b23a-230">Расширения шлюза API отправляет запрос в расширения агрегатора или серверной службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-230">The API gateway sidecar sends the request to the sidecar of the aggregator or back-end service.</span></span>

1. <span data-ttu-id="1b23a-231">Служба агрегатора использует пакет SDK для .NET ДАПР для вызова внутренних служб через их архитектуру расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-231">The aggregator service uses the Dapr .NET SDK to call back-end services through their sidecar architecture.</span></span>

<span data-ttu-id="1b23a-232">ДАПР реализует вызовы между сидекарс и gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-232">Dapr implements calls between sidecars with gRPC.</span></span> <span data-ttu-id="1b23a-233">Поэтому даже при вызове удаленной службы с семантикой HTTP/RESTFUL часть транспорта по-прежнему реализуется с помощью gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-233">So even if you're invoking a remote service with HTTP/REST semantics, a part of the transport is still implemented using gRPC.</span></span>

<span data-ttu-id="1b23a-234">Преимущества эталонного приложения Ешопондапр из стандартного блока вызова службы ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-234">The eShopOnDapr reference application benefits from the Dapr service invocation building block.</span></span> <span data-ttu-id="1b23a-235">К преимуществам относятся обнаружение служб, автоматическая функция mTLS и наблюдаемость.</span><span class="sxs-lookup"><span data-stu-id="1b23a-235">The benefits include service discovery, automatic mTLS, and observability.</span></span>

### <a name="forward-http-requests-using-envoy-and-dapr"></a><span data-ttu-id="1b23a-236">Пересылка HTTP-запросов с помощью делегата и ДАПР</span><span class="sxs-lookup"><span data-stu-id="1b23a-236">Forward HTTP requests using Envoy and Dapr</span></span>

<span data-ttu-id="1b23a-237">Как исходное, так и обновленное приложение Ешоп использует [прокси-сервер делегата](https://www.envoyproxy.io/) в качестве шлюза API.</span><span class="sxs-lookup"><span data-stu-id="1b23a-237">Both the original and updated eShop application leverage the [Envoy proxy](https://www.envoyproxy.io/) as an API gateway.</span></span> <span data-ttu-id="1b23a-238">Делегат — это прокси-сервер с открытым исходным кодом и шина связи, которые популярны среди современных распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="1b23a-238">Envoy is an open-source proxy and communication bus that is popular across modern distributed applications.</span></span> <span data-ttu-id="1b23a-239">Исходя из Лифт, представитель владеет и обслуживается [облачной вычислительной средой](https://www.cncf.io/).</span><span class="sxs-lookup"><span data-stu-id="1b23a-239">Originating from Lyft, Envoy is owned and maintained by the [Cloud-Native Computing Foundation](https://www.cncf.io/).</span></span>

<span data-ttu-id="1b23a-240">В первоначальной реализации eShopOnContainers шлюз API делегата перенаправляет входящие HTTP-запросы непосредственно в агрегаторы или серверные службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-240">In the original eShopOnContainers implementation, the Envoy API gateway forwarded incoming HTTP requests directly to aggregator or back-end services.</span></span> <span data-ttu-id="1b23a-241">В новом Ешопондапр прокси-сервер перенаправляет запрос в ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="1b23a-241">In the new eShopOnDapr, the Envoy proxy forwards the request to a Dapr sidecar.</span></span> <span data-ttu-id="1b23a-242">Расширения обеспечивает вызов службы, mTLS и наблюдаемость.</span><span class="sxs-lookup"><span data-stu-id="1b23a-242">The sidecar provides service invocation, mTLS, and observability.</span></span>

<span data-ttu-id="1b23a-243">Представитель настраивается с помощью файла определения YAML для управления поведением прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="1b23a-243">Envoy is configured using a YAML definition file to control the proxy's behavior.</span></span> <span data-ttu-id="1b23a-244">Чтобы разрешить представителю пересылать HTTP-запросы в контейнер ДАПР расширения, в `dapr` конфигурацию добавляется кластер.</span><span class="sxs-lookup"><span data-stu-id="1b23a-244">To enable Envoy to forward HTTP requests to a Dapr sidecar container, a `dapr` cluster is added to the configuration.</span></span> <span data-ttu-id="1b23a-245">Конфигурация кластера содержит узел, указывающий на HTTP-порт, который прослушивает расширения ДАПР:</span><span class="sxs-lookup"><span data-stu-id="1b23a-245">The cluster configuration contains a host that points to the HTTP port on which the Dapr sidecar is listening:</span></span>

``` yaml
clusters:
- name: dapr
  connect_timeout: 0.25s
  type: strict_dns
  hosts:
  - socket_address:
    address: 127.0.0.1
    port_value: 3500
```

<span data-ttu-id="1b23a-246">Конфигурация маршрутизации делегатов обновляется для перезаписи входящих запросов в виде вызовов ДАПР расширения (Обратите особое внимание на `prefix_rewrite` пару "ключ-значение"):</span><span class="sxs-lookup"><span data-stu-id="1b23a-246">The Envoy routes configuration is updated to rewrite incoming requests as calls to the Dapr sidecar (pay close attention to the `prefix_rewrite` key/value pair):</span></span>

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

<span data-ttu-id="1b23a-247">Рассмотрим ситуацию, когда клиент переднего плана хочет получить список элементов каталога.</span><span class="sxs-lookup"><span data-stu-id="1b23a-247">Consider a scenario where the front-end client wants to retrieve a list of catalog items.</span></span> <span data-ttu-id="1b23a-248">API каталога предоставляет конечную точку для получения элементов каталога:</span><span class="sxs-lookup"><span data-stu-id="1b23a-248">The Catalog API provides an endpoint for getting the catalog items:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[ApiController]
public class CatalogController : ControllerBase
{
    [HttpGet("items")]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery] int pageSize = 10,
        [FromQuery] int pageIndex = 0)
    {
        // ...
    }
```

<span data-ttu-id="1b23a-249">Во-первых, внешний интерфейс выполняет прямой вызов HTTP к шлюзу API делегата.</span><span class="sxs-lookup"><span data-stu-id="1b23a-249">First, the front end makes a direct HTTP call to the Envoy API gateway.</span></span>

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="1b23a-250">Прокси-сервер делегата соответствует маршруту, переписывает HTTP-запрос и пересылает его `invoke` API ДАПР расширения:</span><span class="sxs-lookup"><span data-stu-id="1b23a-250">The Envoy proxy matches the route, rewrites the HTTP request, and forwards it to the `invoke` API of its Dapr sidecar:</span></span>

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

<span data-ttu-id="1b23a-251">Расширения обрабатывает обнаружение службы и направляет запрос в расширения API каталога.</span><span class="sxs-lookup"><span data-stu-id="1b23a-251">The sidecar handles service discovery and routes the request to the Catalog API sidecar.</span></span> <span data-ttu-id="1b23a-252">Наконец, расширения вызывает API каталога для выполнения запроса, получения элементов каталога и возврата ответа:</span><span class="sxs-lookup"><span data-stu-id="1b23a-252">Finally, the sidecar calls the Catalog API to execute the request, fetch catalog items, and return a response:</span></span>

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a><span data-ttu-id="1b23a-253">Осуществление агрегированных вызовов служб с помощью пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="1b23a-253">Make aggregated service calls using the .NET SDK</span></span>

<span data-ttu-id="1b23a-254">Большинство вызовов из внешнего интерфейса Ешоп являются простыми вызовами CRUD.</span><span class="sxs-lookup"><span data-stu-id="1b23a-254">Most calls from the eShop front end are simple CRUD calls.</span></span> <span data-ttu-id="1b23a-255">Шлюз API перенаправляет их в одну службу для обработки.</span><span class="sxs-lookup"><span data-stu-id="1b23a-255">The API gateway forwards them to a single service for processing.</span></span> <span data-ttu-id="1b23a-256">Однако в некоторых случаях требуется, чтобы несколько серверных служб работали вместе для выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="1b23a-256">Some scenarios, however, require multiple back-end services to work together to complete a request.</span></span> <span data-ttu-id="1b23a-257">Для этих более сложных вызовов Ешоп использует службу агрегации веб-покупок, чтобы исправлять рабочий процесс по нескольким службам.</span><span class="sxs-lookup"><span data-stu-id="1b23a-257">For these more complex calls, eShop uses the web shopping aggregator service to mediate the workflow across multiple services.</span></span> <span data-ttu-id="1b23a-258">Рис. 6-4. отображение последовательности действий по добавлению элемента в корзину для покупок:</span><span class="sxs-lookup"><span data-stu-id="1b23a-258">Figure 6-4 show the processing sequence of adding an item to your shopping basket:</span></span>

![Схема последовательностей обновления корзины](./media/service-invocation/complex-call.png)

<span data-ttu-id="1b23a-260">**Рис. 6-4**.</span><span class="sxs-lookup"><span data-stu-id="1b23a-260">**Figure 6-4**.</span></span> <span data-ttu-id="1b23a-261">Обновление последовательности покупательских корзин.</span><span class="sxs-lookup"><span data-stu-id="1b23a-261">Update shopping basket sequence.</span></span>

<span data-ttu-id="1b23a-262">Служба агрегатора сначала извлекает элементы каталога из API каталога.</span><span class="sxs-lookup"><span data-stu-id="1b23a-262">The aggregator service first retrieves catalog items from the Catalog API.</span></span> <span data-ttu-id="1b23a-263">Затем он проверяет доступность и цены номенклатуры.</span><span class="sxs-lookup"><span data-stu-id="1b23a-263">It then validates item availability and pricing.</span></span> <span data-ttu-id="1b23a-264">Наконец, служба агрегатора сохраняет обновленную корзину покупок, вызывая API корзины.</span><span class="sxs-lookup"><span data-stu-id="1b23a-264">Finally, the aggregator service saves the updated shopping basket by calling the Basket API.</span></span>

<span data-ttu-id="1b23a-265">Служба агрегатора содержит `BasketController` , который предоставляет конечную точку для обновления корзины покупок:</span><span class="sxs-lookup"><span data-stu-id="1b23a-265">The aggregator service contains a `BasketController` that provides an endpoint for updating the shopping basket:</span></span>

``` csharp
[Route("api/v1/[controller]")]
[Authorize]
[ApiController]
public class BasketController : ControllerBase
{
    private readonly ICatalogService _catalog;
    private readonly IBasketService _basket;

    [HttpPost]
    [HttpPut]
    public async Task<ActionResult<BasketData>> UpdateAllBasketAsync(
        [FromBody] UpdateBasketRequest data, [FromHeader] string authorization)
    {
        // Get the item details from the catalog API.
        var catalogItems = await _catalog.GetCatalogItemsAsync(
            data.Items.Select(x => x.ProductId));

        // Check item availability and prices; store results in basket object.
        var basket = CreateValidatedBasket(data, catalogItems);

        // Save the shopping basket.
        await _basket.UpdateAsync(basket, authorization);

        return basket;
    }

    // ...
}
```

<span data-ttu-id="1b23a-266">`UpdateAllBasketAsync`Метод получает заголовок *авторизации* входящего запроса, используя `FromHeader` атрибут.</span><span class="sxs-lookup"><span data-stu-id="1b23a-266">The `UpdateAllBasketAsync` method gets the *Authorization* header of the incoming request using a `FromHeader` attribute.</span></span> <span data-ttu-id="1b23a-267">Заголовок *authorization* содержит маркер доступа, необходимый для вызова защищенных серверных служб.</span><span class="sxs-lookup"><span data-stu-id="1b23a-267">The *Authorization* header contains the access token that is needed to call protected back-end services.</span></span>

<span data-ttu-id="1b23a-268">После получения запроса на обновление корзины служба агрегатора вызывает API каталога для получения сведений об элементе.</span><span class="sxs-lookup"><span data-stu-id="1b23a-268">After receiving a request to update the basket, the aggregator service calls the Catalog API to get the item details.</span></span> <span data-ttu-id="1b23a-269">Контроллер подсистемы подбора использует внедренный `ICatalogService` объект, чтобы сделать вызов и взаимодействовать с API каталога.</span><span class="sxs-lookup"><span data-stu-id="1b23a-269">The Basket controller uses an injected `ICatalogService` object to make that call and communicate with the Catalog API.</span></span> <span data-ttu-id="1b23a-270">Исходная реализация интерфейса, используемая gRPC для выполнения вызова.</span><span class="sxs-lookup"><span data-stu-id="1b23a-270">The original implementation of the interface used gRPC to make the call.</span></span> <span data-ttu-id="1b23a-271">В обновленной реализации используется вызов службы ДАПР с поддержкой HttpClient:</span><span class="sxs-lookup"><span data-stu-id="1b23a-271">The updated implementation uses Dapr service invocation with HttpClient support:</span></span>

``` csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient ?? throw new ArgumentNullException(nameof(httpClient));
    }

    public Task<IEnumerable<CatalogItem>> GetCatalogItemsAsync(IEnumerable<int> ids)
    {
        var requestUri = $"api/v1/catalog/items?ids={string.Join(",", ids)}";

        return _httpClient.GetFromJsonAsync<IEnumerable<CatalogItem>>(requestUri);
    }

    // ...
}
```

<span data-ttu-id="1b23a-272">Обратите внимание, что для выполнения вызова службы не требуется код, относящийся к ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-272">Notice how no Dapr specific code is required to make the service invocation call.</span></span> <span data-ttu-id="1b23a-273">Все взаимодействие выполняется с помощью стандартного объекта HttpClient.</span><span class="sxs-lookup"><span data-stu-id="1b23a-273">All communication is done using the standard HttpClient object.</span></span>

<span data-ttu-id="1b23a-274">ДАПР HttpClient внедряется в `CatalogService` класс в `Startup.ConfigureServices` методе:</span><span class="sxs-lookup"><span data-stu-id="1b23a-274">The Dapr HttpClient is injected into the `CatalogService` class in the `Startup.ConfigureServices` method:</span></span>

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

<span data-ttu-id="1b23a-275">Другой вызов, сделанный службой агрегатора, — это API-интерфейс корзины.</span><span class="sxs-lookup"><span data-stu-id="1b23a-275">The other call made by the aggregator service is to the Basket API.</span></span> <span data-ttu-id="1b23a-276">Он разрешает только разрешенные запросы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-276">It only allows authorized requests.</span></span> <span data-ttu-id="1b23a-277">Маркер доступа передается в заголовке запроса *авторизации* , чтобы обеспечить успешный вызов:</span><span class="sxs-lookup"><span data-stu-id="1b23a-277">The access token is passed along in an *Authorization* request header to ensure the call succeeds:</span></span>

``` csharp
public class BasketService : IBasketService
{
    public Task UpdateAsync(BasketData currentBasket, string accessToken)
    {
        var request = new HttpRequestMessage(HttpMethod.Post, "api/v1/basket")
        {
            Content = JsonContent.Create(currentBasket)
        };
        request.Headers.Authorization = new AuthenticationHeaderValue(accessToken);

        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
    }

    // ...
}
```

<span data-ttu-id="1b23a-278">В этом примере также для вызова службы используются только стандартные функции HttpClient.</span><span class="sxs-lookup"><span data-stu-id="1b23a-278">In this example too, only standard HttpClient functionality is used to call the service.</span></span> <span data-ttu-id="1b23a-279">Это позволяет разработчикам, уже знакомым с HttpClient, повторно использовать имеющиеся навыки.</span><span class="sxs-lookup"><span data-stu-id="1b23a-279">This allows developers who are already familiar with HttpClient to reuse their existing skills.</span></span> <span data-ttu-id="1b23a-280">Он даже позволяет существующему коду HttpClient использовать вызов службы ДАПР без внесения каких бы то ни было изменений.</span><span class="sxs-lookup"><span data-stu-id="1b23a-280">It even enables existing HttpClient code to use Dapr service invocation without making any changes.</span></span>

## <a name="summary"></a><span data-ttu-id="1b23a-281">Итоги</span><span class="sxs-lookup"><span data-stu-id="1b23a-281">Summary</span></span>

<span data-ttu-id="1b23a-282">В этой главе вы узнали о стандартном блоке вызова службы.</span><span class="sxs-lookup"><span data-stu-id="1b23a-282">In this chapter, you learned about the service invocation building block.</span></span> <span data-ttu-id="1b23a-283">Вы узнали, как вызывать удаленные методы, делая прямые вызовы HTTP к ДАПР расширения и с помощью пакета SDK для .NET ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-283">You saw how to invoke remote methods both by making direct HTTP calls to the Dapr sidecar, and by using the Dapr .NET SDK.</span></span>

<span data-ttu-id="1b23a-284">Пакет SDK для ДАПР .NET предоставляет несколько способов вызова удаленных методов.</span><span class="sxs-lookup"><span data-stu-id="1b23a-284">The Dapr .NET SDK provides multiple ways to invoke remote methods.</span></span> <span data-ttu-id="1b23a-285">Поддержка HttpClient отлично подходит для разработчиков, желающих повторно использовать имеющиеся навыки и совместимость с множеством существующих платформ и библиотек.</span><span class="sxs-lookup"><span data-stu-id="1b23a-285">HttpClient support is great for developers wanting to reuse existing skills and is compatible with many existing frameworks and libraries.</span></span> <span data-ttu-id="1b23a-286">Дапрклиент предлагает поддержку непосредственного использования API вызова службы ДАПР, используя семантику HTTP или gRPC.</span><span class="sxs-lookup"><span data-stu-id="1b23a-286">DaprClient offers support for directly using the Dapr service invocation API using either HTTP or gRPC semantics.</span></span>

<span data-ttu-id="1b23a-287">Эталонная архитектура Ешопондапр показывает, как исходное решение eShopOnContainers можно использовать для вызова службы ДАПР.</span><span class="sxs-lookup"><span data-stu-id="1b23a-287">The eShopOnDapr reference architecture shows how the original eShopOnContainers solution is modernized by using Dapr service invocation.</span></span> <span data-ttu-id="1b23a-288">Добавление ДАПР в Ешоп предоставляет такие преимущества, как автоматические повторы, шифрование сообщений с помощью mTLS и улучшенная наблюдаемость.</span><span class="sxs-lookup"><span data-stu-id="1b23a-288">Adding Dapr to eShop provides benefits such as automatic retries, message encryption using mTLS, and improved observability.</span></span>

### <a name="references"></a><span data-ttu-id="1b23a-289">Ссылки</span><span class="sxs-lookup"><span data-stu-id="1b23a-289">References</span></span>

- [<span data-ttu-id="1b23a-290">Стандартный блок вызова службы ДАПР</span><span class="sxs-lookup"><span data-stu-id="1b23a-290">Dapr service invocation building block</span></span>](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [<span data-ttu-id="1b23a-291">Наблюдение за распределенным облаком — собственные приложения</span><span class="sxs-lookup"><span data-stu-id="1b23a-291">Monitoring distributed cloud-native applications</span></span>](../cloud-native/observability-patterns.md)

> [!div class="step-by-step"]
> <span data-ttu-id="1b23a-292">[Назад](state-management.md)
> [Вперед](publish-subscribe.md)</span><span class="sxs-lookup"><span data-stu-id="1b23a-292">[Previous](state-management.md)
[Next](publish-subscribe.md)</span></span>
