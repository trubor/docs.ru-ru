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
# <a name="the-dapr-service-invocation-building-block"></a>Стандартный блок вызова службы ДАПР

В распределенной системе одной службе часто требуется взаимодействовать с другой службой для выполнения бизнес-операций. [Стандартный блок вызова службы ДАПР](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/) помогает упростить обмен данными между службами.

## <a name="what-it-solves"></a>Решение

Выполнение вызовов между службами в распределенном приложении может показаться непростым, но существует множество проблем. Например:

- Где расположены другие службы.
- Как безопасно вызывать службу с учетом адреса службы.
- Как выполнять повторные попытки при возникновении кратковременных [временных ошибок](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) .

Наконец, поскольку распределенные приложения состоят из множества различных служб, сбор аналитических сведений между графами вызовов служб очень важен для диагностики проблем в рабочей среде.

Стандартный блок вызова службы решает эти проблемы, используя ДАПР расширения в качестве [обратных прокси-серверов](https://kemptechnologies.com/reverse-proxy/reverse-proxy/) для службы.

## <a name="how-it-works"></a>Принцип работы

Начнем с примера. Рассмотрим две службы: "Service A" и "Service B". Службе A необходимо вызвать `catalog/items` API для службы б. Хотя служба A может взять зависимость от службы б и выполнить прямой вызов, служба а вместо этого вызывает API вызова службы на ДАПР расширения. На рис. 6-1 показана операция.

![Как работает вызов службы ДАПР](./media/service-invocation/service-invocation-flow.png)

**Рис. 6-1**. Как работает вызов службы ДАПР.

Обратите внимание на шаги, приведенные на предыдущем рисунке.

1. Служба A вызывает `catalog/items` конечную точку в службе B, вызывая API вызова службы в службе A расширения.

    > [!NOTE]
    > Расширения использует подключаемый механизм разрешения имен для разрешения адреса службы б. В режиме с автономным размещением ДАПР использует [MDN](https://www.ionos.com/digitalguide/server/know-how/multicast-dns/) для его поиска. При работе в режиме Kubernetes служба DNS Kubernetes определяет адрес.  

1. Служба A расширения перенаправляет запрос к службе B расширения.

1. Служба B расширения выполняет фактический `catalog/items` запрос к API-интерфейсу Service b.

1. Служба б выполняет запрос и возвращает ответ обратно в его расширения.

1. Служба б расширения перенаправляет ответ обратно в службу A расширения.

1. Служба A расширения возвращает ответ обратно службе.

Так как вызовы проходят через сидекарс, ДАПР может внедрить некоторые полезные перекрестные поведения:

- Автоматически повторять вызовы при сбое.
- Обеспечьте безопасность вызовов между службами с помощью взаимной проверки подлинности (mTLS), включая автоматическую смену сертификатов.
- Контролируйте, какие операции клиенты могут выполнять с помощью политик управления доступом.
- Сбор трассировок и метрик для всех вызовов между службами для получения ценной информации и диагностики.

Любое приложение может вызвать расширения ДАПР с помощью собственного API **вызова** , встроенного в ДАПР. API можно вызывать с помощью HTTP или gRPC. Используйте следующий URL-адрес для вызова API HTTP:

``` http
http://localhost:<dapr-port>/v1.0/invoke/<application-id>/method/<method-name>
```

- `<dapr-port>` HTTP-порт, прослушиваемый ДАПР.
- `<application-id>` Идентификатор приложения для вызова.
- `<method-name>` имя метода, вызываемого в удаленной службе.

В следующем примере *выполняется вызов с помощью* приведения к `catalog/items` конечной точке Get `Service B` :

```console
curl http://localhost:3500/v1.0/invoke/serviceb/method/catalog/items
```

> [!NOTE]
> Интерфейсы API ДАПР позволяют любому стеку приложений, поддерживающему HTTP или gRPC, использовать стандартные блоки ДАПР. Таким образом, Стандартный блок вызова службы может действовать как мост между протоколами. Службы могут взаимодействовать друг с другом с помощью протокола HTTP, gRPC или их комбинации.

В следующем разделе вы узнаете, как использовать пакет SDK для .NET, чтобы упростить вызовы вызова служб.

## <a name="use-the-dapr-net-sdk"></a>Использование пакета SDK для ДАПР .NET

[Пакет SDK](https://github.com/dapr/dotnet-sdk) для ДАПР .net предоставляет разработчикам .NET интуитивно понятный и языковый способ взаимодействия с ДАПР. Пакет SDK предоставляет разработчикам три способа выполнения вызовов удаленного вызова службы:

1. Вызов служб HTTP с помощью HttpClient
1. Вызов служб HTTP с помощью Дапрклиент
1. Вызов служб gRPC с помощью Дапрклиент

### <a name="invoke-http-services-using-httpclient"></a>Вызов служб HTTP с помощью HttpClient

Предпочтительным способом вызова конечной точки HTTP является использование расширенной интеграции ДАПР с `HttpClient` . В следующем примере заказ отправляется путем вызова `submit` метода `orderservice` приложения:

```csharp
var httpClient = DaprClient.CreateHttpClient();
await httpClient.PostAsJsonAsync("http://orderservice/submit", order);
```

В этом примере `DaprClient.CreateHttpClient` возвращает `HttpClient` экземпляр, который используется для выполнения вызова службы ДАПР. Возвращаемый объект `HttpClient` использует специальный обработчик сообщений ДАПР, который перезаписывает URI исходящих запросов. Имя узла интерпретируется как идентификатор приложения для вызова. Фактически вызывается перезаписанный запрос:

```http
http://127.0.0.1:3500/v1/invoke/orderservice/method/submit
```

В этом примере используется значение по умолчанию для конечной точки HTTP ДАПР, то есть `http://127.0.0.1:<dapr-http-port>/` . Значение `dapr-http-port` берется из `DAPR_HTTP_PORT` переменной среды. Если он не задан, используется номер порта по умолчанию `3500` .

Кроме того, можно настроить пользовательскую конечную точку в вызове `DaprClient.CreateHttpClient` :

```csharp
var httpClient = DaprClient.CreateHttpClient(daprEndpoint = "localhost:4000");
```

Можно также напрямую задать базовый адрес, указав идентификатор приложения. Это позволяет использовать относительные URI при совершении вызова:

```csharp
var httpClient = DaprClient.CreateHttpClient("orderservice");
await httpClient.PostAsJsonAsync("/submit");
```

`HttpClient`Объект должен быть длительным. Один `HttpClient` экземпляр можно повторно использовать в течение времени существования приложения. В следующем сценарии показано, как `OrderServiceClient` класс повторно использует экземпляр ДАПР `HttpClient` :  

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddSingleton<IOrderServiceClient, OrderServiceClient>(
        _ => new OrderServiceClient(DaprClient.CreateInvokeHttpClient("orderservice")));
}
```

В приведенном выше фрагменте объект `OrderServiceClient` регистрируется как одноэлементный с системой внедрения зависимостей ASP.NET Core. Фабрика реализации создает новый `HttpClient` экземпляр путем вызова метода `DaprClient.CreateInvokeHttpClient` . Затем он использует только что созданный `HttpClient` объект для создания экземпляра `OrderServiceClient` объекта. Регистрация в `OrderServiceClient` качестве одноэлементного экземпляра будет повторно использоваться в течение времени существования приложения.

`OrderServiceClient`Сам по себе не имеет кода, зависящего от ДАПР. Несмотря на то, что вызов службы ДАПР используется внутри, можно считать ДАПР HttpClient, как и любые другие HttpClient:

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

Использование класса HttpClient с вызовом службы ДАПР имеет много преимуществ:

- HttpClient — хорошо известный класс, который многие разработчики уже используют в своем коде. Использование HttpClient для вызова службы ДАПР позволяет разработчикам повторно использовать имеющиеся навыки.
- HttpClient поддерживает расширенные сценарии, такие как пользовательские заголовки, и полный контроль над сообщениями запросов и ответов.
- В .NET 5 HttpClient поддерживает автоматическую сериализацию и десериализацию с помощью System.Text.Jsв.
- HttpClient интегрируется с множеством существующих платформ и библиотек, таких как [refit](https://github.com/reactiveui/refit), [рестшарп](https://restsharp.dev/getting-started/getting-started.html#basic-usage)и [Polly](https://github.com/App-vNext/Polly).

### <a name="invoke-http-services-using-daprclient"></a>Вызов служб HTTP с помощью Дапрклиент

Хотя HttpClient является предпочтительным способом вызова служб с использованием семантики HTTP, можно также использовать `DaprClient.InvokeMethodAsync` семейство методов. В следующем примере заказ отправляется путем вызова `submit` метода `orderservice` приложения:

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

Третий аргумент, `order` объект, сериализуется внутренне (с `System.Text.JsonSerializer` ) и отправляется в качестве полезных данных запроса. Пакет SDK для .NET позаботится о вызове расширения. Он также Десериализует ответ на `OrderConfirmation` объект. Поскольку метод HTTP не указан, запрос выполняется как HTTP POST.

В следующем примере показано, как можно выполнить HTTP-запрос GET, указав `HttpMethod` :

```csharp
var catalogItems = await daprClient.InvokeMethodAsync<IEnumerable<CatalogItem>>(HttpMethod.Get, "catalogservice", "items");
```

В некоторых сценариях может потребоваться больший контроль над сообщением запроса. Например, если необходимо указать заголовки запроса или вы хотите использовать пользовательский сериализатор для полезных данных. `DaprClient.CreateInvokeMethodRequest` создает `HttpRequestMessage` . В следующем примере показано, как добавить заголовок авторизации HTTP к сообщению запроса:

```csharp
var request = daprClient.CreateInvokeMethodRequest("orderservice", "submit", order);
request.Headers.Authorization = new AuthenticationHeaderValue("bearer", token);
```

`HttpRequestMessage`Теперь установлены следующие свойства:

- URL-адрес = `http://127.0.0.1:3500/v1.0/invoke/orderservice/method/submit`
- HttpMethod = POST
- Content =  `JsonContent` объект, содержащий сериализованный JSON `order`
- Headers. Authorization = "Bearer \<token> "

Когда запрос будет настроен так, как вам нужно, используйте `DaprClient.InvokeMethodAsync` для его отправки:

```csharp
var orderConfirmation = await daprClient.InvokeMethodAsync<OrderConfirmation>(request);
```

`DaprClient.InvokeMethodAsync` Десериализует ответ на `OrderConfirmation` объект, если запрос выполнен успешно. Кроме того, можно использовать `DaprClient.InvokeMethodWithResponseAsync` для получения полного доступа к базовому `HttpResponseMessage` :

```csharp
var response = await daprClient.InvokeMethodWithResponseAsync(request);
response.EnsureSuccessStatusCode();

var orderConfirmation = response.Content.ReadFromJsonAsync<OrderConfirmation>();
```

> [!NOTE]
> Для вызовов вызова служб по протоколу HTTP стоит рассмотреть использование интеграции ДАПР HttpClient, представленной в предыдущем разделе. Использование HttpClient предоставляет дополнительные преимущества, такие как интеграция с существующими платформами и библиотеками.

### <a name="invoke-grpc-services-using-daprclient"></a>Вызов служб gRPC с помощью Дапрклиент

Дапрклиент предоставляет семейство `InvokeMethodGrpcAsync` методов для вызова конечных точек gRPC. Основное отличие от методов HTTP заключается в использовании сериализатора protobuf, а не JSON. В следующем примере вызывается `submitOrder` метод класса `orderservice` over gRPC.

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

В приведенном выше примере Дапрклиент Сериализует данный `order` объект с помощью [protobuf](https://developers.google.com/protocol-buffers) и использует результат в качестве тела запроса gRPC. Аналогичным образом, текст ответа protobuf десериализуется и возвращается вызывающему объекту. Protobuf обычно обеспечивает лучшую производительность, чем полезные данные JSON, используемые в вызове службы HTTP.

## <a name="reference-application-eshopondapr"></a>Эталонное приложение: Ешопондапр

Исходная Эталонная архитектура микрослужбы [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) от корпорации Майкрософт использует сочетание служб HTTP/RESTful и gRPC Services. Использование gRPC было ограничено обменом данными между [службой агрегатора](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) и основными серверными службами. На рис. 6-2 показана архитектура:

![вызовы gRPC и HTTP/RESTFUL в eShopOnContainers](./media/service-invocation/eshop-on-containers.png)

**Рис. 6-2**. вызовы gRPC и HTTP/RESTFUL в eShopOnContainers.

Обратите внимание на шаги, приведенные на предыдущем рисунке.

1. Внешний интерфейс вызывает [шлюз API](/azure/architecture/microservices/design/gateway) с помощью протокола HTTP/RESTful.

1. Шлюз API перенаправляет простые запросы [CRUD](https://www.sumologic.com/glossary/crud/) (создание, чтение, обновление и удаление) непосредственно в основную серверную службу с помощью протокола HTTP/RESTful.

1. Шлюз API перенаправляет сложные запросы, которые подразумевают координированные вызовы к нескольким внутренним службам, в службу агрегатора веб-покупок.

1. Служба агрегатора использует gRPC для вызова основных серверных служб.

В недавно обновленной реализации Ешопондапр в службы и шлюз API добавляются ДАПР сидекарс. На рис. 6-3 показана Обновленная архитектура:

![вызовы gRPC и HTTP/RESTFUL с сидекарс в eShopOnContainers](./media/service-invocation/eshop-on-dapr.png)

**Рис. 6-3.** Обновлена архитектура Ешоп с помощью ДАПР.

Обратите внимание на обновленные шаги, приведенные на предыдущем рисунке.

1. Внешний интерфейс по-прежнему использует протокол HTTP/RESTFUL для вызова шлюза API.

1. Шлюз API перенаправляет HTTP-запросы к своему ДАПР расширения.

1. Расширения шлюза API отправляет запрос в расширения агрегатора или серверной службы.

1. Служба агрегатора использует пакет SDK для .NET ДАПР для вызова внутренних служб через их архитектуру расширения.

ДАПР реализует вызовы между сидекарс и gRPC. Поэтому даже при вызове удаленной службы с семантикой HTTP/RESTFUL часть транспорта по-прежнему реализуется с помощью gRPC.

Преимущества эталонного приложения Ешопондапр из стандартного блока вызова службы ДАПР. К преимуществам относятся обнаружение служб, автоматическая функция mTLS и наблюдаемость.

### <a name="forward-http-requests-using-envoy-and-dapr"></a>Пересылка HTTP-запросов с помощью делегата и ДАПР

Как исходное, так и обновленное приложение Ешоп использует [прокси-сервер делегата](https://www.envoyproxy.io/) в качестве шлюза API. Делегат — это прокси-сервер с открытым исходным кодом и шина связи, которые популярны среди современных распределенных приложений. Исходя из Лифт, представитель владеет и обслуживается [облачной вычислительной средой](https://www.cncf.io/).

В первоначальной реализации eShopOnContainers шлюз API делегата перенаправляет входящие HTTP-запросы непосредственно в агрегаторы или серверные службы. В новом Ешопондапр прокси-сервер перенаправляет запрос в ДАПР расширения. Расширения обеспечивает вызов службы, mTLS и наблюдаемость.

Представитель настраивается с помощью файла определения YAML для управления поведением прокси-сервера. Чтобы разрешить представителю пересылать HTTP-запросы в контейнер ДАПР расширения, в `dapr` конфигурацию добавляется кластер. Конфигурация кластера содержит узел, указывающий на HTTP-порт, который прослушивает расширения ДАПР:

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

Конфигурация маршрутизации делегатов обновляется для перезаписи входящих запросов в виде вызовов ДАПР расширения (Обратите особое внимание на `prefix_rewrite` пару "ключ-значение"):

``` yaml
- name: "c-short"
  match:
    prefix: "/c/"
  route:
    auto_host_rewrite: true
    prefix_rewrite: "/v1.0/invoke/catalog-api/method/"
    cluster: dapr
```

Рассмотрим ситуацию, когда клиент переднего плана хочет получить список элементов каталога. API каталога предоставляет конечную точку для получения элементов каталога:

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

Во-первых, внешний интерфейс выполняет прямой вызов HTTP к шлюзу API делегата.

```
GET http://<api-gateway>/c/api/v1/catalog/items?pageSize=20
```

Прокси-сервер делегата соответствует маршруту, переписывает HTTP-запрос и пересылает его `invoke` API ДАПР расширения:

```
GET http://127.0.0.1:3500/v1.0/invoke/catalog-api/method/api/v1/catalog/items?pageSize=20
```

Расширения обрабатывает обнаружение службы и направляет запрос в расширения API каталога. Наконец, расширения вызывает API каталога для выполнения запроса, получения элементов каталога и возврата ответа:

```
GET http://localhost/api/v1/catalog/items?pageSize=20
```

### <a name="make-aggregated-service-calls-using-the-net-sdk"></a>Осуществление агрегированных вызовов служб с помощью пакета SDK для .NET

Большинство вызовов из внешнего интерфейса Ешоп являются простыми вызовами CRUD. Шлюз API перенаправляет их в одну службу для обработки. Однако в некоторых случаях требуется, чтобы несколько серверных служб работали вместе для выполнения запроса. Для этих более сложных вызовов Ешоп использует службу агрегации веб-покупок, чтобы исправлять рабочий процесс по нескольким службам. Рис. 6-4. отображение последовательности действий по добавлению элемента в корзину для покупок:

![Схема последовательностей обновления корзины](./media/service-invocation/complex-call.png)

**Рис. 6-4**. Обновление последовательности покупательских корзин.

Служба агрегатора сначала извлекает элементы каталога из API каталога. Затем он проверяет доступность и цены номенклатуры. Наконец, служба агрегатора сохраняет обновленную корзину покупок, вызывая API корзины.

Служба агрегатора содержит `BasketController` , который предоставляет конечную точку для обновления корзины покупок:

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

`UpdateAllBasketAsync`Метод получает заголовок *авторизации* входящего запроса, используя `FromHeader` атрибут. Заголовок *authorization* содержит маркер доступа, необходимый для вызова защищенных серверных служб.

После получения запроса на обновление корзины служба агрегатора вызывает API каталога для получения сведений об элементе. Контроллер подсистемы подбора использует внедренный `ICatalogService` объект, чтобы сделать вызов и взаимодействовать с API каталога. Исходная реализация интерфейса, используемая gRPC для выполнения вызова. В обновленной реализации используется вызов службы ДАПР с поддержкой HttpClient:

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

Обратите внимание, что для выполнения вызова службы не требуется код, относящийся к ДАПР. Все взаимодействие выполняется с помощью стандартного объекта HttpClient.

ДАПР HttpClient внедряется в `CatalogService` класс в `Startup.ConfigureServices` методе:

```csharp
services.AddSingleton<ICatalogService, CatalogService>(
    _ => new CatalogService(DaprClient.CreateInvokeHttpClient("catalog-api")));
```

Другой вызов, сделанный службой агрегатора, — это API-интерфейс корзины. Он разрешает только разрешенные запросы. Маркер доступа передается в заголовке запроса *авторизации* , чтобы обеспечить успешный вызов:

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

В этом примере также для вызова службы используются только стандартные функции HttpClient. Это позволяет разработчикам, уже знакомым с HttpClient, повторно использовать имеющиеся навыки. Он даже позволяет существующему коду HttpClient использовать вызов службы ДАПР без внесения каких бы то ни было изменений.

## <a name="summary"></a>Итоги

В этой главе вы узнали о стандартном блоке вызова службы. Вы узнали, как вызывать удаленные методы, делая прямые вызовы HTTP к ДАПР расширения и с помощью пакета SDK для .NET ДАПР.

Пакет SDK для ДАПР .NET предоставляет несколько способов вызова удаленных методов. Поддержка HttpClient отлично подходит для разработчиков, желающих повторно использовать имеющиеся навыки и совместимость с множеством существующих платформ и библиотек. Дапрклиент предлагает поддержку непосредственного использования API вызова службы ДАПР, используя семантику HTTP или gRPC.

Эталонная архитектура Ешопондапр показывает, как исходное решение eShopOnContainers можно использовать для вызова службы ДАПР. Добавление ДАПР в Ешоп предоставляет такие преимущества, как автоматические повторы, шифрование сообщений с помощью mTLS и улучшенная наблюдаемость.

### <a name="references"></a>Ссылки

- [Стандартный блок вызова службы ДАПР](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/)

- [Наблюдение за распределенным облаком — собственные приложения](../cloud-native/observability-patterns.md)

> [!div class="step-by-step"]
> [Назад](state-management.md)
> [Вперед](publish-subscribe.md)
