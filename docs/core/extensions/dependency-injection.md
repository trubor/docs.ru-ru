---
title: Внедрение зависимостей в .NET
description: Сведения о том, как .NET реализует внедрение зависимостей и как его использовать.
author: IEvangelist
ms.author: dapine
ms.date: 04/12/2021
ms.topic: overview
ms.openlocfilehash: 2feb8b44d7701839bd889138c1f7c8f1fb2be71a
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494289"
---
# <a name="dependency-injection-in-net"></a><span data-ttu-id="3408f-103">Внедрение зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="3408f-103">Dependency injection in .NET</span></span>

<span data-ttu-id="3408f-104">.NET поддерживает проектирование программного обеспечения с возможностью внедрения зависимостей. При таком подходе достигается [инверсия управления](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) между классами и их зависимостями.</span><span class="sxs-lookup"><span data-stu-id="3408f-104">.NET supports the dependency injection (DI) software design pattern, which is a technique for achieving [Inversion of Control (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) between classes and their dependencies.</span></span> <span data-ttu-id="3408f-105">Внедрение зависимостей — своего рода [почетный гражданин](https://en.wikipedia.org/wiki/First-class_citizen) .NET наряду с конфигурацией, ведением журнала и шаблоном параметров.</span><span class="sxs-lookup"><span data-stu-id="3408f-105">Dependency injection in .NET is a [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen), along with configuration, logging, and the options pattern.</span></span>

<span data-ttu-id="3408f-106">*Зависимость* — это любой объект, от которого зависит другой объект.</span><span class="sxs-lookup"><span data-stu-id="3408f-106">A *dependency* is an object that another object depends on.</span></span> <span data-ttu-id="3408f-107">Рассмотрим следующий класс `MessageWriter` с методом `Write`, от которого зависят другие классы:</span><span class="sxs-lookup"><span data-stu-id="3408f-107">Examine the following `MessageWriter` class with a `Write` method that other classes depend on:</span></span>

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

<span data-ttu-id="3408f-108">Класс может создать экземпляр класса `MessageWriter`, чтобы использовать его метод `Write`.</span><span class="sxs-lookup"><span data-stu-id="3408f-108">A class can create an instance of the `MessageWriter` class to make use of its `Write` method.</span></span> <span data-ttu-id="3408f-109">В следующем примере класс `MessageWriter` выступает зависимостью класса `Worker`:</span><span class="sxs-lookup"><span data-stu-id="3408f-109">In the following example, the `MessageWriter` class is a dependency of the `Worker` class:</span></span>

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

<span data-ttu-id="3408f-110">Этот класс создает `MessageWriter` и напрямую зависит от этого класса.</span><span class="sxs-lookup"><span data-stu-id="3408f-110">The class creates and directly depends on the `MessageWriter` class.</span></span> <span data-ttu-id="3408f-111">Включенные в код зависимости, как в предыдущем примере, представляют собой определенную проблему. Их следует избегать по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="3408f-111">Hard-coded dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:</span></span>

- <span data-ttu-id="3408f-112">Чтобы заменить `MessageWriter` другой реализацией, класс `Worker` необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="3408f-112">To replace `MessageWriter` with a different implementation, the `Worker` class must be modified.</span></span>
- <span data-ttu-id="3408f-113">Если у `MessageWriter` есть зависимости, их конфигурацию должен выполнять класс `Worker`.</span><span class="sxs-lookup"><span data-stu-id="3408f-113">If `MessageWriter` has dependencies, they must also be configured by the `Worker` class.</span></span> <span data-ttu-id="3408f-114">В больших проектах, когда от `MessageWriter` зависят многие классы, код конфигурации растягивается по всему приложению.</span><span class="sxs-lookup"><span data-stu-id="3408f-114">In a large project with multiple classes depending on `MessageWriter`, the configuration code becomes scattered across the app.</span></span>
- <span data-ttu-id="3408f-115">Такая реализация плохо подходит для модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="3408f-115">This implementation is difficult to unit test.</span></span> <span data-ttu-id="3408f-116">В приложении нужно использовать имитацию или заглушку в виде класса `MessageWriter`, что при таком подходе невозможно.</span><span class="sxs-lookup"><span data-stu-id="3408f-116">The app should use a mock or stub `MessageWriter` class, which isn't possible with this approach.</span></span>

<span data-ttu-id="3408f-117">Внедрение зависимостей устраняет эти проблемы следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3408f-117">Dependency injection addresses these problems through:</span></span>

- <span data-ttu-id="3408f-118">Используется интерфейс или базовый класс для абстрагирования реализации зависимостей.</span><span class="sxs-lookup"><span data-stu-id="3408f-118">The use of an interface or base class to abstract the dependency implementation.</span></span>
- <span data-ttu-id="3408f-119">Зависимость регистрируется в контейнере служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-119">Registration of the dependency in a service container.</span></span> <span data-ttu-id="3408f-120">.NET предоставляет встроенный контейнер служб <xref:System.IServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="3408f-120">.NET provides a built-in service container, <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="3408f-121">Службы обычно регистрируются при запуске приложения и добавляются в <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="3408f-121">Services are typically registered at the app's start-up, and appended to an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="3408f-122">После добавления всех служб выполните <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> для создания контейнера службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-122">Once all services are added, you use <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> to create the service container.</span></span>
- <span data-ttu-id="3408f-123">Служба *внедряется* в конструктор класса там, где он используется.</span><span class="sxs-lookup"><span data-stu-id="3408f-123">*Injection* of the service into the constructor of the class where it's used.</span></span> <span data-ttu-id="3408f-124">Платформа берет на себя создание экземпляра зависимости и его удаление, когда он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="3408f-124">The framework takes on the responsibility of creating an instance of the dependency and disposing of it when it's no longer needed.</span></span>

<span data-ttu-id="3408f-125">В качестве примера рассмотрим интерфейс `IMessageWriter`, который определяет метод `Write`:</span><span class="sxs-lookup"><span data-stu-id="3408f-125">As an example, the `IMessageWriter` interface defines the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

<span data-ttu-id="3408f-126">Этот интерфейс реализуется конкретным типом, `MessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-126">This interface is implemented by a concrete type, `MessageWriter`:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

<span data-ttu-id="3408f-127">Этот пример кода регистрирует службу `IMessageWriter` с конкретным типом `MessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-127">The sample code registers the `IMessageWriter` service with the concrete type `MessageWriter`.</span></span> <span data-ttu-id="3408f-128">Метод <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> регистрирует службу с заданной областью времени существования, временем существования одного запроса.</span><span class="sxs-lookup"><span data-stu-id="3408f-128">The <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> method registers the service with a scoped lifetime, the lifetime of a single request.</span></span> <span data-ttu-id="3408f-129">Подробнее о [времени существования служб](#service-lifetimes) мы поговорим далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="3408f-129">[Service lifetimes](#service-lifetimes) are described later in this article.</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

<span data-ttu-id="3408f-130">В примере приложения запрашивается служба `IMessageWriter`, которая затем используется для вызова метода `Write`:</span><span class="sxs-lookup"><span data-stu-id="3408f-130">In the sample app, the `IMessageWriter` service is requested and used to call the `Write` method:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

<span data-ttu-id="3408f-131">При использовании шаблона внедрения зависимостей рабочая служба имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="3408f-131">By using the DI pattern, the worker service:</span></span>

- <span data-ttu-id="3408f-132">Не использует конкретный тип `MessageWriter`, а только интерфейс `IMessageWriter`, который его реализует.</span><span class="sxs-lookup"><span data-stu-id="3408f-132">Doesn't use the concrete type `MessageWriter`, only the `IMessageWriter` interface that implements it.</span></span> <span data-ttu-id="3408f-133">Это упрощает изменение реализации, используемой контроллером, без изменения контроллера.</span><span class="sxs-lookup"><span data-stu-id="3408f-133">That makes it easy to change the implementation that the controller uses without modifying the controller.</span></span>
- <span data-ttu-id="3408f-134">не создает экземпляр `MessageWriter`, он создается контейнером внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="3408f-134">Doesn't create an instance of `MessageWriter`, it's created by the DI container.</span></span>

<span data-ttu-id="3408f-135">Реализацию интерфейса `IMessageWriter` можно улучшить с помощью встроенного API ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="3408f-135">The implementation of the `IMessageWriter` interface can be improved by using the built-in logging API:</span></span>

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

<span data-ttu-id="3408f-136">Обновленный метод `ConfigureServices` регистрирует новую реализацию `IMessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="3408f-136">The updated `ConfigureServices` method registers the new `IMessageWriter` implementation:</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

<span data-ttu-id="3408f-137">`LoggingMessageWriter` зависит от <xref:Microsoft.Extensions.Logging.ILogger%601>, который запрашивается в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="3408f-137">`LoggingMessageWriter` depends on <xref:Microsoft.Extensions.Logging.ILogger%601>, which it requests in the constructor.</span></span> <span data-ttu-id="3408f-138">`ILogger<TCategoryName>` — это [предоставленная платформой служба](#framework-provided-services).</span><span class="sxs-lookup"><span data-stu-id="3408f-138">`ILogger<TCategoryName>` is a [framework-provided service](#framework-provided-services).</span></span>

<span data-ttu-id="3408f-139">Использование цепочки внедрений зависимостей не является чем-то необычным.</span><span class="sxs-lookup"><span data-stu-id="3408f-139">It's not unusual to use dependency injection in a chained fashion.</span></span> <span data-ttu-id="3408f-140">Каждая запрашиваемая зависимость запрашивает собственные зависимости.</span><span class="sxs-lookup"><span data-stu-id="3408f-140">Each requested dependency in turn requests its own dependencies.</span></span> <span data-ttu-id="3408f-141">Контейнер разрешает зависимости в графе и возвращает полностью разрешенную службу.</span><span class="sxs-lookup"><span data-stu-id="3408f-141">The container resolves the dependencies in the graph and returns the fully resolved service.</span></span> <span data-ttu-id="3408f-142">Весь набор зависимостей, которые нужно разрешить, обычно называют *деревом зависимостей*, *графом зависимостей* или *графом объектов*.</span><span class="sxs-lookup"><span data-stu-id="3408f-142">The collective set of dependencies that must be resolved is typically referred to as a *dependency tree*, *dependency graph*, or *object graph*.</span></span>

<span data-ttu-id="3408f-143">Контейнер разрешает `ILogger<TCategoryName>`, используя преимущества [(универсальных) открытых типов](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), что устраняет необходимость регистрации каждого [(универсального) сконструированного типа](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="3408f-143">The container resolves `ILogger<TCategoryName>` by taking advantage of [(generic) open types](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), eliminating the need to register every [(generic) constructed type](/dotnet/csharp/language-reference/language-specification/types#constructed-types).</span></span>

<span data-ttu-id="3408f-144">В терминологии внедрения зависимостей — служба:</span><span class="sxs-lookup"><span data-stu-id="3408f-144">In dependency injection terminology, a service:</span></span>

- <span data-ttu-id="3408f-145">Обычно является объектом, предоставляющим службу для других объектов, например службу `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-145">Is typically an object that provides a service to other objects, such as the `IMessageWriter` service.</span></span>
- <span data-ttu-id="3408f-146">Не относится к веб-службе, хотя служба может использовать веб-службу.</span><span class="sxs-lookup"><span data-stu-id="3408f-146">Is not related to a web service, although the service may use a web service.</span></span>

<span data-ttu-id="3408f-147">Платформа предоставляет эффективную систему ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3408f-147">The framework provides a robust logging system.</span></span> <span data-ttu-id="3408f-148">Реализации `IMessageWriter`, приведенные в предыдущем примере были написаны для демонстрации базового внедрения зависимостей, а не для реализации ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3408f-148">The `IMessageWriter` implementations shown in the preceding examples were written to demonstrate basic DI, not to implement logging.</span></span> <span data-ttu-id="3408f-149">Большинству приложений не нужно писать средства ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3408f-149">Most apps shouldn't need to write loggers.</span></span> <span data-ttu-id="3408f-150">В следующем коде демонстрируется использование механизма ведения журнала по умолчанию, для которого требуется только регистрация `Worker` в `ConfigureServices` в качестве размещенной службы <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>.</span><span class="sxs-lookup"><span data-stu-id="3408f-150">The following code demonstrates using the default logging, which only requires the `Worker` to be registered in `ConfigureServices` as a hosted service <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>:</span></span>

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

<span data-ttu-id="3408f-151">Используя приведенный выше код, не нужно обновлять `ConfigureServices`, поскольку платформа предоставляет возможность ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="3408f-151">Using the preceding code, there is no need to update `ConfigureServices`, because logging is provided by the framework.</span></span>

## <a name="register-groups-of-services-with-extension-methods"></a><span data-ttu-id="3408f-152">Регистрация групп служб с помощью методов расширения</span><span class="sxs-lookup"><span data-stu-id="3408f-152">Register groups of services with extension methods</span></span>

<span data-ttu-id="3408f-153">Расширения Microsoft используют конвенцию для регистрации группы связанных служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-153">Microsoft Extensions uses a convention for registering a group of related services.</span></span> <span data-ttu-id="3408f-154">Соглашение заключается в использовании одного метода расширения `Add{GROUP_NAME}` для регистрации всех служб, необходимых компоненту платформы.</span><span class="sxs-lookup"><span data-stu-id="3408f-154">The convention is to use a single `Add{GROUP_NAME}` extension method to register all of the services required by a framework feature.</span></span> <span data-ttu-id="3408f-155">Например, метод расширения <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> регистрирует все службы, необходимые для работы с параметрами.</span><span class="sxs-lookup"><span data-stu-id="3408f-155">For example, the <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> extension method registers all of the services required for using options.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="3408f-156">Платформенные службы</span><span class="sxs-lookup"><span data-stu-id="3408f-156">Framework-provided services</span></span>

<span data-ttu-id="3408f-157">Метод `ConfigureServices` регистрирует используемые приложением службы, включая функции платформы.</span><span class="sxs-lookup"><span data-stu-id="3408f-157">The `ConfigureServices` method registers services that the app uses, including platform features.</span></span> <span data-ttu-id="3408f-158">Изначально коллекция `IServiceCollection`, предоставленная для `ConfigureServices`, содержит определенные платформой службы (в зависимости от [настройки узла](generic-host.md#host-configuration)).</span><span class="sxs-lookup"><span data-stu-id="3408f-158">Initially, the `IServiceCollection` provided to `ConfigureServices` has services defined by the framework depending on [how the host was configured](generic-host.md#host-configuration).</span></span> <span data-ttu-id="3408f-159">Для приложений, основанных на шаблонах .NET, платформа регистрирует несколько сотен служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-159">For apps based on the .NET templates, the framework registers hundreds of services.</span></span>

<span data-ttu-id="3408f-160">В следующей таблице перечислены некоторые примеры этих зарегистрированных платформой служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-160">The following table lists a small sample of these framework-registered services:</span></span>

| <span data-ttu-id="3408f-161">Тип службы</span><span class="sxs-lookup"><span data-stu-id="3408f-161">Service Type</span></span>                                                                                  | <span data-ttu-id="3408f-162">Время существования</span><span class="sxs-lookup"><span data-stu-id="3408f-162">Lifetime</span></span>  |
|-----------------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory?displayProperty=fullName> | <span data-ttu-id="3408f-163">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-163">Singleton</span></span> |
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                                  | <span data-ttu-id="3408f-164">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-164">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>                      | <span data-ttu-id="3408f-165">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-165">Singleton</span></span> |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>                   | <span data-ttu-id="3408f-166">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-166">Singleton</span></span> |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName>            | <span data-ttu-id="3408f-167">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-167">Singleton</span></span> |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName>            | <span data-ttu-id="3408f-168">Временный</span><span class="sxs-lookup"><span data-stu-id="3408f-168">Transient</span></span> |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>                     | <span data-ttu-id="3408f-169">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-169">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>                         | <span data-ttu-id="3408f-170">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-170">Singleton</span></span> |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                           | <span data-ttu-id="3408f-171">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-171">Singleton</span></span> |

## <a name="service-lifetimes"></a><span data-ttu-id="3408f-172">Время существования служб</span><span class="sxs-lookup"><span data-stu-id="3408f-172">Service lifetimes</span></span>

<span data-ttu-id="3408f-173">Службы можно зарегистрировать с одним из следующих вариантов времени существования:</span><span class="sxs-lookup"><span data-stu-id="3408f-173">Services can be registered with one of the following lifetimes:</span></span>

- <span data-ttu-id="3408f-174">Временный</span><span class="sxs-lookup"><span data-stu-id="3408f-174">Transient</span></span>
- <span data-ttu-id="3408f-175">Область действия</span><span class="sxs-lookup"><span data-stu-id="3408f-175">Scoped</span></span>
- <span data-ttu-id="3408f-176">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-176">Singleton</span></span>

<span data-ttu-id="3408f-177">Они описываются в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="3408f-177">The following sections describe each of the preceding lifetimes.</span></span> <span data-ttu-id="3408f-178">Для каждой зарегистрированной службы выбирайте подходящее время существования.</span><span class="sxs-lookup"><span data-stu-id="3408f-178">Choose an appropriate lifetime for each registered service.</span></span>

### <a name="transient"></a><span data-ttu-id="3408f-179">Временный</span><span class="sxs-lookup"><span data-stu-id="3408f-179">Transient</span></span>

<span data-ttu-id="3408f-180">Временные службы времени существования создаются при каждом их запросе из контейнера служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-180">Transient lifetime services are created each time they're requested from the service container.</span></span> <span data-ttu-id="3408f-181">Это время существования лучше всего подходит для простых служб без отслеживания состояния.</span><span class="sxs-lookup"><span data-stu-id="3408f-181">This lifetime works best for lightweight, stateless services.</span></span> <span data-ttu-id="3408f-182">Регистрируйте временные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span><span class="sxs-lookup"><span data-stu-id="3408f-182">Register transient services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.</span></span>

<span data-ttu-id="3408f-183">В приложениях, обрабатывающих запросы, временные службы удаляются в конце запроса.</span><span class="sxs-lookup"><span data-stu-id="3408f-183">In apps that process requests, transient services are disposed at the end of the request.</span></span>

### <a name="scoped"></a><span data-ttu-id="3408f-184">Область действия</span><span class="sxs-lookup"><span data-stu-id="3408f-184">Scoped</span></span>

<span data-ttu-id="3408f-185">Для веб-приложений время существования, привязанное к области, означает, что службы создаются один раз для каждого запроса (подключения) клиента.</span><span class="sxs-lookup"><span data-stu-id="3408f-185">For web applications, a scoped lifetime indicates that services are created once per client request (connection).</span></span> <span data-ttu-id="3408f-186">Регистрируйте службы с заданной областью с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span><span class="sxs-lookup"><span data-stu-id="3408f-186">Register scoped services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.</span></span>

<span data-ttu-id="3408f-187">В приложениях, обрабатывающих запросы, службы с заданной областью удаляются в конце запроса.</span><span class="sxs-lookup"><span data-stu-id="3408f-187">In apps that process requests, scoped services are disposed at the end of the request.</span></span>

<span data-ttu-id="3408f-188">При использовании Entity Framework Core метод расширения <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> по умолчанию регистрирует типы `DbContext` с заданной областью времени существования.</span><span class="sxs-lookup"><span data-stu-id="3408f-188">When using Entity Framework Core, the <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> extension method registers `DbContext` types with a scoped lifetime by default.</span></span>

> [!NOTE]
> <span data-ttu-id="3408f-189">Разрешать службу с заданной областью из одноэлементной службы ***запрещено***, и будьте внимательны, чтобы не сделать это неявно, например, через временную службу.</span><span class="sxs-lookup"><span data-stu-id="3408f-189">Do ***not*** resolve a scoped service from a singleton and be careful not to do so indirectly, for example, through a transient service.</span></span> <span data-ttu-id="3408f-190">При обработке последующих запросов это может вызвать неправильное состояние службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-190">It may cause the service to have incorrect state when processing subsequent requests.</span></span> <span data-ttu-id="3408f-191">Допускается следующее:</span><span class="sxs-lookup"><span data-stu-id="3408f-191">It's fine to:</span></span>
>
> - <span data-ttu-id="3408f-192">Разрешение одноэлементной службы из службы с заданной областью или временной службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-192">Resolve a singleton service from a scoped or transient service.</span></span>
> - <span data-ttu-id="3408f-193">Разрешение службы с заданной областью из другой службы с заданной областью или временной службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-193">Resolve a scoped service from another scoped or transient service.</span></span>

<span data-ttu-id="3408f-194">По умолчанию в среде разработки разрешение службы из другой службы с более длинным временем существования вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="3408f-194">By default, in the development environment, resolving a service from another service with a longer lifetime throws an exception.</span></span> <span data-ttu-id="3408f-195">Дополнительные сведения см. в разделе [Проверка области](#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="3408f-195">For more information, see [Scope validation](#scope-validation).</span></span>

### <a name="singleton"></a><span data-ttu-id="3408f-196">Одноэлементный</span><span class="sxs-lookup"><span data-stu-id="3408f-196">Singleton</span></span>

<span data-ttu-id="3408f-197">Одноэлементные службы времени существования создаются в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="3408f-197">Singleton lifetime services are created either:</span></span>

- <span data-ttu-id="3408f-198">При первом запросе.</span><span class="sxs-lookup"><span data-stu-id="3408f-198">The first time they're requested.</span></span>
- <span data-ttu-id="3408f-199">Разработчиком при предоставлении экземпляра реализации непосредственно в контейнер.</span><span class="sxs-lookup"><span data-stu-id="3408f-199">By the developer, when providing an implementation instance directly to the container.</span></span> <span data-ttu-id="3408f-200">Этот подход требуется достаточно редко.</span><span class="sxs-lookup"><span data-stu-id="3408f-200">This approach is rarely needed.</span></span>

<span data-ttu-id="3408f-201">Каждый последующий запрос на реализацию службы из контейнера внедрения зависимостей использует тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="3408f-201">Every subsequent request of the service implementation from the dependency injection container uses the same instance.</span></span> <span data-ttu-id="3408f-202">Если в приложении нужно использовать одноэлементные службы, разрешите контейнеру служб управлять временем их существования.</span><span class="sxs-lookup"><span data-stu-id="3408f-202">If the app requires singleton behavior, allow the service container to manage the service's lifetime.</span></span> <span data-ttu-id="3408f-203">Не реализуйте одноэлементный подход и предоставьте код для удаления одноэлементных объектов.</span><span class="sxs-lookup"><span data-stu-id="3408f-203">Don't implement the singleton design pattern and provide code to dispose of the singleton.</span></span> <span data-ttu-id="3408f-204">Службы никогда не должны удаляться кодом, который разрешил службу из контейнера.</span><span class="sxs-lookup"><span data-stu-id="3408f-204">Services should never be disposed by code that resolved the service from the container.</span></span> <span data-ttu-id="3408f-205">Если тип или фабрика зарегистрированы как одноэлементный объект, контейнер автоматически удалит одноэлементные объекты.</span><span class="sxs-lookup"><span data-stu-id="3408f-205">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="3408f-206">Зарегистрируйте одноэлементные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span><span class="sxs-lookup"><span data-stu-id="3408f-206">Register singleton services with <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>.</span></span> <span data-ttu-id="3408f-207">Одноэлементные службы должны быть потокобезопасными и часто использоваться в службах без отслеживания состояния.</span><span class="sxs-lookup"><span data-stu-id="3408f-207">Singleton services must be thread safe and are often used in stateless services.</span></span>

<span data-ttu-id="3408f-208">В приложениях, обрабатывающих запросы, отдельные службы удаляются, когда <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> удаляется по завершении работы приложения.</span><span class="sxs-lookup"><span data-stu-id="3408f-208">In apps that process requests, singleton services are disposed when the <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> is disposed on application shutdown.</span></span> <span data-ttu-id="3408f-209">Поскольку память не освобождается до завершения работы приложения, рекомендуется учитывать использование памяти одноэлементным объектом.</span><span class="sxs-lookup"><span data-stu-id="3408f-209">Because memory is not released until the app is shut down, consider memory use with a singleton service.</span></span>

## <a name="service-registration-methods"></a><span data-ttu-id="3408f-210">Методы регистрации службы</span><span class="sxs-lookup"><span data-stu-id="3408f-210">Service registration methods</span></span>

<span data-ttu-id="3408f-211">Платформа предоставляет методы расширения регистрации службы, которые полезны в определенных сценариях.</span><span class="sxs-lookup"><span data-stu-id="3408f-211">The framework provides service registration extension methods that are useful in specific scenarios:</span></span>

| <span data-ttu-id="3408f-212">Метод</span><span class="sxs-lookup"><span data-stu-id="3408f-212">Method</span></span> | <span data-ttu-id="3408f-213">Автоматически</span><span class="sxs-lookup"><span data-stu-id="3408f-213">Automatic</span></span><br><span data-ttu-id="3408f-214">объект</span><span class="sxs-lookup"><span data-stu-id="3408f-214">object</span></span><br><span data-ttu-id="3408f-215">удаление</span><span class="sxs-lookup"><span data-stu-id="3408f-215">disposal</span></span> | <span data-ttu-id="3408f-216">Несколько</span><span class="sxs-lookup"><span data-stu-id="3408f-216">Multiple</span></span><br><span data-ttu-id="3408f-217">реализации</span><span class="sxs-lookup"><span data-stu-id="3408f-217">implementations</span></span> | <span data-ttu-id="3408f-218">Передача аргументов</span><span class="sxs-lookup"><span data-stu-id="3408f-218">Pass args</span></span> |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br><span data-ttu-id="3408f-219">Пример</span><span class="sxs-lookup"><span data-stu-id="3408f-219">Example:</span></span><br><br>`services.AddSingleton<IMyDep, MyDep>();` | <span data-ttu-id="3408f-220">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-220">Yes</span></span> | <span data-ttu-id="3408f-221">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-221">Yes</span></span> | <span data-ttu-id="3408f-222">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-222">No</span></span> |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br><span data-ttu-id="3408f-223">Примеры:</span><span class="sxs-lookup"><span data-stu-id="3408f-223">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | <span data-ttu-id="3408f-224">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-224">Yes</span></span> | <span data-ttu-id="3408f-225">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-225">Yes</span></span> | <span data-ttu-id="3408f-226">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-226">Yes</span></span> |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br><span data-ttu-id="3408f-227">Пример</span><span class="sxs-lookup"><span data-stu-id="3408f-227">Example:</span></span><br><br>`services.AddSingleton<MyDep>();` | <span data-ttu-id="3408f-228">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-228">Yes</span></span> | <span data-ttu-id="3408f-229">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-229">No</span></span> | <span data-ttu-id="3408f-230">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-230">No</span></span> |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br><span data-ttu-id="3408f-231">Примеры:</span><span class="sxs-lookup"><span data-stu-id="3408f-231">Examples:</span></span><br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | <span data-ttu-id="3408f-232">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-232">No</span></span> | <span data-ttu-id="3408f-233">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-233">Yes</span></span> | <span data-ttu-id="3408f-234">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-234">Yes</span></span> |
| `AddSingleton(new {IMPLEMENTATION})`<br><br><span data-ttu-id="3408f-235">Примеры:</span><span class="sxs-lookup"><span data-stu-id="3408f-235">Examples:</span></span><br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | <span data-ttu-id="3408f-236">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-236">No</span></span> | <span data-ttu-id="3408f-237">Нет</span><span class="sxs-lookup"><span data-stu-id="3408f-237">No</span></span> | <span data-ttu-id="3408f-238">Да</span><span class="sxs-lookup"><span data-stu-id="3408f-238">Yes</span></span> |

<span data-ttu-id="3408f-239">Дополнительные сведения об удалении типа см. в разделе [Удаление служб](dependency-injection-guidelines.md#disposal-of-services).</span><span class="sxs-lookup"><span data-stu-id="3408f-239">For more information on type disposal, see the [Disposal of services](dependency-injection-guidelines.md#disposal-of-services) section.</span></span>

<span data-ttu-id="3408f-240">Регистрация службы только с типом реализации эквивалентна регистрации этой службы с той же реализацией и типом службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-240">Registering a service with only an implementation type is equivalent to registering that service with the same implementation and service type.</span></span> <span data-ttu-id="3408f-241">Именно поэтому несколько реализаций службы не могут быть зарегистрированы с помощью методов, которые не принимают явный тип службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-241">This is why multiple implementations of a service cannot be registered using the methods that don't take an explicit service type.</span></span> <span data-ttu-id="3408f-242">Эти методы могут регистрировать несколько *экземпляров* службы, но все они будут иметь одинаковую *реализацию* типа.</span><span class="sxs-lookup"><span data-stu-id="3408f-242">These methods can register multiple *instances* of a service, but they will all have the same *implementation* type.</span></span>

<span data-ttu-id="3408f-243">Любой из указанных выше методов регистрации службы можно использовать для регистрации нескольких экземпляров службы одного типа службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-243">Any of the above service registration methods can be used to register multiple service instances of the same service type.</span></span> <span data-ttu-id="3408f-244">В следующем примере метод `AddSingleton` вызывается дважды с типом службы `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-244">In the following example, `AddSingleton` is called twice with `IMessageWriter` as the service type.</span></span> <span data-ttu-id="3408f-245">Второй вызов `AddSingleton` переопределяет предыдущий, если он разрешается как `IMessageWriter`, и добавляет к предыдущему, если несколько служб разрешаются через `IEnumerable<IMessageWriter>`.</span><span class="sxs-lookup"><span data-stu-id="3408f-245">The second call to `AddSingleton` overrides the previous one when resolved as `IMessageWriter` and adds to the previous one when multiple services are resolved via `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="3408f-246">Службы отображаются в том порядке, в котором они были зарегистрированы при разрешении через `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="3408f-246">Services appear in the order they were registered when resolved via `IEnumerable<{SERVICE}>`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

<span data-ttu-id="3408f-247">Предыдущий пример исходного кода регистрирует две реализации `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-247">The preceding sample source code registers two implementations of the `IMessageWriter`.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

<span data-ttu-id="3408f-248">Компонент `ExampleService` определяет два параметра конструктора: одиночный `IMessageWriter` и `IEnumerable<IMessageWriter>`.</span><span class="sxs-lookup"><span data-stu-id="3408f-248">The `ExampleService` defines two constructor parameters; a single `IMessageWriter`, and an `IEnumerable<IMessageWriter>`.</span></span> <span data-ttu-id="3408f-249">Одиночный `IMessageWriter` здесь является последней зарегистрированной реализацией, а `IEnumerable<IMessageWriter>` представляет все зарегистрированные реализации.</span><span class="sxs-lookup"><span data-stu-id="3408f-249">The single `IMessageWriter` is the last implementation to have been registered, whereas the `IEnumerable<IMessageWriter>` represents all registered implementations.</span></span>

<span data-ttu-id="3408f-250">Платформа также предоставляет методы расширения `TryAdd{LIFETIME}`, которые регистрируют службу только в том случае, если реализация еще не зарегистрирована.</span><span class="sxs-lookup"><span data-stu-id="3408f-250">The framework also provides `TryAdd{LIFETIME}` extension methods, which register the service only if there isn't already an implementation registered.</span></span>

<span data-ttu-id="3408f-251">В следующем примере вызов `AddSingleton` регистрирует `ConsoleMessageWriter` как реализацию для `IMessageWriter`.</span><span class="sxs-lookup"><span data-stu-id="3408f-251">In the following example, the call to `AddSingleton` registers `ConsoleMessageWriter` as an implementation for `IMessageWriter`.</span></span> <span data-ttu-id="3408f-252">Вызов `TryAddSingleton` ничего не делает, поскольку у `IMessageWriter` уже есть зарегистрированная реализация:</span><span class="sxs-lookup"><span data-stu-id="3408f-252">The call to `TryAddSingleton` has no effect because `IMessageWriter` already has a registered implementation:</span></span>

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

<span data-ttu-id="3408f-253">Параметр `TryAddSingleton` не применяется, так как он уже был добавлен, поэтому выполнение "try" завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3408f-253">The `TryAddSingleton` has no effect, as it was already added and the "try" will fail.</span></span> <span data-ttu-id="3408f-254">В `ExampleService` будут следующие утверждения:</span><span class="sxs-lookup"><span data-stu-id="3408f-254">The `ExampleService` would assert the following:</span></span>

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

<span data-ttu-id="3408f-255">Дополнительные сведения см. в разделе:</span><span class="sxs-lookup"><span data-stu-id="3408f-255">For more information, see:</span></span>

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

<span data-ttu-id="3408f-256">Методы [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) регистрируют службу только в том случае, если еще не существует реализации *того же типа*.</span><span class="sxs-lookup"><span data-stu-id="3408f-256">The [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) methods register the service only if there isn't already an implementation *of the same type*.</span></span> <span data-ttu-id="3408f-257">Несколько служб разрешается через `IEnumerable<{SERVICE}>`.</span><span class="sxs-lookup"><span data-stu-id="3408f-257">Multiple services are resolved via `IEnumerable<{SERVICE}>`.</span></span> <span data-ttu-id="3408f-258">При регистрации служб добавляйте экземпляр в том случае, если экземпляр такого типа еще не был добавлен.</span><span class="sxs-lookup"><span data-stu-id="3408f-258">When registering services, add an instance if one of the same types hasn't already been added.</span></span> <span data-ttu-id="3408f-259">Авторы библиотек используют `TryAddEnumerable`, чтобы избежать регистрации нескольких копий реализации в контейнере.</span><span class="sxs-lookup"><span data-stu-id="3408f-259">Library authors use `TryAddEnumerable` to avoid registering multiple copies of an implementation in the container.</span></span>

<span data-ttu-id="3408f-260">В следующем примере первый вызов `TryAddEnumerable` регистрирует `MessageWriter` как реализацию для `IMessageWriter1`.</span><span class="sxs-lookup"><span data-stu-id="3408f-260">In the following example, the first call to `TryAddEnumerable` registers `MessageWriter` as an implementation for `IMessageWriter1`.</span></span> <span data-ttu-id="3408f-261">Второй вызов регистрирует `MessageWriter` для `IMessageWriter2`.</span><span class="sxs-lookup"><span data-stu-id="3408f-261">The second call registers `MessageWriter` for `IMessageWriter2`.</span></span> <span data-ttu-id="3408f-262">Третий вызов ничего не делает, поскольку у `IMessageWriter1` уже есть зарегистрированная реализация `MessageWriter`:</span><span class="sxs-lookup"><span data-stu-id="3408f-262">The third call has no effect because `IMessageWriter1` already has a registered implementation of `MessageWriter`:</span></span>

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

<span data-ttu-id="3408f-263">Регистрация службы обычно не зависит от порядка, за исключением случаев регистрации нескольких реализаций одного типа.</span><span class="sxs-lookup"><span data-stu-id="3408f-263">Service registration is generally order independent except when registering multiple implementations of the same type.</span></span>

<span data-ttu-id="3408f-264">`IServiceCollection` является коллекцией объектов <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="3408f-264">`IServiceCollection` is a collection of <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objects.</span></span> <span data-ttu-id="3408f-265">В следующем примере показано, как зарегистрировать службу, создав и добавив `ServiceDescriptor`:</span><span class="sxs-lookup"><span data-stu-id="3408f-265">The following example shows how to register a service by creating and adding a `ServiceDescriptor`:</span></span>

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

<span data-ttu-id="3408f-266">Встроенные методы `Add{LIFETIME}` используют аналогичный подход.</span><span class="sxs-lookup"><span data-stu-id="3408f-266">The built-in `Add{LIFETIME}` methods use the same approach.</span></span> <span data-ttu-id="3408f-267">Например, см. [исходный код для AddScoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span><span class="sxs-lookup"><span data-stu-id="3408f-267">For example, see the [AddScoped source code](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).</span></span>

### <a name="constructor-injection-behavior"></a><span data-ttu-id="3408f-268">Поведение внедрения через конструктор</span><span class="sxs-lookup"><span data-stu-id="3408f-268">Constructor injection behavior</span></span>

<span data-ttu-id="3408f-269">Службы можно разрешать с помощью:</span><span class="sxs-lookup"><span data-stu-id="3408f-269">Services can be resolved by using:</span></span>

- <xref:System.IServiceProvider>
- <span data-ttu-id="3408f-270"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span><span class="sxs-lookup"><span data-stu-id="3408f-270"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:</span></span>
  - <span data-ttu-id="3408f-271">Создает объекты, которые не зарегистрированы в контейнере.</span><span class="sxs-lookup"><span data-stu-id="3408f-271">Creates objects that aren't registered in the container.</span></span>
  - <span data-ttu-id="3408f-272">Используется в сочетании с некоторыми возможностями платформы.</span><span class="sxs-lookup"><span data-stu-id="3408f-272">Used with some framework features.</span></span>

<span data-ttu-id="3408f-273">Конструкторы могут принимать аргументы, которые не предоставляются внедрением зависимостей, но эти аргументы должны назначать значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3408f-273">Constructors can accept arguments that aren't provided by dependency injection, but the arguments must assign default values.</span></span>

<span data-ttu-id="3408f-274">Когда разрешение служб выполняется через `IServiceProvider` или `ActivatorUtilities`, для внедрения через конструктор требуется *открытый* конструктор.</span><span class="sxs-lookup"><span data-stu-id="3408f-274">When services are resolved by `IServiceProvider` or `ActivatorUtilities`, constructor injection requires a *public* constructor.</span></span>

<span data-ttu-id="3408f-275">Когда разрешение служб выполняется через `ActivatorUtilities`, для внедрения с помощью конструктора требуется наличие только одного соответствующего конструктора.</span><span class="sxs-lookup"><span data-stu-id="3408f-275">When services are resolved by `ActivatorUtilities`, constructor injection requires that only one applicable constructor exists.</span></span> <span data-ttu-id="3408f-276">Перегрузки конструктора поддерживаются, но может существовать всего одна перегрузка, все аргументы которой могут быть обработаны с помощью внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="3408f-276">Constructor overloads are supported, but only one overload can exist whose arguments can all be fulfilled by dependency injection.</span></span>

## <a name="scope-validation"></a><span data-ttu-id="3408f-277">Проверка области</span><span class="sxs-lookup"><span data-stu-id="3408f-277">Scope validation</span></span>

<span data-ttu-id="3408f-278">Когда приложение выполняется в среде `Development` и вызывает [CreateDefaultBuilder](generic-host.md#default-builder-settings) для создания узла, поставщик службы по умолчанию проверяет следующее:</span><span class="sxs-lookup"><span data-stu-id="3408f-278">When the app runs in the `Development` environment and calls [CreateDefaultBuilder](generic-host.md#default-builder-settings) to build the host, the default service provider performs checks to verify that:</span></span>

- <span data-ttu-id="3408f-279">Службы с заданной областью не разрешаются из корневого поставщика службы.</span><span class="sxs-lookup"><span data-stu-id="3408f-279">Scoped services aren't resolved from the root service provider.</span></span>
- <span data-ttu-id="3408f-280">Службы с заданной областью не вводятся в одноэлементные объекты.</span><span class="sxs-lookup"><span data-stu-id="3408f-280">Scoped services aren't injected into singletons.</span></span>

<span data-ttu-id="3408f-281">Корневой поставщик службы создается при вызове <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A>.</span><span class="sxs-lookup"><span data-stu-id="3408f-281">The root service provider is created when <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> is called.</span></span> <span data-ttu-id="3408f-282">Время существования корневого поставщика службы соответствует времени существования приложения — поставщик запускается с приложением и удаляется, когда приложение завершает работу.</span><span class="sxs-lookup"><span data-stu-id="3408f-282">The root service provider's lifetime corresponds to the app's lifetime when the provider starts with the app and is disposed when the app shuts down.</span></span>

<span data-ttu-id="3408f-283">Службы с заданной областью удаляются создавшим их контейнером.</span><span class="sxs-lookup"><span data-stu-id="3408f-283">Scoped services are disposed by the container that created them.</span></span> <span data-ttu-id="3408f-284">Если служба с заданной областью создается в корневом контейнере, время существования службы повышается до уровня одноэлементного объекта, поскольку она удаляется только корневым контейнером при завершении работы приложения.</span><span class="sxs-lookup"><span data-stu-id="3408f-284">If a scoped service is created in the root container, the service's lifetime is effectively promoted to singleton because it's only disposed by the root container when the app shuts down.</span></span> <span data-ttu-id="3408f-285">Проверка областей службы перехватывает эти ситуации при вызове `BuildServiceProvider`.</span><span class="sxs-lookup"><span data-stu-id="3408f-285">Validating service scopes catches these situations when `BuildServiceProvider` is called.</span></span>

## <a name="scope-scenarios"></a><span data-ttu-id="3408f-286">Сценарии применения области</span><span class="sxs-lookup"><span data-stu-id="3408f-286">Scope scenarios</span></span>

<span data-ttu-id="3408f-287">Интерфейс <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory> всегда регистрируется как отдельный (singleton), но <xref:System.IServiceProvider> зависит от времени существования содержащего класса.</span><span class="sxs-lookup"><span data-stu-id="3408f-287">The <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory> is always registered as a singleton, but the <xref:System.IServiceProvider> can vary based on the lifetime of the containing class.</span></span> <span data-ttu-id="3408f-288">Например, если при разрешении служб из области какая-то из служб принимает интерфейс <xref:System.IServiceProvider>, это будет экземпляр с заданной областью.</span><span class="sxs-lookup"><span data-stu-id="3408f-288">For example, if you resolve services from a scope, and any of those services take an <xref:System.IServiceProvider>, it'll be a scoped instance.</span></span>

<span data-ttu-id="3408f-289">Для получения служб с заданной областью в реализациях <xref:Microsoft.Extensions.Hosting.IHostedService>, например службы <xref:Microsoft.Extensions.Hosting.BackgroundService>, *не внедряйте* зависимости служб через конструктор.</span><span class="sxs-lookup"><span data-stu-id="3408f-289">To achieve scoping services within implementations of <xref:Microsoft.Extensions.Hosting.IHostedService>, such as the <xref:Microsoft.Extensions.Hosting.BackgroundService>, do *not* inject the service dependencies via constructor injection.</span></span> <span data-ttu-id="3408f-290">Вместо этого внедрите <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory>, создайте область, а затем используйте разрешение зависимостей из области, чтобы применить подходящее время существования служб.</span><span class="sxs-lookup"><span data-stu-id="3408f-290">Instead, inject <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory>, create a scope, then resolve dependencies from the scope to use the appropriate service lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/worker-scope/Worker.cs" highlight="13,15-16,22":::

<span data-ttu-id="3408f-291">В приведенном выше коде во время выполнения приложения фоновая служба:</span><span class="sxs-lookup"><span data-stu-id="3408f-291">In the preceding code, while the app is running, the background service:</span></span>

- <span data-ttu-id="3408f-292">зависит от <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory>;</span><span class="sxs-lookup"><span data-stu-id="3408f-292">Depends on the <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory>.</span></span>
- <span data-ttu-id="3408f-293">создает <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> для разрешения дополнительных служб;</span><span class="sxs-lookup"><span data-stu-id="3408f-293">Creates an <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> for resolving additional services.</span></span>
- <span data-ttu-id="3408f-294">разрешает службы с заданной областью для использования;</span><span class="sxs-lookup"><span data-stu-id="3408f-294">Resolves scoped services for consumption.</span></span>
- <span data-ttu-id="3408f-295">обрабатывает объекты, затем ретранслирует их и в итоге помечает как обработанные.</span><span class="sxs-lookup"><span data-stu-id="3408f-295">Works on processing objects and then relaying them, and finally marks them as processed.</span></span>

<span data-ttu-id="3408f-296">В примере исходного кода можно увидеть, как реализации <xref:Microsoft.Extensions.Hosting.IHostedService> могут использовать преимущества времени существования служб с заданной областью.</span><span class="sxs-lookup"><span data-stu-id="3408f-296">From the sample source code, you can see how implementations of <xref:Microsoft.Extensions.Hosting.IHostedService> can benefit from scoped service lifetimes.</span></span>

## <a name="see-also"></a><span data-ttu-id="3408f-297">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3408f-297">See also</span></span>

- [<span data-ttu-id="3408f-298">Использование внедрения зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="3408f-298">Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
- [<span data-ttu-id="3408f-299">Рекомендации по внедрению зависимостей</span><span class="sxs-lookup"><span data-stu-id="3408f-299">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
- [<span data-ttu-id="3408f-300">Внедрение зависимостей в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3408f-300">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
- [<span data-ttu-id="3408f-301">Шаблоны конференций NDC для разработки приложений с внедрением зависимостей</span><span class="sxs-lookup"><span data-stu-id="3408f-301">NDC Conference Patterns for DI app development</span></span>](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [<span data-ttu-id="3408f-302">Принцип явных зависимостей</span><span class="sxs-lookup"><span data-stu-id="3408f-302">Explicit dependencies principle</span></span>](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [<span data-ttu-id="3408f-303">Контейнеры с инверсией управления и шаблон внедрения зависимостей (Мартин Фаулер (Martin Fowler))</span><span class="sxs-lookup"><span data-stu-id="3408f-303">Inversion of control containers and the dependency injection pattern (Martin Fowler)</span></span>](https://www.martinfowler.com/articles/injection.html)
- <span data-ttu-id="3408f-304">Запросы на исправление ошибок, связанных с внедрением зависимостей, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)</span><span class="sxs-lookup"><span data-stu-id="3408f-304">DI bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
