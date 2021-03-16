---
title: Универсальный узел .NET
author: IEvangelist
description: Сведения об универсальном узле .NET, который отвечает за запуск приложений и управление временем существования.
ms.author: dapine
ms.date: 12/18/2020
ms.openlocfilehash: bf6d5ad624bbed46994633abace0af64712757f3
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2020
ms.locfileid: "102402120"
---
# <a name="net-generic-host"></a><span data-ttu-id="a2e4f-103">Универсальный узел .NET</span><span class="sxs-lookup"><span data-stu-id="a2e4f-103">.NET Generic Host</span></span>

<span data-ttu-id="a2e4f-104">Шаблоны рабочей службы создают универсальный узел .NET <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="a2e4f-105">Этот универсальный узел можно использовать в сочетании с другими типами приложений .NET, такими как консольные приложения.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="a2e4f-106">*Узел* — это объект, который инкапсулирует все ресурсы приложения, такие как:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="a2e4f-107">Внедрение зависимостей</span><span class="sxs-lookup"><span data-stu-id="a2e4f-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="a2e4f-108">Ведение журнала</span><span class="sxs-lookup"><span data-stu-id="a2e4f-108">Logging</span></span>
- <span data-ttu-id="a2e4f-109">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="a2e4f-109">Configuration</span></span>
- <span data-ttu-id="a2e4f-110">Реализации `IHostedService`</span><span class="sxs-lookup"><span data-stu-id="a2e4f-110">`IHostedService` implementations</span></span>

<span data-ttu-id="a2e4f-111">После запуска узла он вызывает <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> в каждой реализации <xref:Microsoft.Extensions.Hosting.IHostedService>, зарегистрированной в коллекции размещенных служб контейнера службы.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="a2e4f-112">В приложении рабочей службы для всех реализаций `IHostedService`, которые содержат экземпляры <xref:Microsoft.Extensions.Hosting.BackgroundService>, вызываются соответствующие методы <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="a2e4f-113">Основной причиной включения всех взаимозависимых ресурсов приложения в один объект является управление жизненным циклом: контроль запуска и корректного завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="a2e4f-114">Это достигается с помощью пакета NuGet [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting).</span><span class="sxs-lookup"><span data-stu-id="a2e4f-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="a2e4f-115">Создание узла</span><span class="sxs-lookup"><span data-stu-id="a2e4f-115">Set up a host</span></span>

<span data-ttu-id="a2e4f-116">Узел обычно настраивается, собирается и выполняется кодом в классе `Program`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="a2e4f-117">Метод `Main`:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-117">The `Main` method:</span></span>

- <span data-ttu-id="a2e4f-118">Вызывает метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> для создания и настройки объекта построителя.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="a2e4f-119">Вызывает метод <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> для создания экземпляра <xref:Microsoft.Extensions.Hosting.IHost>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="a2e4f-120">Вызывает метод <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> или <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> для объекта узла.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="a2e4f-121">Шаблоны рабочей службы .NET генерируют следующий код для создания универсального узла:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="a2e4f-122">Параметры построителя по умолчанию</span><span class="sxs-lookup"><span data-stu-id="a2e4f-122">Default builder settings</span></span>

<span data-ttu-id="a2e4f-123">Метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="a2e4f-124">В качестве корня содержимого задает путь, возвращенный методом <xref:System.IO.Directory.GetCurrentDirectory>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="a2e4f-125">Загружает [конфигурацию узла](#host-configuration) из:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="a2e4f-126">Переменные среды с префиксом `DOTNET_`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="a2e4f-127">аргументы командной строки.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-127">Command-line arguments.</span></span>
- <span data-ttu-id="a2e4f-128">Загружает конфигурацию приложения из:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="a2e4f-129">*appsettings.json*;</span><span class="sxs-lookup"><span data-stu-id="a2e4f-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="a2e4f-130">*appsettings.{Environment}.json*;</span><span class="sxs-lookup"><span data-stu-id="a2e4f-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="a2e4f-131">диспетчер секретов, когда приложение выполняется в среде `Development`;</span><span class="sxs-lookup"><span data-stu-id="a2e4f-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="a2e4f-132">Переменные среды.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-132">Environment variables.</span></span>
  - <span data-ttu-id="a2e4f-133">аргументы командной строки.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-133">Command-line arguments.</span></span>
- <span data-ttu-id="a2e4f-134">Добавляет следующие регистраторы:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="a2e4f-135">Консоль</span><span class="sxs-lookup"><span data-stu-id="a2e4f-135">Console</span></span>
  - <span data-ttu-id="a2e4f-136">Отладка</span><span class="sxs-lookup"><span data-stu-id="a2e4f-136">Debug</span></span>
  - <span data-ttu-id="a2e4f-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="a2e4f-137">EventSource</span></span>
  - <span data-ttu-id="a2e4f-138">Журнал событий (только при запуске в Windows)</span><span class="sxs-lookup"><span data-stu-id="a2e4f-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="a2e4f-139">Включает проверку области и [проверку зависимостей](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild), если используется среда `Development`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="a2e4f-140">Метод `ConfigureServices` позволяет добавлять службы в экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a2e4f-141">Позже эти службы можно будет сделать доступными через внедрение зависимостей.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="a2e4f-142">Платформенные службы</span><span class="sxs-lookup"><span data-stu-id="a2e4f-142">Framework-provided services</span></span>

<span data-ttu-id="a2e4f-143">Следующие службы регистрируются автоматически.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="a2e4f-144">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="a2e4f-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="a2e4f-145">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="a2e4f-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="a2e4f-146">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="a2e4f-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="a2e4f-147">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="a2e4f-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="a2e4f-148">Внедрите службу <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> в любой класс для выполнения задач после запуска и корректного завершения работы.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="a2e4f-149">Три свойства этого интерфейса представляют собой токены отмены, которые служат для регистрации методов обработчика событий запуска и завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="a2e4f-150">Этот интерфейс также включает метод <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="a2e4f-151">Ниже приведен пример реализации `IHostedService`, которая регистрирует события `IHostApplicationLifetime`:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="a2e4f-152">Шаблон рабочей службы можно изменить, чтобы добавить в него реализацию `ExampleHostedService`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="a2e4f-153">Приложение запишет следующий образец выходных данных:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="a2e4f-154">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="a2e4f-154">IHostLifetime</span></span>

<span data-ttu-id="a2e4f-155">Реализация <xref:Microsoft.Extensions.Hosting.IHostLifetime> контролирует, когда узел запускается и останавливается.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="a2e4f-156">Используется последняя зарегистрированная реализация.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-156">The last implementation registered is used.</span></span>

<span data-ttu-id="a2e4f-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` — это реализация `IHostLifetime` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="a2e4f-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="a2e4f-159">Прослушивает сигналы <kbd>CTRL</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT) или [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) и вызывает метод <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> для запуска процесса завершения работы.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="a2e4f-160">разблокирует расширения, такие как `RunAsync` и `WaitForShutdownAsync`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="a2e4f-161">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="a2e4f-161">IHostEnvironment</span></span>

