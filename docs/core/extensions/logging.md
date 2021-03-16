---
title: Ведение журнала в .NET
author: IEvangelist
description: Узнайте, как использовать платформу ведения журналов, предоставляемую пакетом NuGet Microsoft.Extensions.Logging.
ms.author: dapine
ms.date: 02/19/2021
ms.openlocfilehash: 834331b9e103138012bbe91586d0d5a7c08654ce
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102402168"
---
# <a name="logging-in-net"></a>Ведение журнала в .NET

.NET поддерживает API ведения журнала, который работает с разными встроенными и сторонними поставщиками. В этой статье описано, как использовать в коде API ведения журналов, работающего со встроенными поставщиками. Большинство примеров кода, приведенных в этой статье, применимы к любому приложению .NET, которое использует [универсальный узел](generic-host.md). Если вы используете приложения, которые не используют универсальный узел, см. статью [Консольное приложение без размещения](#non-host-console-app).

## <a name="create-logs"></a>Создание журналов

Чтобы создавать журналы, используйте объект <xref:Microsoft.Extensions.Logging.ILogger%601> из [внедрения зависимостей](dependency-injection.md).

В следующем примере происходит следующее:

- Создает средство ведения журнала `ILogger<Worker>`, которое использует *категорию* журналов с полным именем типа `Worker`. Категория ведения журналов представляет строку, которая связана с каждым журналом.
- Вызывает метод <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> для ведения журналов на уровне `Information`. *Уровень* ведения журналов определяет степень серьезности или важности записанного в журнал события.

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

[Уровни](#log-level) и [категории](#log-category) рассматриваются подробнее далее в этой статье.

## <a name="configure-logging"></a>Настройка журнала

Конфигурацию ведения журналов обычно предоставляет раздел `Logging` в файлах *appsettings*.`{Environment}` *.json*. Шаблоны рабочей службы .NET создают следующий файл *appsettings.Development.json*:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

В приведенном выше документе JSON:

- Указаны категории `"Default"`, `"Microsoft"`и `"Microsoft.Hosting.Lifetime"`.
- Категория `"Microsoft"` применяется ко всем категориям, начинающимся с `"Microsoft"`.
- Категория `"Microsoft"` задает ведение журналов на уровне `Warning` и более высоком.
- Категория `"Microsoft.Hosting.Lifetime"` является более детальной по сравнению с `"Microsoft"`, поэтому при выборе категории `"Microsoft.Hosting.Lifetime"` ведение журналов осуществляется на уровне "Информация" и более высоком.
- Поскольку конкретный поставщик журналов не указан, `LogLevel` применяется ко всем включенным поставщикам, за исключением [Windows EventLog](logging-providers.md#windows-eventlog).

Свойство `Logging` может иметь свойство <xref:Microsoft.Extensions.Logging.LogLevel> и свойства поставщика журналов. Свойство `LogLevel` указывает минимальный [уровень](#log-level) журнала для выбранных категорий. В приведенном выше коде JSON заданы уровни ведения журнала `Information` и `Warning`. `LogLevel` определяет степень серьезности журнала и задается в диапазоне от 0 до 6:

`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 и `None` = 6.

Если задан `LogLevel`, журналы будут вестись для сообщений с указанным и более высокими уровнями. В приведенном выше коде JSON задается ведение журналов для категории `Default` для сообщений с уровнем `Information` и более высоким. Например, в журнал записываются сообщения с уровнями `Information`, `Warning`, `Error` и `Critical`. Если `LogLevel` не задан, по умолчанию устанавливается уровень ведения журналов `Information`. Дополнительные сведения см. в статье [Уровни ведения журналов](#log-level).

Свойство поставщика может задавать свойство `LogLevel`. Свойство `LogLevel` поставщика определяет уровень ведения журналов для этого поставщика и переопределяет любые другие не относящиеся к поставщику параметры ведения журналов. Рассмотрите следующий файл *appsettings.json*:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

Параметры в `Logging.{ProviderName}.LogLevel` переопределяют параметры в `Logging.LogLevel`. В приведенном выше коде JSON для поставщика `Debug` задается уровень ведения журнала по умолчанию `Information`:

`Logging:Debug:LogLevel:Default:Information`

Приведенный выше параметр задает уровень ведения журнала `Information` для всех категорий `Logging:Debug:`, за исключением `Microsoft.Hosting`. Если задана конкретная категория, она переопределяет категорию по умолчанию. В приведенном выше коде JSON категории `Logging:Debug:LogLevel` `"Microsoft.Hosting"` и `"Default"` переопределяют параметры в `Logging:LogLevel`.

Минимальный уровень ведения журнала можно указать для:

- конкретных поставщиков.  Например: `Logging:EventSource:LogLevel:Default:Information`
- конкретных категорий. Например: `Logging:LogLevel:Microsoft:Warning`
- всех поставщиков и всех категорий: `Logging:LogLevel:Default:Warning`

***Любые*** журналы с уровнем ниже минимального:

- не передаются поставщику;
- не записываются в журнал и не отображаются.

Чтобы отключить все журналы, укажите [LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel). `LogLevel.None` имеет значение 6, то есть выше `LogLevel.Critical` (5).

Если поставщик поддерживает [области журналов](#log-scopes), `IncludeScopes` определяет, включены ли они. Дополнительные сведения см. в статье [Области журналов](#log-scopes).

Следующий файл *appsettings.json* содержит параметры для всех встроенных поставщиков:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

В предыдущем примере:

- Категории и уровни не являются предлагаемыми значениями. Этот пример представлен с целью продемонстрировать все поставщики по умолчанию.
- Параметры в `Logging.{ProviderName}.LogLevel` переопределяют параметры в `Logging.LogLevel`. Например, уровень в `Debug.LogLevel.Default` переопределяет уровень в `LogLevel.Default`.
- Для каждого поставщика используется *псевдоним*. Каждый поставщик определяет *псевдоним*, используемый в конфигурации вместо полного имени типа. Ниже перечислены псевдонимы встроенных поставщиков.
  - Консоль
  - Отладка
  - EventSource
  - EventLog
  - AzureAppServicesFile
  - AzureAppServicesBlob
  - ApplicationInsights

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a>Настройка уровня ведения журнала с помощью командной строки, переменных среды и других способов конфигурации

Уровень ведения журнала может задаваться любыми [поставщиками конфигурации](configuration-providers.md). Например, вы можете создать хранимую переменную среды с именем `Logging:LogLevel:Microsoft` и значением `Information`.

## <a name="command-line"></a>[Командная строка](#tab/command-line)

Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.

```CMD
:: Assigns the env var to the value
setx "Logging__LogLevel__Microsoft" "Information" /M
```

В *новом* экземпляре **командной строки** считайте эту переменную среды.

```CMD
:: Prints the env var value
echo %Logging__LogLevel__Microsoft%
```

## <a name="powershell"></a>[PowerShell](#tab/powershell)

Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.

```powershell
# Assigns the env var to the value
[System.Environment]::SetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Information", "Machine")
```

В *новом* экземпляре **PowerShell** считайте эту переменную среды.

```powershell
# Prints the env var value
[System.Environment]::GetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Machine")
```

## <a name="bash"></a>[Bash](#tab/bash)

Создайте хранимую переменную среды и присвойте ей значение уровня ведения журнала.

```Bash
# Assigns the env var to the value, persists it across sessions
echo export Logging__LogLevel__Microsoft="Information" >> ~/.bashrc && source ~/.bashrc
```

Считывание переменной среды.

```Bash
# Prints the env var value
echo $Logging__LogLevel__Microsoft

# Or use printenv:
# printenv Logging__LogLevel__Microsoft
```

> [!NOTE]
> При настройке переменных среды, имена которых содержат точки (`.`), просмотрите вопрос об экспорте переменной с точкой (.) на **форуме Stack Exchange** и [утвержденный ответ](https://unix.stackexchange.com/a/93533).

---

Указанный выше параметр среды сохраняется в среде. Чтобы проверить параметры при работе с приложением, созданным на базе шаблонов рабочей службы .NET, выполните команду `dotnet run` в каталоге проекта после назначения переменной среды.

```dotnetcli
dotnet run
```

> [!TIP]
> После настройки переменной среды перезапустите интегрированную среду разработки, чтобы гарантировать доступность добавленных переменных среды.

В [Службе приложений Azure](https://azure.microsoft.com/services/app-service/) выберите **Новый параметр приложения** на странице **Параметры > Конфигурация**. Параметры приложения Службы приложений Azure:

- Шифруются, когда они неактивны, и передаются по зашифрованному каналу.
- Предоставляются как переменные среды.

Дополнительные сведения о настройке значений конфигурации .NET с помощью переменных среды см. в разделе [Поставщик конфигурации переменных среды](configuration-providers.md#environment-variable-configuration-provider).

## <a name="how-filtering-rules-are-applied"></a>Применение правил фильтрации

При создании объекта <xref:Microsoft.Extensions.Logging.ILogger%601> объект <xref:Microsoft.Extensions.Logging.ILoggerFactory> выбирает одно правило для каждого поставщика, которое будет применено к этому средству ведения журналов. Все сообщения, записываемые с помощью экземпляра `ILogger`, фильтруются на основе выбранных правил. Самое подробное правило для каждой пары поставщика и категории выбирается из списка доступных правил.

При создании `ILogger` для данной категории для каждого поставщика используется приведенный далее алгоритм:

- Выберите все правила, которые соответствуют поставщику или его псевдониму. Если ничего не найдено, выберите все правила с пустым поставщиком.
- В результатах предыдущего шага выберите правила с самым длинным соответствующим префиксом категории. Если ничего не найдено, выберите все правила, которые не указывают категорию.
- Если выбрано несколько правил, примите **последнее**.
- Если правила не выбраны, укажите минимальный уровень ведения журнала с помощью <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType>.

## <a name="log-category"></a>Категория журнала

При создании объекта `ILogger` указывается *категория*. Эта категория входит в состав каждого сообщения журнала, создаваемого этим экземпляром `ILogger`. Строка категории является необязательной, однако по соглашению следует использовать имя класса. Например, если служба в приложении определяется следующим объектом, категория может иметь значение `"Example.DefaultService"`.

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

Чтобы явно указать категорию, вызовите <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>:

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = loggerFactory.CreateLogger("CustomCategory");

        // ...
    }
}
```

Вызов `CreateLogger` с фиксированным именем может быть полезным при использовании в нескольких классах или типах, чтобы события можно было упорядочить по категориям.

Использование `ILogger<T>` эквивалентно вызову `CreateLogger` с полным именем типа `T`.

## <a name="log-level"></a>Уровень ведения журнала

В следующей таблице перечислены значения <xref:Microsoft.Extensions.Logging.LogLevel>, используемый для удобства метод расширения `Log{LogLevel}`, а также приводятся сведения о предполагаемом применении:

| LogLevel | Значение | Метод | Описание |
|--|--|--|--|
| [Трассировка](xref:Microsoft.Extensions.Logging.LogLevel) | 0 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | Содержит наиболее подробные сообщения. Эти сообщения могут содержать конфиденциальные данные приложения. Эти сообщения по умолчанию отключены, и их ***никогда*** не следует включать в рабочей среде. |
| [Отладка](xref:Microsoft.Extensions.Logging.LogLevel) | 1 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | Используется для отладки и разработки. В рабочей среде следует использовать с осторожностью из-за большого объема. |
| [Информация](xref:Microsoft.Extensions.Logging.LogLevel) | 2 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | Отслеживание общего потока работы приложения. Может использоваться в долгосрочных целях. |
| [Предупреждение](xref:Microsoft.Extensions.Logging.LogLevel) | 3 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | Для нестандартных или непредвиденных событий. Обычно содержит ошибки или условия, которые не приводят к сбою приложения. |
| [Ошибка](xref:Microsoft.Extensions.Logging.LogLevel) | 4 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | Для ошибок и исключений, которые не могут быть обработаны. Эти сообщения указывают на сбой текущих операции или запроса, а не на ошибку уровня приложения. |
| [Критическая](xref:Microsoft.Extensions.Logging.LogLevel) | 5 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | Для сбоев, которые требуют немедленного внимания. Примеры: потеря данных, нехватка места на диске. |
| [None](xref:Microsoft.Extensions.Logging.LogLevel) | 6 |  | Указывает, что сообщения не должны записываться. |

В приведенной выше таблице значения `LogLevel` приведены в порядке от самого низкого к самому высокому уровню серьезности.

Первый параметр метода [Log](xref:Microsoft.Extensions.Logging.LoggerExtensions), <xref:Microsoft.Extensions.Logging.LogLevel>, указывает на степень серьезности журнала. Вместо вызова `Log(LogLevel, ...)` большинство разработчиков вызывают методы расширения [Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions). Методы расширения `Log{LogLevel}` [вызывают метод Log и задают значение LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs). Например, следующие два вызова ведения журнала функционально эквивалентны и позволяют получить одинаковые журналы:

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

`AppLogEvents.Details` содержит идентификатор события и неявным образом представляется постоянным значением <xref:System.Int32>. `AppLogEvents` обозначает класс, который предоставляет разные именованные константы для идентификаторов и отображается в разделе [Идентификатор события журнала](#log-event-id).

Следующий код создает журналы `Information`и `Warning`:

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

В коде выше первый параметр, `AppLogEvents.Read`, — это `Log{LogLevel}`[идентификатор события журнала](#log-event-id). Второй параметр — это шаблон сообщения с заполнителями для значений аргументов, предоставляемых оставшимися параметрами метода. Параметры метода рассматриваются более подробно в разделе, посвященном [шаблону сообщений](#log-message-template) далее в этой статье.

Настройте подходящий уровень ведения журнала и вызовите правильные методы `Log{LogLevel}`, чтобы управлять объемом данных журнала, записываемых на определенный носитель. Пример:

- В рабочей среде:
  - При ведении журнала на уровнях `Trace` или `Information` создается большой объем подробных сообщений журнала. Чтобы контролировать затраты и не превысить лимиты объема хранилища данных, записывайте сообщения на уровнях `Trace` и `Information` в хранилище данных с низкими затратами и большим объемом. Рассмотрите возможность ограничения уровней `Trace` и `Information` конкретными категориями.
  - При ведении журналов на уровнях с `Warning` по `Critical` создается немного сообщений.
    - При этом стоимость и ограничения хранения, как правило, не важны.
    - Меньший объем журналов позволяет выбирать среди большего количества вариантов хранения данных.
- В среде разработки:
  - Задайте значение `Warning`.
  - Добавляйте сообщения уровней `Trace` или `Information` при устранении неполадок. Чтобы ограничить объем выходных данных, задавайте уровни `Trace` или `Information` только для исследуемых категорий.

Приведенный ниже код JSON задает уровень `Logging:Console:LogLevel:Microsoft:Information`:

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a>Идентификатор события журнала

Каждый журнал может содержать *идентификатор события*, где <xref:Microsoft.Extensions.Logging.EventId> представляет структуру с идентификатором (`Id`) и необязательными свойствами `Name` только для чтения. В этом примере исходного кода для определения идентификаторов событий используется класс `AppLogEvents`.

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

Идентификатор события связывает набор событий. Например, все журналы, связанные с чтением значений из репозитория, могут иметь идентификатор `1001`.

Поставщик ведения журналов может записывать идентификатор события в поле идентификатора, в сообщении журнала, или вообще не сохранять его. Поставщик Debug не отображает идентификаторы событий. Поставщик Console отображает идентификаторы событий в квадратных скобках после категории:

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

Некоторые поставщики ведения журнала хранят идентификатор события в поле, что позволяет выполнять фильтрацию по идентификатору.

## <a name="log-message-template"></a>Шаблон сообщения журнала

Каждый API ведения журнала использует шаблон сообщения. Шаблон сообщения может содержать заполнители, для которых предоставляются аргументы. Используйте для заполнителей имена, а не числа. Параметры, используемые для предоставления значений, определяются порядком заполнителей, а не их именами. В приведенном ниже коде имена параметров идут не по порядку в шаблоне сообщения:

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

Приведенный выше код создает сообщение журнала со значениями параметров в определенном порядке:

```text
Parameter values: param1, param2
```

Такой подход позволяет поставщикам ведения журнала реализовывать [семантическое или структурированное ведение журналов](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging). Сами аргументы передаются в систему ведения журналов, а не только в отформатированный шаблон сообщения. Это позволяет поставщикам ведения журнала хранить значения параметров как поля. Давайте рассмотрим следующий метод средства ведения журнала:

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

Например, при ведении журнала в хранилище таблиц Azure:

- каждая сущность таблицы Azure может иметь свойства `ID` и `RunTime`;
- использование таблиц со свойствами позволяет упростить выполнение запросов к данным журнала. Например, с помощью запроса можно находить все журналы в пределах определенного диапазона `RunTime`, не анализируя время ожидания текстового сообщения.

## <a name="log-exceptions"></a>Запись исключений в журнал

Методы средства ведения журнала имеют перегрузки, которые принимают параметр исключения:

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

Принципы записи исключений в журнал зависят от конкретного поставщика.

### <a name="default-log-level"></a>Уровень ведения журнала по умолчанию

Если не задан уровень ведения журнала по умолчанию, то по умолчанию используется уровень `Information`.

Давайте рассмотрим следующее приложение службы рабочей роли:

- Создано на основе шаблонов рабочей роли .NET.
- файлы *appsettings.json* и *appsettings.Development.json* были удалены или переименованы.

В рамках приведенной выше конфигурации при переходе на страницу сведений о конфиденциальности или домашнюю страницу создается множество сообщений с уровнем `Trace`, `Debug` и `Information`, в имени категории которых используется `Microsoft`.

В следующем коде задается уровень ведения журнала по умолчанию в том случае, если этот уровень не определен в конфигурации:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a>Функция фильтрации

Функция фильтрации вызывается для всех поставщиков и категорий, которым в конфигурации и (или) коде не назначены правила:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

Приведенный выше код отображает журналы консоли, если категория содержит `Example` или `Microsoft` и задан уровень ведения журнала `Information` или выше.

## <a name="log-scopes"></a>Области журналов

 *Область* может группировать набор логических операций. Эту возможность можно использовать для присоединения одних и тех же данных к каждому журналу, созданному как часть набора. Например, каждый журнал, созданный в ходе обработки транзакции, может включать идентификатор транзакции.

Область:

- имеет тип <xref:System.IDisposable>, который возвращается методом <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A>;
- действует вплоть до удаления.

Области поддерживаются следующими поставщиками:

- `Console`
- [AzureAppServicesFile и AzureAppServicesBlob](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

Используйте область, заключив вызовы средства ведения журналов в блок `using`:

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

Следующий код JSON предоставляет области для поставщика Console:

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

Следующий код предоставляет области для поставщика Console:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a>Консольные приложения без размещения

Код ведения журнала для приложений без [универсального узла](generic-host.md) отличается тем, как [добавляются поставщики](logging-providers.md#built-in-logging-providers) и [создаются средства ведения журнала](#create-logs). В консольном приложении, не использующем узел, вызовите метод расширения `Add{provider name}` поставщика при создании `LoggerFactory`:

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

Объект `loggerFactory` используется для создания экземпляра <xref:Microsoft.Extensions.Logging.ILogger>.

## <a name="create-logs-in-main"></a>Создание журналов в классе Main

Следующий код создает журналы в `Main`, получая экземпляр `ILogger` путем внедрения зависимостей после создания узла:

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a>Асинхронные методы ведения журналов не выполняются

Скорость ведения журналов не должна влиять на производительность выполнения асинхронного кода. Если хранилище данных, предназначенное для регистрации сообщений журнала, работает медленно, сначала записывайте эти сообщения в быстродействующее хранилище, а затем перемещайте их в медленное хранилище. Например, если вы записываете журналы в SQL Server, вам не нужно делать это непосредственно в методе `Log`, так как методы `Log` являются синхронными. Вместо этого синхронно добавьте сообщения журнала в очередь в памяти, и фоновый рабочий поток извлечет сообщения из очереди для выполнения асинхронных операций передачи данных в SQL Server.

## <a name="change-log-levels-in-a-running-app"></a>Изменение уровней ведения журнала в работающем приложении

API ведения журнала не включает сценарий для изменения уровней журнала во время работы приложения. Однако некоторые поставщики конфигурации могут перезагружать конфигурацию, что немедленно влияет на конфигурацию ведения журнала. Например, [поставщик конфигурации файлов](configuration-providers.md#file-configuration-provider) по умолчанию перезагружает конфигурацию ведения журнала. Если конфигурация изменяется в коде во время выполнения приложения, приложение может вызвать [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A), чтобы обновить конфигурацию ведения журнала приложения.

## <a name="nuget-packages"></a>Пакеты NuGet

Интерфейсы <xref:Microsoft.Extensions.Logging.ILogger%601> и <xref:Microsoft.Extensions.Logging.ILoggerFactory>, а также их реализации включены в пакет SDK для .NET Core. Кроме того, они доступны в следующих пакетах NuGet:

- Эти интерфейсы находятся в пространстве имен [Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).
- Их реализации по умолчанию находятся в пакете [Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging).

## <a name="apply-log-filter-rules-in-code"></a>Применение правил фильтрации журналов в коде

Для настройки правил фильтрации журналов рекомендуется использовать [конфигурацию](configuration.md).

В следующем примере показано, как зарегистрировать в коде правила фильтрации:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

`logging.AddFilter("System", LogLevel.Debug)` задает категорию `System` и уровень ведения журнала `Debug`. Поскольку конкретный поставщик не задан, фильтр применяется ко всем поставщикам.

`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` задает:

- поставщик ведения журнала `Debug`;
- уровень ведения журнала `Information` и выше;
- все категории, начинающиеся с `"Microsoft"`.

## <a name="see-also"></a>См. также раздел

- [Поставщики ведения журнала в NET](logging-providers.md)
- [Реализация пользовательского поставщика ведения журнала в .NET](custom-logging-provider.md)
- [Форматирование журнала консоли](console-log-formatter.md)
- [Ведение журнала с высокой производительностью в .NET](high-performance-logging.md)
- Ошибки, связанные с ведением журнала, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues).
