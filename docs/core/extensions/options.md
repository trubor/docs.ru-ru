---
title: Шаблон параметров в .NET
author: IEvangelist
description: Сведения о том, как использовать шаблон параметров для представления групп связанных параметров в приложениях .NET.
ms.author: dapine
ms.date: 02/18/2021
ms.openlocfilehash: df30928cdb1832e94f89abbdf8cc41e1304f8e2e
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102402165"
---
# <a name="options-pattern-in-net"></a>Шаблон параметров в .NET

Шаблон параметров использует классы для обеспечения строго типизированного доступа к группам связанных параметров. Когда [параметры конфигурации](configuration.md) изолируются по сценарию в отдельных классах, в приложениях соблюдаются два важных принципа программной инженерии.

- [Принцип разделения интерфейса (ISP) или инкапсуляция.](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation) Сценарии (классы), которые зависят от параметров конфигурации, зависят только от используемых ими параметров конфигурации.
- [Разделение областей ответственности](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns). Параметры для разных частей приложения не зависят друг от друга и не связаны друг с другом.

В параметрах также предусмотрен механизм для проверки данных конфигурации. Дополнительные сведения см. в разделе [Проверка параметров](#options-validation).

## <a name="bind-hierarchical-configuration"></a>Привязка иерархической конфигурации

Предпочтительный способ чтения связанных значений конфигурации — использование шаблона параметров. Шаблон параметров можно реализовать через интерфейс <xref:Microsoft.Extensions.Options.IOptions%601>, где параметр `TOptions` универсального типа ограничен атрибутом `class`. Позднее можно предоставить `IOptions<TOptions>` через внедрение зависимостей. Дополнительные сведения см. в статье [Внедрение зависимостей в .NET](dependency-injection.md).

Например, чтобы считать следующие значения конфигурации:

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

Создайте следующий класс `TransientFaultHandlingOptions`:

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span id="options-class"></span> При использовании шаблона параметров класс параметров должен иметь следующие характеристики:

- Являться неабстрактным с открытым конструктором без параметров.
- Содержать открытые свойства для чтения и записи для привязки (поля ***не*** привязываются).

В приведенном ниже коде

* Вызывает [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) для привязки класса `TransientFaultHandlingOptions` к разделу `"TransientFaultHandlingOptions"`.
* Отображает данные конфигурации.

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.

[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) привязывает и возвращает указанный тип. Метод `ConfigurationBinder.Get<T>` может быть более удобным, чем `ConfigurationBinder.Bind`. В приведенном ниже примере кода демонстрируются способы использования `ConfigurationBinder.Get<T>` с классом `TransientFaultHandlingOptions`:

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.

> [!IMPORTANT]
> Класс <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> предоставляет несколько интерфейсов API, например `.Bind(object instance)` и `.Get<T>()`, которые ***не*** ограничены атрибутом `class`. При использовании любого из [интерфейсов параметров](#options-interfaces) необходимо соблюдать вышеупомянутые [ограничения для класса параметров](#options-class).

Альтернативный подход при использовании шаблона параметров — привязать раздел `"TransientFaultHandlingOptions"` и добавить его в [контейнер службы внедрения зависимостей](dependency-injection.md). В следующем коде `TransientFaultHandlingOptions` добавляется в контейнер службы с помощью интерфейса <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> и привязывается к конфигурации:

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> Параметр `key` содержит имя раздела конфигурации для поиска. Это значение *не обязано* совпадать с именем типа, который его представляет. Например, у вас может существовать раздел с именем `"FaultHandling"`, представленный классом `TransientFaultHandlingOptions`. В этом случае вы будете передавать `"FaultHandling"` в функцию <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A>. Оператор `nameof` используется для удобства, когда имя именованного раздела совпадает с типом, которому он соответствует.

С помощью приведенного выше кода следующий код считывает параметры расположения:

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, ***не*** считываются. Чтобы считать изменения после запуска приложения, используйте [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).

## <a name="options-interfaces"></a>Интерфейсы параметров

<xref:Microsoft.Extensions.Options.IOptions%601>:

- ***Не*** поддерживает:
  - чтение данных конфигурации после запуска приложения;
  - [именованные параметры](#named-options-support-using-iconfigurenamedoptions);
- Регистрируется в качестве элемента [singleton](dependency-injection.md#singleton) и может быть внедрен в любое [время существования службы](dependency-injection.md#service-lifetimes).

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:

- Полезен в сценариях, где параметры должны вычисляться заново при каждом разрешении внедрения, для [временных или ограниченных областью](dependency-injection.md#service-lifetimes) зависимостей. Дополнительные сведения см. в разделе [Использование IOptionsSnapshot для чтения обновленных данных](#use-ioptionssnapshot-to-read-updated-data).
- Регистрируется как [Scoped](dependency-injection.md#scoped) (с областью), поэтому его нельзя внедрить в службу singleton.
- Поддерживает [именованные параметры](#named-options-support-using-iconfigurenamedoptions).

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:

- Используется для извлечения параметров и управления уведомлениями о параметрах для экземпляров `TOptions`.
- Регистрируется в качестве элемента [singleton](dependency-injection.md#singleton) и может быть внедрен в любое [время существования службы](dependency-injection.md#service-lifetimes).
- Поддерживаются следующие возможности:
  - уведомления об изменениях;
  - [именованные параметры](#named-options-support-using-iconfigurenamedoptions);
  - [перезагружаемые конфигурации](#use-ioptionssnapshot-to-read-updated-data);
  - объявление определенных параметров недействительными (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>).

Интерфейс <xref:Microsoft.Extensions.Options.IOptionsFactory%601> отвечает за создание экземпляров параметров. Он имеет единственный метод <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A>. При реализации по умолчанию принимаются все зарегистрированные интерфейсы <xref:Microsoft.Extensions.Options.IConfigureOptions%601> и <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>. Также сначала выполняются все основные настройки, а затем действия после конфигурации. Она различает интерфейсы <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> и <xref:Microsoft.Extensions.Options.IConfigureOptions%601> и вызывает только соответствующий интерфейс.

<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> используется интерфейсом <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> для записи экземпляров `TOptions` в кэш. <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> делает экземпляры параметров в мониторе недействительными, что приводит к повторному вычислению значений (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>). Значения можно также вводить вручную с помощью <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>. Метод <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> используется, если необходимо повторно создать все именованные экземпляры по требованию.

### <a name="options-interfaces-benefits"></a>Преимущества интерфейсов параметров

Использование универсального типа оболочки позволяет отвязать время существования параметра от контейнера внедрения зависимостей. Интерфейс <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> предоставляет уровень абстракции для типа параметров, включая универсальные ограничения. Это обеспечивает следующие преимущества.

- Вычисление экземпляра конфигурации `T` выполняется только при доступе к <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>, а не при его внедрении. Это важно, так как вы можете использовать параметр `T` из разных мест и выбирать семантику времени существования, не изменяя данные о `T`.
- При регистрации параметров с типом `T` вам не придется явно регистрировать тип `T`. Это очень удобно при [создании библиотеки](options-library-authors.md) с простыми параметрами по умолчанию, если вы не хотите вынуждать вызывающую сторону регистрировать параметры в контейнере внедрения зависимостей с конкретным временем существования.
- С точки зрения API это позволяет создавать ограничения типа `T` (в нашем примере параметр `T` ограничен ссылочным типом).

## <a name="use-ioptionssnapshot-to-read-updated-data"></a>Использование IOptionsSnapshot для чтения обновленных данных

При использовании <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> параметры вычисляются один раз на каждый запрос при обращении к ним и кэшируются на все время существования запроса. Изменения конфигурации считываются после запуска приложения при использовании поставщиков конфигурации, поддерживающих чтение обновленных значений конфигурации.

Разница между `IOptionsMonitor` и `IOptionsSnapshot`:

- `IOptionsMonitor` — это [одноэлементная служба](dependency-injection.md#singleton), которая получает текущие значения параметров в любое время, что особенно полезно в одноэлементных зависимостях.
- `IOptionsSnapshot` — это [служба с заданной областью действия](dependency-injection.md#scoped), предоставляющая моментальный снимок параметров на момент создания объекта `IOptionsSnapshot<T>`. Моментальные снимки параметров предназначены для использования с временными зависимостями и зависимостями с заданной областью действия.

В приведенном ниже коде используется <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

Следующий код регистрирует экземпляр конфигурации, к которому привязывается `TransientFaultHandlingOptions`.

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.

## <a name="ioptionsmonitor"></a>IOptionsMonitor

Следующий код регистрирует экземпляр конфигурации, к которому привязывается `TransientFaultHandlingOptions`.

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

В следующем примере используется <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>.

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.

## <a name="named-options-support-using-iconfigurenamedoptions"></a>Поддержка именованных параметров с использованием IConfigureNamedOptions

Именованные параметры:

- полезны, если несколько разделов конфигурации привязываются к одним и тем же свойствам;
- используются с учетом регистра.

Рассмотрите следующий файл *appsettings.json*:

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

Вместо создания двух классов для привязки `Features:Personalize` и `Features:WeatherStation` для каждого раздела используется следующий класс:

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

Следующий код служит для настройки именованных параметров:

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

Следующий код отображает именованные параметры:

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

Все параметры являются именованными экземплярами. Экземпляры <xref:Microsoft.Extensions.Options.IConfigureOptions%601> считаются нацеленными на экземпляр `Options.DefaultName`, который имеет значение `string.Empty`. Интерфейс <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> также реализует интерфейс <xref:Microsoft.Extensions.Options.IConfigureOptions%601>. Реализация <xref:Microsoft.Extensions.Options.IOptionsFactory%601> по умолчанию содержит логику для надлежащего использования каждого экземпляра. Именованный параметр `null` предназначен для всех именованных экземпляров, а не для какого-то определенного. <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> и <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> следуют этому соглашению.

## <a name="optionsbuilder-api"></a>API OptionsBuilder

<xref:Microsoft.Extensions.Options.OptionsBuilder%601> используется для настройки экземпляров `TOptions`. `OptionsBuilder` упрощает создание именованных параметров, так как он является единственным параметром для первоначального вызова `AddOptions<TOptions>(string optionsName)` и не должен появляться во всех последующих вызовах. Проверка параметров и перегрузки `ConfigureOptions`, принимающие зависимости службы, доступны только через `OptionsBuilder`.

`OptionsBuilder` используется в разделе [Проверка параметров](#options-validation).

## <a name="use-di-services-to-configure-options"></a>Использование служб внедрения зависимостей для настройки параметров

Использовать службы, доступные в результате внедрения зависимостей при настройке параметров, можно двумя способами.

- Передайте делегат конфигурации методу [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) в [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601). `OptionsBuilder<TOptions>` предоставляет перегрузки метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), которые позволяют использовать до пяти служб для настройки параметров:

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- Создайте тип, реализующий <xref:Microsoft.Extensions.Options.IConfigureOptions%601> или <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, и зарегистрируйте этот тип как службу.

Рекомендуем передать делегат конфигурации методу [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), так как создать службу сложнее. Создание типа эквивалентно тому, что делает платформа при вызове метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A). При вызове метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) регистрируется временный универсальный интерфейс <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, имеющий конструктор, который принимает указанные универсальные типы службы.

## <a name="options-validation"></a>Проверка параметров

Проверка параметров позволяет проверять значения параметров.

Рассмотрите следующий файл *appsettings.json*:

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

Следующий класс привязывается к разделу конфигурации `"Settings"` и применяет несколько правил `DataAnnotations`:

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

В приведенном ниже коде

- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A>, чтобы получить класс [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601), который привязывается к классу `SettingsOptions`;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> для включения проверки с помощью `DataAnnotations`.

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

Метод расширения `ValidateDataAnnotations` определен в пакете NuGet [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations).

Следующий код отображает значения конфигурации или ошибки проверки:

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

Следующий код применяет более сложное правило проверки с использованием делегата:

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a>IValidateOptions для сложной проверки

Следующий класс реализует <xref:Microsoft.Extensions.Options.IValidateOptions%601>:

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

`IValidateOptions` позволяет переместить код проверки в класс.

С использованием приведенного выше кода проверка включается в `ConfigureServices` с помощью следующего кода:

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a>Пост-конфигурация параметров

Задайте пост-конфигурацию с помощью <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>. Процессы после завершения настройки выполняются после всех конфигураций <xref:Microsoft.Extensions.Options.IConfigureOptions%601>. Это может быть полезно в сценариях, когда требуется переопределять конфигурацию.

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

Для последующей настройки именованных параметров доступен метод <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A>.

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

Для последующей настройки всех экземпляров конфигурации служит метод <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A>.

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a>См. также раздел

- [Конфигурация в .NET](configuration.md)
- [Руководство по шаблону параметров для авторов библиотек .NET](options-library-authors.md)
