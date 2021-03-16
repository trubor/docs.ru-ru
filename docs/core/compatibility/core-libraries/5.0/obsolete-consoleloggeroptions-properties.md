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
# <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="582cf-103">Устаревшие свойства ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="582cf-103">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="582cf-104">Тип <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> и некоторые свойства <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="582cf-104">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

## <a name="change-description"></a><span data-ttu-id="582cf-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="582cf-105">Change description</span></span>

<span data-ttu-id="582cf-106">Начиная с .NET 5 тип <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> и несколько свойств <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="582cf-106">Starting in .NET 5, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="582cf-107">Устаревшие свойства:</span><span class="sxs-lookup"><span data-stu-id="582cf-107">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="582cf-108">Эти свойства теперь доступны в отдельных новых форматировщиках.</span><span class="sxs-lookup"><span data-stu-id="582cf-108">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="582cf-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="582cf-109">Reason for change</span></span>

<span data-ttu-id="582cf-110">Свойство <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> является типом перечисления, который не может представлять пользовательский форматировщик.</span><span class="sxs-lookup"><span data-stu-id="582cf-110">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="582cf-111">Остальные свойства были заданы в <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> и применены к обоим встроенным форматам для журналов консоли.</span><span class="sxs-lookup"><span data-stu-id="582cf-111">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="582cf-112">Но с введением нового API форматировщика будет логичным, если форматирование будет представлено в параметрах, относящихся к форматировщику.</span><span class="sxs-lookup"><span data-stu-id="582cf-112">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="582cf-113">Это изменение обеспечивает лучшее разделение средств ведения журнала и связанных форматировщиков.</span><span class="sxs-lookup"><span data-stu-id="582cf-113">This change provides better separation between the logger and logger formatters.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="582cf-114">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="582cf-114">Version introduced</span></span>

<span data-ttu-id="582cf-115">5.0</span><span class="sxs-lookup"><span data-stu-id="582cf-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="582cf-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="582cf-116">Recommended action</span></span>

- <span data-ttu-id="582cf-117">Используйте новое свойство <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> вместо свойства <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="582cf-117">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="582cf-118">Пример:</span><span class="sxs-lookup"><span data-stu-id="582cf-118">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="582cf-119">Есть несколько различий между <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> и <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span><span class="sxs-lookup"><span data-stu-id="582cf-119">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="582cf-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> имеет только два возможных параметра: `Default` и `Systemd`.</span><span class="sxs-lookup"><span data-stu-id="582cf-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="582cf-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> не учитывает регистр и может быть любой строкой.</span><span class="sxs-lookup"><span data-stu-id="582cf-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="582cf-122">Зарезервированные встроенные имена — это `Simple`, `Systemd` и `Json` (.NET 5 и выше).</span><span class="sxs-lookup"><span data-stu-id="582cf-122">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5 and later).</span></span>
  - <span data-ttu-id="582cf-123">`"Format": "Systemd"` сопоставляется с `"FormatterName": "Systemd"`.</span><span class="sxs-lookup"><span data-stu-id="582cf-123">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="582cf-124">`"Format": "Default"` сопоставляется с `"FormatterName": "Simple"`.</span><span class="sxs-lookup"><span data-stu-id="582cf-124">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="582cf-125">Для свойств <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> и <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> используйте соответствующее свойство в новых типах <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>или <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions>.</span><span class="sxs-lookup"><span data-stu-id="582cf-125">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="582cf-126">Например, соответствующим параметром для <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> является <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="582cf-126">For example, the corresponding setting for <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> is <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>.</span></span>

  <span data-ttu-id="582cf-127">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="582cf-127">Previous code:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  <span data-ttu-id="582cf-128">Новый код:</span><span class="sxs-lookup"><span data-stu-id="582cf-128">New code:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

<span data-ttu-id="582cf-129">В следующих двух фрагментах кода JSON показано, как изменяется файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="582cf-129">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="582cf-130">Старый файл конфигурации:</span><span class="sxs-lookup"><span data-stu-id="582cf-130">Old configuration file:</span></span>

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

<span data-ttu-id="582cf-131">Новый файл конфигурации:</span><span class="sxs-lookup"><span data-stu-id="582cf-131">New configuration file:</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="582cf-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="582cf-132">Affected APIs</span></span>

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
