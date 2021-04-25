---
title: Различия в конфигурации между ASP.NET MVC и ASP.NET Core
description: Сохранение значений конфигурации и существенное считывание изменений между ASP.NET и ASP.NET Core. В этом разделе рассматриваются подробные сведения и способы миграции конфигурации из ASP.NET в ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0e788c8606af05570d64bba257236feea11d5768
ms.sourcegitcommit: 5cad087ed0cfc4cf632b6d8270ed311e4d8b5217
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2021
ms.locfileid: "107928713"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="22491-104">Различия в конфигурации между ASP.NET MVC и ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22491-104">Configuration differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="22491-105">Сохранение значений конфигурации и существенное считывание изменений между ASP.NET и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="22491-105">How configuration values are stored and read changed dramatically between ASP.NET and ASP.NET Core.</span></span>

## <a name="aspnet-mvc-configuration"></a><span data-ttu-id="22491-106">Конфигурация MVC ASP.NET</span><span class="sxs-lookup"><span data-stu-id="22491-106">ASP.NET MVC configuration</span></span>

<span data-ttu-id="22491-107">В приложениях ASP.NET в конфигурации используются встроенные файлы конфигурации .NET, *web.config* в папке приложения и *machine.config* на сервере.</span><span class="sxs-lookup"><span data-stu-id="22491-107">In ASP.NET apps, configuration uses the built-in .NET configuration files, *web.config* in the app folder and *machine.config* on the server.</span></span> <span data-ttu-id="22491-108">Большинство приложений ASP.NET MVC и веб-API сохраняют свои параметры в файлах конфигурации `appSettings` или `connectionStrings` .</span><span class="sxs-lookup"><span data-stu-id="22491-108">Most ASP.NET MVC and Web API apps store their settings in the configuration file's `appSettings` or `connectionStrings` elements.</span></span> <span data-ttu-id="22491-109">Некоторые также используют пользовательские разделы конфигурации, которые можно сопоставить с классом параметров.</span><span class="sxs-lookup"><span data-stu-id="22491-109">Some also use custom configuration sections that can be mapped to a settings class.</span></span>

<span data-ttu-id="22491-110">Доступ к конфигурации в платформа .NET Framework приложении осуществляется с помощью `System.Configuration.ConfigurationManager` класса.</span><span class="sxs-lookup"><span data-stu-id="22491-110">Configuration in a .NET Framework app is accessed using the `System.Configuration.ConfigurationManager` class.</span></span> <span data-ttu-id="22491-111">К сожалению, этот класс предоставляет статический доступ к элементам конфигурации.</span><span class="sxs-lookup"><span data-stu-id="22491-111">Unfortunately, this class provides static access to the configuration elements.</span></span> <span data-ttu-id="22491-112">В результате очень мало ASP.NET приложений MVC, как правило, имеют абстрактный доступ к параметрам конфигурации или вводят их там, где это необходимо.</span><span class="sxs-lookup"><span data-stu-id="22491-112">As a result, very few ASP.NET MVC apps tend to abstract access to their configuration settings or inject them where needed.</span></span> <span data-ttu-id="22491-113">Вместо этого большинство платформа .NET Framework приложений, как правило, обращаются напрямую к системе конфигурации, где приложение должно использовать параметр.</span><span class="sxs-lookup"><span data-stu-id="22491-113">Instead, most .NET Framework apps tend to directly access the configuration system anywhere the app needs to use a setting.</span></span>

<span data-ttu-id="22491-114">Стандартный доступ к конфигурации MVC ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="22491-114">Typical ASP.NET MVC configuration access:</span></span>

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a><span data-ttu-id="22491-115">Конфигурация ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22491-115">ASP.NET Core configuration</span></span>

