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
# <a name="options-pattern-in-net"></a><span data-ttu-id="0ea46-103">Шаблон параметров в .NET</span><span class="sxs-lookup"><span data-stu-id="0ea46-103">Options pattern in .NET</span></span>

<span data-ttu-id="0ea46-104">Шаблон параметров использует классы для обеспечения строго типизированного доступа к группам связанных параметров.</span><span class="sxs-lookup"><span data-stu-id="0ea46-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="0ea46-105">Когда [параметры конфигурации](configuration.md) изолируются по сценарию в отдельных классах, в приложениях соблюдаются два важных принципа программной инженерии.</span><span class="sxs-lookup"><span data-stu-id="0ea46-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="0ea46-106">[Принцип разделения интерфейса (ISP) или инкапсуляция.](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation) Сценарии (классы), которые зависят от параметров конфигурации, зависят только от используемых ими параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0ea46-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="0ea46-107">[Разделение областей ответственности](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns). Параметры для разных частей приложения не зависят друг от друга и не связаны друг с другом.</span><span class="sxs-lookup"><span data-stu-id="0ea46-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="0ea46-108">В параметрах также предусмотрен механизм для проверки данных конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0ea46-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="0ea46-109">Дополнительные сведения см. в разделе [Проверка параметров](#options-validation).</span><span class="sxs-lookup"><span data-stu-id="0ea46-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="0ea46-110">Привязка иерархической конфигурации</span><span class="sxs-lookup"><span data-stu-id="0ea46-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="0ea46-111">Предпочтительный способ чтения связанных значений конфигурации — использование шаблона параметров.</span><span class="sxs-lookup"><span data-stu-id="0ea46-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="0ea46-112">Шаблон параметров можно реализовать через интерфейс <xref:Microsoft.Extensions.Options.IOptions%601>, где параметр `TOptions` универсального типа ограничен атрибутом `class`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-112">The options pattern is possible through the <xref:Microsoft.Extensions.Options.IOptions%601> interface, where the generic type parameter `TOptions` is constrained to `class`.</span></span> <span data-ttu-id="0ea46-113">Позднее можно предоставить `IOptions<TOptions>` через внедрение зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0ea46-113">The `IOptions<TOptions>` can later be provided through dependency injection.</span></span> <span data-ttu-id="0ea46-114">Дополнительные сведения см. в статье [Внедрение зависимостей в .NET](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="0ea46-114">For more information, see [Dependency injection in .NET](dependency-injection.md).</span></span>

<span data-ttu-id="0ea46-115">Например, чтобы считать следующие значения конфигурации:</span><span class="sxs-lookup"><span data-stu-id="0ea46-115">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="0ea46-116">Создайте следующий класс `TransientFaultHandlingOptions`:</span><span class="sxs-lookup"><span data-stu-id="0ea46-116">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span data-ttu-id="0ea46-117"><span id="options-class"></span> При использовании шаблона параметров класс параметров должен иметь следующие характеристики:</span><span class="sxs-lookup"><span data-stu-id="0ea46-117"><span id="options-class"></span> When using the options pattern, an options class:</span></span>

- <span data-ttu-id="0ea46-118">Являться неабстрактным с открытым конструктором без параметров.</span><span class="sxs-lookup"><span data-stu-id="0ea46-118">Must be non-abstract with a public parameterless constructor</span></span>
- <span data-ttu-id="0ea46-119">Содержать открытые свойства для чтения и записи для привязки (поля ***не*** привязываются).</span><span class="sxs-lookup"><span data-stu-id="0ea46-119">Contain public read-write properties to bind (fields are ***not*** bound)</span></span>

<span data-ttu-id="0ea46-120">В приведенном ниже коде</span><span class="sxs-lookup"><span data-stu-id="0ea46-120">The following code:</span></span>

* <span data-ttu-id="0ea46-121">Вызывает [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) для привязки класса `TransientFaultHandlingOptions` к разделу `"TransientFaultHandlingOptions"`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-121">Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="0ea46-122">Отображает данные конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0ea46-122">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="0ea46-123">В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.</span><span class="sxs-lookup"><span data-stu-id="0ea46-123">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="0ea46-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) привязывает и возвращает указанный тип.</span><span class="sxs-lookup"><span data-stu-id="0ea46-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="0ea46-125">Метод `ConfigurationBinder.Get<T>` может быть более удобным, чем `ConfigurationBinder.Bind`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-125">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="0ea46-126">В приведенном ниже примере кода демонстрируются способы использования `ConfigurationBinder.Get<T>` с классом `TransientFaultHandlingOptions`:</span><span class="sxs-lookup"><span data-stu-id="0ea46-126">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="0ea46-127">В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.</span><span class="sxs-lookup"><span data-stu-id="0ea46-127">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ea46-128">Класс <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> предоставляет несколько интерфейсов API, например `.Bind(object instance)` и `.Get<T>()`, которые ***не*** ограничены атрибутом `class`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-128">The <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> class exposes several APIs, such as `.Bind(object instance)` and `.Get<T>()` that are ***not*** constrained to `class`.</span></span> <span data-ttu-id="0ea46-129">При использовании любого из [интерфейсов параметров](#options-interfaces) необходимо соблюдать вышеупомянутые [ограничения для класса параметров](#options-class).</span><span class="sxs-lookup"><span data-stu-id="0ea46-129">When using any of the [Options interfaces](#options-interfaces), you must adhere to aforementioned [options class constraints](#options-class).</span></span>

<span data-ttu-id="0ea46-130">Альтернативный подход при использовании шаблона параметров — привязать раздел `"TransientFaultHandlingOptions"` и добавить его в [контейнер службы внедрения зависимостей](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="0ea46-130">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="0ea46-131">В следующем коде `TransientFaultHandlingOptions` добавляется в контейнер службы с помощью интерфейса <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> и привязывается к конфигурации:</span><span class="sxs-lookup"><span data-stu-id="0ea46-131">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="0ea46-132">Параметр `key` содержит имя раздела конфигурации для поиска.</span><span class="sxs-lookup"><span data-stu-id="0ea46-132">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="0ea46-133">Это значение *не обязано* совпадать с именем типа, который его представляет.</span><span class="sxs-lookup"><span data-stu-id="0ea46-133">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="0ea46-134">Например, у вас может существовать раздел с именем `"FaultHandling"`, представленный классом `TransientFaultHandlingOptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-134">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="0ea46-135">В этом случае вы будете передавать `"FaultHandling"` в функцию <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-135">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="0ea46-136">Оператор `nameof` используется для удобства, когда имя именованного раздела совпадает с типом, которому он соответствует.</span><span class="sxs-lookup"><span data-stu-id="0ea46-136">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="0ea46-137">С помощью приведенного выше кода следующий код считывает параметры расположения:</span><span class="sxs-lookup"><span data-stu-id="0ea46-137">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="0ea46-138">В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, ***не*** считываются.</span><span class="sxs-lookup"><span data-stu-id="0ea46-138">In the preceding code, changes to the JSON configuration file after the app has started are ***not*** read.</span></span> <span data-ttu-id="0ea46-139">Чтобы считать изменения после запуска приложения, используйте [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="0ea46-139">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="0ea46-140">Интерфейсы параметров</span><span class="sxs-lookup"><span data-stu-id="0ea46-140">Options interfaces</span></span>

<span data-ttu-id="0ea46-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="0ea46-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="0ea46-142">***Не*** поддерживает:</span><span class="sxs-lookup"><span data-stu-id="0ea46-142">Does ***not*** support:</span></span>
  - <span data-ttu-id="0ea46-143">чтение данных конфигурации после запуска приложения;</span><span class="sxs-lookup"><span data-stu-id="0ea46-143">Reading of configuration data after the app has started.</span></span>
  - <span data-ttu-id="0ea46-144">[именованные параметры](#named-options-support-using-iconfigurenamedoptions);</span><span class="sxs-lookup"><span data-stu-id="0ea46-144">[Named options](#named-options-support-using-iconfigurenamedoptions)</span></span>
- <span data-ttu-id="0ea46-145">Регистрируется в качестве элемента [singleton](dependency-injection.md#singleton) и может быть внедрен в любое [время существования службы](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="0ea46-145">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="0ea46-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="0ea46-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="0ea46-147">Полезен в сценариях, где параметры должны вычисляться заново при каждом разрешении внедрения, для [временных или ограниченных областью](dependency-injection.md#service-lifetimes) зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0ea46-147">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="0ea46-148">Дополнительные сведения см. в разделе [Использование IOptionsSnapshot для чтения обновленных данных](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="0ea46-148">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="0ea46-149">Регистрируется как [Scoped](dependency-injection.md#scoped) (с областью), поэтому его нельзя внедрить в службу singleton.</span><span class="sxs-lookup"><span data-stu-id="0ea46-149">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="0ea46-150">Поддерживает [именованные параметры](#named-options-support-using-iconfigurenamedoptions).</span><span class="sxs-lookup"><span data-stu-id="0ea46-150">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="0ea46-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="0ea46-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="0ea46-152">Используется для извлечения параметров и управления уведомлениями о параметрах для экземпляров `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-152">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="0ea46-153">Регистрируется в качестве элемента [singleton](dependency-injection.md#singleton) и может быть внедрен в любое [время существования службы](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="0ea46-153">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="0ea46-154">Поддерживаются следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="0ea46-154">Supports:</span></span>
  - <span data-ttu-id="0ea46-155">уведомления об изменениях;</span><span class="sxs-lookup"><span data-stu-id="0ea46-155">Change notifications</span></span>
  - <span data-ttu-id="0ea46-156">[именованные параметры](#named-options-support-using-iconfigurenamedoptions);</span><span class="sxs-lookup"><span data-stu-id="0ea46-156">[Named options](#named-options-support-using-iconfigurenamedoptions)</span></span>
  - <span data-ttu-id="0ea46-157">[перезагружаемые конфигурации](#use-ioptionssnapshot-to-read-updated-data);</span><span class="sxs-lookup"><span data-stu-id="0ea46-157">[Reloadable configuration](#use-ioptionssnapshot-to-read-updated-data)</span></span>
  - <span data-ttu-id="0ea46-158">объявление определенных параметров недействительными (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>).</span><span class="sxs-lookup"><span data-stu-id="0ea46-158">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>

<span data-ttu-id="0ea46-159">Интерфейс <xref:Microsoft.Extensions.Options.IOptionsFactory%601> отвечает за создание экземпляров параметров.</span><span class="sxs-lookup"><span data-stu-id="0ea46-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="0ea46-160">Он имеет единственный метод <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-160">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="0ea46-161">При реализации по умолчанию принимаются все зарегистрированные интерфейсы <xref:Microsoft.Extensions.Options.IConfigureOptions%601> и <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>. Также сначала выполняются все основные настройки, а затем действия после конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0ea46-161">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="0ea46-162">Она различает интерфейсы <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> и <xref:Microsoft.Extensions.Options.IConfigureOptions%601> и вызывает только соответствующий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0ea46-162">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="0ea46-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> используется интерфейсом <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> для записи экземпляров `TOptions` в кэш.</span><span class="sxs-lookup"><span data-stu-id="0ea46-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="0ea46-164"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> делает экземпляры параметров в мониторе недействительными, что приводит к повторному вычислению значений (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span><span class="sxs-lookup"><span data-stu-id="0ea46-164">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="0ea46-165">Значения можно также вводить вручную с помощью <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-165">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="0ea46-166">Метод <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> используется, если необходимо повторно создать все именованные экземпляры по требованию.</span><span class="sxs-lookup"><span data-stu-id="0ea46-166">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

### <a name="options-interfaces-benefits"></a><span data-ttu-id="0ea46-167">Преимущества интерфейсов параметров</span><span class="sxs-lookup"><span data-stu-id="0ea46-167">Options interfaces benefits</span></span>

<span data-ttu-id="0ea46-168">Использование универсального типа оболочки позволяет отвязать время существования параметра от контейнера внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0ea46-168">Using a generic wrapper type gives you the ability to decouple the lifetime of the option from the DI container.</span></span> <span data-ttu-id="0ea46-169">Интерфейс <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> предоставляет уровень абстракции для типа параметров, включая универсальные ограничения.</span><span class="sxs-lookup"><span data-stu-id="0ea46-169">The <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> interface provides a layer of abstraction, including generic constraints, on your options type.</span></span> <span data-ttu-id="0ea46-170">Это обеспечивает следующие преимущества.</span><span class="sxs-lookup"><span data-stu-id="0ea46-170">This provides the following benefits:</span></span>

- <span data-ttu-id="0ea46-171">Вычисление экземпляра конфигурации `T` выполняется только при доступе к <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>, а не при его внедрении.</span><span class="sxs-lookup"><span data-stu-id="0ea46-171">The evaluation of the `T` configuration instance is deferred to the accessing of <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>, rather than when it is injected.</span></span> <span data-ttu-id="0ea46-172">Это важно, так как вы можете использовать параметр `T` из разных мест и выбирать семантику времени существования, не изменяя данные о `T`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-172">This is important because you can consume the `T` option from various places and choose the lifetime semantics without changing anything about `T`.</span></span>
- <span data-ttu-id="0ea46-173">При регистрации параметров с типом `T` вам не придется явно регистрировать тип `T`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-173">When registering options of type `T`, you do not need to explicitly register the `T` type.</span></span> <span data-ttu-id="0ea46-174">Это очень удобно при [создании библиотеки](options-library-authors.md) с простыми параметрами по умолчанию, если вы не хотите вынуждать вызывающую сторону регистрировать параметры в контейнере внедрения зависимостей с конкретным временем существования.</span><span class="sxs-lookup"><span data-stu-id="0ea46-174">This is a convenience when you're [authoring a library](options-library-authors.md) with simple defaults, and you don't want to force the caller to register options into the DI container with a specific lifetime.</span></span>
- <span data-ttu-id="0ea46-175">С точки зрения API это позволяет создавать ограничения типа `T` (в нашем примере параметр `T` ограничен ссылочным типом).</span><span class="sxs-lookup"><span data-stu-id="0ea46-175">From the perspective of the API, it allows for constraints on the type `T` (in this case, `T` is constrained to a reference type).</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="0ea46-176">Использование IOptionsSnapshot для чтения обновленных данных</span><span class="sxs-lookup"><span data-stu-id="0ea46-176">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="0ea46-177">При использовании <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> параметры вычисляются один раз на каждый запрос при обращении к ним и кэшируются на все время существования запроса.</span><span class="sxs-lookup"><span data-stu-id="0ea46-177">When you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="0ea46-178">Изменения конфигурации считываются после запуска приложения при использовании поставщиков конфигурации, поддерживающих чтение обновленных значений конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0ea46-178">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="0ea46-179">Разница между `IOptionsMonitor` и `IOptionsSnapshot`:</span><span class="sxs-lookup"><span data-stu-id="0ea46-179">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="0ea46-180">`IOptionsMonitor` — это [одноэлементная служба](dependency-injection.md#singleton), которая получает текущие значения параметров в любое время, что особенно полезно в одноэлементных зависимостях.</span><span class="sxs-lookup"><span data-stu-id="0ea46-180">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="0ea46-181">`IOptionsSnapshot` — это [служба с заданной областью действия](dependency-injection.md#scoped), предоставляющая моментальный снимок параметров на момент создания объекта `IOptionsSnapshot<T>`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-181">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="0ea46-182">Моментальные снимки параметров предназначены для использования с временными зависимостями и зависимостями с заданной областью действия.</span><span class="sxs-lookup"><span data-stu-id="0ea46-182">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="0ea46-183">В приведенном ниже коде используется <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-183">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="0ea46-184">Следующий код регистрирует экземпляр конфигурации, к которому привязывается `TransientFaultHandlingOptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-184">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="0ea46-185">В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.</span><span class="sxs-lookup"><span data-stu-id="0ea46-185">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="0ea46-186">IOptionsMonitor</span><span class="sxs-lookup"><span data-stu-id="0ea46-186">IOptionsMonitor</span></span>

<span data-ttu-id="0ea46-187">Следующий код регистрирует экземпляр конфигурации, к которому привязывается `TransientFaultHandlingOptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-187">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="0ea46-188">В следующем примере используется <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-188">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="0ea46-189">В приведенном выше коде изменения в файле конфигурации JSON, внесенные после запуска приложения, считываются.</span><span class="sxs-lookup"><span data-stu-id="0ea46-189">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="0ea46-190">Поддержка именованных параметров с использованием IConfigureNamedOptions</span><span class="sxs-lookup"><span data-stu-id="0ea46-190">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="0ea46-191">Именованные параметры:</span><span class="sxs-lookup"><span data-stu-id="0ea46-191">Named options:</span></span>

- <span data-ttu-id="0ea46-192">полезны, если несколько разделов конфигурации привязываются к одним и тем же свойствам;</span><span class="sxs-lookup"><span data-stu-id="0ea46-192">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="0ea46-193">используются с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="0ea46-193">Are case-sensitive.</span></span>

<span data-ttu-id="0ea46-194">Рассмотрите следующий файл *appsettings.json*:</span><span class="sxs-lookup"><span data-stu-id="0ea46-194">Consider the following *appsettings.json* file:</span></span>

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

<span data-ttu-id="0ea46-195">Вместо создания двух классов для привязки `Features:Personalize` и `Features:WeatherStation` для каждого раздела используется следующий класс:</span><span class="sxs-lookup"><span data-stu-id="0ea46-195">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="0ea46-196">Следующий код служит для настройки именованных параметров:</span><span class="sxs-lookup"><span data-stu-id="0ea46-196">The following code configures the named options:</span></span>

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

<span data-ttu-id="0ea46-197">Следующий код отображает именованные параметры:</span><span class="sxs-lookup"><span data-stu-id="0ea46-197">The following code displays the named options:</span></span>

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

<span data-ttu-id="0ea46-198">Все параметры являются именованными экземплярами.</span><span class="sxs-lookup"><span data-stu-id="0ea46-198">All options are named instances.</span></span> <span data-ttu-id="0ea46-199">Экземпляры <xref:Microsoft.Extensions.Options.IConfigureOptions%601> считаются нацеленными на экземпляр `Options.DefaultName`, который имеет значение `string.Empty`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-199"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="0ea46-200">Интерфейс <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> также реализует интерфейс <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-200"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="0ea46-201">Реализация <xref:Microsoft.Extensions.Options.IOptionsFactory%601> по умолчанию содержит логику для надлежащего использования каждого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="0ea46-201">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="0ea46-202">Именованный параметр `null` предназначен для всех именованных экземпляров, а не для какого-то определенного.</span><span class="sxs-lookup"><span data-stu-id="0ea46-202">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="0ea46-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> и <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> следуют этому соглашению.</span><span class="sxs-lookup"><span data-stu-id="0ea46-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="0ea46-204">API OptionsBuilder</span><span class="sxs-lookup"><span data-stu-id="0ea46-204">OptionsBuilder API</span></span>

<span data-ttu-id="0ea46-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> используется для настройки экземпляров `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="0ea46-206">`OptionsBuilder` упрощает создание именованных параметров, так как он является единственным параметром для первоначального вызова `AddOptions<TOptions>(string optionsName)` и не должен появляться во всех последующих вызовах.</span><span class="sxs-lookup"><span data-stu-id="0ea46-206">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="0ea46-207">Проверка параметров и перегрузки `ConfigureOptions`, принимающие зависимости службы, доступны только через `OptionsBuilder`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-207">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="0ea46-208">`OptionsBuilder` используется в разделе [Проверка параметров](#options-validation).</span><span class="sxs-lookup"><span data-stu-id="0ea46-208">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="0ea46-209">Использование служб внедрения зависимостей для настройки параметров</span><span class="sxs-lookup"><span data-stu-id="0ea46-209">Use DI services to configure options</span></span>

<span data-ttu-id="0ea46-210">Использовать службы, доступные в результате внедрения зависимостей при настройке параметров, можно двумя способами.</span><span class="sxs-lookup"><span data-stu-id="0ea46-210">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="0ea46-211">Передайте делегат конфигурации методу [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) в [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span><span class="sxs-lookup"><span data-stu-id="0ea46-211">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="0ea46-212">`OptionsBuilder<TOptions>` предоставляет перегрузки метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), которые позволяют использовать до пяти служб для настройки параметров:</span><span class="sxs-lookup"><span data-stu-id="0ea46-212">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="0ea46-213">Создайте тип, реализующий <xref:Microsoft.Extensions.Options.IConfigureOptions%601> или <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, и зарегистрируйте этот тип как службу.</span><span class="sxs-lookup"><span data-stu-id="0ea46-213">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="0ea46-214">Рекомендуем передать делегат конфигурации методу [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), так как создать службу сложнее.</span><span class="sxs-lookup"><span data-stu-id="0ea46-214">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="0ea46-215">Создание типа эквивалентно тому, что делает платформа при вызове метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span><span class="sxs-lookup"><span data-stu-id="0ea46-215">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="0ea46-216">При вызове метода [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) регистрируется временный универсальный интерфейс <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, имеющий конструктор, который принимает указанные универсальные типы службы.</span><span class="sxs-lookup"><span data-stu-id="0ea46-216">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="0ea46-217">Проверка параметров</span><span class="sxs-lookup"><span data-stu-id="0ea46-217">Options validation</span></span>

<span data-ttu-id="0ea46-218">Проверка параметров позволяет проверять значения параметров.</span><span class="sxs-lookup"><span data-stu-id="0ea46-218">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="0ea46-219">Рассмотрите следующий файл *appsettings.json*:</span><span class="sxs-lookup"><span data-stu-id="0ea46-219">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="0ea46-220">Следующий класс привязывается к разделу конфигурации `"Settings"` и применяет несколько правил `DataAnnotations`:</span><span class="sxs-lookup"><span data-stu-id="0ea46-220">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="0ea46-221">В приведенном ниже коде</span><span class="sxs-lookup"><span data-stu-id="0ea46-221">The following code:</span></span>

- <span data-ttu-id="0ea46-222">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A>, чтобы получить класс [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601), который привязывается к классу `SettingsOptions`;</span><span class="sxs-lookup"><span data-stu-id="0ea46-222">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="0ea46-223">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> для включения проверки с помощью `DataAnnotations`.</span><span class="sxs-lookup"><span data-stu-id="0ea46-223">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="0ea46-224">Метод расширения `ValidateDataAnnotations` определен в пакете NuGet [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations).</span><span class="sxs-lookup"><span data-stu-id="0ea46-224">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="0ea46-225">Следующий код отображает значения конфигурации или ошибки проверки:</span><span class="sxs-lookup"><span data-stu-id="0ea46-225">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="0ea46-226">Следующий код применяет более сложное правило проверки с использованием делегата:</span><span class="sxs-lookup"><span data-stu-id="0ea46-226">The following code applies a more complex validation rule using a delegate:</span></span>

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

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="0ea46-227">IValidateOptions для сложной проверки</span><span class="sxs-lookup"><span data-stu-id="0ea46-227">IValidateOptions for complex validation</span></span>

<span data-ttu-id="0ea46-228">Следующий класс реализует <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="0ea46-228">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="0ea46-229">`IValidateOptions` позволяет переместить код проверки в класс.</span><span class="sxs-lookup"><span data-stu-id="0ea46-229">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="0ea46-230">С использованием приведенного выше кода проверка включается в `ConfigureServices` с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="0ea46-230">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="0ea46-231">Пост-конфигурация параметров</span><span class="sxs-lookup"><span data-stu-id="0ea46-231">Options post-configuration</span></span>

<span data-ttu-id="0ea46-232">Задайте пост-конфигурацию с помощью <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-232">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="0ea46-233">Процессы после завершения настройки выполняются после всех конфигураций <xref:Microsoft.Extensions.Options.IConfigureOptions%601>. Это может быть полезно в сценариях, когда требуется переопределять конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="0ea46-233">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="0ea46-234">Для последующей настройки именованных параметров доступен метод <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-234"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="0ea46-235">Для последующей настройки всех экземпляров конфигурации служит метод <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ea46-235">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="0ea46-236">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ea46-236">See also</span></span>

- [<span data-ttu-id="0ea46-237">Конфигурация в .NET</span><span class="sxs-lookup"><span data-stu-id="0ea46-237">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="0ea46-238">Руководство по шаблону параметров для авторов библиотек .NET</span><span class="sxs-lookup"><span data-stu-id="0ea46-238">Options pattern guidance for .NET library authors</span></span>](options-library-authors.md)
