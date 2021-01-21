---
title: Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Новые варианты использования IHostedService и BackgroundService для реализации фоновых задач в микрослужбах .NET Core.
ms.date: 01/13/2021
ms.openlocfilehash: 26bc06c4a63cddcd32bf7da705f6258fab8eaafa
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188807"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="3f06b-103">Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService</span><span class="sxs-lookup"><span data-stu-id="3f06b-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="3f06b-104">Фоновые задачи и запланированные задания обычно требуется использовать в любом приложении независимо от того, строится ли оно на основе архитектуры микрослужб.</span><span class="sxs-lookup"><span data-stu-id="3f06b-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="3f06b-105">Разница при использовании архитектуры микрослужб в том, что вы можете реализовать фоновую задачу в отдельном процессе или контейнере, чтобы затем масштабировать его по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="3f06b-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="3f06b-106">Если посмотреть шире, в .NET такие задачи называются *размещенными службами*, так как они представляют собой службы или логику, размещаемые в узле, приложении или микрослужбе.</span><span class="sxs-lookup"><span data-stu-id="3f06b-106">From a generic point of view, in .NET we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="3f06b-107">Обратите внимание на то, что в этом случае под размещенной службой понимается просто класс с логикой фоновой задачи.</span><span class="sxs-lookup"><span data-stu-id="3f06b-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="3f06b-108">Начиная с версии .NET Core 2.0, платформа предоставляет новый интерфейс <xref:Microsoft.Extensions.Hosting.IHostedService>, который позволяет легко реализовывать размещенные службы.</span><span class="sxs-lookup"><span data-stu-id="3f06b-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="3f06b-109">Главная идея заключается в том, что вы можете регистрировать несколько фоновых задач (размещенных служб), которые выполняются в фоновом режиме в процессе работы веб-узла или обычного узла, как показано на рис. 6-26.</span><span class="sxs-lookup"><span data-stu-id="3f06b-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Схема сравнения IWebHost в ASP.NET Core и IHost в .NET Core.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="3f06b-111">**Рис. 6-26**.</span><span class="sxs-lookup"><span data-stu-id="3f06b-111">**Figure 6-26**.</span></span> <span data-ttu-id="3f06b-112">Использование интерфейса IHostedService в классах WebHost и Host</span><span class="sxs-lookup"><span data-stu-id="3f06b-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="3f06b-113">ASP.NET Core версий 1.x и 2.x поддерживает `IWebHost` для фоновых процессов в веб-приложениях.</span><span class="sxs-lookup"><span data-stu-id="3f06b-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="3f06b-114">.NET Core 2.1 и более поздних версий поддерживает `IHost` для фоновых процессов с простыми консольными приложениями.</span><span class="sxs-lookup"><span data-stu-id="3f06b-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="3f06b-115">Обратите внимание на различие между `WebHost` и `Host`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="3f06b-116">`WebHost` (базовый класс, реализующий интерфейс `IWebHost`) в ASP.NET Core 2.0 — это артефакт инфраструктуры, с помощью которого процесс получает доступ к возможностям сервера HTTP, например при реализации веб-приложения MVC или службы веб-интерфейса API.</span><span class="sxs-lookup"><span data-stu-id="3f06b-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="3f06b-117">Он предоставляет все новые преимущества инфраструктуры в ASP.NET Core, позволяя использовать внедрение зависимостей, вставлять промежуточные слои в конвейер запросов и т. д.</span><span class="sxs-lookup"><span data-stu-id="3f06b-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="3f06b-118">`WebHost` использует те же `IHostedServices` для фоновых задач.</span><span class="sxs-lookup"><span data-stu-id="3f06b-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="3f06b-119">Объект `Host` (базовый класс, реализующий `IHost`) впервые появился в .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="3f06b-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="3f06b-120">По существу, класс `Host` обеспечивает практически такую же инфраструктуру, что и класс `WebHost` (внедрение зависимостей, размещенные службы и т. д.), но в этом случае узел должен представлять собой более простой процесс без связанных с MVC веб-интерфейсами API или сервером HTTP возможностей.</span><span class="sxs-lookup"><span data-stu-id="3f06b-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="3f06b-121">Таким образом, вы можете либо создать специальный хост-процесс с помощью `IHost` для реализации только размещенных служб, например микрослужбу, предназначенную для размещения `IHostedServices`, либо расширить существующий в ASP.NET Core класс `WebHost`, например существующий веб-интерфейс API ASP.NET Core или приложение MVC.</span><span class="sxs-lookup"><span data-stu-id="3f06b-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="3f06b-122">Каждый подход имеет свои преимущества и недостатки в зависимости от потребностей бизнеса и требований к масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="3f06b-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="3f06b-123">Основной принцип заключается в том, что если фоновые задачи не связаны с HTTP (`IWebHost`), следует использовать интерфейс `IHost`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="3f06b-124">Регистрация размещенных служб в WebHost или Host</span><span class="sxs-lookup"><span data-stu-id="3f06b-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="3f06b-125">Давайте более подробно разберем интерфейс `IHostedService`, так как его использование в классах `WebHost` и `Host` во многом схоже.</span><span class="sxs-lookup"><span data-stu-id="3f06b-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="3f06b-126">Библиотека SignalR — один из примеров артефактов, использующих размещенные службы, однако ее можно применять и для более простых задач, таких как следующие:</span><span class="sxs-lookup"><span data-stu-id="3f06b-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="3f06b-127">фоновая задача опроса базы данных для поиска изменений;</span><span class="sxs-lookup"><span data-stu-id="3f06b-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="3f06b-128">запланированная задача для периодического обновления кэша;</span><span class="sxs-lookup"><span data-stu-id="3f06b-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="3f06b-129">реализация QueueBackgroundWorkItem, которая позволяет задаче выполняться в фоновом потоке;</span><span class="sxs-lookup"><span data-stu-id="3f06b-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="3f06b-130">обработка сообщений из очереди сообщений веб-приложения в фоновом режиме при использовании общих служб, таких как `ILogger`;</span><span class="sxs-lookup"><span data-stu-id="3f06b-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="3f06b-131">фоновая задача, запускаемая с помощью `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="3f06b-132">Выполнение любого из этих действий можно перенести в фоновую задачу, которая реализует `IHostedService`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="3f06b-133">Для добавления одного или нескольких экземпляров `IHostedServices` в `WebHost` или `Host` их следует зарегистрировать посредством метода расширения <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> в классе ASP.NET Core `WebHost` (или в классе `Host` в .NET Core 2.1 и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="3f06b-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="3f06b-134">Фактически размещенные службы регистрируются в известном методе `ConfigureServices()` класса `Startup`, как в следующем коде типичного класса ASP.NET WebHost:</span><span class="sxs-lookup"><span data-stu-id="3f06b-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="3f06b-135">В этом коде размещенная служба `GracePeriodManagerService` представляет собой реальный код микрослужбы размещения заказов в приложении eShopOnContainers, а другие две службы — это просто дополнительные примеры.</span><span class="sxs-lookup"><span data-stu-id="3f06b-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="3f06b-136">Выполнение фоновой задачи `IHostedService` согласуется с временем существования приложения (узла или микрослужбы).</span><span class="sxs-lookup"><span data-stu-id="3f06b-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="3f06b-137">Задачи регистрируются при запуске приложения, а при завершении его работы есть возможность произвести надлежащую обработку или очистку.</span><span class="sxs-lookup"><span data-stu-id="3f06b-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="3f06b-138">Фоновый поток можно запускать для выполнения любой задачи и без использования `IHostedService`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="3f06b-139">Различие именно в том, что будет происходить при завершении работы приложения: поток будет просто завершаться без возможности надлежащей очистки.</span><span class="sxs-lookup"><span data-stu-id="3f06b-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="3f06b-140">Интерфейс IHostedService</span><span class="sxs-lookup"><span data-stu-id="3f06b-140">The IHostedService interface</span></span>

<span data-ttu-id="3f06b-141">При регистрации интерфейса `IHostedService` платформа .NET вызывает методы `StartAsync()` и `StopAsync()` типа `IHostedService` во время запуска и остановки приложения соответственно.</span><span class="sxs-lookup"><span data-stu-id="3f06b-141">When you register an `IHostedService`, .NET will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="3f06b-142">Дополнительные сведения см. в разделе [Интерфейс IHostedService](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface).</span><span class="sxs-lookup"><span data-stu-id="3f06b-142">For more details, refer [IHostedService interface](/aspnet/core/fundamentals/host/hosted-services?tabs=visual-studio&view=aspnetcore-3.1#ihostedservice-interface)</span></span>

<span data-ttu-id="3f06b-143">Как было показано ранее, вы можете создать несколько реализаций IHostedService и зарегистрировать их в методе `ConfigureService()` в контейнере внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="3f06b-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="3f06b-144">Все эти размещенные службы будут запускаться и останавливаться вместе с приложением или микрослужбой.</span><span class="sxs-lookup"><span data-stu-id="3f06b-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="3f06b-145">Как разработчик, вы несете ответственность за обработку действия завершения своих служб при активации метода `StopAsync()` узлом.</span><span class="sxs-lookup"><span data-stu-id="3f06b-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="3f06b-146">Реализация IHostedService с помощью пользовательского класса размещенной службы, производного от базового класса BackgroundService</span><span class="sxs-lookup"><span data-stu-id="3f06b-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="3f06b-147">Можно пойти дальше и создать пользовательский класс размещенной службы с нуля, реализовав интерфейс `IHostedService`, как это требуется делать в .NET Core 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="3f06b-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0 and later.</span></span>

<span data-ttu-id="3f06b-148">Но большинство фоновых задач имеют схожие потребности в отношении управления токенами отмены и других типичных операций, поэтому существует удобный абстрактный базовый класс `BackgroundService`, от которого можно создавать производные классы (доступно с .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="3f06b-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="3f06b-149">Он будет выполнять основную часть работы, связанной с настройкой фоновой задачи.</span><span class="sxs-lookup"><span data-stu-id="3f06b-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="3f06b-150">Следующий код — это абстрактный базовый класс BackgroundService, реализованный в .NET.</span><span class="sxs-lookup"><span data-stu-id="3f06b-150">The next code is the abstract BackgroundService base class as implemented in .NET.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="3f06b-151">Благодаря такой унаследованной реализации при создании собственного класса размещенной службы, производного от приведенного выше абстрактного базового класса, необходимо просто реализовать в нем метод `ExecuteAsync()`. Пример представлен в следующем упрощенном коде из приложения eShopOnContainers, который опрашивает базу данных и при необходимости публикует события интеграции в шине событий.</span><span class="sxs-lookup"><span data-stu-id="3f06b-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="3f06b-152">В этом конкретном примере eShopOnContainers выполняет метод приложения, который отправляет запрос к таблице базы данных для поиска заказов с определенным состоянием, а при применении изменений публикует события интеграции через шину событий (она может быть основана на RabbitMQ или служебной шине Azure).</span><span class="sxs-lookup"><span data-stu-id="3f06b-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="3f06b-153">Естественно, вместо этого можно выполнять любую другую фоновую бизнес-задачу.</span><span class="sxs-lookup"><span data-stu-id="3f06b-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="3f06b-154">По умолчанию для токена отмены задается время ожидания, равное 5 секундам, хотя это значение можно изменить при создании `WebHost` с помощью расширения `UseShutdownTimeout` интерфейса `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="3f06b-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="3f06b-155">Это означает, что отмена службы ожидается в течение 5 секунд. В противном случае ее работа будет завершена внезапно.</span><span class="sxs-lookup"><span data-stu-id="3f06b-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="3f06b-156">В следующем коде это время изменяется на 10 секунд:</span><span class="sxs-lookup"><span data-stu-id="3f06b-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="3f06b-157">Сводная диаграмма классов</span><span class="sxs-lookup"><span data-stu-id="3f06b-157">Summary class diagram</span></span>

