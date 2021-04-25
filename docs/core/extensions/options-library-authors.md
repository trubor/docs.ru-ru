---
title: Руководство по шаблону параметров для авторов библиотек .NET
author: IEvangelist
description: Узнайте, как реализовать шаблон параметров при разработке библиотеки в .NET.
ms.author: dapine
ms.date: 04/12/2021
ms.openlocfilehash: 7e1bfeadff92f5d0d979ef2d7da11d7c1b47c58d
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369625"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a>Руководство по шаблону параметров для авторов библиотек .NET

С помощью внедрения зависимостей можно зарегистрировать службы и их соответствующие конфигурации, чтобы использовать *шаблон параметров*. Шаблон параметров позволяет потребителям библиотеки (и ваших служб) запрашивать экземпляры [интерфейсов параметров](options.md#options-interfaces), где `TOptions` — это ваш класс параметров. Использование параметров конфигурации через строго типизированные объекты помогает сохранить согласованное представление значений и устраняет необходимость вручную анализировать строковые значения. Существует множество [поставщиков конфигурации](configuration-providers.md), которые могут использоваться потребителями библиотеки. Эти поставщики позволяют пользователям настраивать библиотеку разными способами.

Авторы библиотек для .NET получат здесь общие рекомендации по правильному предоставлению шаблона параметров для потребителей библиотеки. Существует множество способов решить одну задачу. При этом нужно учитывать несколько факторов.

## <a name="naming-conventions"></a>Соглашения об именах

По соглашению методы расширения, отвечающие за регистрацию служб, получают имена вида `Add{Service}`, где `{Service}` — это понятное описательное имя. В зависимости от пакета регистрация служб может дополняться методами расширения `Use{Service}`. Методы расширения `Use{Service}` широко используются в [ASP.NET Core](/aspnet).

✔️ РЕКОМЕНДУЕТСЯ использовать имена, которые отличают службу от других предложений.

❌НЕ ИСПОЛЬЗУЙТЕ имена, которые уже являются частью экосистемы .NET из официальных пакетов Майкрософт.

✔️ РЕКОМЕНДУЕТСЯ присваивать статическим классам, которые предоставляют методы расширения, имена вида `{Type}Extensions`, где `{Type}` — это расширяемый тип.

### <a name="namespace-guidance"></a>Рекомендации по использованию пространства имен

Пакеты Майкрософт используют пространство имен `Microsoft.Extensions.DependencyInjection`, чтобы унифицировать регистрацию разных предложений услуг.

✔️ РЕКОМЕНДУЕТСЯ использовать пространство имен, которое четко описывает предложение пакета.

❌НЕ ИСПОЛЬЗУЙТЕ пространство имен `Microsoft.Extensions.DependencyInjection` для пакетов, не являющихся официальными пакетами Майкрософт.

## <a name="parameterless"></a>Использование без параметров

Если служба может работать с минимальной конфигурацией или без явно заданной конфигурации, постарайтесь использовать метод расширения без параметров.

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

Приведенный выше код `AddMyLibraryService` выполняет следующее:

- расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> с параметром типа `LibraryOptions`;
- передает результат в следующий вызов к <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> для определения значений параметров по умолчанию.

## <a name="iconfiguration-parameter"></a>Параметр `IConfiguration`

При создании библиотеки, которая предоставляет потребителям большой набор параметров, может быть полезно потребовать метод расширения параметра `IConfiguration`. Ожидаемый экземпляр `IConfiguration` должен быть ограничен областью именованного раздела конфигурации путем применения функции <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType>.

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-14":::

Приведенный выше код `AddMyLibraryService` выполняет следующее:

- расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;
- определяет параметр <xref:Microsoft.Extensions.Configuration.IConfiguration> `namedConfigurationSection`;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)>, передавая параметр универсального типа для `LibraryOptions` и экземпляр `namedConfigurationSection` для настройки.

Потребители в этом шаблоне предоставляют экземпляр именованного раздела `IConfiguration` с заданной областью.

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

В методе <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> выполняется вызов метода `.AddMyLibraryService`. Это же справедливо и при использовании класса `Startup`, где добавление регистрируемых служб происходит в `ConfigureServices`.

За определение значений по умолчанию отвечает автор библиотеки.

> [!NOTE]
> Есть возможность привязать конфигурацию к экземпляру параметров. Но при этом существует риск возникновения конфликтов имен, что приведет к ошибкам. Кроме того, при таком способе выполнения привязки вручную вы ограничиваете использование шаблона параметров однократной операцией чтения. Изменения параметров не будут привязываться повторно, а значит потребители не смогут использовать интерфейс [IOptionsMonitor](options.md#ioptionsmonitor).
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a>Параметр `Action<TOptions>`

Потребителям библиотеки может быть интересен вариант предоставления лямбда-выражения, которое возвращает экземпляр класса параметров. В этом сценарии вы определяете параметр `Action<LibraryOptions>` в методе расширения.

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

Приведенный выше код `AddMyLibraryService` выполняет следующее:

- расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;
- определяет <xref:System.Action%601>, где `T` является параметром `LibraryOptions` `configureOptions`;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> для действия `configureOptions`.

Потребители в этом шаблоне предоставляют лямбда-выражение (или делегат, который соответствует параметру `Action<LibraryOptions>`).

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a>Параметр экземпляра параметров

Потребители библиотеки могут предоставлять экземпляр встроенных параметров. В этом сценарии вы предоставляете метод расширения, который принимает экземпляр объекта параметров `LibraryOptions`.

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

Приведенный выше код `AddMyLibraryService` выполняет следующее:

- расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> с параметром типа `LibraryOptions`;
- привязывает вызов к <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, который задает значения параметров по умолчанию, которые затем могут быть переопределены из конкретного экземпляра `userOptions`.

Потребители в этом шаблоне предоставляют экземпляр класса `LibraryOptions`, определяя требуемые значения свойств в строке.

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a>После настройки

Когда все значения параметров конфигурации будут привязаны или определены, станут доступными процессы, выполняемые после настройки. Предоставляя тот же [параметр `Action<TOptions>`](#actiontoptions-parameter), который был описан ранее, можно выбрать вызов <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>. Процесс, выполняемый после настройки, начинается после всех вызовов `.Configure`.

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

Приведенный выше код `AddMyLibraryService` выполняет следующее:

- расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;
- определяет <xref:System.Action%601>, где `T` является параметром `LibraryOptions` `configureOptions`;
- вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> для действия `configureOptions`.

Потребители в этом шаблоне предоставляют лямбда-выражение (или делегат, который соответствует параметру `Action<LibraryOptions>`), точно так же как с [параметром `Action<TOptions>`] в сценарии без процессов, выполняемых после конфигурации.

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a>См. также раздел

- [Шаблон параметров в .NET](options.md)
- [Внедрение зависимостей в .NET](dependency-injection.md)
- [Рекомендации по внедрению зависимостей](dependency-injection-guidelines.md)
