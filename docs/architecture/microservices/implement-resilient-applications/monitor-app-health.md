---
title: Мониторинг работоспособности
description: Изучите один из способов реализации мониторинга работоспособности.
ms.date: 01/13/2021
ms.openlocfilehash: 4b85193c260b950b0c7a1c97ca5c83dfc87e5fb3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189067"
---
# <a name="health-monitoring"></a><span data-ttu-id="e3b27-103">Мониторинг работоспособности</span><span class="sxs-lookup"><span data-stu-id="e3b27-103">Health monitoring</span></span>

<span data-ttu-id="e3b27-104">Мониторинг работоспособности позволяет практически в реальном времени получать сведения о состоянии ваших контейнеров и микрослужб.</span><span class="sxs-lookup"><span data-stu-id="e3b27-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="e3b27-105">Мониторинг работоспособности очень важен для нескольких аспектов работы микрослужб и особенно важен, когда оркестраторы выполняют частичное многоэтапное обновление приложений, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="e3b27-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="e3b27-106">Приложения на основе микрослужб часто используют пульс или проверки работоспособности, чтобы системные мониторы, планировщики и оркестраторы могли отслеживать большое количество служб.</span><span class="sxs-lookup"><span data-stu-id="e3b27-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="e3b27-107">Если службам не удается отправить сигнал "Я в порядке", ваше приложение может подвергнуться риску при развертывании обновлений или просто обнаружить ошибки слишком поздно. Это приведет к каскадным сбоям, которые будет невозможно остановить, а они, в свою очередь, приведут к масштабным сбоям.</span><span class="sxs-lookup"><span data-stu-id="e3b27-107">If services cannot send some sort of "I'm alive" signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="e3b27-108">В обычной модели службы отправляют отчеты о своем состоянии, и эти сведения агрегируются для создания общего представления о состоянии работоспособности приложения.</span><span class="sxs-lookup"><span data-stu-id="e3b27-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="e3b27-109">При использовании оркестратора можно предоставить сведения работоспособности кластеру оркестратора, чтобы кластер мог предпринять необходимые действия.</span><span class="sxs-lookup"><span data-stu-id="e3b27-109">If you're using an orchestrator, you can provide health information to your orchestrator's cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="e3b27-110">Если воспользоваться высококачественными средствами создания отчетов о работоспособности, специально адаптированных для вашего приложения, вы сможете гораздо быстрее и эффективнее обнаруживать и устранять проблемы с приложением.</span><span class="sxs-lookup"><span data-stu-id="e3b27-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="e3b27-111">Реализация проверки работоспособности в службах ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e3b27-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="e3b27-112">При разработке микрослужбы или веб-приложения ASP.NET Core можно использовать встроенную функцию проверки работоспособности, выпущенную в ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span><span class="sxs-lookup"><span data-stu-id="e3b27-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="e3b27-113">Как и многие функции ASP.NET Core, проверки работоспособности поставляются с набором служб и ПО промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="e3b27-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="e3b27-114">Службы и ПО промежуточного слоя проверки работоспособности просты в использовании и предоставляют функции, которые позволяют убедиться, что любой внешний ресурс, необходимый для вашего приложения (например, база данных SQL Server или удаленный API), работает правильно.</span><span class="sxs-lookup"><span data-stu-id="e3b27-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="e3b27-115">При использовании этой функции также можно определить критерии работоспособности ресурса, о которых мы расскажем ниже.</span><span class="sxs-lookup"><span data-stu-id="e3b27-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="e3b27-116">Чтобы эффективно использовать эту функцию, необходимо сначала настроить службы в микрослужбах.</span><span class="sxs-lookup"><span data-stu-id="e3b27-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="e3b27-117">Во-вторых, вам понадобится клиентское приложение, которое запрашивает отчеты о работоспособности.</span><span class="sxs-lookup"><span data-stu-id="e3b27-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="e3b27-118">Это клиентское приложение может быть пользовательским приложением для создания отчетов или оркестратором, который будет предпринимать необходимые действия в соответствии с состоянием работоспособности.</span><span class="sxs-lookup"><span data-stu-id="e3b27-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="e3b27-119">Использование функции HealthChecks в серверных микрослужбах ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e3b27-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="e3b27-120">В этом разделе вы узнаете, как реализовать функцию HealthChecks в примере приложения веб-API ASP.NET Core 3.1 при использовании пакета [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="e3b27-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="e3b27-121">Реализация этой функции в крупномасштабных микрослужбах, например eShopOnContainers, рассматривается в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="e3b27-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="e3b27-122">Для начала необходимо определить, что входит в состояние работоспособности для каждой микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="e3b27-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="e3b27-123">В примере приложения мы определяем, что микрослужба находится в работоспособном состоянии, если ее API доступен через HTTP и соответствующая база данных SQL Server также доступна.</span><span class="sxs-lookup"><span data-stu-id="e3b27-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="e3b27-124">В .NET 5 со встроенными API-интерфейсами можно настроить службы, добавить проверку работоспособности для микрослужбы и ее зависимые базы данных SQL Server следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e3b27-124">In .NET 5, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET 5 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

