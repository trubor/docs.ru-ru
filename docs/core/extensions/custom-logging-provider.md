---
title: Реализация пользовательского поставщика ведения журнала в .NET
description: Узнайте, как реализовать пользовательского поставщика ведения журнала в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 04/07/2021
ms.topic: how-to
ms.openlocfilehash: 56dd3aa9962d2cdaf13df85960a99aab7b050477
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255133"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="be4bd-103">Реализация пользовательского поставщика ведения журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="be4bd-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="be4bd-104">Существует множество [поставщиков ведения журнала](logging-providers.md), доступных для общих задач ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="be4bd-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="be4bd-105">Вам может потребоваться реализовать свой объект <xref:Microsoft.Extensions.Logging.ILoggerProvider>, если ни один из доступных поставщиков не соответствует потребностям вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="be4bd-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="be4bd-106">Из этой статьи вы узнаете, как реализовать настраиваемый поставщик ведения журнала, который можно использовать для выделения цветом журналов в консоли.</span><span class="sxs-lookup"><span data-stu-id="be4bd-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="be4bd-107">Пример конфигурации пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="be4bd-107">Sample custom logger configuration</span></span>

<span data-ttu-id="be4bd-108">В этом примере создаются записи консоли разного цвета в соответствии с уровнем ведения журнала и идентификатором события с использованием следующего типа конфигурации:</span><span class="sxs-lookup"><span data-stu-id="be4bd-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="be4bd-109">Приведенный выше код задает уровень по умолчанию `Information` и цвет `Green`, а `EventId` неявно равен `0`.</span><span class="sxs-lookup"><span data-stu-id="be4bd-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="be4bd-110">Создание пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="be4bd-110">Create the custom logger</span></span>

<span data-ttu-id="be4bd-111">В качестве имени категории реализации `ILogger`, как правило, используется источник журнала.</span><span class="sxs-lookup"><span data-stu-id="be4bd-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="be4bd-112">Например, тип, в котором создается средство ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="be4bd-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="be4bd-113">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="be4bd-113">The preceding code:</span></span>

- <span data-ttu-id="be4bd-114">создает экземпляр средства ведения журнала по имени категории;</span><span class="sxs-lookup"><span data-stu-id="be4bd-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="be4bd-115">проверяет `_config.LogLevels.ContainsKey(logLevel)` в `IsEnabled`, благодаря чему каждому `logLevel` соответствует уникальное средство ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="be4bd-115">Checks `_config.LogLevels.ContainsKey(logLevel)` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="be4bd-116">Средства ведения журнала также должны быть включены для всех более высоких уровней ведения журнала:</span><span class="sxs-lookup"><span data-stu-id="be4bd-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="be4bd-117">Пользовательский поставщик ведения журнала</span><span class="sxs-lookup"><span data-stu-id="be4bd-117">Custom logger provider</span></span>

<span data-ttu-id="be4bd-118">Объект `ILoggerProvider` отвечает за создание экземпляров средства ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="be4bd-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="be4bd-119">Возможно, создавать экземпляры средства ведения журнала для каждой категории не требуется, однако это может быть полезно для некоторых таких средств, например NLog или log4net.</span><span class="sxs-lookup"><span data-stu-id="be4bd-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="be4bd-120">Таким образом, при необходимости вы можете выбрать разные целевые объекты вывода журнала для каждой категории:</span><span class="sxs-lookup"><span data-stu-id="be4bd-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="be4bd-121">В приведенном выше коде <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> создает один экземпляр `ColorConsoleLogger` для каждого имени категории и сохраняет его в [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span><span class="sxs-lookup"><span data-stu-id="be4bd-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span> <span data-ttu-id="be4bd-122">Кроме того, интерфейс <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> требуется для обновления изменений в базовом объекте `ColorConsoleLoggerConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="be4bd-122">Additionally, the <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> interface is required to update changes to the underlying `ColorConsoleLoggerConfiguration` object.</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="be4bd-123">Использование и регистрация пользовательского средства ведения журнала</span><span class="sxs-lookup"><span data-stu-id="be4bd-123">Usage and registration of the custom logger</span></span>

<span data-ttu-id="be4bd-124">Чтобы добавить пользовательского поставщика ведения журнала и соответствующее средство ведения журнала, добавьте <xref:Microsoft.Extensions.Logging.ILoggerProvider> с помощью <xref:Microsoft.Extensions.Logging.ILoggingBuilder> из <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="be4bd-124">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-33":::

<span data-ttu-id="be4bd-125">`ILoggingBuilder` создает один или несколько экземпляров `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="be4bd-125">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="be4bd-126">Экземпляры `ILogger` используются платформой для записи данных в журнал.</span><span class="sxs-lookup"><span data-stu-id="be4bd-126">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="be4bd-127">По соглашению методы расширения в `ILoggingBuilder` используются для регистрации настраиваемого поставщика:</span><span class="sxs-lookup"><span data-stu-id="be4bd-127">By convention, extension methods on `ILoggingBuilder` are used to register the custom provider:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="be4bd-128">При запуске этого простого приложения в окне консоли будет выведен цветной текст, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="be4bd-128">Running this simple application will render color output to the console window similar to the following image:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="Пример вывода цветного журнала в консоль":::

## <a name="see-also"></a><span data-ttu-id="be4bd-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="be4bd-130">See also</span></span>

- [<span data-ttu-id="be4bd-131">Ведение журнала в .NET</span><span class="sxs-lookup"><span data-stu-id="be4bd-131">Logging in .NET</span></span>](logging.md)
- [<span data-ttu-id="be4bd-132">Поставщики ведения журнала в NET</span><span class="sxs-lookup"><span data-stu-id="be4bd-132">Logging providers in .NET</span></span>](logging-providers.md)
- [<span data-ttu-id="be4bd-133">Внедрение зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="be4bd-133">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="be4bd-134">Ведение журнала с высокой производительностью в .NET</span><span class="sxs-lookup"><span data-stu-id="be4bd-134">High-performance logging in .NET</span></span>](high-performance-logging.md)