<span data-ttu-id="22491-116">В ASP.NET Coreных приложениях конфигурация сама по себе настраивается.</span><span class="sxs-lookup"><span data-stu-id="22491-116">In ASP.NET Core apps, configuration is, itself, configurable.</span></span> <span data-ttu-id="22491-117">Однако большинство приложений используют набор значений по умолчанию, предоставляемых как часть стандартных шаблонов проектов, и `ConfigureWebHostDefaults` используемый в них метод.</span><span class="sxs-lookup"><span data-stu-id="22491-117">However, most apps use a set of defaults provided as part of the standard project templates and the `ConfigureWebHostDefaults` method used in them.</span></span> <span data-ttu-id="22491-118">Параметры по умолчанию используют отформатированные файлы JSON с возможностью переопределения параметров в базовом *appsettings.js* файле с файлами, зависящими от среды, например *appsettings.Development.js*.</span><span class="sxs-lookup"><span data-stu-id="22491-118">The default settings use JSON formatted files, with the ability to override settings in the base *appsettings.json* file with environment-specific files like *appsettings.Development.json*.</span></span> <span data-ttu-id="22491-119">Кроме того, система конфигурации по умолчанию дополнительно переопределяет все параметры на основе файлов с любой переменной среды, которая существует для того же именованного параметра.</span><span class="sxs-lookup"><span data-stu-id="22491-119">Additionally, the default configuration system further overrides all file-based settings with any environment variable that exists for the same named setting.</span></span> <span data-ttu-id="22491-120">Это полезно во многих сценариях и особенно полезно при развертывании в среде размещения, так как устраняет необходимость в необходимости беспокоиться о том, будут ли при развертывании файлов конфигурации случайно перезаписываться важные параметры рабочей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="22491-120">This is useful in many scenarios and is especially useful when deploying to a hosting environment, since it eliminates the need to worry about whether deploying configuration files will accidentally overwrite important production configuration settings.</span></span> <span data-ttu-id="22491-121">Значения конфигурации также можно указать в качестве аргументов командной строки.</span><span class="sxs-lookup"><span data-stu-id="22491-121">Configuration values can also be provided as command line arguments.</span></span>

<span data-ttu-id="22491-122">Доступ к значениям конфигурации можно выполнять различными способами в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="22491-122">Accessing configuration values can be done in many ways in .NET Core.</span></span> <span data-ttu-id="22491-123">Поскольку внедрение зависимостей встроено в .NET Core, значения конфигурации обычно доступны через интерфейс, который внедряется в классы, которым они требуются.</span><span class="sxs-lookup"><span data-stu-id="22491-123">Because dependency injection is built into .NET Core, configuration values are generally accessed through an interface that is injected into classes that need them.</span></span> <span data-ttu-id="22491-124">Это может привести к передаче интерфейса <xref:Microsoft.Extensions.Configuration.IConfiguration> , как, но обычно лучше передать только те параметры, которые необходимы классу, используя [шаблон параметров](/aspnet/core/fundamentals/configuration/options).</span><span class="sxs-lookup"><span data-stu-id="22491-124">This can involve passing a interface like <xref:Microsoft.Extensions.Configuration.IConfiguration>, but usually it's better to pass just the settings required by the class using the [options pattern](/aspnet/core/fundamentals/configuration/options).</span></span>

<span data-ttu-id="22491-125">На рис. 2-2 показано, как передать `IConfiguration` страницу Razor и получить доступ к параметрам конфигурации.</span><span class="sxs-lookup"><span data-stu-id="22491-125">Figure 2-2 shows how to pass `IConfiguration` into a Razor Page and access configuration settings from it:</span></span>

```csharp
using Microsoft.Extensions.Configuration;

public class TestModel : PageModel
{
    private readonly IConfiguration _configuration;

    public TestModel(IConfiguration configuration)
    {
        _configuration= configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = _configuration["MyKey"];

        // ...
    }
}
```

<span data-ttu-id="22491-126">**Рис. 2-2.**</span><span class="sxs-lookup"><span data-stu-id="22491-126">**Figure 2-2.**</span></span> <span data-ttu-id="22491-127">Доступ к значениям конфигурации с помощью `IConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="22491-127">Accessing configuration values with `IConfiguration`.</span></span>

<span data-ttu-id="22491-128">С помощью [шаблона параметров](../../core/extensions/options.md)доступ к параметрам аналогичен, но он строго типизирован и более специфичен для параметров, необходимых классу, как показано на рис. 2-3.</span><span class="sxs-lookup"><span data-stu-id="22491-128">Using the [options pattern](../../core/extensions/options.md), settings access is similar but is strongly typed and more specific to the setting(s) needed by the consuming class, as Figure 2-3 demonstrates.</span></span>

```csharp
public class PositionOptions
{
    public const string Position = nameof(Position);

    public string Title { get; set; }
    public string Name { get; set; }
}

public class Test2Model : PageModel
{
    private readonly PositionOptions _options;

    public Test2Model(IOptions<PositionOptions> options)
    {
        _options = options.Value;
    }