<span data-ttu-id="e3b27-125">В приведенном выше коде метод `services.AddHealthChecks()` настраивает базовую проверку HTTP, которая возвращает код состояния **200** "Работоспособно".</span><span class="sxs-lookup"><span data-stu-id="e3b27-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with "Healthy".</span></span>  <span data-ttu-id="e3b27-126">Далее метод расширения `AddCheck()` настраивает пользовательский `SqlConnectionHealthCheck`, который проверяет работоспособность связанных баз данных SQL.</span><span class="sxs-lookup"><span data-stu-id="e3b27-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database's health.</span></span>

<span data-ttu-id="e3b27-127">Метод `AddCheck()` добавляет новые проверки работоспособности с указанным именем и реализацией типа `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="e3b27-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="e3b27-128">Вы можете добавить несколько проверок работоспособности с помощью метода AddCheck, чтобы микрослужба не отображала состояние "Работоспособно", пока все проверки не покажут работоспособность.</span><span class="sxs-lookup"><span data-stu-id="e3b27-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a "healthy" status until all its checks are healthy.</span></span>

<span data-ttu-id="e3b27-129">`SqlConnectionHealthCheck` — это пользовательский класс, реализующий `IHealthCheck`, который принимает строку подключения в качестве параметра конструктора и выполняет простой запрос для проверки успешного подключения к базе данных SQL.</span><span class="sxs-lookup"><span data-stu-id="e3b27-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="e3b27-130">Он возвращает `HealthCheckResult.Healthy()`, если запрос был выполнен успешно, и `FailureStatus` с исключением, если нет.</span><span class="sxs-lookup"><span data-stu-id="e3b27-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

<span data-ttu-id="e3b27-131">В предыдущем коде `Select 1` — это запрос, который используется для проверки работоспособности базы данных.</span><span class="sxs-lookup"><span data-stu-id="e3b27-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="e3b27-132">Для отслеживания доступности ваших микрослужб оркестраторы, такие как Kubernetes, периодически выполняют проверки работоспособности, отправляя запросы для проверки микрослужб.</span><span class="sxs-lookup"><span data-stu-id="e3b27-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="e3b27-133">Очень важно сохранить эффективность запросов к базе данных, чтобы эти операции выполнялись быстро и не приводили к повышенному использованию ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e3b27-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="e3b27-134">Наконец, добавьте ПО промежуточного слоя, которое отвечает на URL пути `/hc`:</span><span class="sxs-lookup"><span data-stu-id="e3b27-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

```csharp
// Startup.cs from .NET 5 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

