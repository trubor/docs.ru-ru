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
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="65994-103">Реализация пользовательского поставщика ведения журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="65994-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="65994-104">Существует множество [поставщиков ведения журнала](logging-providers.md), доступных для общих задач ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="65994-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="65994-105">Вам может потребоваться реализовать свой объект <xref:Microsoft.Extensions.Logging.ILoggerProvider>, если ни один из доступных поставщиков не соответствует потребностям вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="65994-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="65994-106">Из этой статьи вы узнаете, как реализовать настраиваемый поставщик ведения журнала, который можно использовать для выделения цветом журналов в консоли.</span><span class="sxs-lookup"><span data-stu-id="65994-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="65994-107">Пример конфигурации пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="65994-107">Sample custom logger configuration</span></span>

<span data-ttu-id="65994-108">В этом примере создаются записи консоли разного цвета в соответствии с уровнем ведения журнала и идентификатором события с использованием следующего типа конфигурации:</span><span class="sxs-lookup"><span data-stu-id="65994-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="65994-109">Приведенный выше код задает уровень по умолчанию `Information` и цвет `Green`, а `EventId` неявно равен `0`.</span><span class="sxs-lookup"><span data-stu-id="65994-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="65994-110">Создание пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="65994-110">Create the custom logger</span></span>

<span data-ttu-id="65994-111">В качестве имени категории реализации `ILogger`, как правило, используется источник журнала.</span><span class="sxs-lookup"><span data-stu-id="65994-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="65994-112">Например, тип, в котором создается средство ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="65994-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="65994-113">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="65994-113">The preceding code:</span></span>

- <span data-ttu-id="65994-114">создает экземпляр средства ведения журнала по имени категории;</span><span class="sxs-lookup"><span data-stu-id="65994-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="65994-115">проверяет `logLevel == _config.LogLevel` в `IsEnabled`, благодаря чему каждому `logLevel` соответствует уникальное средство ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="65994-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="65994-116">Средства ведения журнала также должны быть включены для всех более высоких уровней ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="65994-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="65994-117">Пользовательский поставщик ведения журнала</span><span class="sxs-lookup"><span data-stu-id="65994-117">Custom logger provider</span></span>

<span data-ttu-id="65994-118">Объект `ILoggerProvider` отвечает за создание экземпляров средства ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="65994-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="65994-119">Возможно, создавать экземпляры средства ведения журнала для каждой категории не требуется, однако это может быть полезно для некоторых таких средств, например NLog или log4net.</span><span class="sxs-lookup"><span data-stu-id="65994-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="65994-120">Таким образом, при необходимости вы можете выбрать разные целевые объекты вывода журнала для каждой категории:</span><span class="sxs-lookup"><span data-stu-id="65994-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="65994-121">В приведенном выше коде <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> создает один экземпляр `ColorConsoleLogger` для каждого имени категории и сохраняет его в [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span><span class="sxs-lookup"><span data-stu-id="65994-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="65994-122">Использование и регистрация пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="65994-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="65994-123">Чтобы добавить пользовательского поставщика ведения журнала и соответствующее средство ведения журнала, добавьте <xref:Microsoft.Extensions.Logging.ILoggerProvider> с помощью <xref:Microsoft.Extensions.Logging.ILoggingBuilder> из <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="65994-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="65994-124">`ILoggingBuilder` создает один или несколько экземпляров `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="65994-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="65994-125">Экземпляры `ILogger` используются платформой для записи данных в журнал.</span><span class="sxs-lookup"><span data-stu-id="65994-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="65994-126">В приведенном выше коде необходимо указать по крайней мере один метод расширения для `ILoggerFactory`:</span><span class="sxs-lookup"><span data-stu-id="65994-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="65994-127">Выполнение этого простого приложения будет отображено в консоли примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="65994-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="Пример вывода цветного журнала в консоль":::

## <a name="see-also"></a><span data-ttu-id="65994-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="65994-129">See also</span></span>

- <span data-ttu-id="65994-130">[Ведение журнала в .NET](logging.md).</span><span class="sxs-lookup"><span data-stu-id="65994-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="65994-131">[Поставщики ведения журнала в NET](logging-providers.md).</span><span class="sxs-lookup"><span data-stu-id="65994-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="65994-132">[Ведение журнала с высокой производительностью в .NET](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="65994-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
