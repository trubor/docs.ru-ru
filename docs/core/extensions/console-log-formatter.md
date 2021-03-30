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
# <a name="console-log-formatting"></a><span data-ttu-id="cea75-103">Форматирование журнала консоли</span><span class="sxs-lookup"><span data-stu-id="cea75-103">Console log formatting</span></span>

<span data-ttu-id="cea75-104">В .NET 5 была добавлена поддержка пользовательского форматирования в журналах консоли в пространстве имен `Microsoft.Extensions.Logging.Console`.</span><span class="sxs-lookup"><span data-stu-id="cea75-104">In .NET 5, support for custom formatting was added to console logs in the `Microsoft.Extensions.Logging.Console` namespace.</span></span> <span data-ttu-id="cea75-105">Доступны три предопределенных варианта форматирования: [`Simple`](#simple), [`Systemd`](#systemd) и [`Json`](#json).</span><span class="sxs-lookup"><span data-stu-id="cea75-105">There are three predefined formatting options available: [`Simple`](#simple), [`Systemd`](#systemd), and [`Json`](#json).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cea75-106">Ранее перечисление <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> позволяло выбрать требуемый формат журнала: либо удобный для чтения (`Default`), либо запись в одну строку (`Systemd`).</span><span class="sxs-lookup"><span data-stu-id="cea75-106">Previously, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> enum allowed for selecting the desired log format, either human readable which was the `Default`, or single line which is also known as `Systemd`.</span></span> <span data-ttu-id="cea75-107">Но настроить их было **нельзя**, и теперь эти варианты считаются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="cea75-107">However, these were **not** customizable, and are now deprecated.</span></span>

<span data-ttu-id="cea75-108">В этой статье собраны сведения о форматировщиках журнала консоли.</span><span class="sxs-lookup"><span data-stu-id="cea75-108">In this article, you will learn about console log formatters.</span></span> <span data-ttu-id="cea75-109">Этот пример исходного кода демонстрирует следующие действия:</span><span class="sxs-lookup"><span data-stu-id="cea75-109">The sample source code demonstrates how to:</span></span>

- <span data-ttu-id="cea75-110">регистрация нового форматировщика;</span><span class="sxs-lookup"><span data-stu-id="cea75-110">Register a new formatter</span></span>
- <span data-ttu-id="cea75-111">выбор зарегистрированного форматировщика для использования;</span><span class="sxs-lookup"><span data-stu-id="cea75-111">Select a registered formatter to use</span></span>
  - <span data-ttu-id="cea75-112">настройка в коде или через [конфигурацию](configuration.md);</span><span class="sxs-lookup"><span data-stu-id="cea75-112">Either through code, or [configuration](configuration.md)</span></span>
- <span data-ttu-id="cea75-113">реализация пользовательского форматировщика;</span><span class="sxs-lookup"><span data-stu-id="cea75-113">Implement a custom formatter</span></span>
  - <span data-ttu-id="cea75-114">обновление конфигурации через <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>;</span><span class="sxs-lookup"><span data-stu-id="cea75-114">Update configuration via <xref:Microsoft.Extensions.Options.IOptionsMonitor%601></span></span>
  - <span data-ttu-id="cea75-115">включение пользовательского цветового форматирования.</span><span class="sxs-lookup"><span data-stu-id="cea75-115">Enable custom color formatting</span></span>

## <a name="register-formatter"></a><span data-ttu-id="cea75-116">Регистрация форматировщика</span><span class="sxs-lookup"><span data-stu-id="cea75-116">Register formatter</span></span>

<span data-ttu-id="cea75-117">[Поставщик ведения журнала `Console`](logging-providers.md#console) имеет несколько предопределенных форматировщиков и предоставляет возможность создавать собственные пользовательские форматировщики.</span><span class="sxs-lookup"><span data-stu-id="cea75-117">The [`Console` logging provider](logging-providers.md#console) has several predefined formatters, and exposes the ability to author your own custom formatter.</span></span> <span data-ttu-id="cea75-118">Чтобы зарегистрировать любой из уже доступных форматировщиков, используйте соответствующий метод расширения `Add{Type}Console`.</span><span class="sxs-lookup"><span data-stu-id="cea75-118">To register any of the available formatters, use the corresponding `Add{Type}Console` extension method:</span></span>

| <span data-ttu-id="cea75-119">Доступные типы</span><span class="sxs-lookup"><span data-stu-id="cea75-119">Available types</span></span> | <span data-ttu-id="cea75-120">Метод для регистрации этого типа</span><span class="sxs-lookup"><span data-stu-id="cea75-120">Method to register type</span></span> |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a><span data-ttu-id="cea75-121">Простота</span><span class="sxs-lookup"><span data-stu-id="cea75-121">Simple</span></span>

<span data-ttu-id="cea75-122">Чтобы использовать форматировщик консоли `Simple`, зарегистрируйте его с помощью `AddSimpleConsole`.</span><span class="sxs-lookup"><span data-stu-id="cea75-122">To use the `Simple` console formatter, register it with `AddSimpleConsole`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

<span data-ttu-id="cea75-123">В предыдущем примере исходного кода регистрируется форматировщик <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cea75-123">In the preceding sample source code, the <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> formatter was registered.</span></span> <span data-ttu-id="cea75-124">Он позволяет не только включать в каждое сообщение журнала дополнительные сведения, как, например, текущее время и уровень ведения журнала, но и использовать внедрение цветов ANSI, а также отступы.</span><span class="sxs-lookup"><span data-stu-id="cea75-124">It provides logs with the ability to not only wrap information such as time and log level in each log message, but also allows for ANSI color embedding and indentation of messages.</span></span>

### <a name="systemd"></a><span data-ttu-id="cea75-125">Systemd</span><span class="sxs-lookup"><span data-stu-id="cea75-125">Systemd</span></span>

<span data-ttu-id="cea75-126">Средство ведения журнала консоли <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> имеет следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="cea75-126">The <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> console logger:</span></span>

- <span data-ttu-id="cea75-127">использует формат и серьезность на уровне журнала "syslog";</span><span class="sxs-lookup"><span data-stu-id="cea75-127">Uses the "Syslog" log level format and severities</span></span>
- <span data-ttu-id="cea75-128">**не использует** цвета при форматировании сообщений;</span><span class="sxs-lookup"><span data-stu-id="cea75-128">Does **not** format messages with colors</span></span>
- <span data-ttu-id="cea75-129">позволяет записывать сообщения в одну строку.</span><span class="sxs-lookup"><span data-stu-id="cea75-129">Always logs messages in a single line</span></span>

<span data-ttu-id="cea75-130">Обычно это удобно для контейнеров, которые часто используют ведение журнала консоли `Systemd`.</span><span class="sxs-lookup"><span data-stu-id="cea75-130">This is commonly useful for containers, which often make use of `Systemd` console logging.</span></span> <span data-ttu-id="cea75-131">Кроме того, в .NET 5 средство ведения журнала консоли `Simple` поддерживает компактную версию записи (в одну строку), а также позволяет отключить цвета, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="cea75-131">With .NET 5, the `Simple` console logger also enables a compact version that logs in a single line, and also allows for disabling colors as shown in an earlier sample.</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a><span data-ttu-id="cea75-132">Json</span><span class="sxs-lookup"><span data-stu-id="cea75-132">Json</span></span>

<span data-ttu-id="cea75-133">Для записи журналов в формате JSON используется форматировщик консоли `Json`.</span><span class="sxs-lookup"><span data-stu-id="cea75-133">To write logs in a JSON format, the `Json` console formatter is used.</span></span> <span data-ttu-id="cea75-134">В этом примере кода показано, как зарегистрировать его из приложения ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cea75-134">The sample source code shows how an ASP.NET Core app might register it.</span></span> <span data-ttu-id="cea75-135">Используя шаблон `webapp`, создайте новое приложение ASP.NET Core с помощью команды [dotnet new](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="cea75-135">Using the `webapp` template, create a new ASP.NET Core app with the [dotnet new](../tools/dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

<span data-ttu-id="cea75-136">Запустив приложение с этим шаблоном кода, вы получите следующий формат журнала по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="cea75-136">When running the app, using the template code, you get the default log format below:</span></span>

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

<span data-ttu-id="cea75-137">По умолчанию выбирается форматировщик журнала консоли `Simple` с конфигурацией по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="cea75-137">By default, the `Simple` console log formatter is selected with default configuration.</span></span> <span data-ttu-id="cea75-138">Это можно изменить, вызвав `AddJsonConsole` из *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="cea75-138">You change this by calling `AddJsonConsole` in the *Program.cs*:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

<span data-ttu-id="cea75-139">Еще раз запустите приложение, в которое вы внесли указанное выше изменение. Теперь сообщения журнала будут иметь формат JSON.</span><span class="sxs-lookup"><span data-stu-id="cea75-139">Run the app again, with the above change, the log message is now formatted as JSON:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> <span data-ttu-id="cea75-140">Форматировщик консоли `Json` по умолчанию записывает каждое сообщение в одну строку.</span><span class="sxs-lookup"><span data-stu-id="cea75-140">The `Json` console formatter, by default, logs each message in a single line.</span></span> <span data-ttu-id="cea75-141">Чтобы сделать вывод более удобным для чтения, при настройке форматировщика задайте для <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="cea75-141">In order to make it more readable while configuring the formatter, set <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> to `true`.</span></span>

## <a name="set-formatter-with-configuration"></a><span data-ttu-id="cea75-142">Настройка форматировщика с помощью конфигурации</span><span class="sxs-lookup"><span data-stu-id="cea75-142">Set formatter with configuration</span></span>

<span data-ttu-id="cea75-143">В предыдущих примерах показано, как зарегистрировать форматировщик программными средствами.</span><span class="sxs-lookup"><span data-stu-id="cea75-143">The previous samples have shown how to register a formatter programmatically.</span></span> <span data-ttu-id="cea75-144">Эту же операцию можно выполнить путем [настройки](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="cea75-144">Alternatively, this can be done with [configuration](configuration.md).</span></span> <span data-ttu-id="cea75-145">Давайте рассмотрим приведенный выше пример исходного кода веб-приложения. Вместо вызова `ConfigureLogging` в файле *program.cs*, можно получить такой же результат изменением файла *appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="cea75-145">Consider the previous web application sample source code, if you update the *appsettings.json* file rather than calling `ConfigureLogging` in the *Program.cs* file, you could get the same outcome.</span></span> <span data-ttu-id="cea75-146">Обновленный `appsettings.json` файл настроит форматировщик следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cea75-146">The updated `appsettings.json` file would configure the formatter as follows:</span></span>

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

<span data-ttu-id="cea75-147">Два основных значения здесь — `"FormatterName"` и `"FormatterOptions"`.</span><span class="sxs-lookup"><span data-stu-id="cea75-147">The two key values that need to be set are `"FormatterName"` and `"FormatterOptions"`.</span></span> <span data-ttu-id="cea75-148">Если форматировщик уже зарегистрирован с тем значением, которое вы задали для `"FormatterName"`, будет выбран уже существующий форматировщик. Кроме того, можно настроить его свойства, если они указаны в качестве ключа внутри узла `"FormatterOptions"`.</span><span class="sxs-lookup"><span data-stu-id="cea75-148">If a formatter with the value set for `"FormatterName"` is already registered, that formatter is selected, and its properties can be configured as long as they are provided as a key inside the `"FormatterOptions"` node.</span></span> <span data-ttu-id="cea75-149">Предопределенные имена модулей форматирования зарезервированы в <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>.</span><span class="sxs-lookup"><span data-stu-id="cea75-149">The predefined formatter names are reserved under <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames>:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a><span data-ttu-id="cea75-150">Реализация пользовательского форматировщика</span><span class="sxs-lookup"><span data-stu-id="cea75-150">Implement a custom formatter</span></span>

<span data-ttu-id="cea75-151">Для реализации пользовательского форматировщика сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="cea75-151">To implement a custom formatter, you need to:</span></span>

- <span data-ttu-id="cea75-152">Создайте подкласс в <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, который представляет пользовательский форматировщик.</span><span class="sxs-lookup"><span data-stu-id="cea75-152">Create a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter>, this represents your custom formatter</span></span>
- <span data-ttu-id="cea75-153">Зарегистрируйте пользовательский форматировщик с помощью:</span><span class="sxs-lookup"><span data-stu-id="cea75-153">Register your custom formatter with</span></span>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

<span data-ttu-id="cea75-154">Создайте метод расширения для решения этой задачи.</span><span class="sxs-lookup"><span data-stu-id="cea75-154">Create an extension method to handle this for you:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

<span data-ttu-id="cea75-155">Для определения `CustomOptions` используется такой код:</span><span class="sxs-lookup"><span data-stu-id="cea75-155">The `CustomOptions` are defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

<span data-ttu-id="cea75-156">В приведенном выше примере кода параметры являются подклассом <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span><span class="sxs-lookup"><span data-stu-id="cea75-156">In the preceding code, the options are a subclass of <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>.</span></span>

<span data-ttu-id="cea75-157">API-интерфейс `AddConsoleFormatter` выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="cea75-157">The `AddConsoleFormatter` API:</span></span>

- <span data-ttu-id="cea75-158">Регистрирует подкласс `ConsoleFormatter`.</span><span class="sxs-lookup"><span data-stu-id="cea75-158">Registers a subclass of `ConsoleFormatter`</span></span>
- <span data-ttu-id="cea75-159">Обрабатывает конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="cea75-159">Handles configuration:</span></span>
  - <span data-ttu-id="cea75-160">Использует маркер изменения для синхронизации обновлений по [шаблону параметров](options.md) с применением интерфейса [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601).</span><span class="sxs-lookup"><span data-stu-id="cea75-160">Uses a change token to synchronize updates, based on the [options pattern](options.md), and the [IOptionsMonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) interface</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

<span data-ttu-id="cea75-161">Определите подкласс `CustomerFormatter` в `ConsoleFormatter`.</span><span class="sxs-lookup"><span data-stu-id="cea75-161">Define a `CustomerFormatter` subclass of `ConsoleFormatter`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

<span data-ttu-id="cea75-162">Приведенный выше API `CustomFormatter.Write<TState>` определяет, какой текст добавляется вокруг каждого сообщения журнала.</span><span class="sxs-lookup"><span data-stu-id="cea75-162">The preceding `CustomFormatter.Write<TState>` API dictates what text gets wrapped around each log message.</span></span> <span data-ttu-id="cea75-163">В стандартной реализации `ConsoleFormatter` должна создаваться оболочка по меньшей мере для областей, меток времени и степени серьезности записи журнала.</span><span class="sxs-lookup"><span data-stu-id="cea75-163">A standard `ConsoleFormatter` should be able to wrap around scopes, time stamps, and severity level of logs at a minimum.</span></span> <span data-ttu-id="cea75-164">Кроме того, в сообщениях журнала можно кодировать цвета ANSI и указывать отступы.</span><span class="sxs-lookup"><span data-stu-id="cea75-164">Additionally, you can encode ANSI colors in the log messages, and provide desired indentations as well.</span></span> <span data-ttu-id="cea75-165">В реализации `CustomFormatter.Write<TState>` таких возможностей нет.</span><span class="sxs-lookup"><span data-stu-id="cea75-165">The implementation of the `CustomFormatter.Write<TState>` lacks these capabilities.</span></span>

<span data-ttu-id="cea75-166">Дополнительные идеи по настройке форматирования вы найдете в примерах реализации для пространства имен `Microsoft.Extensions.Logging.Console`:</span><span class="sxs-lookup"><span data-stu-id="cea75-166">For inspiration on further customizing formatting, see the existing implementations in the `Microsoft.Extensions.Logging.Console` namespace:</span></span>

- <span data-ttu-id="cea75-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs);</span><span class="sxs-lookup"><span data-stu-id="cea75-167">[SimpleConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).</span></span>
- <span data-ttu-id="cea75-168">[SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs);</span><span class="sxs-lookup"><span data-stu-id="cea75-168">[SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)</span></span>
- <span data-ttu-id="cea75-169">[JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs).</span><span class="sxs-lookup"><span data-stu-id="cea75-169">[JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)</span></span>

## <a name="implement-custom-color-formatting"></a><span data-ttu-id="cea75-170">Реализация пользовательского форматирования цвета</span><span class="sxs-lookup"><span data-stu-id="cea75-170">Implement custom color formatting</span></span>

<span data-ttu-id="cea75-171">Чтобы правильно внедрить поддержку цвета в пользовательский форматировщик, расширьте <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions>, у которого уже есть свойство <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>. Оно будет полезным для включения цвета в журналы.</span><span class="sxs-lookup"><span data-stu-id="cea75-171">In order to properly enable color capabilities in your custom logging formatter, you can extend the <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> as it has a <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> property that can be useful for enabling colors in logs.</span></span>

<span data-ttu-id="cea75-172">Создайте `CustomColorOptions`, который наследует от `SimpleConsoleFormatterOptions`.</span><span class="sxs-lookup"><span data-stu-id="cea75-172">Create a `CustomColorOptions` that derives from `SimpleConsoleFormatterOptions`:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

<span data-ttu-id="cea75-173">Теперь создайте несколько методов расширения в классе `TextWriterExtensions`, который позволяет легко внедрять цвета в кодировке ANSI в форматированные сообщения журнала.</span><span class="sxs-lookup"><span data-stu-id="cea75-173">Next, write some extension methods in a `TextWriterExtensions` class that allow for conveniently embedding ANSI coded colors within formatted log messages:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

<span data-ttu-id="cea75-174">Пользовательский форматировщик, который обрабатывает применение пользовательских цветов, можно определить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cea75-174">A custom color formatter that handles applying custom colors could be defined as follows:</span></span>

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

<span data-ttu-id="cea75-175">При запуске приложения в журналах сообщение `CustomPrefix` будет отображаться зеленым цветом, если `FormatterOptions.ColorBehavior` имеет значение `Enabled`.</span><span class="sxs-lookup"><span data-stu-id="cea75-175">When you run the application, the logs will show the `CustomPrefix` message in the color green when `FormatterOptions.ColorBehavior` is `Enabled`.</span></span>

> [!NOTE]
> <span data-ttu-id="cea75-176">Если <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> имеет значение `Disabled`, сообщения журнала _не_ обрабатывают внедренные коды цветов ANSI в сообщениях журнала.</span><span class="sxs-lookup"><span data-stu-id="cea75-176">When <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> is `Disabled`, log messages do _not_ interpret embedded ANSI color codes within log messages.</span></span> <span data-ttu-id="cea75-177">Вместо этого они выводят необработанное сообщение.</span><span class="sxs-lookup"><span data-stu-id="cea75-177">Instead, they output the raw message.</span></span> <span data-ttu-id="cea75-178">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="cea75-178">For example, consider the following:</span></span>
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> <span data-ttu-id="cea75-179">При выполнении этого кода выводится строка в неизменном виде _без_ добавления цветов.</span><span class="sxs-lookup"><span data-stu-id="cea75-179">This would output the verbatim string, and it is _not_ colorized.</span></span>
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a><span data-ttu-id="cea75-180">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cea75-180">See also</span></span>

- [<span data-ttu-id="cea75-181">Ведение журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="cea75-181">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="cea75-182">Реализация пользовательского поставщика ведения журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="cea75-182">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="cea75-183">Ведение журнала с высокой производительностью в .NET</span><span class="sxs-lookup"><span data-stu-id="cea75-183">High-performance logging in .NET</span></span>](high-performance-logging.md)