    public ContentResult OnGet()
    {
        return Content($"Title: {_options.Title}\nName: {_options.Name}");
    }
}
```

<span data-ttu-id="22491-129">**Рис. 2-3.**</span><span class="sxs-lookup"><span data-stu-id="22491-129">**Figure 2-3.**</span></span> <span data-ttu-id="22491-130">Использование шаблона параметров в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="22491-130">Using the options pattern in ASP.NET Core.</span></span>

<span data-ttu-id="22491-131">Чтобы шаблон параметров работал, при запуске приложения необходимо настроить тип параметров `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="22491-131">For the options pattern to work, the options type must be configured in `ConfigureServices` when the app starts up:</span></span>

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a><span data-ttu-id="22491-132">Миграция конфигурации</span><span class="sxs-lookup"><span data-stu-id="22491-132">Migrate configuration</span></span>

<span data-ttu-id="22491-133">При рассмотрении способа переноса параметров конфигурации приложения с платформа .NET Framework на .NET Core, первым шагом является определение всех используемых параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="22491-133">When considering how to port an app's configuration settings from .NET Framework to .NET Core, the first step is to identify all of the configuration settings that are being used.</span></span> <span data-ttu-id="22491-134">Большинство из них будут находиться в файле *web.config* в корневой папке приложения, но некоторые приложения должны найти параметры в общем *machine.configном* файле.</span><span class="sxs-lookup"><span data-stu-id="22491-134">Most of these will be in the *web.config* file in the app's root folder, but some apps expect settings to be found in the shared *machine.config* file as well.</span></span> <span data-ttu-id="22491-135">Эти параметры будут включать элементы `appSettings` элемента, `connectionStrings` элемента и любые пользовательские элементы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="22491-135">These settings will include elements of the `appSettings` element, the `connectionStrings` element, and any custom configuration elements as well.</span></span> <span data-ttu-id="22491-136">В .NET Core все эти параметры обычно хранятся в *appsettings.js* в файле.</span><span class="sxs-lookup"><span data-stu-id="22491-136">In .NET Core, all of these settings are typically stored in the *appsettings.json* file.</span></span>

<span data-ttu-id="22491-137">После каталогизации всех параметров в файлах конфигурации следует указать, где и как эти параметры используются в самом приложении.</span><span class="sxs-lookup"><span data-stu-id="22491-137">Once all settings in the config files have been cataloged, the next step should be to identify where and how the settings are used in the app itself.</span></span> <span data-ttu-id="22491-138">Если некоторые параметры не используются, их можно опустить при миграции.</span><span class="sxs-lookup"><span data-stu-id="22491-138">If some settings aren't being used, these can probably be omitted from the migration.</span></span> <span data-ttu-id="22491-139">Для каждого параметра обратите внимание на все места, где они используются, чтобы вы могли быть уверены, что при переносе кода вы не пропустили.</span><span class="sxs-lookup"><span data-stu-id="22491-139">For each setting, note all of the places it's being used so you can be sure you don't miss any when you migrate the code.</span></span>

<span data-ttu-id="22491-140">Если вы по-прежнему обслуживаете приложение ASP.NET, может быть полезно избежать статических ссылок `ConfigurationManager` и заменить их доступом через интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="22491-140">If you're still maintaining the ASP.NET app, it may be helpful to avoid static references to `ConfigurationManager` and replace them with access through interfaces.</span></span> <span data-ttu-id="22491-141">Это упростит переход на систему конфигурации ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="22491-141">This will ease the transition to ASP.NET Core's configuration system.</span></span> <span data-ttu-id="22491-142">Как правило, статический доступ к внешним ресурсам усложняет тестирование и обслуживание кода, поэтому Lookout в любом месте, где приложение может следовать этому шаблону.</span><span class="sxs-lookup"><span data-stu-id="22491-142">In general, static access to external resources makes code harder to test and maintain, so be on the lookout for anywhere else the app may be following this pattern.</span></span>

## <a name="references"></a><span data-ttu-id="22491-143">Ссылки</span><span class="sxs-lookup"><span data-stu-id="22491-143">References</span></span>

- [<span data-ttu-id="22491-144">Конфигурация в .NET Core</span><span class="sxs-lookup"><span data-stu-id="22491-144">Configuration in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/)
- [<span data-ttu-id="22491-145">Шаблон параметров в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22491-145">Options pattern in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/options)
- [<span data-ttu-id="22491-146">Перенос конфигурации в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22491-146">Migrate configuration to ASP.NET Core</span></span>](/aspnet/core/migration/configuration)
- [<span data-ttu-id="22491-147">Рефакторинг статического доступа к конфигурации</span><span class="sxs-lookup"><span data-stu-id="22491-147">Refactoring Static Config Access</span></span>](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
><span data-ttu-id="22491-148">[Назад](middleware-modules-handlers.md)
>[Вперед](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="22491-148">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
