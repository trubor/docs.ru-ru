---
title: Реализация пользовательского поставщика ведения журнала в .NET
description: Узнайте, как реализовать пользовательского поставщика ведения журнала в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2020
ms.locfileid: "102402073"
---
# <a name="implement-a-custom-logging-provider-in-net"></a>Реализация пользовательского поставщика ведения журнала в .NET

Существует множество [поставщиков ведения журнала](logging-providers.md), доступных для общих задач ведения журнала. Вам может потребоваться реализовать свой объект <xref:Microsoft.Extensions.Logging.ILoggerProvider>, если ни один из доступных поставщиков не соответствует потребностям вашего приложения. Из этой статьи вы узнаете, как реализовать настраиваемый поставщик ведения журнала, который можно использовать для выделения цветом журналов в консоли.

### <a name="sample-custom-logger-configuration"></a>Пример конфигурации пользовательского средства ведения журнала

В этом примере создаются записи консоли разного цвета в соответствии с уровнем ведения журнала и идентификатором события с использованием следующего типа конфигурации:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

Приведенный выше код задает уровень по умолчанию `Information` и цвет `Green`, а `EventId` неявно равен `0`.

### <a name="create-the-custom-logger"></a>Создание пользовательского средства ведения журнала

В качестве имени категории реализации `ILogger`, как правило, используется источник журнала. Например, тип, в котором создается средство ведения журнала:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

Предыдущий код:

- создает экземпляр средства ведения журнала по имени категории;
- проверяет `logLevel == _config.LogLevel` в `IsEnabled`, благодаря чему каждому `logLevel` соответствует уникальное средство ведения журнала. Средства ведения журнала также должны быть включены для всех более высоких уровней ведения журнала:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>Пользовательский поставщик ведения журнала

Объект `ILoggerProvider` отвечает за создание экземпляров средства ведения журналов. Возможно, создавать экземпляры средства ведения журнала для каждой категории не требуется, однако это может быть полезно для некоторых таких средств, например NLog или log4net. Таким образом, при необходимости вы можете выбрать разные целевые объекты вывода журнала для каждой категории:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

В приведенном выше коде <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> создает один экземпляр `ColorConsoleLogger` для каждого имени категории и сохраняет его в [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).

## <a name="usage-and-registration-of-the-custom-logger"></a>Использование и регистрация пользовательского средства ведения журнала

Чтобы добавить пользовательского поставщика ведения журнала и соответствующее средство ведения журнала, добавьте <xref:Microsoft.Extensions.Logging.ILoggerProvider> с помощью <xref:Microsoft.Extensions.Logging.ILoggingBuilder> из <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

`ILoggingBuilder` создает один или несколько экземпляров `ILogger`. Экземпляры `ILogger` используются платформой для записи данных в журнал.

В приведенном выше коде необходимо указать по крайней мере один метод расширения для `ILoggerFactory`:

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

Выполнение этого простого приложения будет отображено в консоли примерно следующим образом:

:::image type="content" source="media/color-console-logger.png" alt-text="Пример вывода цветного журнала в консоль":::

## <a name="see-also"></a>См. также раздел

- [Ведение журнала в .NET](logging.md).
- [Поставщики ведения журнала в NET](logging-providers.md).
- [Ведение журнала с высокой производительностью в .NET](high-performance-logging.md).
