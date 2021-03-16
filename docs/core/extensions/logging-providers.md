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
# <a name="logging-providers-in-net"></a>Поставщики ведения журнала в NET

Поставщики ведения журналов сохраняют журналы, за исключением поставщика `Console`, в котором журналы отображаются только в стандартном выводе. Например, поставщик Azure Application Insights хранит журналы в Azure Application Insights. Вы можете включить несколько поставщиков.

Шаблоны приложений .NET Worker по умолчанию:

- используют [универсальный узел](generic-host.md);
- вызывают метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, который добавляет следующие поставщики ведения журнала:
  - [Консоль](#console)
  - [Отладка](#debug)
  - [EventSource](#event-source)
  - [EventLog](#windows-eventlog): Только для Windows

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

В предыдущем коде показан класс `Program`, созданный с использованием шаблонов приложений .NET Worker. В следующих разделах приводятся примеры, которые построены на основе шаблонов приложений .NET Worker и используют универсальный узел.

Чтобы переопределить заданный по умолчанию набор поставщиков ведения журнала, добавленных с помощью `Host.CreateDefaultBuilder`, вызовите метод `ClearProviders` и добавьте необходимых поставщиков. Например, приведенный ниже код

- вызывает метод <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> для удаления всех экземпляров <xref:Microsoft.Extensions.Logging.ILoggerProvider> из построителя;
- добавляет поставщик ведения журнала [Console](#console).

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

Сведения о других поставщиках см. в следующих статьях:

- [Встроенные поставщики ведения журнала](#built-in-logging-providers).
- [Сторонние поставщики ведения журнала](#third-party-logging-providers).

## <a name="configure-a-service-that-depends-on-ilogger"></a>Настройка службы, зависящей от ILogger

Чтобы настроить службу, зависящую от `ILogger<T>`, используйте внедрение конструктора или предоставьте фабричный метод. Фабричный метод рекомендуется использовать, только если нет других вариантов. Например, рассмотрим службу, которой требуется экземпляр `ILogger<T>`, предоставляемый путем внедрения зависимостей:

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

Приведенный выше код — это функция [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2), которая выполняется, когда контейнеру внедрения зависимостей впервые требуется создать экземпляр `IExampleService`. Таким образом можно обращаться к любым зарегистрированным службам.

## <a name="built-in-logging-providers"></a>Встроенные поставщики ведения журналов

Расширения Майкрософт включают в себя следующих поставщиков ведения журналов в составе библиотек среды выполнения:

- [Консоль](#console)
- [Отладка](#debug)
- [EventSource](#event-source)
- [EventLog](#windows-eventlog)

Следующие поставщики ведения журналов поставляются корпорацией Майкрософт, но не в составе библиотек среды выполнения. Их необходимо устанавливать в виде дополнительных пакетов NuGet.

- [AzureAppServicesFile и AzureAppServicesBlob](#azure-app-service)
- [ApplicationInsights](#azure-application-insights)

### <a name="console"></a>Консоль

Поставщик `Console` выводит выходные данные в консоль.

### <a name="debug"></a>Отладка

Поставщик `Debug` записывает выходные данные журнала с использованием класса [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug). При вызове методов `System.Diagnostics.Debug.WriteLine` выполняется запись в поставщик `Debug`.

В Linux расположение журнала поставщика `Debug` зависит от дистрибутива и может быть одним из следующих:

- */var/log/message*
- */var/log/syslog*

### <a name="event-source"></a>Источник события

Поставщик `EventSource` выполняет запись в кроссплатформенный источник событий с именем `Microsoft-Extensions-Logging`. В Windows поставщик использует [ETW](/windows/win32/etw/event-tracing-portal).

#### <a name="dotnet-trace-tooling"></a>Средства трассировки dotnet

Средство [dotnet-trace](../diagnostics/dotnet-trace.md) — это универсальное кроссплатформенное средство командной строки, которое выполняет сбор трассировок .NET Core для запущенного процесса. Средство собирает данные поставщика <xref:Microsoft.Extensions.Logging.EventSource> с помощью <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.

Инструкции по установке см. в статье [dotnet-trace](../diagnostics/dotnet-trace.md). Руководство по диагностике с использованием `dotnet-trace` см. в разделе [Отладка высокой загрузки ЦП в .NET Core](../diagnostics/debug-highcpu.md).

### <a name="windows-eventlog"></a>Windows EventLog

Поставщик `EventLog` отправляет выходные данные журнала в журнал событий Windows. В отличие от других поставщиков, поставщик `EventLog` ***не наследует*** параметры по умолчанию, не относящиеся к поставщику. Если параметры журнала `EventLog` не указаны, то принимается значение по умолчанию `LogLevel.Warning`.

Чтобы регистрировать события с уровнем ниже <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, следует явно задать уровень ведения журнала. В следующем примере для журнала событий по умолчанию задается уровень <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

[Перегрузки AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) позволяют передавать <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>. Если `null` или не указан, используются следующие параметры по умолчанию:

- `LogName`. "Application"
- `SourceName`: ".NET Runtime"
- `MachineName`. Используется имя локального компьютера.

Следующий код изменяет `SourceName` со значения по умолчанию `".NET Runtime"` на `CustomLogs`:

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

### <a name="azure-app-service"></a>Служба приложений Azure

Пакет поставщика [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) записывает журналы в текстовые файлы в файловой системе приложения службы приложений Azure и в [хранилище больших двоичных объектов](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) в учетной записи хранения Azure.

Пакет поставщика не входит в библиотеки среды выполнения. Чтобы использовать поставщик, добавьте пакет поставщика в проект.

Для настройки параметров поставщика используйте <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> и <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, как показано в следующем примере:

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

При развертывании в службе приложений Azure ваше приложение использует параметры в разделе [Журналы службы приложений](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) на странице **Служба приложений** на портале Azure. При обновлении следующих параметров изменения вступают в силу немедленно без перезапуска или повторного развертывания приложения:

- **Ведение журнала приложения (файловая система)** ;
- **Ведение журнала приложения (BLOB-объект)** .

По умолчанию файлы журнала находятся в папке *D:\\home\\LogFiles\\Application*, а имя файла по умолчанию — *diagnostics-yyyymmdd.txt*. Максимальный размер файла по умолчанию составляет 10 МБ, а максимальное количество сохраняемых по умолчанию файлов равно 2. Имя BLOB-объекта по умолчанию — *{имя_приложения}{метка_времени}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.

Этот поставщик работает только при выполнении проекта в среде Azure.

#### <a name="azure-log-streaming"></a>Потоковая передача журналов Azure

Потоковая передача журналов Azure позволяет просматривать активность журнала в реальном времени из следующих источников:

- сервер приложений;
- веб-сервер;
- трассировка неудачно завершенных запросов.

Настройка потоковой передачи журналов Azure

- Со страницы портала приложения перейдите на страницу **Журналы службы приложений**.
- **Включите** параметр **Ведение журнала приложения (файловая система)** .
- Выберите **уровень** ведения журнала. Этот параметр применяется только к потоковой передаче журналов Azure.

Перейдите на страницу **Поток журналов**, чтобы просмотреть журналы. Сообщения записываются в журнал с помощью интерфейса `ILogger`.

### <a name="azure-application-insights"></a>Azure Application Insights

Пакет поставщика [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) записывает журналы в [Azure Application Insights](/azure/azure-monitor/app/cloudservices). Служба Application Insights отслеживает веб-приложения и предоставляет средства для создания запросов и анализа данных телеметрии. Используя этого поставщика, вы сможете выполнять запросы к журналам и их анализ с помощью средств Application Insights.

Дополнительные сведения см. в следующих ресурсах:

- [Общие сведения об Application Insights](/azure/application-insights/app-insights-overview)
- [ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) (Поставщик ведения журналов Application Insights для журналов .NET Core ILogger) — начните изучение с этой статьи, если вы хотите внедрить поставщика ведения журналов, не используя остальные возможности Application Insights для телеметрии.
- [Адаптеры ведения журналов в Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).
- [Инструментирование серверного кода веб-приложения с помощью Application Insights](/learn/modules/instrument-web-app-code-with-application-insights) — интерактивный учебник на сайте Microsoft Learn.

## <a name="third-party-logging-providers"></a>Сторонние поставщики ведения журналов

Ниже приведены некоторые сторонние платформы ведения журналов, которые работают с различными рабочими нагрузками .NET:

- [ELMAH.IO](https://elmah.io) ([в репозитории GitHub](https://github.com/elmahio/Elmah.Io.Extensions.Logging));
- [Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([в репозитории GitHub](https://github.com/mattwcole/gelf-extensions-logging))
- [JSNLog](http://jsnlog.com) ([в репозитории GitHub](https://github.com/mperdeck/jsnlog));
- [KissLog.net](https://kisslog.net) ([репозиторий GitHub](https://github.com/catalingavan/KissLog-net))
- [Log4Net](https://logging.apache.org/log4net) ([репозиторий GitHub](https://github.com/apache/logging-log4net))
- [Loggr](https://loggr.net) ([в репозитории GitHub](https://github.com/imobile3/Loggr.Extensions.Logging));
- [NLog](https://nlog-project.org) ([в репозитории GitHub](https://github.com/NLog/NLog.Extensions.Logging));
- [NReco.Logging](https://github.com/nreco/logging/blob/master/README.md) ([в репозитории GitHub](https://github.com/nreco/logging))
- [Sentry](https://sentry.io/welcome) ([репозиторий GitHub](https://github.com/getsentry/sentry-dotnet))
- [Serilog](https://serilog.net) ([в репозитории GitHub](https://github.com/serilog/serilog-sinks-console)).
- [Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([репозиторий GitHub](https://github.com/googleapis/google-cloud-dotnet))

Некоторые сторонние платформы выполняют [семантическое ведение журналов, также известное как структурированное ведение журналов](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).

Использование сторонней платформы аналогично использованию одного из встроенных поставщиков:

1. Добавьте пакет NuGet в проект.
1. Вызовите метод расширения `ILoggerFactory` или `ILoggingBuilder`, предоставляемый платформой ведения журналов.

Дополнительные сведения см. в документации по каждому поставщику. Сторонние поставщики ведения журналов не поддерживаются корпорацией Майкрософт.

## <a name="see-also"></a>См. также раздел

- [Ведение журнала в .NET](logging.md).
- [Реализация пользовательского поставщика ведения журнала в .NET](custom-logging-provider.md).
- [Ведение журнала с высокой производительностью в .NET](high-performance-logging.md).
