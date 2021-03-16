---
title: Критическое изменение. Устаревшие свойства ConsoleLoggerOptions
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где тип ConsoleLoggerFormat и некоторые свойства в ConsoleLoggerOptions теперь являются устаревшими.
ms.date: 11/01/2020
ms.openlocfilehash: c6ee294f90e304cebd517bd0139c58a6c7a41e0c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257314"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a>Устаревшие свойства ConsoleLoggerOptions

Тип <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> и некоторые свойства <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> являются устаревшими.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5 тип <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> и несколько свойств <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> являются устаревшими. Устаревшие свойства:

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

Эти свойства теперь доступны в отдельных новых форматировщиках.

## <a name="reason-for-change"></a>Причина изменения

Свойство <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> является типом перечисления, который не может представлять пользовательский форматировщик.

Остальные свойства были заданы в <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> и применены к обоим встроенным форматам для журналов консоли. Но с введением нового API форматировщика будет логичным, если форматирование будет представлено в параметрах, относящихся к форматировщику. Это изменение обеспечивает лучшее разделение средств ведения журнала и связанных форматировщиков.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Используйте новое свойство <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> вместо свойства <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>. Пример:

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  Есть несколько различий между <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> и <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> имеет только два возможных параметра: `Default` и `Systemd`.
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> не учитывает регистр и может быть любой строкой. Зарезервированные встроенные имена — это `Simple`, `Systemd` и `Json` (.NET 5 и выше).
  - `"Format": "Systemd"` сопоставляется с `"FormatterName": "Systemd"`.
  - `"Format": "Default"` сопоставляется с `"FormatterName": "Simple"`.

- Для свойств <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> и <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> используйте соответствующее свойство в новых типах <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>или <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions>. Например, соответствующим параметром для <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> является <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>.

  Предыдущий код:

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  Новый код:

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

В следующих двух фрагментах кода JSON показано, как изменяется файл конфигурации. Старый файл конфигурации:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

Новый файл конфигурации:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

## <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
