---
title: Поставщики ведения журнала в NET
description: Узнайте, как API поставщика ведения журнала используется в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 02/16/2021
ms.openlocfilehash: 7265e51a4d92cd99abebef2ebf0bc5db37b306e3
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "102402153"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="47640-103">Поставщики ведения журнала в NET</span><span class="sxs-lookup"><span data-stu-id="47640-103">Logging providers in .NET</span></span>

<span data-ttu-id="47640-104">Поставщики ведения журналов сохраняют журналы, за исключением поставщика `Console`, в котором журналы отображаются только в стандартном выводе.</span><span class="sxs-lookup"><span data-stu-id="47640-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="47640-105">Например, поставщик Azure Application Insights хранит журналы в Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="47640-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="47640-106">Вы можете включить несколько поставщиков.</span><span class="sxs-lookup"><span data-stu-id="47640-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="47640-107">Шаблоны приложений .NET Worker по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="47640-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="47640-108">используют [универсальный узел](generic-host.md);</span><span class="sxs-lookup"><span data-stu-id="47640-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="47640-109">вызывают метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, который добавляет следующие поставщики ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="47640-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="47640-110">Консоль</span><span class="sxs-lookup"><span data-stu-id="47640-110">Console</span></span>](#console)
  - [<span data-ttu-id="47640-111">Отладка</span><span class="sxs-lookup"><span data-stu-id="47640-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="47640-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="47640-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="47640-113">[EventLog](#windows-eventlog): Только для Windows</span><span class="sxs-lookup"><span data-stu-id="47640-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

<span data-ttu-id="47640-114">В предыдущем коде показан класс `Program`, созданный с использованием шаблонов приложений .NET Worker.</span><span class="sxs-lookup"><span data-stu-id="47640-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="47640-115">В следующих разделах приводятся примеры, которые построены на основе шаблонов приложений .NET Worker и используют универсальный узел.</span><span class="sxs-lookup"><span data-stu-id="47640-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="47640-116">Чтобы переопределить заданный по умолчанию набор поставщиков ведения журнала, добавленных с помощью `Host.CreateDefaultBuilder`, вызовите метод `ClearProviders` и добавьте необходимых поставщиков.</span><span class="sxs-lookup"><span data-stu-id="47640-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="47640-117">Например, приведенный ниже код</span><span class="sxs-lookup"><span data-stu-id="47640-117">For example, the following code:</span></span>

- <span data-ttu-id="47640-118">вызывает метод <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> для удаления всех экземпляров <xref:Microsoft.Extensions.Logging.ILoggerProvider> из построителя;</span><span class="sxs-lookup"><span data-stu-id="47640-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="47640-119">добавляет поставщик ведения журнала [Console](#console).</span><span class="sxs-lookup"><span data-stu-id="47640-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="47640-120">Сведения о других поставщиках см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="47640-120">For additional providers, see:</span></span>

- <span data-ttu-id="47640-121">[Встроенные поставщики ведения журнала](#built-in-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="47640-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="47640-122">[Сторонние поставщики ведения журнала](#third-party-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="47640-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="47640-123">Настройка службы, зависящей от ILogger</span><span class="sxs-lookup"><span data-stu-id="47640-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="47640-124">Чтобы настроить службу, зависящую от `ILogger<T>`, используйте внедрение конструктора или предоставьте фабричный метод.</span><span class="sxs-lookup"><span data-stu-id="47640-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="47640-125">Фабричный метод рекомендуется использовать, только если нет других вариантов.</span><span class="sxs-lookup"><span data-stu-id="47640-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="47640-126">Например, рассмотрим службу, которой требуется экземпляр `ILogger<T>`, предоставляемый путем внедрения зависимостей:</span><span class="sxs-lookup"><span data-stu-id="47640-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="47640-127">Приведенный выше код — это функция [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2), которая выполняется, когда контейнеру внедрения зависимостей впервые требуется создать экземпляр `IExampleService`.</span><span class="sxs-lookup"><span data-stu-id="47640-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="47640-128">Таким образом можно обращаться к любым зарегистрированным службам.</span><span class="sxs-lookup"><span data-stu-id="47640-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="47640-129">Встроенные поставщики ведения журналов</span><span class="sxs-lookup"><span data-stu-id="47640-129">Built-in logging providers</span></span>

<span data-ttu-id="47640-130">Расширения Майкрософт включают в себя следующих поставщиков ведения журналов в составе библиотек среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="47640-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="47640-131">Консоль</span><span class="sxs-lookup"><span data-stu-id="47640-131">Console</span></span>](#console)
- [<span data-ttu-id="47640-132">Отладка</span><span class="sxs-lookup"><span data-stu-id="47640-132">Debug</span></span>](#debug)
- [<span data-ttu-id="47640-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="47640-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="47640-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="47640-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="47640-135">Следующие поставщики ведения журналов поставляются корпорацией Майкрософт, но не в составе библиотек среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="47640-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="47640-136">Их необходимо устанавливать в виде дополнительных пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="47640-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="47640-137">AzureAppServicesFile и AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="47640-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="47640-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="47640-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="47640-139">Консоль</span><span class="sxs-lookup"><span data-stu-id="47640-139">Console</span></span>

<span data-ttu-id="47640-140">Поставщик `Console` выводит выходные данные в консоль.</span><span class="sxs-lookup"><span data-stu-id="47640-140">The `Console` provider logs output to the console.</span></span>

### <a name="debug"></a><span data-ttu-id="47640-141">Отладка</span><span class="sxs-lookup"><span data-stu-id="47640-141">Debug</span></span>

<span data-ttu-id="47640-142">Поставщик `Debug` записывает выходные данные журнала с использованием класса [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug).</span><span class="sxs-lookup"><span data-stu-id="47640-142">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="47640-143">При вызове методов `System.Diagnostics.Debug.WriteLine` выполняется запись в поставщик `Debug`.</span><span class="sxs-lookup"><span data-stu-id="47640-143">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="47640-144">В Linux расположение журнала поставщика `Debug` зависит от дистрибутива и может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="47640-144">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="47640-145">*/var/log/message*</span><span class="sxs-lookup"><span data-stu-id="47640-145">*/var/log/message*</span></span>
- <span data-ttu-id="47640-146">*/var/log/syslog*</span><span class="sxs-lookup"><span data-stu-id="47640-146">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="47640-147">Источник события</span><span class="sxs-lookup"><span data-stu-id="47640-147">Event Source</span></span>

<span data-ttu-id="47640-148">Поставщик `EventSource` выполняет запись в кроссплатформенный источник событий с именем `Microsoft-Extensions-Logging`.</span><span class="sxs-lookup"><span data-stu-id="47640-148">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="47640-149">В Windows поставщик использует [ETW](/windows/win32/etw/event-tracing-portal).</span><span class="sxs-lookup"><span data-stu-id="47640-149">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="47640-150">Средства трассировки dotnet</span><span class="sxs-lookup"><span data-stu-id="47640-150">dotnet trace tooling</span></span>

<span data-ttu-id="47640-151">Средство [dotnet-trace](../diagnostics/dotnet-trace.md) — это универсальное кроссплатформенное средство командной строки, которое выполняет сбор трассировок .NET Core для запущенного процесса.</span><span class="sxs-lookup"><span data-stu-id="47640-151">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="47640-152">Средство собирает данные поставщика <xref:Microsoft.Extensions.Logging.EventSource> с помощью <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span><span class="sxs-lookup"><span data-stu-id="47640-152">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="47640-153">Инструкции по установке см. в статье [dotnet-trace](../diagnostics/dotnet-trace.md).</span><span class="sxs-lookup"><span data-stu-id="47640-153">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="47640-154">Руководство по диагностике с использованием `dotnet-trace` см. в разделе [Отладка высокой загрузки ЦП в .NET Core](../diagnostics/debug-highcpu.md).</span><span class="sxs-lookup"><span data-stu-id="47640-154">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="47640-155">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="47640-155">Windows EventLog</span></span>

<span data-ttu-id="47640-156">Поставщик `EventLog` отправляет выходные данные журнала в журнал событий Windows.</span><span class="sxs-lookup"><span data-stu-id="47640-156">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="47640-157">В отличие от других поставщиков, поставщик `EventLog` ***не наследует*** параметры по умолчанию, не относящиеся к поставщику.</span><span class="sxs-lookup"><span data-stu-id="47640-157">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="47640-158">Если параметры журнала `EventLog` не указаны, то принимается значение по умолчанию `LogLevel.Warning`.</span><span class="sxs-lookup"><span data-stu-id="47640-158">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="47640-159">Чтобы регистрировать события с уровнем ниже <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, следует явно задать уровень ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="47640-159">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="47640-160">В следующем примере для журнала событий по умолчанию задается уровень <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="47640-160">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="47640-161">[Перегрузки AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) позволяют передавать <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span><span class="sxs-lookup"><span data-stu-id="47640-161">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="47640-162">Если `null` или не указан, используются следующие параметры по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="47640-162">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="47640-163">`LogName`. "Application"</span><span class="sxs-lookup"><span data-stu-id="47640-163">`LogName`: "Application"</span></span>
- <span data-ttu-id="47640-164">`SourceName`: ".NET Runtime"</span><span class="sxs-lookup"><span data-stu-id="47640-164">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="47640-165">`MachineName`. Используется имя локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="47640-165">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="47640-166">Следующий код изменяет `SourceName` со значения по умолчанию `".NET Runtime"` на `CustomLogs`:</span><span class="sxs-lookup"><span data-stu-id="47640-166">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="47640-167">Служба приложений Azure</span><span class="sxs-lookup"><span data-stu-id="47640-167">Azure App Service</span></span>

<span data-ttu-id="47640-168">Пакет поставщика [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) записывает журналы в текстовые файлы в файловой системе приложения службы приложений Azure и в [хранилище больших двоичных объектов](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) в учетной записи хранения Azure.</span><span class="sxs-lookup"><span data-stu-id="47640-168">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="47640-169">Пакет поставщика не входит в библиотеки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="47640-169">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="47640-170">Чтобы использовать поставщик, добавьте пакет поставщика в проект.</span><span class="sxs-lookup"><span data-stu-id="47640-170">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="47640-171">Для настройки параметров поставщика используйте <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> и <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="47640-171">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using IHost host = CreateHostBuilder(args).Build();

        // Application code should start here.

        await host.RunAsync();
    }

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="47640-172">При развертывании в службе приложений Azure ваше приложение использует параметры в разделе [Журналы службы приложений](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) на странице **Служба приложений** на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="47640-172">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="47640-173">При обновлении следующих параметров изменения вступают в силу немедленно без перезапуска или повторного развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="47640-173">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="47640-174">**Ведение журнала приложения (файловая система)** ;</span><span class="sxs-lookup"><span data-stu-id="47640-174">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="47640-175">**Ведение журнала приложения (BLOB-объект)** .</span><span class="sxs-lookup"><span data-stu-id="47640-175">**Application Logging (Blob)**</span></span>

<span data-ttu-id="47640-176">По умолчанию файлы журнала находятся в папке *D:\\home\\LogFiles\\Application*, а имя файла по умолчанию — *diagnostics-yyyymmdd.txt*.</span><span class="sxs-lookup"><span data-stu-id="47640-176">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="47640-177">Максимальный размер файла по умолчанию составляет 10 МБ, а максимальное количество сохраняемых по умолчанию файлов равно 2.</span><span class="sxs-lookup"><span data-stu-id="47640-177">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="47640-178">Имя BLOB-объекта по умолчанию — *{имя_приложения}{метка_времени}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span><span class="sxs-lookup"><span data-stu-id="47640-178">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="47640-179">Этот поставщик работает только при выполнении проекта в среде Azure.</span><span class="sxs-lookup"><span data-stu-id="47640-179">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="47640-180">Потоковая передача журналов Azure</span><span class="sxs-lookup"><span data-stu-id="47640-180">Azure log streaming</span></span>

<span data-ttu-id="47640-181">Потоковая передача журналов Azure позволяет просматривать активность журнала в реальном времени из следующих источников:</span><span class="sxs-lookup"><span data-stu-id="47640-181">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="47640-182">сервер приложений;</span><span class="sxs-lookup"><span data-stu-id="47640-182">The app server</span></span>
- <span data-ttu-id="47640-183">веб-сервер;</span><span class="sxs-lookup"><span data-stu-id="47640-183">The web server</span></span>
- <span data-ttu-id="47640-184">трассировка неудачно завершенных запросов.</span><span class="sxs-lookup"><span data-stu-id="47640-184">Failed request tracing</span></span>

<span data-ttu-id="47640-185">Настройка потоковой передачи журналов Azure</span><span class="sxs-lookup"><span data-stu-id="47640-185">To configure Azure log streaming:</span></span>

- <span data-ttu-id="47640-186">Со страницы портала приложения перейдите на страницу **Журналы службы приложений**.</span><span class="sxs-lookup"><span data-stu-id="47640-186">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="47640-187">**Включите** параметр **Ведение журнала приложения (файловая система)** .</span><span class="sxs-lookup"><span data-stu-id="47640-187">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="47640-188">Выберите **уровень** ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="47640-188">Choose the log **Level**.</span></span> <span data-ttu-id="47640-189">Этот параметр применяется только к потоковой передаче журналов Azure.</span><span class="sxs-lookup"><span data-stu-id="47640-189">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="47640-190">Перейдите на страницу **Поток журналов**, чтобы просмотреть журналы.</span><span class="sxs-lookup"><span data-stu-id="47640-190">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="47640-191">Сообщения записываются в журнал с помощью интерфейса `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="47640-191">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="47640-192">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="47640-192">Azure Application Insights</span></span>

<span data-ttu-id="47640-193">Пакет поставщика [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) записывает журналы в [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span><span class="sxs-lookup"><span data-stu-id="47640-193">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="47640-194">Служба Application Insights отслеживает веб-приложения и предоставляет средства для создания запросов и анализа данных телеметрии.</span><span class="sxs-lookup"><span data-stu-id="47640-194">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="47640-195">Используя этого поставщика, вы сможете выполнять запросы к журналам и их анализ с помощью средств Application Insights.</span><span class="sxs-lookup"><span data-stu-id="47640-195">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="47640-196">Дополнительные сведения см. в следующих ресурсах:</span><span class="sxs-lookup"><span data-stu-id="47640-196">For more information, see the following resources:</span></span>

- [<span data-ttu-id="47640-197">Общие сведения об Application Insights</span><span class="sxs-lookup"><span data-stu-id="47640-197">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="47640-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) (Поставщик ведения журналов Application Insights для журналов .NET Core ILogger) — начните изучение с этой статьи, если вы хотите внедрить поставщика ведения журналов, не используя остальные возможности Application Insights для телеметрии.</span><span class="sxs-lookup"><span data-stu-id="47640-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="47640-199">[Адаптеры ведения журналов в Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).</span><span class="sxs-lookup"><span data-stu-id="47640-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="47640-200">[Инструментирование серверного кода веб-приложения с помощью Application Insights](/learn/modules/instrument-web-app-code-with-application-insights) — интерактивный учебник на сайте Microsoft Learn.</span><span class="sxs-lookup"><span data-stu-id="47640-200">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="47640-201">Сторонние поставщики ведения журналов</span><span class="sxs-lookup"><span data-stu-id="47640-201">Third-party logging providers</span></span>

<span data-ttu-id="47640-202">Ниже приведены некоторые сторонние платформы ведения журналов, которые работают с различными рабочими нагрузками .NET:</span><span class="sxs-lookup"><span data-stu-id="47640-202">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="47640-203">[ELMAH.IO](https://elmah.io) ([в репозитории GitHub](https://github.com/elmahio/Elmah.Io.Extensions.Logging));</span><span class="sxs-lookup"><span data-stu-id="47640-203">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="47640-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([в репозитории GitHub](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="47640-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="47640-205">[JSNLog](http://jsnlog.com) ([в репозитории GitHub](https://github.com/mperdeck/jsnlog));</span><span class="sxs-lookup"><span data-stu-id="47640-205">[JSNLog](http://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="47640-206">[KissLog.net](https://kisslog.net) ([репозиторий GitHub](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="47640-206">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="47640-207">[Log4Net](https://logging.apache.org/log4net) ([репозиторий GitHub](https://github.com/apache/logging-log4net))</span><span class="sxs-lookup"><span data-stu-id="47640-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="47640-208">[Loggr](https://loggr.net) ([в репозитории GitHub](https://github.com/imobile3/Loggr.Extensions.Logging));</span><span class="sxs-lookup"><span data-stu-id="47640-208">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="47640-209">[NLog](https://nlog-project.org) ([в репозитории GitHub](https://github.com/NLog/NLog.Extensions.Logging));</span><span class="sxs-lookup"><span data-stu-id="47640-209">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="47640-210">[NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([в репозитории GitHub](https://github.com/nreco/logging))</span><span class="sxs-lookup"><span data-stu-id="47640-210">[NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([GitHub repo](https://github.com/nreco/logging))</span></span>
- <span data-ttu-id="47640-211">[Sentry](https://sentry.io/welcome) ([репозиторий GitHub](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="47640-211">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="47640-212">[Serilog](https://serilog.net) ([в репозитории GitHub](https://github.com/serilog/serilog-sinks-console)).</span><span class="sxs-lookup"><span data-stu-id="47640-212">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="47640-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([репозиторий GitHub](https://github.com/googleapis/google-cloud-dotnet))</span><span class="sxs-lookup"><span data-stu-id="47640-213">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="47640-214">Некоторые сторонние платформы выполняют [семантическое ведение журналов, также известное как структурированное ведение журналов](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span><span class="sxs-lookup"><span data-stu-id="47640-214">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="47640-215">Использование сторонней платформы аналогично использованию одного из встроенных поставщиков:</span><span class="sxs-lookup"><span data-stu-id="47640-215">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="47640-216">Добавьте пакет NuGet в проект.</span><span class="sxs-lookup"><span data-stu-id="47640-216">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="47640-217">Вызовите метод расширения `ILoggerFactory` или `ILoggingBuilder`, предоставляемый платформой ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="47640-217">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="47640-218">Дополнительные сведения см. в документации по каждому поставщику.</span><span class="sxs-lookup"><span data-stu-id="47640-218">For more information, see each provider's documentation.</span></span> <span data-ttu-id="47640-219">Сторонние поставщики ведения журналов не поддерживаются корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="47640-219">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="47640-220">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="47640-220">See also</span></span>

- <span data-ttu-id="47640-221">[Ведение журнала в .NET](logging.md).</span><span class="sxs-lookup"><span data-stu-id="47640-221">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="47640-222">[Реализация пользовательского поставщика ведения журнала в .NET](custom-logging-provider.md).</span><span class="sxs-lookup"><span data-stu-id="47640-222">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="47640-223">[Ведение журнала с высокой производительностью в .NET](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="47640-223">[High-performance logging in .NET](high-performance-logging.md).</span></span>
