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
# <a name="options-pattern-guidance-for-net-library-authors"></a><span data-ttu-id="a8c85-103">Руководство по шаблону параметров для авторов библиотек .NET</span><span class="sxs-lookup"><span data-stu-id="a8c85-103">Options pattern guidance for .NET library authors</span></span>

<span data-ttu-id="a8c85-104">С помощью внедрения зависимостей можно зарегистрировать службы и их соответствующие конфигурации, чтобы использовать *шаблон параметров*.</span><span class="sxs-lookup"><span data-stu-id="a8c85-104">With the help of dependency injection, registering your services and their corresponding configurations can make use of the *options pattern*.</span></span> <span data-ttu-id="a8c85-105">Шаблон параметров позволяет потребителям библиотеки (и ваших служб) запрашивать экземпляры [интерфейсов параметров](options.md#options-interfaces), где `TOptions` — это ваш класс параметров.</span><span class="sxs-lookup"><span data-stu-id="a8c85-105">The options pattern enables consumers of your library (and your services) to require instances of [options interfaces](options.md#options-interfaces) where `TOptions` is your options class.</span></span> <span data-ttu-id="a8c85-106">Использование параметров конфигурации через строго типизированные объекты помогает сохранить согласованное представление значений и устраняет необходимость вручную анализировать строковые значения.</span><span class="sxs-lookup"><span data-stu-id="a8c85-106">Consuming configuration options through strongly-typed objects helps to ensure consistent value representation, and removes the burden of manually parsing string values.</span></span> <span data-ttu-id="a8c85-107">Существует множество [поставщиков конфигурации](configuration-providers.md), которые могут использоваться потребителями библиотеки.</span><span class="sxs-lookup"><span data-stu-id="a8c85-107">There are many [configuration providers](configuration-providers.md) for consumers of your library to use.</span></span> <span data-ttu-id="a8c85-108">Эти поставщики позволяют пользователям настраивать библиотеку разными способами.</span><span class="sxs-lookup"><span data-stu-id="a8c85-108">With these providers, consumers can configure your library in many ways.</span></span>

<span data-ttu-id="a8c85-109">Авторы библиотек для .NET получат здесь общие рекомендации по правильному предоставлению шаблона параметров для потребителей библиотеки.</span><span class="sxs-lookup"><span data-stu-id="a8c85-109">As a .NET library author, you'll learn general guidance on how to correctly expose the options pattern to consumers of your library.</span></span> <span data-ttu-id="a8c85-110">Существует множество способов решить одну задачу. При этом нужно учитывать несколько факторов.</span><span class="sxs-lookup"><span data-stu-id="a8c85-110">There are various ways to achieve the same thing, and several considerations to make.</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="a8c85-111">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="a8c85-111">Naming conventions</span></span>

<span data-ttu-id="a8c85-112">По соглашению методы расширения, отвечающие за регистрацию служб, получают имена вида `Add{Service}`, где `{Service}` — это понятное описательное имя.</span><span class="sxs-lookup"><span data-stu-id="a8c85-112">By convention, extension methods responsible for registering services are named `Add{Service}`, where `{Service}` is a meaningful and descriptive name.</span></span> <span data-ttu-id="a8c85-113">В зависимости от пакета регистрация служб может дополняться методами расширения `Use{Service}`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-113">Depending on the package, the registration of services may be accompanied by `Use{Service}` extension methods.</span></span> <span data-ttu-id="a8c85-114">Методы расширения `Use{Service}` широко используются в [ASP.NET Core](/aspnet).</span><span class="sxs-lookup"><span data-stu-id="a8c85-114">The `Use{Service}` extension methods are commonplace in [ASP.NET Core](/aspnet).</span></span>

<span data-ttu-id="a8c85-115">✔️ РЕКОМЕНДУЕТСЯ использовать имена, которые отличают службу от других предложений.</span><span class="sxs-lookup"><span data-stu-id="a8c85-115">✔️ CONSIDER names that disambiguate your service from other offerings.</span></span>

<span data-ttu-id="a8c85-116">❌НЕ ИСПОЛЬЗУЙТЕ имена, которые уже являются частью экосистемы .NET из официальных пакетов Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a8c85-116">❌ DO NOT use names that are already part of the .NET ecosystem from official Microsoft packages.</span></span>

<span data-ttu-id="a8c85-117">✔️ РЕКОМЕНДУЕТСЯ присваивать статическим классам, которые предоставляют методы расширения, имена вида `{Type}Extensions`, где `{Type}` — это расширяемый тип.</span><span class="sxs-lookup"><span data-stu-id="a8c85-117">✔️ CONSIDER naming static classes that expose extension methods as `{Type}Extensions`, where `{Type}` is the type that you're extending.</span></span>

### <a name="namespace-guidance"></a><span data-ttu-id="a8c85-118">Рекомендации по использованию пространства имен</span><span class="sxs-lookup"><span data-stu-id="a8c85-118">Namespace guidance</span></span>

<span data-ttu-id="a8c85-119">Пакеты Майкрософт используют пространство имен `Microsoft.Extensions.DependencyInjection`, чтобы унифицировать регистрацию разных предложений услуг.</span><span class="sxs-lookup"><span data-stu-id="a8c85-119">Microsoft packages make use of the `Microsoft.Extensions.DependencyInjection` namespace to unify the registration of various service offerings.</span></span>

<span data-ttu-id="a8c85-120">✔️ РЕКОМЕНДУЕТСЯ использовать пространство имен, которое четко описывает предложение пакета.</span><span class="sxs-lookup"><span data-stu-id="a8c85-120">✔️ CONSIDER a namespace that clearly identifies your package offering.</span></span>

<span data-ttu-id="a8c85-121">❌НЕ ИСПОЛЬЗУЙТЕ пространство имен `Microsoft.Extensions.DependencyInjection` для пакетов, не являющихся официальными пакетами Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a8c85-121">❌ DO NOT use the `Microsoft.Extensions.DependencyInjection` namespace for non-official Microsoft packages.</span></span>

## <a name="parameterless"></a><span data-ttu-id="a8c85-122">Использование без параметров</span><span class="sxs-lookup"><span data-stu-id="a8c85-122">Parameterless</span></span>

<span data-ttu-id="a8c85-123">Если служба может работать с минимальной конфигурацией или без явно заданной конфигурации, постарайтесь использовать метод расширения без параметров.</span><span class="sxs-lookup"><span data-stu-id="a8c85-123">If your service can work with minimal or no explicit configuration, consider a parameterless extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

<span data-ttu-id="a8c85-124">Приведенный выше код `AddMyLibraryService` выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="a8c85-124">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="a8c85-125">расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;</span><span class="sxs-lookup"><span data-stu-id="a8c85-125">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="a8c85-126">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> с параметром типа `LibraryOptions`;</span><span class="sxs-lookup"><span data-stu-id="a8c85-126">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="a8c85-127">передает результат в следующий вызов к <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> для определения значений параметров по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a8c85-127">Chains a call to <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>, which specifies the default option values</span></span>

## <a name="iconfiguration-parameter"></a><span data-ttu-id="a8c85-128">Параметр `IConfiguration`</span><span class="sxs-lookup"><span data-stu-id="a8c85-128">`IConfiguration` parameter</span></span>

<span data-ttu-id="a8c85-129">При создании библиотеки, которая предоставляет потребителям большой набор параметров, может быть полезно потребовать метод расширения параметра `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-129">When you author a library that exposes many options to consumers, you may want to consider requiring an `IConfiguration` parameter extension method.</span></span> <span data-ttu-id="a8c85-130">Ожидаемый экземпляр `IConfiguration` должен быть ограничен областью именованного раздела конфигурации путем применения функции <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8c85-130">The expected `IConfiguration` instance should be scoped to a named section of the configuration by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> function.</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-14":::

<span data-ttu-id="a8c85-131">Приведенный выше код `AddMyLibraryService` выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="a8c85-131">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="a8c85-132">расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;</span><span class="sxs-lookup"><span data-stu-id="a8c85-132">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="a8c85-133">определяет параметр <xref:Microsoft.Extensions.Configuration.IConfiguration> `namedConfigurationSection`;</span><span class="sxs-lookup"><span data-stu-id="a8c85-133">Defines an <xref:Microsoft.Extensions.Configuration.IConfiguration> parameter `namedConfigurationSection`</span></span>
- <span data-ttu-id="a8c85-134">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)>, передавая параметр универсального типа для `LibraryOptions` и экземпляр `namedConfigurationSection` для настройки.</span><span class="sxs-lookup"><span data-stu-id="a8c85-134">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)> passing the generic type parameter of `LibraryOptions` and the `namedConfigurationSection` instance to configure</span></span>

<span data-ttu-id="a8c85-135">Потребители в этом шаблоне предоставляют экземпляр именованного раздела `IConfiguration` с заданной областью.</span><span class="sxs-lookup"><span data-stu-id="a8c85-135">Consumers in this pattern provide the scoped `IConfiguration` instance of the named section:</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

<span data-ttu-id="a8c85-136">В методе <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> выполняется вызов метода `.AddMyLibraryService`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-136">The call to `.AddMyLibraryService` is made in the <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> method.</span></span> <span data-ttu-id="a8c85-137">Это же справедливо и при использовании класса `Startup`, где добавление регистрируемых служб происходит в `ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-137">The same is true when using a `Startup` class, the addition of services being registered occurs in `ConfigureServices`.</span></span>

<span data-ttu-id="a8c85-138">За определение значений по умолчанию отвечает автор библиотеки.</span><span class="sxs-lookup"><span data-stu-id="a8c85-138">As the library author, specifying default values is up to you.</span></span>

> [!NOTE]
> <span data-ttu-id="a8c85-139">Есть возможность привязать конфигурацию к экземпляру параметров.</span><span class="sxs-lookup"><span data-stu-id="a8c85-139">It is possible to bind configuration to an options instance.</span></span> <span data-ttu-id="a8c85-140">Но при этом существует риск возникновения конфликтов имен, что приведет к ошибкам.</span><span class="sxs-lookup"><span data-stu-id="a8c85-140">However, there is a risk of name collisions - which will cause errors.</span></span> <span data-ttu-id="a8c85-141">Кроме того, при таком способе выполнения привязки вручную вы ограничиваете использование шаблона параметров однократной операцией чтения.</span><span class="sxs-lookup"><span data-stu-id="a8c85-141">Additionally, when manually binding in this way, you limit the consumption of your options pattern to read-once.</span></span> <span data-ttu-id="a8c85-142">Изменения параметров не будут привязываться повторно, а значит потребители не смогут использовать интерфейс [IOptionsMonitor](options.md#ioptionsmonitor).</span><span class="sxs-lookup"><span data-stu-id="a8c85-142">Changes to settings will not be re-bound, as such consumers will not be able to use the [IOptionsMonitor](options.md#ioptionsmonitor) interface.</span></span>
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a><span data-ttu-id="a8c85-143">Параметр `Action<TOptions>`</span><span class="sxs-lookup"><span data-stu-id="a8c85-143">`Action<TOptions>` parameter</span></span>

<span data-ttu-id="a8c85-144">Потребителям библиотеки может быть интересен вариант предоставления лямбда-выражения, которое возвращает экземпляр класса параметров.</span><span class="sxs-lookup"><span data-stu-id="a8c85-144">Consumers of your library may be interested in providing a lambda expression that yields an instance of your options class.</span></span> <span data-ttu-id="a8c85-145">В этом сценарии вы определяете параметр `Action<LibraryOptions>` в методе расширения.</span><span class="sxs-lookup"><span data-stu-id="a8c85-145">In this scenario, you define an `Action<LibraryOptions>` parameter in your extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="a8c85-146">Приведенный выше код `AddMyLibraryService` выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="a8c85-146">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="a8c85-147">расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;</span><span class="sxs-lookup"><span data-stu-id="a8c85-147">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="a8c85-148">определяет <xref:System.Action%601>, где `T` является параметром `LibraryOptions` `configureOptions`;</span><span class="sxs-lookup"><span data-stu-id="a8c85-148">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="a8c85-149">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> для действия `configureOptions`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-149">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="a8c85-150">Потребители в этом шаблоне предоставляют лямбда-выражение (или делегат, который соответствует параметру `Action<LibraryOptions>`).</span><span class="sxs-lookup"><span data-stu-id="a8c85-150">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter):</span></span>

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a><span data-ttu-id="a8c85-151">Параметр экземпляра параметров</span><span class="sxs-lookup"><span data-stu-id="a8c85-151">Options instance parameter</span></span>

<span data-ttu-id="a8c85-152">Потребители библиотеки могут предоставлять экземпляр встроенных параметров.</span><span class="sxs-lookup"><span data-stu-id="a8c85-152">Consumers of your library might prefer to provide an inlined options instance.</span></span> <span data-ttu-id="a8c85-153">В этом сценарии вы предоставляете метод расширения, который принимает экземпляр объекта параметров `LibraryOptions`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-153">In this scenario, you expose an extension method that takes an instance of your options object, `LibraryOptions`.</span></span>

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

<span data-ttu-id="a8c85-154">Приведенный выше код `AddMyLibraryService` выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="a8c85-154">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="a8c85-155">расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;</span><span class="sxs-lookup"><span data-stu-id="a8c85-155">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="a8c85-156">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> с параметром типа `LibraryOptions`;</span><span class="sxs-lookup"><span data-stu-id="a8c85-156">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="a8c85-157">привязывает вызов к <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, который задает значения параметров по умолчанию, которые затем могут быть переопределены из конкретного экземпляра `userOptions`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-157">Chains a call to <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, which specifies default option values that can be overridden from the given `userOptions` instance</span></span>

<span data-ttu-id="a8c85-158">Потребители в этом шаблоне предоставляют экземпляр класса `LibraryOptions`, определяя требуемые значения свойств в строке.</span><span class="sxs-lookup"><span data-stu-id="a8c85-158">Consumers in this pattern provide an instance of the `LibraryOptions` class, defining desired property values inline:</span></span>

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a><span data-ttu-id="a8c85-159">После настройки</span><span class="sxs-lookup"><span data-stu-id="a8c85-159">Post configuration</span></span>

<span data-ttu-id="a8c85-160">Когда все значения параметров конфигурации будут привязаны или определены, станут доступными процессы, выполняемые после настройки.</span><span class="sxs-lookup"><span data-stu-id="a8c85-160">After all configuration option values are bound or specified, post configuration functionality is available.</span></span> <span data-ttu-id="a8c85-161">Предоставляя тот же [параметр `Action<TOptions>`](#actiontoptions-parameter), который был описан ранее, можно выбрать вызов <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8c85-161">Exposing the same [`Action<TOptions>` parameter](#actiontoptions-parameter) detailed earlier, you could choose to call <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span></span> <span data-ttu-id="a8c85-162">Процесс, выполняемый после настройки, начинается после всех вызовов `.Configure`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-162">Post configure runs after all `.Configure` calls.</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="a8c85-163">Приведенный выше код `AddMyLibraryService` выполняет следующее:</span><span class="sxs-lookup"><span data-stu-id="a8c85-163">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="a8c85-164">расширяет экземпляр <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>;</span><span class="sxs-lookup"><span data-stu-id="a8c85-164">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="a8c85-165">определяет <xref:System.Action%601>, где `T` является параметром `LibraryOptions` `configureOptions`;</span><span class="sxs-lookup"><span data-stu-id="a8c85-165">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="a8c85-166">вызывает <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> для действия `configureOptions`.</span><span class="sxs-lookup"><span data-stu-id="a8c85-166">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="a8c85-167">Потребители в этом шаблоне предоставляют лямбда-выражение (или делегат, который соответствует параметру `Action<LibraryOptions>`), точно так же как с [параметром `Action<TOptions>`] в сценарии без процессов, выполняемых после конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a8c85-167">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter), just as they would with the [`Action<TOptions>` parameter] in a non-post configuration scenario:</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a><span data-ttu-id="a8c85-168">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a8c85-168">See also</span></span>

- [<span data-ttu-id="a8c85-169">Шаблон параметров в .NET</span><span class="sxs-lookup"><span data-stu-id="a8c85-169">Options pattern in .NET</span></span>](options.md)
- [<span data-ttu-id="a8c85-170">Внедрение зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="a8c85-170">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="a8c85-171">Рекомендации по внедрению зависимостей</span><span class="sxs-lookup"><span data-stu-id="a8c85-171">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
