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
# <a name="net-generic-host"></a>Универсальный узел .NET

Шаблоны рабочей службы создают универсальный узел .NET <xref:Microsoft.Extensions.Hosting.HostBuilder>. Этот универсальный узел можно использовать в сочетании с другими типами приложений .NET, такими как консольные приложения.

*Узел* — это объект, который инкапсулирует все ресурсы приложения, такие как:

- Внедрение зависимостей
- Ведение журнала
- Параметр Configuration
- Реализации `IHostedService`

После запуска узла он вызывает <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> в каждой реализации <xref:Microsoft.Extensions.Hosting.IHostedService>, зарегистрированной в коллекции размещенных служб контейнера службы. В приложении рабочей службы для всех реализаций `IHostedService`, которые содержат экземпляры <xref:Microsoft.Extensions.Hosting.BackgroundService>, вызываются соответствующие методы <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType>.

Основной причиной включения всех взаимозависимых ресурсов приложения в один объект является управление жизненным циклом: контроль запуска и корректного завершения работы приложения. Это достигается с помощью пакета NuGet [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting).

## <a name="set-up-a-host"></a>Создание узла

Узел обычно настраивается, собирается и выполняется кодом в классе `Program`. Метод `Main`:

- Вызывает метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> для создания и настройки объекта построителя.
- Вызывает метод <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> для создания экземпляра <xref:Microsoft.Extensions.Hosting.IHost>.
- Вызывает метод <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> или <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> для объекта узла.

Шаблоны рабочей службы .NET генерируют следующий код для создания универсального узла:

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

## <a name="default-builder-settings"></a>Параметры построителя по умолчанию

Метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>:

- В качестве корня содержимого задает путь, возвращенный методом <xref:System.IO.Directory.GetCurrentDirectory>.
- Загружает [конфигурацию узла](#host-configuration) из:
  - Переменные среды с префиксом `DOTNET_`.
  - аргументы командной строки.
- Загружает конфигурацию приложения из:
  - *appsettings.json*;
  - *appsettings.{Environment}.json*;
  - диспетчер секретов, когда приложение выполняется в среде `Development`;
  - Переменные среды.
  - аргументы командной строки.
- Добавляет следующие регистраторы:
  - Консоль
  - Отладка
  - EventSource
  - Журнал событий (только при запуске в Windows)
- Включает проверку области и [проверку зависимостей](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild), если используется среда `Development`.

Метод `ConfigureServices` позволяет добавлять службы в экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType>. Позже эти службы можно будет сделать доступными через внедрение зависимостей.

## <a name="framework-provided-services"></a>Платформенные службы

Следующие службы регистрируются автоматически.

- [IHostApplicationLifetime](#ihostapplicationlifetime)
- [IHostLifetime](#ihostlifetime)
- [IHostEnvironment](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a>IHostApplicationLifetime

Внедрите службу <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> в любой класс для выполнения задач после запуска и корректного завершения работы. Три свойства этого интерфейса представляют собой токены отмены, которые служат для регистрации методов обработчика событий запуска и завершения работы приложения. Этот интерфейс также включает метод <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication>.

Ниже приведен пример реализации `IHostedService`, которая регистрирует события `IHostApplicationLifetime`:

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

Шаблон рабочей службы можно изменить, чтобы добавить в него реализацию `ExampleHostedService`.

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

Приложение запишет следующий образец выходных данных:

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a>IHostLifetime

Реализация <xref:Microsoft.Extensions.Hosting.IHostLifetime> контролирует, когда узел запускается и останавливается. Используется последняя зарегистрированная реализация.

`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` — это реализация `IHostLifetime` по умолчанию. `ConsoleLifetime`:

- Прослушивает сигналы <kbd>CTRL</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT) или [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) и вызывает метод <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> для запуска процесса завершения работы.
- разблокирует расширения, такие как `RunAsync` и `WaitForShutdownAsync`.

## <a name="ihostenvironment"></a>IHostEnvironment

Внедряет службу <xref:Microsoft.Extensions.Hosting.IHostEnvironment> в класс, чтобы получить сведения о следующих параметрах.

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a>Конфигурация узла

Конфигурация узла используется для настройки свойств реализации [IHostEnvironment](#ihostenvironment).

Конфигурация узла доступна в [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) через метод <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>. При вызове метода `ConfigureAppConfiguration` в `configureDelegate` передаются `HostBuilderContext` и `IConfigurationBuilder`. Для `configureDelegate` используется определение `Action<HostBuilderContext, IConfigurationBuilder>`. Контекст построителя узла предоставляет свойство `.Configuration`, которое является экземпляром `IConfiguration`. Он представляет конфигурацию, созданную на основе узла, тогда как `IConfigurationBuilder` представляет собой объект построителя, используемый для настройки приложения.

> [!TIP]
> После вызова `ConfigureAppConfiguration` элемент `HostBuilderContext.Configuration` заменяется на [app config](#app-configuration).

Чтобы добавить конфигурацию узла, вызовите <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> в `IHostBuilder`. Метод `ConfigureHostConfiguration` может вызываться несколько раз с накоплением результатов. Узел использует значение, заданное последним для данного ключа.

В следующем примере создается конфигурация узла:

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a>Конфигурация приложения

Конфигурация приложения создается путем вызова метода <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> в `IHostBuilder`. Метод `ConfigureAppConfiguration` может вызываться несколько раз с накоплением результатов. Приложение использует значение, заданное последним для данного ключа.

Конфигурация, созданная с помощью `ConfigureAppConfiguration`, доступна в [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) для последующих операций и как служба через внедрение зависимостей. Конфигурация узла также добавляется к конфигурации приложения.

Дополнительные сведения см. в статье [Конфигурация в .NET](configuration.md).

## <a name="see-also"></a>См. также раздел

- [Конфигурация в .NET](configuration.md)
- [Веб-узел ASP.NET Core](/aspnet/core/fundamentals/host/web-host)
- Запросы на исправление ошибок, связанных с универсальным узлом, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)
