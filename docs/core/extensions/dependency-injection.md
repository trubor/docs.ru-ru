---
title: Внедрение зависимостей в .NET
description: Сведения о том, как .NET реализует внедрение зависимостей и как его использовать.
author: IEvangelist
ms.author: dapine
ms.date: 10/28/2020
ms.topic: overview
ms.openlocfilehash: cc030e32846690b6544b99030800b50055a3113e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "102402105"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="ccf3e-103">Внедрение зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="ccf3e-103">Dependency injection in .NET</span></span>

<span data-ttu-id="ccf3e-104">.NET поддерживает проектирование программного обеспечения с возможностью внедрения зависимостей. При таком подходе достигается [инверсия управления](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) между классами и их зависимостями.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="ccf3e-105">Внедрение зависимостей — своего рода [почетный гражданин](https://en.wikipedia.org/wiki/First-class_citizen) .NET наряду с конфигурацией, ведением журнала и шаблоном параметров.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="ccf3e-106">*Зависимость* — это любой объект, от которого зависит другой объект.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="ccf3e-107">Рассмотрим следующий класс `MessageWriter` с методом `Write`, от которого зависят другие классы:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="ccf3e-108">Класс может создать экземпляр класса `MessageWriter`, чтобы использовать его метод `Write`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="ccf3e-109">В следующем примере класс `MessageWriter` выступает зависимостью класса `Worker`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="ccf3e-110">Этот класс создает `MessageWriter` и напрямую зависит от этого класса.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="ccf3e-111">Включенные в код зависимости, как в предыдущем примере, представляют собой определенную проблему. Их следует избегать по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="ccf3e-112">Чтобы заменить `MessageWriter` другой реализацией, класс `Worker` необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-112">To replace `MessageWriter` with a different implementation, the `Worker` class must be modified.</span></span>
- <span data-ttu-id="ccf3e-113">Если у `MessageWriter` есть зависимости, их конфигурацию должен выполнять класс `Worker`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-113">If `MessageWriter` has dependencies, they must also be configured by the `Worker` class.</span></span> <span data-ttu-id="ccf3e-114">В больших проектах, когда от `MessageWriter` зависят многие классы, код конфигурации растягивается по всему приложению.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="ccf3e-115">Такая реализация плохо подходит для модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="ccf3e-116">В приложении нужно использовать имитацию или заглушку в виде класса `MessageWriter`, что при таком подходе невозможно.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="ccf3e-117">Внедрение зависимостей устраняет эти проблемы следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="ccf3e-118">Используется интерфейс или базовый класс для абстрагирования реализации зависимостей.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="ccf3e-119">Зависимость регистрируется в контейнере служб.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="ccf3e-120">.NET предоставляет встроенный контейнер служб <xref:System.IServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="ccf3e-121">Службы обычно регистрируются при запуске приложения и добавляются в <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="ccf3e-122">После добавления всех служб выполните <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> для создания контейнера службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="ccf3e-123">Служба *внедряется* в конструктор класса там, где он используется.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="ccf3e-124">Платформа берет на себя создание экземпляра зависимости и его удаление, когда он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="ccf3e-125">В качестве примера рассмотрим интерфейс `IMessageWriter`, который определяет метод `Write`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="ccf3e-126">Этот интерфейс реализуется конкретным типом, `MessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="ccf3e-127">Этот пример кода регистрирует службу `IMessageWriter` с конкретным типом `MessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="ccf3e-128">Метод <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> регистрирует службу с заданной областью времени существования, временем существования одного запроса.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="ccf3e-129">Подробнее о [времени существования служб](#service-lifetimes) мы поговорим далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-129">[Service lifetimes](#service-lifetimes) are described later in this article.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="ccf3e-130">В примере приложения запрашивается служба `IMessageWriter`, которая затем используется для вызова метода `Write`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="ccf3e-131">При использовании шаблона внедрения зависимостей рабочая служба имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="ccf3e-132">Не использует конкретный тип `MessageWriter`, а только интерфейс `IMessageWriter`, который его реализует.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="ccf3e-133">Это упрощает изменение реализации, используемой контроллером, без изменения контроллера.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="ccf3e-134">не создает экземпляр `MessageWriter`, он создается контейнером внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="ccf3e-135">Реализацию интерфейса `IMessageWriter` можно улучшить с помощью встроенного API ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="ccf3e-136">Обновленный метод `ConfigureServices` регистрирует новую реализацию `IMessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="ccf3e-137">`LoggingMessageWriter` зависит от <xref:Microsoft.Extensions.Logging.ILogger%601>, который запрашивается в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="ccf3e-138">`ILogger<TCategoryName>` — это [предоставленная платформой служба](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="ccf3e-139">Использование цепочки внедрений зависимостей не является чем-то необычным.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="ccf3e-140">Каждая запрашиваемая зависимость запрашивает собственные зависимости.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="ccf3e-141">Контейнер разрешает зависимости в графе и возвращает полностью разрешенную службу.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="ccf3e-142">Весь набор зависимостей, которые нужно разрешить, обычно называют *деревом зависимостей*, *графом зависимостей* или *графом объектов*.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree*, *dependency graph*, or *object graph*.</span></span>

<span data-ttu-id="ccf3e-143">Контейнер разрешает `ILogger<TCategoryName>`, используя преимущества [(универсальных) открытых типов](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), что устраняет необходимость регистрации каждого [(универсального) сконструированного типа](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="ccf3e-144">В терминологии внедрения зависимостей — служба:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="ccf3e-145">Обычно является объектом, предоставляющим службу для других объектов, например службу `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="ccf3e-146">Не относится к веб-службе, хотя служба может использовать веб-службу.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="ccf3e-147">Платформа предоставляет эффективную систему ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="ccf3e-148">Реализации `IMessageWriter`, приведенные в предыдущем примере были написаны для демонстрации базового внедрения зависимостей, а не для реализации ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="ccf3e-149">Большинству приложений не нужно писать средства ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="ccf3e-150">В следующем коде демонстрируется использование механизма ведения журнала по умолчанию, для которого требуется только регистрация `Worker` в `ConfigureServices` в качестве размещенной службы <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

<span data-ttu-id="ccf3e-151">Используя приведенный выше код, не нужно обновлять `ConfigureServices`, поскольку платформа предоставляет возможность ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="ccf3e-152">Регистрация групп служб с помощью методов расширения</span><span class="sxs-lookup"><span data-stu-id="ccf3e-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="ccf3e-153">Расширения Microsoft используют конвенцию для регистрации группы связанных служб.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="ccf3e-154">Соглашение заключается в использовании одного метода расширения `Add{GROUP_NAME}` для регистрации всех служб, необходимых компоненту платформы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="ccf3e-155">Например, метод расширения <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> регистрирует все службы, необходимые для работы с параметрами.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="ccf3e-156">Платформенные службы</span><span class="sxs-lookup"><span data-stu-id="ccf3e-156">Framework-provided services</span></span>

<span data-ttu-id="ccf3e-157">Метод `ConfigureServices` регистрирует используемые приложением службы, включая функции платформы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="ccf3e-158">Изначально коллекция `IServiceCollection`, предоставленная для `ConfigureServices`, содержит определенные платформой службы (в зависимости от [настройки узла](generic-host.md#host-configuration)).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="ccf3e-159">Для приложений, основанных на шаблонах .NET, платформа регистрирует несколько сотен служб.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="ccf3e-160">В следующей таблице перечислены некоторые примеры этих зарегистрированных платформой служб.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="ccf3e-161">Тип службы</span><span class="sxs-lookup"><span data-stu-id="ccf3e-161">Service Type</span></span>                                                                       | <span data-ttu-id="ccf3e-162">Время существования</span><span class="sxs-lookup"><span data-stu-id="ccf3e-162">Lifetime</span></span>  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | <span data-ttu-id="ccf3e-163">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | <span data-ttu-id="ccf3e-164">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | <span data-ttu-id="ccf3e-165">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | <span data-ttu-id="ccf3e-166">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | <span data-ttu-id="ccf3e-167">Временный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-167">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | <span data-ttu-id="ccf3e-168">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-168">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | <span data-ttu-id="ccf3e-169">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | <span data-ttu-id="ccf3e-170">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-170">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="ccf3e-171">Время существования служб</span><span class="sxs-lookup"><span data-stu-id="ccf3e-171">Service lifetimes</span></span>

<span data-ttu-id="ccf3e-172">Службы можно зарегистрировать с одним из следующих вариантов времени существования:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-172">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="ccf3e-173">Временный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-173">Transient</span></span>
- <span data-ttu-id="ccf3e-174">Область действия</span><span class="sxs-lookup"><span data-stu-id="ccf3e-174">Scoped</span></span>
- <span data-ttu-id="ccf3e-175">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-175">Singleton</span></span>

<span data-ttu-id="ccf3e-176">Они описываются в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-176">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="ccf3e-177">Для каждой зарегистрированной службы выбирайте подходящее время существования.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-177">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="ccf3e-178">Временный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-178">Transient</span></span>

<span data-ttu-id="ccf3e-179">Временные службы времени существования создаются при каждом их запросе из контейнера служб.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-179">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="ccf3e-180">Это время существования лучше всего подходит для простых служб без отслеживания состояния.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-180">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="ccf3e-181">Регистрируйте временные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-181">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="ccf3e-182">В приложениях, обрабатывающих запросы, временные службы удаляются в конце запроса.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-182">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="ccf3e-183">Область действия</span><span class="sxs-lookup"><span data-stu-id="ccf3e-183">Scoped</span></span>

<span data-ttu-id="ccf3e-184">Для веб-приложений время существования, привязанное к области, означает, что службы создаются один раз для каждого запроса (подключения) клиента.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-184">For web applications, a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="ccf3e-185">Регистрируйте службы с заданной областью с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-185">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="ccf3e-186">В приложениях, обрабатывающих запросы, службы с заданной областью удаляются в конце запроса.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-186">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="ccf3e-187">При использовании Entity Framework Core метод расширения <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> по умолчанию регистрирует типы `DbContext` с заданной областью времени существования.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-187">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="ccf3e-188">Разрешать службу с заданной областью из одноэлементного объекта \***запрещено** _, и будьте внимательны, чтобы не сделать это неявно, например, через временную службу.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-188">Do \***not** _ resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="ccf3e-189">При обработке последующих запросов это может вызвать неправильное состояние службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-189">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="ccf3e-190">Допускается следующее:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-190">It's fine to:</span></span>
>
> - <span data-ttu-id="ccf3e-191">Разрешение одноэлементной службы из службы с заданной областью или временной службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-191">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="ccf3e-192">Разрешение службы с заданной областью из другой службы с заданной областью или временной службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-192">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="ccf3e-193">По умолчанию в среде разработки разрешение службы из другой службы с более длинным временем существования вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-193">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="ccf3e-194">Дополнительные сведения см. в разделе [Проверка области](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-194">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="ccf3e-195">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="ccf3e-195">Singleton</span></span>

<span data-ttu-id="ccf3e-196">Одноэлементные службы времени существования создаются в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-196">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="ccf3e-197">При первом запросе.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-197">The first time they're requested.</span></span>
- <span data-ttu-id="ccf3e-198">Разработчиком при предоставлении экземпляра реализации непосредственно в контейнер.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-198">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="ccf3e-199">Этот подход требуется достаточно редко.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-199">This approach is rarely needed.</span></span>

<span data-ttu-id="ccf3e-200">Каждый последующий запрос на реализацию службы из контейнера внедрения зависимостей использует тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-200">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="ccf3e-201">Если в приложении нужно использовать одноэлементные службы, разрешите контейнеру служб управлять временем их существования.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-201">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="ccf3e-202">Не реализуйте одноэлементный подход и предоставьте код для удаления одноэлементных объектов.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-202">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="ccf3e-203">Службы никогда не должны удаляться кодом, который разрешил службу из контейнера.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-203">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="ccf3e-204">Если тип или фабрика зарегистрированы как одноэлементный объект, контейнер автоматически удалит одноэлементные объекты.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-204">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="ccf3e-205">Зарегистрируйте одноэлементные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-205">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="ccf3e-206">Одноэлементные службы должны быть потокобезопасными и часто использоваться в службах без отслеживания состояния.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-206">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="ccf3e-207">В приложениях, обрабатывающих запросы, отдельные службы удаляются, когда <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> удаляется по завершении работы приложения.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-207">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="ccf3e-208">Поскольку память не освобождается до завершения работы приложения, рекомендуется учитывать использование памяти одноэлементным объектом.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-208">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

> [!WARNING]
> <span data-ttu-id="ccf3e-209">Разрешать службу с заданной областью из отдельного объекта _\*_нельзя_\*_.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-209">Do _*_not_*_ resolve a scoped service from a singleton.</span></span> <span data-ttu-id="ccf3e-210">При обработке последующих запросов это может вызвать неправильное состояние службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-210">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="ccf3e-211">Допускается разрешать одноэлементную службу из службы с заданной областью или временной службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-211">It's fine to resolve a singleton service from a scoped or transient service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="ccf3e-212">Методы регистрации службы</span><span class="sxs-lookup"><span data-stu-id="ccf3e-212">Service registration methods</span></span>

<span data-ttu-id="ccf3e-213">Платформа предоставляет методы расширения регистрации службы, которые полезны в определенных сценариях.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-213">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="ccf3e-214">Метод</span><span class="sxs-lookup"><span data-stu-id="ccf3e-214">Method</span></span> | <span data-ttu-id="ccf3e-215">Автоматически</span><span class="sxs-lookup"><span data-stu-id="ccf3e-215">Automatic</span></span><br><span data-ttu-id="ccf3e-216">object</span><span class="sxs-lookup"><span data-stu-id="ccf3e-216">object</span></span><br><span data-ttu-id="ccf3e-217">удаление</span><span class="sxs-lookup"><span data-stu-id="ccf3e-217">disposal</span></span> | <span data-ttu-id="ccf3e-218">Несколько</span><span class="sxs-lookup"><span data-stu-id="ccf3e-218">Multiple</span></span><br><span data-ttu-id="ccf3e-219">реализации</span><span class="sxs-lookup"><span data-stu-id="ccf3e-219">implementations</span></span> | <span data-ttu-id="ccf3e-220">Передача аргументов</span><span class="sxs-lookup"><span data-stu-id="ccf3e-220">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="ccf3e-221">Пример</span><span class="sxs-lookup"><span data-stu-id="ccf3e-221">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="ccf3e-222">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-222">Yes</span></span> | <span data-ttu-id="ccf3e-223">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-223">Yes</span></span> | <span data-ttu-id="ccf3e-224">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-224">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="ccf3e-225">Примеры:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-225">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="ccf3e-226">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-226">Yes</span></span> | <span data-ttu-id="ccf3e-227">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-227">Yes</span></span> | <span data-ttu-id="ccf3e-228">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-228">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="ccf3e-229">Пример</span><span class="sxs-lookup"><span data-stu-id="ccf3e-229">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="ccf3e-230">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-230">Yes</span></span> | <span data-ttu-id="ccf3e-231">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-231">No</span></span> | <span data-ttu-id="ccf3e-232">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-232">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="ccf3e-233">Примеры:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-233">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="ccf3e-234">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-234">No</span></span> | <span data-ttu-id="ccf3e-235">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-235">Yes</span></span> | <span data-ttu-id="ccf3e-236">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-236">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="ccf3e-237">Примеры:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-237">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="ccf3e-238">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-238">No</span></span> | <span data-ttu-id="ccf3e-239">Нет</span><span class="sxs-lookup"><span data-stu-id="ccf3e-239">No</span></span> | <span data-ttu-id="ccf3e-240">Да</span><span class="sxs-lookup"><span data-stu-id="ccf3e-240">Yes</span></span> |

<span data-ttu-id="ccf3e-241">Дополнительные сведения об удалении типа см. в разделе [Удаление служб](dependency-injection-guidelines.md#disposal-of-services).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-241">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="ccf3e-242">Регистрация службы только с типом реализации эквивалентна регистрации этой службы с той же реализацией и типом службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-242">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="ccf3e-243">Именно поэтому несколько реализаций службы не могут быть зарегистрированы с помощью методов, которые не принимают явный тип службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-243">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="ccf3e-244">Эти методы могут регистрировать несколько _экземпляров\* службы, но все они будут иметь одинаковую *реализацию* типа.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-244">These methods can register multiple _instances\* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="ccf3e-245">Любой из указанных выше методов регистрации службы можно использовать для регистрации нескольких экземпляров службы одного типа службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-245">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="ccf3e-246">В следующем примере метод `AddSingleton` вызывается дважды с типом службы `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-246">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="ccf3e-247">Второй вызов `AddSingleton` переопределяет предыдущий, если он разрешается как `IMessageWriter`, и добавляет к предыдущему, если несколько служб разрешаются через `IEnumerable<IMessageWriter>`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-247">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="ccf3e-248">Службы отображаются в том порядке, в котором они были зарегистрированы при разрешении через `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-248">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="ccf3e-249">Предыдущий пример исходного кода регистрирует две реализации `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-249">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="ccf3e-250">Компонент `ExampleService` определяет два параметра конструктора: одиночный `IMessageWriter` и `IEnumerable<IMessageWriter>`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-250">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="ccf3e-251">Одиночный `IMessageWriter` здесь является последней зарегистрированной реализацией, а `IEnumerable<IMessageWriter>` представляет все зарегистрированные реализации.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-251">The single `IMessageWriter` is the last implementation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="ccf3e-252">Платформа также предоставляет методы расширения `TryAdd{LIFETIME}`, которые регистрируют службу только в том случае, если реализация еще не зарегистрирована.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-252">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="ccf3e-253">В следующем примере вызов `AddSingleton` регистрирует `ConsoleMessageWriter` как реализацию для `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-253">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="ccf3e-254">Вызов `TryAddSingleton` ничего не делает, поскольку у `IMessageWriter` уже есть зарегистрированная реализация:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-254">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="ccf3e-255">Параметр `TryAddSingleton` не применяется, так как он уже был добавлен, поэтому выполнение "try" завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-255">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="ccf3e-256">В `ExampleService` будут следующие утверждения:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-256">The `ExampleService` would assert the following:</span></span>

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

<span data-ttu-id="ccf3e-257">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-257">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="ccf3e-258">Методы [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) регистрируют службу только в том случае, если еще не существует реализации *того же типа*.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-258">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type*.</span></span> <span data-ttu-id="ccf3e-259">Несколько служб разрешается через `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-259">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="ccf3e-260">При регистрации служб добавляйте экземпляр в том случае, если экземпляр такого типа еще не был добавлен.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-260">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="ccf3e-261">Авторы библиотек используют `TryAddEnumerable`, чтобы избежать регистрации нескольких копий реализации в контейнере.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-261">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="ccf3e-262">В следующем примере первый вызов `TryAddEnumerable` регистрирует `MessageWriter` как реализацию для `IMessageWriter1`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-262">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="ccf3e-263">Второй вызов регистрирует `MessageWriter` для `IMessageWriter2`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-263">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="ccf3e-264">Третий вызов ничего не делает, поскольку у `IMessageWriter1` уже есть зарегистрированная реализация `MessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-264">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

<span data-ttu-id="ccf3e-265">Регистрация службы обычно не зависит от порядка, за исключением случаев регистрации нескольких реализаций одного типа.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-265">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="ccf3e-266">`IServiceCollection` является коллекцией объектов <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-266">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="ccf3e-267">В следующем примере показано, как зарегистрировать службу, создав и добавив `ServiceDescriptor`:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-267">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="ccf3e-268">Встроенные методы `Add{LIFETIME}` используют аналогичный подход.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-268">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="ccf3e-269">Например, см. [исходный код для AddScoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="ccf3e-269">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="ccf3e-270">Поведение внедрения через конструктор</span><span class="sxs-lookup"><span data-stu-id="ccf3e-270">Constructor injection behavior</span></span>

<span data-ttu-id="ccf3e-271">Службы можно разрешать с помощью:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-271">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="ccf3e-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-272"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="ccf3e-273">Создает объекты, которые не зарегистрированы в контейнере.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-273">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="ccf3e-274">Используется в сочетании с некоторыми возможностями платформы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-274">Used with some framework features.</span></span>

<span data-ttu-id="ccf3e-275">Конструкторы могут принимать аргументы, которые не предоставляются внедрением зависимостей, но эти аргументы должны назначать значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-275">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="ccf3e-276">Когда разрешение служб выполняется через `IServiceProvider` или `ActivatorUtilities`, для внедрения через конструктор требуется *открытый* конструктор.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-276">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="ccf3e-277">Когда разрешение служб выполняется через `ActivatorUtilities`, для внедрения с помощью конструктора требуется наличие только одного соответствующего конструктора.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-277">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="ccf3e-278">Перегрузки конструктора поддерживаются, но может существовать всего одна перегрузка, все аргументы которой могут быть обработаны с помощью внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-278">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="ccf3e-279">Проверка области</span><span class="sxs-lookup"><span data-stu-id="ccf3e-279">Scope validation</span></span>

<span data-ttu-id="ccf3e-280">Когда приложение выполняется в среде `Development` и вызывает [CreateDefaultBuilder](generic-host.md#default-builder-settings) для создания узла, поставщик службы по умолчанию проверяет следующее:</span><span class="sxs-lookup"><span data-stu-id="ccf3e-280">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="ccf3e-281">Службы с заданной областью не разрешаются из корневого поставщика службы.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-281">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="ccf3e-282">Службы с заданной областью не вводятся в одноэлементные объекты.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-282">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="ccf3e-283">Корневой поставщик службы создается при вызове <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-283">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="ccf3e-284">Время существования корневого поставщика службы соответствует времени существования приложения — поставщик запускается с приложением и удаляется, когда приложение завершает работу.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-284">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="ccf3e-285">Службы с заданной областью удаляются создавшим их контейнером.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-285">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="ccf3e-286">Если служба с заданной областью создается в корневом контейнере, время существования службы повышается до уровня одноэлементного объекта, поскольку она удаляется только корневым контейнером при завершении работы приложения.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-286">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="ccf3e-287">Проверка областей службы перехватывает эти ситуации при вызове `BuildServiceProvider`.</span><span class="sxs-lookup"><span data-stu-id="ccf3e-287">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccf3e-288">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ccf3e-288">See also</span></span>

- [<span data-ttu-id="ccf3e-289">Использование внедрения зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="ccf3e-289">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="ccf3e-290">Рекомендации по внедрению зависимостей</span><span class="sxs-lookup"><span data-stu-id="ccf3e-290">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="ccf3e-291">Внедрение зависимостей в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ccf3e-291">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="ccf3e-292">Шаблоны конференций NDC для разработки приложений с внедрением зависимостей</span><span class="sxs-lookup"><span data-stu-id="ccf3e-292">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="ccf3e-293">Принцип явных зависимостей</span><span class="sxs-lookup"><span data-stu-id="ccf3e-293">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="ccf3e-294">Контейнеры с инверсией управления и шаблон внедрения зависимостей (Мартин Фаулер (Martin Fowler))</span><span class="sxs-lookup"><span data-stu-id="ccf3e-294">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="ccf3e-295">Запросы на исправление ошибок, связанных с внедрением зависимостей, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)</span><span class="sxs-lookup"><span data-stu-id="ccf3e-295">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