<span data-ttu-id="e3b27-135">При вызове конечной точки `<yourmicroservice>/hc` она запускает все проверки работоспособности, которые были настроены в методе `AddHealthChecks()` в классе Startup, и показывает результат.</span><span class="sxs-lookup"><span data-stu-id="e3b27-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="e3b27-136">Реализация HealthChecks в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e3b27-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="e3b27-137">Микрослужбы в eShopOnContainers зависят от нескольких служб, которые выполняют задачи.</span><span class="sxs-lookup"><span data-stu-id="e3b27-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="e3b27-138">Например, микрослужба `Catalog.API` из eShopOnContainers зависит от многих служб, таких как хранилище BLOB-объектов Azure, SQL Server и RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="e3b27-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="e3b27-139">Поэтому к ней добавляется несколько проверок работоспособности с помощью метода `AddCheck()`.</span><span class="sxs-lookup"><span data-stu-id="e3b27-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="e3b27-140">Для каждой зависимой службы необходимо добавить пользовательскую реализацию `IHealthCheck`, которая будет определять соответствующее состояние работоспособности.</span><span class="sxs-lookup"><span data-stu-id="e3b27-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="e3b27-141">Проект с открытым кодом [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) решает эту проблему путем предоставления пользовательских реализаций проверки работоспособности для каждой из этих корпоративных служб, которые построены на основе .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e3b27-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET 5.</span></span> <span data-ttu-id="e3b27-142">Каждая проверка работоспособности доступна в виде отдельного пакета NuGet, который можно легко добавить в проект.</span><span class="sxs-lookup"><span data-stu-id="e3b27-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="e3b27-143">eShopOnContainers широко использует их во всех своих микрослужбах.</span><span class="sxs-lookup"><span data-stu-id="e3b27-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="e3b27-144">Например, в микрослужбе `Catalog.API` добавлены следующие пакеты NuGet:</span><span class="sxs-lookup"><span data-stu-id="e3b27-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Снимок экрана: пакеты NuGet AspNetCore.Diagnostics.HealthChecks.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="e3b27-146">**Рис. 8-7**.</span><span class="sxs-lookup"><span data-stu-id="e3b27-146">**Figure 8-7**.</span></span> <span data-ttu-id="e3b27-147">Пользовательские проверки работоспособности, реализованные в Catalog.API с помощью AspNetCore.Diagnostics.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="e3b27-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="e3b27-148">В следующем коде реализации проверки работоспособности добавляются для каждой зависимой службы, а затем настраивается ПО промежуточного слоя:</span><span class="sxs-lookup"><span data-stu-id="e3b27-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

<span data-ttu-id="e3b27-149">Наконец, добавьте ПО промежуточного слоя проверки работоспособности для ожидания передачи данных от конечной точки "/hc":</span><span class="sxs-lookup"><span data-stu-id="e3b27-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="e3b27-150">Отправка запроса состояния работоспособности у микрослужб</span><span class="sxs-lookup"><span data-stu-id="e3b27-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="e3b27-151">Настроив проверки работоспособности, описанные в этой статье, вы можете непосредственно проверить работоспособность микрослужбы из браузера, если эта микрослужба запущена в Docker.</span><span class="sxs-lookup"><span data-stu-id="e3b27-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="e3b27-152">Для этого необходимо опубликовать порт контейнера в узле Docker, чтобы вы могли обращаться к контейнеру по внешнему IP-адресу узла Docker или через `localhost`, как показано на рисунке 8-8.</span><span class="sxs-lookup"><span data-stu-id="e3b27-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Снимок экрана: ответ в формате JSON, полученный при проверке работоспособности.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="e3b27-154">**Рис. 8-8**.</span><span class="sxs-lookup"><span data-stu-id="e3b27-154">**Figure 8-8**.</span></span> <span data-ttu-id="e3b27-155">Проверка состояния работоспособности для одной службы из браузера</span><span class="sxs-lookup"><span data-stu-id="e3b27-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="e3b27-156">В этом тесте видно, что микрослужба `Catalog.API` (которая запущена на порте 5101) находится в работоспособном состоянии. Она возвращает код HTTP 200 и сведения о состоянии в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="e3b27-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="e3b27-157">Служба также проверила работоспособность зависимости базы данных SQL Server и RabbitMQ, и проверка сообщила о работоспособности.</span><span class="sxs-lookup"><span data-stu-id="e3b27-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="e3b27-158">Использование наблюдателей</span><span class="sxs-lookup"><span data-stu-id="e3b27-158">Use watchdogs</span></span>