<span data-ttu-id="a2e4f-162">Внедряет службу <xref:Microsoft.Extensions.Hosting.IHostEnvironment> в класс, чтобы получить сведения о следующих параметрах.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="a2e4f-163">Конфигурация узла</span><span class="sxs-lookup"><span data-stu-id="a2e4f-163">Host configuration</span></span>

<span data-ttu-id="a2e4f-164">Конфигурация узла используется для настройки свойств реализации [IHostEnvironment](#ihostenvironment).</span><span class="sxs-lookup"><span data-stu-id="a2e4f-164">Host configuration is used to configure properties of the [IHostEnvironment](#ihostenvironment) implementation.</span></span>

<span data-ttu-id="a2e4f-165">Конфигурация узла доступна в [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) через метод <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-165">The host configuration is available in [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) within the <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> method.</span></span> <span data-ttu-id="a2e4f-166">При вызове метода `ConfigureAppConfiguration` в `configureDelegate` передаются `HostBuilderContext` и `IConfigurationBuilder`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-166">When calling the `ConfigureAppConfiguration` method, the `HostBuilderContext` and `IConfigurationBuilder` are passed into the `configureDelegate`.</span></span> <span data-ttu-id="a2e4f-167">Для `configureDelegate` используется определение `Action<HostBuilderContext, IConfigurationBuilder>`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-167">The `configureDelegate` is defined as an `Action<HostBuilderContext, IConfigurationBuilder>`.</span></span> <span data-ttu-id="a2e4f-168">Контекст построителя узла предоставляет свойство `.Configuration`, которое является экземпляром `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-168">The host builder context exposes the `.Configuration` property, which is an instance of `IConfiguration`.</span></span> <span data-ttu-id="a2e4f-169">Он представляет конфигурацию, созданную на основе узла, тогда как `IConfigurationBuilder` представляет собой объект построителя, используемый для настройки приложения.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-169">It represents the configuration built from the host, whereas the `IConfigurationBuilder` is the builder object used to configure the app.</span></span>

> [!TIP]
> <span data-ttu-id="a2e4f-170">После вызова `ConfigureAppConfiguration` элемент `HostBuilderContext.Configuration` заменяется на [app config](#app-configuration).</span><span class="sxs-lookup"><span data-stu-id="a2e4f-170">After `ConfigureAppConfiguration` is called the `HostBuilderContext.Configuration` is replaced with the [app config](#app-configuration).</span></span>

<span data-ttu-id="a2e4f-171">Чтобы добавить конфигурацию узла, вызовите <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> в `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-171">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="a2e4f-172">Метод `ConfigureHostConfiguration` может вызываться несколько раз с накоплением результатов.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-172">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="a2e4f-173">Узел использует значение, заданное последним для данного ключа.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-173">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="a2e4f-174">В следующем примере создается конфигурация узла:</span><span class="sxs-lookup"><span data-stu-id="a2e4f-174">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a><span data-ttu-id="a2e4f-175">Конфигурация приложения</span><span class="sxs-lookup"><span data-stu-id="a2e4f-175">App configuration</span></span>

<span data-ttu-id="a2e4f-176">Конфигурация приложения создается путем вызова метода <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> в `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-176">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="a2e4f-177">Метод `ConfigureAppConfiguration` может вызываться несколько раз с накоплением результатов.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-177">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="a2e4f-178">Приложение использует значение, заданное последним для данного ключа.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-178">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="a2e4f-179">Конфигурация, созданная с помощью `ConfigureAppConfiguration`, доступна в [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) для последующих операций и как служба через внедрение зависимостей.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-179">The configuration created by `ConfigureAppConfiguration` is available in [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="a2e4f-180">Конфигурация узла также добавляется к конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="a2e4f-180">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="a2e4f-181">Дополнительные сведения см. в статье [Конфигурация в .NET](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a2e4f-181">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e4f-182">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a2e4f-182">See also</span></span>

- [<span data-ttu-id="a2e4f-183">Конфигурация в .NET</span><span class="sxs-lookup"><span data-stu-id="a2e4f-183">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="a2e4f-184">Веб-узел ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2e4f-184">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
- <span data-ttu-id="a2e4f-185">Запросы на исправление ошибок, связанных с универсальным узлом, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)</span><span class="sxs-lookup"><span data-stu-id="a2e4f-185">Generic host bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