<span data-ttu-id="3f06b-158">На приведенном ниже рисунке представлена наглядная сводка классов и интерфейсов, которые задействованы в реализации IHostedService.</span><span class="sxs-lookup"><span data-stu-id="3f06b-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Схема, на которой показано, что в IWebHost и IHost может размещаться много служб.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="3f06b-160">**Рис. 6-27**.</span><span class="sxs-lookup"><span data-stu-id="3f06b-160">**Figure 6-27**.</span></span> <span data-ttu-id="3f06b-161">Диаграмма классов и интерфейсов, связанных с IHostedService</span><span class="sxs-lookup"><span data-stu-id="3f06b-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="3f06b-162">Диаграмма классов: IWebHost и IHost могут разместить много служб, наследующих от BackgroundService, который реализует IHostedService.</span><span class="sxs-lookup"><span data-stu-id="3f06b-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="3f06b-163">Основные положения и моменты, связанные с развертыванием</span><span class="sxs-lookup"><span data-stu-id="3f06b-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="3f06b-164">Важно отметить, что способ развертывания узла `WebHost` в ASP.NET Core или `Host` в .NET может влиять на конечное решение.</span><span class="sxs-lookup"><span data-stu-id="3f06b-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET `Host` might impact the final solution.</span></span> <span data-ttu-id="3f06b-165">Например, если вы развертываете `WebHost` в службах IIS или обычной службе приложений Azure, работа узла может быть завершена из-за перезапуска пула приложений.</span><span class="sxs-lookup"><span data-stu-id="3f06b-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="3f06b-166">Однако если вы развертываете узел как контейнер в оркестраторе, таком как Kubernetes, вы можете контролировать гарантированное число активных экземпляров узла.</span><span class="sxs-lookup"><span data-stu-id="3f06b-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="3f06b-167">Кроме того, в облачной среде можно рассмотреть другие подходы, особенно предназначенные для таких сценариев, как Функции Azure.</span><span class="sxs-lookup"><span data-stu-id="3f06b-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="3f06b-168">Если же требуется, чтобы служба работала постоянно и была развернута в Windows Server, используйте службу Windows.</span><span class="sxs-lookup"><span data-stu-id="3f06b-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="3f06b-169">Даже при развертывании `WebHost` в пуле приложений применим ряд сценариев, таких как повторное заполнение или сброс кэша в памяти для приложения.</span><span class="sxs-lookup"><span data-stu-id="3f06b-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="3f06b-170">Интерфейс `IHostedService` предоставляет удобный способ запуска фоновых задач в веб-приложении ASP.NET Core (в .NET Core 2.0 или более поздних версий) или в любом процессе или узле (при использовании `IHost` начиная с .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="3f06b-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="3f06b-171">Его главное преимущество — это возможность надлежащей отмены с целью очистки кода фоновых задач при завершении работы самого узла.</span><span class="sxs-lookup"><span data-stu-id="3f06b-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3f06b-172">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="3f06b-172">Additional resources</span></span>

- <span data-ttu-id="3f06b-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** (Создание запланированной задачи в ASP.NET Core или Standard 2.0) </span><span class="sxs-lookup"><span data-stu-id="3f06b-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="3f06b-174">**Implementing IHostedService in ASP.NET Core 2.0** (Реализация интерфейса IHostedService в ASP.NET Core 2.0) </span><span class="sxs-lookup"><span data-stu-id="3f06b-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="3f06b-175">**Пример GenericHost с ASP.NET Core 2.1** </span><span class="sxs-lookup"><span data-stu-id="3f06b-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="3f06b-176">[Назад](test-aspnet-core-services-web-apps.md)
> [Вперед](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="3f06b-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