<span data-ttu-id="e3b27-159">Наблюдатель — это отдельная служба, которая отслеживает работоспособность и загрузку различных служб и отправляет отчет о работоспособности микрослужб, опрашивая библиотеку `HealthChecks`, о которой мы рассказывали ранее.</span><span class="sxs-lookup"><span data-stu-id="e3b27-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="e3b27-160">Это помогает предотвратить ошибки, которые не будут обнаружены для представления одной службы.</span><span class="sxs-lookup"><span data-stu-id="e3b27-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="e3b27-161">В наблюдателях также можно размещать код, который может выполнять действия по исправлению для известных условий без вмешательства пользователя.</span><span class="sxs-lookup"><span data-stu-id="e3b27-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="e3b27-162">Пример eShopOnContainers содержит веб-страницу с примерами отчетов о проверке работоспособности, как показано на рис. 8-9.</span><span class="sxs-lookup"><span data-stu-id="e3b27-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="e3b27-163">Это простейший наблюдатель, который можно создать, так как он только отображает состояние микрослужб и веб-приложений в eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e3b27-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="e3b27-164">Обычно наблюдатель предпринимает необходимые действия при обнаружении состояний неработоспособности.</span><span class="sxs-lookup"><span data-stu-id="e3b27-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="e3b27-165">К счастью, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) также предоставляет пакет NuGet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/), который можно использовать для отображения результатов проверки работоспособности на основе настроенных URI.</span><span class="sxs-lookup"><span data-stu-id="e3b27-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Снимок экрана: состояние работоспособности eShopOnContainers в пользовательском интерфейсе проверки работоспособности.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="e3b27-167">**Рис. 8-9**.</span><span class="sxs-lookup"><span data-stu-id="e3b27-167">**Figure 8-9**.</span></span> <span data-ttu-id="e3b27-168">Пример отчета о проверке работоспособности в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e3b27-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="e3b27-169">Таким образом, эта служба наблюдения запрашивает конечную точку "/hc" каждой микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="e3b27-169">In summary, this watchdog service queries each microservice's "/hc" endpoint.</span></span> <span data-ttu-id="e3b27-170">При этом будут выполнены все проверки работоспособности, определенные в этой конечной точке, и возвращено общее состояние работоспособности в зависимости от результатов этих проверок.</span><span class="sxs-lookup"><span data-stu-id="e3b27-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="e3b27-171">HealthChecksUI удобно использовать с несколькими записями конфигурации и двумя строками кода, которые нужно добавить в *Startup.cs* службы наблюдения.</span><span class="sxs-lookup"><span data-stu-id="e3b27-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the *Startup.cs* of the watchdog service.</span></span>

<span data-ttu-id="e3b27-172">Пример файла конфигурации для пользовательского интерфейса проверки работоспособности:</span><span class="sxs-lookup"><span data-stu-id="e3b27-172">Sample configuration file for health check UI:</span></span>

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

