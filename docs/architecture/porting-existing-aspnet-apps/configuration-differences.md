---
title: Различия в конфигурации между ASP.NET MVC и ASP.NET Core
description: Сохранение значений конфигурации и существенное считывание изменений между ASP.NET и ASP.NET Core. В этом разделе рассматриваются подробные сведения и способы миграции конфигурации из ASP.NET в ASP.NET Core.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3d721c028b1e760a6227855451e2194d9e471a58
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122954"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a>Различия в конфигурации между ASP.NET MVC и ASP.NET Core

Сохранение значений конфигурации и существенное считывание изменений между ASP.NET и ASP.NET Core.

## <a name="aspnet-mvc-configuration"></a>Конфигурация MVC ASP.NET

В приложениях ASP.NET в конфигурации используются встроенные файлы конфигурации .NET, *web.config* в папке приложения и *machine.config* на сервере. Большинство приложений ASP.NET MVC и веб-API сохраняют свои параметры в файлах конфигурации `appSettings` или `connectionStrings` . Некоторые также используют пользовательские разделы конфигурации, которые можно сопоставить с классом параметров.

Доступ к конфигурации в платформа .NET Framework приложении осуществляется с помощью `System.Configuration.ConfigurationManager` класса. К сожалению, этот класс предоставляет статический доступ к элементам конфигурации. В результате очень мало ASP.NET приложений MVC, как правило, имеют абстрактный доступ к параметрам конфигурации или вводят их там, где это необходимо. Вместо этого большинство платформа .NET Framework приложений, как правило, обращаются напрямую к системе конфигурации, где приложение должно использовать параметр.

Стандартный доступ к конфигурации MVC ASP.NET:

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a>Конфигурация ASP.NET Core

В ASP.NET Coreных приложениях конфигурация сама по себе настраивается. Однако большинство приложений используют набор значений по умолчанию, предоставляемых как часть стандартных шаблонов проектов, и `ConfigureWebHostDefaults` используемый в них метод. Параметры по умолчанию используют отформатированные файлы JSON с возможностью переопределения параметров в базовом *appsettings.js* файле с файлами, зависящими от среды, например *appsettings.Development.js*. Кроме того, система конфигурации по умолчанию дополнительно переопределяет все параметры на основе файлов с любой переменной среды, которая существует для того же именованного параметра. Это полезно во многих сценариях и особенно полезно при развертывании в среде размещения, так как устраняет необходимость в необходимости беспокоиться о том, будут ли при развертывании файлов конфигурации случайно перезаписываться важные параметры рабочей конфигурации. Значения конфигурации также можно указать в качестве аргументов командной строки.

Доступ к значениям конфигурации можно выполнять различными способами в .NET Core. Поскольку внедрение зависимостей встроено в .NET Core, значения конфигурации обычно доступны через интерфейс, который внедряется в классы, которым они требуются. Это может привести к передаче интерфейса <xref:Microsoft.Extensions.Configuration.IConfiguration> , как, но обычно лучше передать только те параметры, которые необходимы классу, используя [шаблон параметров](/aspnet/core/fundamentals/configuration/options).

На рис. 2-2 показано, как передать `IConfiguration` страницу Razor и получить доступ к параметрам конфигурации.

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

**Рис. 2-2.** Доступ к значениям конфигурации с помощью `IConfiguration` .

С помощью [шаблона параметров](/dotnet/core/extensions/options)доступ к параметрам аналогичен, но он строго типизирован и более специфичен для параметров, необходимых классу, как показано на рис. 2-3.

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

**Рис. 2-3.** Использование шаблона параметров в ASP.NET Core.

Чтобы шаблон параметров работал, при запуске приложения необходимо настроить тип параметров `ConfigureServices` .

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a>Миграция конфигурации

При рассмотрении способа переноса параметров конфигурации приложения с платформа .NET Framework на .NET Core, первым шагом является определение всех используемых параметров конфигурации. Большинство из них будут находиться в файле *web.config* в корневой папке приложения, но некоторые приложения должны найти параметры в общем *machine.configном* файле. Эти параметры будут включать элементы `appSettings` элемента, `connectionStrings` элемента и любые пользовательские элементы конфигурации. В .NET Core все эти параметры обычно хранятся в *appsettings.js* в файле.

После каталогизации всех параметров в файлах конфигурации следует указать, где и как эти параметры используются в самом приложении. Если некоторые параметры не используются, их можно опустить при миграции. Для каждого параметра обратите внимание на все места, где они используются, чтобы вы могли быть уверены, что при переносе кода вы не пропустили.

Если вы по-прежнему обслуживаете приложение ASP.NET, может быть полезно избежать статических ссылок `ConfigurationManager` и заменить их доступом через интерфейсы. Это упростит переход на систему конфигурации ASP.NET Core. Как правило, статический доступ к внешним ресурсам усложняет тестирование и обслуживание кода, поэтому Lookout в любом месте, где приложение может следовать этому шаблону.

## <a name="references"></a>Ссылки

- [Конфигурация в .NET Core](/aspnet/core/fundamentals/configuration/)
- [Шаблон параметров в ASP.NET Core](/aspnet/core/fundamentals/configuration/options)
- [Перенос конфигурации в ASP.NET Core](/aspnet/core/migration/configuration)
- [Рефакторинг статического доступа к конфигурации](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
>[Назад](middleware-modules-handlers.md)
>[Вперед](routing-differences.md)
