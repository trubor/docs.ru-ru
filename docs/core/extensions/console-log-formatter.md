---
title: Форматирование журнала консоли
description: Сведения о том, как использовать доступное форматирование журнала консоли или реализовать настраиваемое форматирование журнала для приложений .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 178c66a99fac4d706156894cacffa5d902cb7901
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872695"
---
# <a name="console-log-formatting"></a>Форматирование журнала консоли

В .NET 5 была добавлена поддержка пользовательского форматирования в журналах консоли в пространстве имен `Microsoft.Extensions.Logging.Console`. Доступны три предопределенных варианта форматирования: [`Simple`](#simple), [`Systemd`](#systemd) и [`Json`](#json).

> [!IMPORTANT]
> Ранее перечисление <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> позволяло выбрать требуемый формат журнала: либо удобный для чтения (`Default`), либо запись в одну строку (`Systemd`). Но настроить их было **нельзя**, и теперь эти варианты считаются устаревшими.

В этой статье собраны сведения о форматировщиках журнала консоли. Этот пример исходного кода демонстрирует следующие действия:

- регистрация нового форматировщика;
- выбор зарегистрированного форматировщика для использования;
  - настройка в коде или через [конфигурацию](configuration.md);
- реализация пользовательского форматировщика;
  - обновление конфигурации через <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>;
  - включение пользовательского цветового форматирования.

## <a name="register-formatter"></a>Регистрация форматировщика

[Поставщик ведения журнала `Console`](logging-providers.md#console) имеет несколько предопределенных форматировщиков и предоставляет возможность создавать собственные пользовательские форматировщики. Чтобы зарегистрировать любой из уже доступных форматировщиков, используйте соответствующий метод расширения `Add{Type}Console`.

| Доступные типы | Метод для регистрации этого типа |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a>Простота

Чтобы использовать форматировщик консоли `Simple`, зарегистрируйте его с помощью `AddSimpleConsole`.

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

В предыдущем примере исходного кода регистрируется форматировщик <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>. Он позволяет не только включать в каждое сообщение журнала дополнительные сведения, как, например, текущее время и уровень ведения журнала, но и использовать внедрение цветов ANSI, а также отступы.

### <a name="systemd"></a>Systemd

Средство ведения журнала консоли <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> имеет следующие характеристики:

- использует формат и серьезность на уровне журнала "syslog";
- **не использует** цвета при форматировании сообщений;
- позволяет записывать сообщения в одну строку.

Обычно это удобно для контейнеров, которые часто используют ведение журнала консоли `Systemd`. Кроме того, в .NET 5 средство ведения журнала консоли `Simple` поддерживает компактную версию записи (в одну строку), а также позволяет отключить цвета, как показано в предыдущем примере.

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a>Json

Для записи журналов в формате JSON используется форматировщик консоли `Json`. В этом примере кода показано, как зарегистрировать его из приложения ASP.NET Core. Используя шаблон `webapp`, создайте новое приложение ASP.NET Core с помощью команды [dotnet new](../tools/dotnet-new.md).

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

Запустив приложение с этим шаблоном кода, вы получите следующий формат журнала по умолчанию:

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

По умолчанию выбирается форматировщик журнала консоли `Simple` с конфигурацией по умолчанию. Это можно изменить, вызвав `AddJsonConsole` из *program.cs*.

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

Еще раз запустите приложение, в которое вы внесли указанное выше изменение. Теперь сообщения журнала будут иметь формат JSON.

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> Форматировщик консоли `Json` по умолчанию записывает каждое сообщение в одну строку. Чтобы сделать вывод более удобным для чтения, при настройке форматировщика задайте для <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> значение `true`.

## <a name="set-formatter-with-configuration"></a>Настройка форматировщика с помощью конфигурации

В предыдущих примерах показано, как зарегистрировать форматировщик программными средствами. Эту же операцию можно выполнить путем [настройки](configuration.md). Давайте рассмотрим приведенный выше пример исходного кода веб-приложения. Вместо вызова `ConfigureLogging` в файле *program.cs*, можно получить такой же результат изменением файла *appsettings.json*. Обновленный `appsettings.json` файл настроит форматировщик следующим образом:

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

Два основных значения здесь — `"FormatterName"` и `"FormatterOptions"`. Если форматировщик уже зарегистрирован с тем значением, которое вы задали для `"FormatterName"`, будет выбран уже существующий форматировщик. Кроме того, можно настроить его свойства, если они указаны в качестве ключа внутри узла `"FormatterOptions"`. Предопределенные имена модулей форматирования зарезервированы в <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>.

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a>Реализация пользовательского форматировщика

Для реализации пользовательского форматировщика сделайте следующее:

- Создайте подкласс в <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, который представляет пользовательский форматировщик.
- Зарегистрируйте пользовательский форматировщик с помощью:
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

Создайте метод расширения для решения этой задачи.

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

Для определения `CustomOptions` используется такой код:

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

В приведенном выше примере кода параметры являются подклассом <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.

API-интерфейс `AddConsoleFormatter` выполняет следующие действия:

- Регистрирует подкласс `ConsoleFormatter`.
- Обрабатывает конфигурацию.
  - Использует маркер изменения для синхронизации обновлений по [шаблону параметров](options.md) с применением интерфейса [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601).

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

Определите подкласс `CustomerFormatter` в `ConsoleFormatter`.

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

Приведенный выше API `CustomFormatter.Write<TState>` определяет, какой текст добавляется вокруг каждого сообщения журнала. В стандартной реализации `ConsoleFormatter` должна создаваться оболочка по меньшей мере для областей, меток времени и степени серьезности записи журнала. Кроме того, в сообщениях журнала можно кодировать цвета ANSI и указывать отступы. В реализации `CustomFormatter.Write<TState>` таких возможностей нет.

Дополнительные идеи по настройке форматирования вы найдете в примерах реализации для пространства имен `Microsoft.Extensions.Logging.Console`:

- [SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs);
- [SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs);
- [JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs).

## <a name="implement-custom-color-formatting"></a>Реализация пользовательского форматирования цвета

Чтобы правильно внедрить поддержку цвета в пользовательский форматировщик, расширьте <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions>, у которого уже есть свойство <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>. Оно будет полезным для включения цвета в журналы.

Создайте `CustomColorOptions`, который наследует от `SimpleConsoleFormatterOptions`.

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

Теперь создайте несколько методов расширения в классе `TextWriterExtensions`, который позволяет легко внедрять цвета в кодировке ANSI в форматированные сообщения журнала.

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

Пользовательский форматировщик, который обрабатывает применение пользовательских цветов, можно определить следующим образом:

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

При запуске приложения в журналах сообщение `CustomPrefix` будет отображаться зеленым цветом, если `FormatterOptions.ColorBehavior` имеет значение `Enabled`.

> [!NOTE]
> Если <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> имеет значение `Disabled`, сообщения журнала _не_ обрабатывают внедренные коды цветов ANSI в сообщениях журнала. Вместо этого они выводят необработанное сообщение. Рассмотрим следующий пример.
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> При выполнении этого кода выводится строка в неизменном виде _без_ добавления цветов.
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a>См. также раздел

- [Ведение журнала в .NET](logging.md)
- [Реализация пользовательского поставщика ведения журнала в .NET](custom-logging-provider.md)
- [Ведение журнала с высокой производительностью в .NET](high-performance-logging.md)
