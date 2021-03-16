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
# <a name="dependency-injection-in-net"></a>Внедрение зависимостей в .NET

.NET поддерживает проектирование программного обеспечения с возможностью внедрения зависимостей. При таком подходе достигается [инверсия управления](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) между классами и их зависимостями. Внедрение зависимостей — своего рода [почетный гражданин](https://en.wikipedia.org/wiki/First-class_citizen) .NET наряду с конфигурацией, ведением журнала и шаблоном параметров.

*Зависимость* — это любой объект, от которого зависит другой объект. Рассмотрим следующий класс `MessageWriter` с методом `Write`, от которого зависят другие классы:

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

Класс может создать экземпляр класса `MessageWriter`, чтобы использовать его метод `Write`. В следующем примере класс `MessageWriter` выступает зависимостью класса `Worker`:

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

Этот класс создает `MessageWriter` и напрямую зависит от этого класса. Включенные в код зависимости, как в предыдущем примере, представляют собой определенную проблему. Их следует избегать по следующим причинам:

- Чтобы заменить `MessageWriter` другой реализацией, класс `Worker` необходимо изменить.
- Если у `MessageWriter` есть зависимости, их конфигурацию должен выполнять класс `Worker`. В больших проектах, когда от `MessageWriter` зависят многие классы, код конфигурации растягивается по всему приложению.
- Такая реализация плохо подходит для модульных тестов. В приложении нужно использовать имитацию или заглушку в виде класса `MessageWriter`, что при таком подходе невозможно.

Внедрение зависимостей устраняет эти проблемы следующим образом:

- Используется интерфейс или базовый класс для абстрагирования реализации зависимостей.
- Зависимость регистрируется в контейнере служб. .NET предоставляет встроенный контейнер служб <xref:System.IServiceProvider>. Службы обычно регистрируются при запуске приложения и добавляются в <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>. После добавления всех служб выполните <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> для создания контейнера службы.
- Служба *внедряется* в конструктор класса там, где он используется. Платформа берет на себя создание экземпляра зависимости и его удаление, когда он больше не нужен.

В качестве примера рассмотрим интерфейс `IMessageWriter`, который определяет метод `Write`:

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

Этот интерфейс реализуется конкретным типом, `MessageWriter`.

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

Этот пример кода регистрирует службу `IMessageWriter` с конкретным типом `MessageWriter`. Метод <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> регистрирует службу с заданной областью времени существования, временем существования одного запроса. Подробнее о [времени существования служб](#service-lifetimes) мы поговорим далее в этой статье.

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

В примере приложения запрашивается служба `IMessageWriter`, которая затем используется для вызова метода `Write`:

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

При использовании шаблона внедрения зависимостей рабочая служба имеет следующие характеристики:

- Не использует конкретный тип `MessageWriter`, а только интерфейс `IMessageWriter`, который его реализует. Это упрощает изменение реализации, используемой контроллером, без изменения контроллера.
- не создает экземпляр `MessageWriter`, он создается контейнером внедрения зависимостей.

Реализацию интерфейса `IMessageWriter` можно улучшить с помощью встроенного API ведения журнала:

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

Обновленный метод `ConfigureServices` регистрирует новую реализацию `IMessageWriter`:

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

`LoggingMessageWriter` зависит от <xref:Microsoft.Extensions.Logging.ILogger%601>, который запрашивается в конструкторе. `ILogger<TCategoryName>` — это [предоставленная платформой служба](#framework-provided-services).

Использование цепочки внедрений зависимостей не является чем-то необычным. Каждая запрашиваемая зависимость запрашивает собственные зависимости. Контейнер разрешает зависимости в графе и возвращает полностью разрешенную службу. Весь набор зависимостей, которые нужно разрешить, обычно называют *деревом зависимостей*, *графом зависимостей* или *графом объектов*.

Контейнер разрешает `ILogger<TCategoryName>`, используя преимущества [(универсальных) открытых типов](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), что устраняет необходимость регистрации каждого [(универсального) сконструированного типа](/dotnet/csharp/language-reference/language-specification/types#constructed-types).

В терминологии внедрения зависимостей — служба:

- Обычно является объектом, предоставляющим службу для других объектов, например службу `IMessageWriter`.
- Не относится к веб-службе, хотя служба может использовать веб-службу.

Платформа предоставляет эффективную систему ведения журнала. Реализации `IMessageWriter`, приведенные в предыдущем примере были написаны для демонстрации базового внедрения зависимостей, а не для реализации ведения журнала. Большинству приложений не нужно писать средства ведения журнала. В следующем коде демонстрируется использование механизма ведения журнала по умолчанию, для которого требуется только регистрация `Worker` в `ConfigureServices` в качестве размещенной службы <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>.

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

Используя приведенный выше код, не нужно обновлять `ConfigureServices`, поскольку платформа предоставляет возможность ведения журнала.

## <a name="register-groups-of-services-with-extension-methods"></a>Регистрация групп служб с помощью методов расширения

Расширения Microsoft используют конвенцию для регистрации группы связанных служб. Соглашение заключается в использовании одного метода расширения `Add{GROUP_NAME}` для регистрации всех служб, необходимых компоненту платформы. Например, метод расширения <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> регистрирует все службы, необходимые для работы с параметрами.

## <a name="framework-provided-services"></a>Платформенные службы

Метод `ConfigureServices` регистрирует используемые приложением службы, включая функции платформы. Изначально коллекция `IServiceCollection`, предоставленная для `ConfigureServices`, содержит определенные платформой службы (в зависимости от [настройки узла](generic-host.md#host-configuration)). Для приложений, основанных на шаблонах .NET, платформа регистрирует несколько сотен служб.

В следующей таблице перечислены некоторые примеры этих зарегистрированных платформой служб.

| Тип службы                                                                       | Время существования  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | Одноэлементный |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | Одноэлементный |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | Одноэлементный |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | Одноэлементный |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | Временный |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | Одноэлементный |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | Одноэлементный |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | Одноэлементный |

## <a name="service-lifetimes"></a>Время существования служб

Службы можно зарегистрировать с одним из следующих вариантов времени существования:

- Временный
- Область действия
- Одноэлементный

Они описываются в следующих разделах. Для каждой зарегистрированной службы выбирайте подходящее время существования.

### <a name="transient"></a>Временный

Временные службы времени существования создаются при каждом их запросе из контейнера служб. Это время существования лучше всего подходит для простых служб без отслеживания состояния. Регистрируйте временные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A>.

В приложениях, обрабатывающих запросы, временные службы удаляются в конце запроса.

### <a name="scoped"></a>Область действия

Для веб-приложений время существования, привязанное к области, означает, что службы создаются один раз для каждого запроса (подключения) клиента. Регистрируйте службы с заданной областью с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A>.

В приложениях, обрабатывающих запросы, службы с заданной областью удаляются в конце запроса.

При использовании Entity Framework Core метод расширения <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> по умолчанию регистрирует типы `DbContext` с заданной областью времени существования.

> [!NOTE]
> Разрешать службу с заданной областью из одноэлементного объекта ***запрещено** _, и будьте внимательны, чтобы не сделать это неявно, например, через временную службу. При обработке последующих запросов это может вызвать неправильное состояние службы. Допускается следующее:
>
> - Разрешение одноэлементной службы из службы с заданной областью или временной службы.
> - Разрешение службы с заданной областью из другой службы с заданной областью или временной службы.

По умолчанию в среде разработки разрешение службы из другой службы с более длинным временем существования вызывает исключение. Дополнительные сведения см. в разделе [Проверка области](#scope-validation).

### <a name="singleton"></a>Одноэлементный

Одноэлементные службы времени существования создаются в следующих случаях.

- При первом запросе.
- Разработчиком при предоставлении экземпляра реализации непосредственно в контейнер. Этот подход требуется достаточно редко.

Каждый последующий запрос на реализацию службы из контейнера внедрения зависимостей использует тот же экземпляр. Если в приложении нужно использовать одноэлементные службы, разрешите контейнеру служб управлять временем их существования. Не реализуйте одноэлементный подход и предоставьте код для удаления одноэлементных объектов. Службы никогда не должны удаляться кодом, который разрешил службу из контейнера. Если тип или фабрика зарегистрированы как одноэлементный объект, контейнер автоматически удалит одноэлементные объекты.

Зарегистрируйте одноэлементные службы с помощью <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A>. Одноэлементные службы должны быть потокобезопасными и часто использоваться в службах без отслеживания состояния.

В приложениях, обрабатывающих запросы, отдельные службы удаляются, когда <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> удаляется по завершении работы приложения. Поскольку память не освобождается до завершения работы приложения, рекомендуется учитывать использование памяти одноэлементным объектом.

> [!WARNING]
> Разрешать службу с заданной областью из отдельного объекта _*_нельзя_*_. При обработке последующих запросов это может вызвать неправильное состояние службы. Допускается разрешать одноэлементную службу из службы с заданной областью или временной службы.

## <a name="service-registration-methods"></a>Методы регистрации службы

Платформа предоставляет методы расширения регистрации службы, которые полезны в определенных сценариях.

| Метод | Автоматически<br>object<br>удаление | Несколько<br>реализации | Передача аргументов |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br>Пример<br><br>`services.AddSingleton<IMyDep, MyDep>();` | Да | Да | Нет |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br>Примеры:<br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | Да | Да | Да |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br>Пример<br><br>`services.AddSingleton<MyDep>();` | Да | Нет | Нет |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br>Примеры:<br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | Нет | Да | Да |
| `AddSingleton(new {IMPLEMENTATION})`<br><br>Примеры:<br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | Нет | Нет | Да |

Дополнительные сведения об удалении типа см. в разделе [Удаление служб](dependency-injection-guidelines.md#disposal-of-services).

Регистрация службы только с типом реализации эквивалентна регистрации этой службы с той же реализацией и типом службы. Именно поэтому несколько реализаций службы не могут быть зарегистрированы с помощью методов, которые не принимают явный тип службы. Эти методы могут регистрировать несколько _экземпляров* службы, но все они будут иметь одинаковую *реализацию* типа.

Любой из указанных выше методов регистрации службы можно использовать для регистрации нескольких экземпляров службы одного типа службы. В следующем примере метод `AddSingleton` вызывается дважды с типом службы `IMessageWriter`. Второй вызов `AddSingleton` переопределяет предыдущий, если он разрешается как `IMessageWriter`, и добавляет к предыдущему, если несколько служб разрешаются через `IEnumerable<IMessageWriter>`. Службы отображаются в том порядке, в котором они были зарегистрированы при разрешении через `IEnumerable<{SERVICE}>`.

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

Предыдущий пример исходного кода регистрирует две реализации `IMessageWriter`.

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

Компонент `ExampleService` определяет два параметра конструктора: одиночный `IMessageWriter` и `IEnumerable<IMessageWriter>`. Одиночный `IMessageWriter` здесь является последней зарегистрированной реализацией, а `IEnumerable<IMessageWriter>` представляет все зарегистрированные реализации.

Платформа также предоставляет методы расширения `TryAdd{LIFETIME}`, которые регистрируют службу только в том случае, если реализация еще не зарегистрирована.

В следующем примере вызов `AddSingleton` регистрирует `ConsoleMessageWriter` как реализацию для `IMessageWriter`. Вызов `TryAddSingleton` ничего не делает, поскольку у `IMessageWriter` уже есть зарегистрированная реализация:

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

Параметр `TryAddSingleton` не применяется, так как он уже был добавлен, поэтому выполнение "try" завершится ошибкой. В `ExampleService` будут следующие утверждения:

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

Дополнительные сведения см. в разделе:

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

Методы [TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) регистрируют службу только в том случае, если еще не существует реализации *того же типа*. Несколько служб разрешается через `IEnumerable<{SERVICE}>`. При регистрации служб добавляйте экземпляр в том случае, если экземпляр такого типа еще не был добавлен. Авторы библиотек используют `TryAddEnumerable`, чтобы избежать регистрации нескольких копий реализации в контейнере.

В следующем примере первый вызов `TryAddEnumerable` регистрирует `MessageWriter` как реализацию для `IMessageWriter1`. Второй вызов регистрирует `MessageWriter` для `IMessageWriter2`. Третий вызов ничего не делает, поскольку у `IMessageWriter1` уже есть зарегистрированная реализация `MessageWriter`:

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

Регистрация службы обычно не зависит от порядка, за исключением случаев регистрации нескольких реализаций одного типа.

`IServiceCollection` является коллекцией объектов <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor>. В следующем примере показано, как зарегистрировать службу, создав и добавив `ServiceDescriptor`:

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

Встроенные методы `Add{LIFETIME}` используют аналогичный подход. Например, см. [исходный код для AddScoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).

### <a name="constructor-injection-behavior"></a>Поведение внедрения через конструктор

Службы можно разрешать с помощью:

- <xref:System.IServiceProvider>
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:
  - Создает объекты, которые не зарегистрированы в контейнере.
  - Используется в сочетании с некоторыми возможностями платформы.

Конструкторы могут принимать аргументы, которые не предоставляются внедрением зависимостей, но эти аргументы должны назначать значения по умолчанию.

Когда разрешение служб выполняется через `IServiceProvider` или `ActivatorUtilities`, для внедрения через конструктор требуется *открытый* конструктор.

Когда разрешение служб выполняется через `ActivatorUtilities`, для внедрения с помощью конструктора требуется наличие только одного соответствующего конструктора. Перегрузки конструктора поддерживаются, но может существовать всего одна перегрузка, все аргументы которой могут быть обработаны с помощью внедрения зависимостей.

## <a name="scope-validation"></a>Проверка области

Когда приложение выполняется в среде `Development` и вызывает [CreateDefaultBuilder](generic-host.md#default-builder-settings) для создания узла, поставщик службы по умолчанию проверяет следующее:

- Службы с заданной областью не разрешаются из корневого поставщика службы.
- Службы с заданной областью не вводятся в одноэлементные объекты.

Корневой поставщик службы создается при вызове <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A>. Время существования корневого поставщика службы соответствует времени существования приложения — поставщик запускается с приложением и удаляется, когда приложение завершает работу.

Службы с заданной областью удаляются создавшим их контейнером. Если служба с заданной областью создается в корневом контейнере, время существования службы повышается до уровня одноэлементного объекта, поскольку она удаляется только корневым контейнером при завершении работы приложения. Проверка областей службы перехватывает эти ситуации при вызове `BuildServiceProvider`.

## <a name="see-also"></a>См. также раздел

- [Использование внедрения зависимостей в .NET](dependency-injection-usage.md)
- [Рекомендации по внедрению зависимостей](dependency-injection-guidelines.md)
- [Внедрение зависимостей в ASP.NET Core](/aspnet/core/fundamentals/dependency-injection)
- [Шаблоны конференций NDC для разработки приложений с внедрением зависимостей](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [Принцип явных зависимостей](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [Контейнеры с инверсией управления и шаблон внедрения зависимостей (Мартин Фаулер (Martin Fowler))](https://www.martinfowler.com/articles/injection.html)
- Запросы на исправление ошибок, связанных с внедрением зависимостей, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)