<span data-ttu-id="e3b27-173">Файл *Startup.cs*, который добавляет HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="e3b27-173">*Startup.cs* file that adds HealthChecksUI:</span></span>

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config => config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="e3b27-174">Проверка работоспособности при использовании оркестраторов</span><span class="sxs-lookup"><span data-stu-id="e3b27-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="e3b27-175">Для отслеживания доступности ваших микрослужб оркестраторы, такие как Kubernetes и Service Fabric, периодически выполняют проверки работоспособности, отправляя запросы для проверки микрослужб.</span><span class="sxs-lookup"><span data-stu-id="e3b27-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="e3b27-176">Когда оркестратор определяет, что служба или контейнер неработоспособны, она перестает направлять запросы к этому экземпляру.</span><span class="sxs-lookup"><span data-stu-id="e3b27-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="e3b27-177">Она также обычно создает новый экземпляр этого контейнера.</span><span class="sxs-lookup"><span data-stu-id="e3b27-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="e3b27-178">Например, большинство оркестраторов могут использовать проверки работоспособности для реализации развертываний без простоев.</span><span class="sxs-lookup"><span data-stu-id="e3b27-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="e3b27-179">Оркестратор начинает направлять трафик к службе или контейнеру только после того, как состояние службы или контейнера изменится на работоспособное.</span><span class="sxs-lookup"><span data-stu-id="e3b27-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="e3b27-180">Мониторинг работоспособности особенно важен, когда оркестратор выполняет обновление приложения.</span><span class="sxs-lookup"><span data-stu-id="e3b27-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="e3b27-181">Некоторые оркестраторы (например, Azure Service Fabric) обновляют службы поэтапно, например, они могут обновлять одну пятую поверхности кластера при каждом обновлении.</span><span class="sxs-lookup"><span data-stu-id="e3b27-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="e3b27-182">Набор узлов, обновляемых одновременно, называется *доменом обновления*.</span><span class="sxs-lookup"><span data-stu-id="e3b27-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="e3b27-183">После того как каждый домен обновления был обновлен и стал доступен для пользователей, этот домен обновления должен пройти проверку работоспособности перед тем, как развертывание перейдет к следующему домену обновления.</span><span class="sxs-lookup"><span data-stu-id="e3b27-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="e3b27-184">Другой аспект работоспособности службы — метрики отчетов из службы.</span><span class="sxs-lookup"><span data-stu-id="e3b27-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="e3b27-185">Это сложная функция модели работоспособности для некоторых оркестраторов, например Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="e3b27-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="e3b27-186">Метрики важны при использовании оркестраторов, так как они применяются для балансировки использования ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e3b27-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="e3b27-187">Метрики также могут быть индикатором работоспособности системы.</span><span class="sxs-lookup"><span data-stu-id="e3b27-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="e3b27-188">Например, у вас может быть приложение с несколькими микрослужбами, и каждый экземпляр микрослужбы передает метрику "Количество запросов в секунду" (RPS).</span><span class="sxs-lookup"><span data-stu-id="e3b27-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="e3b27-189">Если одна служба использует больше ресурсов (память, процессор и т. д.), чем другая служба, оркестратор может переместить экземпляры служб в кластере для равномерного использования ресурсов.</span><span class="sxs-lookup"><span data-stu-id="e3b27-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="e3b27-190">Обратите внимание, что в Azure Service Fabric есть собственная [модель мониторинга работоспособности](/azure/service-fabric/service-fabric-health-introduction), которая является более сложной по сравнению с простыми решениями для проверки.</span><span class="sxs-lookup"><span data-stu-id="e3b27-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="e3b27-191">Расширенный мониторинг: визуализация, анализ и предупреждения</span><span class="sxs-lookup"><span data-stu-id="e3b27-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="e3b27-192">Последний компонент мониторинга — визуализация потока событий, отчеты о производительности службы и оповещения при обнаружении проблем.</span><span class="sxs-lookup"><span data-stu-id="e3b27-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="e3b27-193">Для реализации этого компонента мониторинга можно использовать различные решения.</span><span class="sxs-lookup"><span data-stu-id="e3b27-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="e3b27-194">Можно использовать простые пользовательские приложения, которые отображают состояние служб, например пользовательскую страницу, о которой идет речь в описании библиотеки [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="e3b27-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="e3b27-195">Или можно использовать более сложные инструменты, такие как [Azure Monitor](https://azure.microsoft.com/services/monitor/), которые будут вызывать оповещения на основе потока событий.</span><span class="sxs-lookup"><span data-stu-id="e3b27-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="e3b27-196">Наконец, если вы сохраняете все потоки событий, для визуализации данных можно использовать Microsoft Power BI или решения других поставщиков, например Kibana или Splunk.</span><span class="sxs-lookup"><span data-stu-id="e3b27-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e3b27-197">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="e3b27-197">Additional resources</span></span>

- <span data-ttu-id="e3b27-198">**HealthChecks и пользовательский интерфейс HealthChecks для ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e3b27-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="e3b27-199">**Общие сведения о мониторинге работоспособности Service Fabric** </span><span class="sxs-lookup"><span data-stu-id="e3b27-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="e3b27-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="e3b27-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="e3b27-201">[Назад](implement-circuit-breaker-pattern.md)
>[Вперед](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e3b27-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
