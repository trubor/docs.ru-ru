---
title: Модули, обработчики и ПО промежуточного слоя
description: Сведения об обработке HTTP-запросов с помощью модулей, обработчиков и ПО промежуточного слоя.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 10/11/2019
ms.openlocfilehash: dbb0a94b0401d58139c024fd8ca3e00353a19efa
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97678027"
---
# <a name="modules-handlers-and-middleware"></a>Модули, обработчики и ПО промежуточного слоя

Приложение ASP.NET Core строится на основе *ПО промежуточного слоя*. ПО промежуточного слоя — это обработчики, добавленные в конвейер для обработки запросов и ответов. В приложении Web Forms аналогичные проблемы решают модули и обработчики HTTP-данных. В ASP.NET Core модули, обработчики, *Global.asax.cs* и жизненный цикл приложения заменяются ПО промежуточного слоя. В этой главе вы узнаете о ПО промежуточного слоя в контексте приложения Blazor.

## <a name="overview"></a>Обзор

Конвейер запросов ASP.NET Core состоит из последовательности делегатов запроса, вызываемых один за другим. На следующей схеме демонстрируется этот принцип. Поток выполнения показан черными стрелками.

![pipeline](media/middleware/request-delegate-pipeline.png)

На предыдущей схеме отсутствует концепция событий жизненного цикла. Данная концепция лежит в основе обработки запросов ASP.NET Web Forms. Эта система упрощает понимание того, какой процесс происходит, и позволяет вставлять ПО промежуточного слоя в любой момент. ПО промежуточного слоя выполняется в том порядке, в котором оно добавляется в конвейер запросов. Оно также добавляется в код вместо файлов конфигурации, обычно в файле *Startup.cs*.

## <a name="katana"></a>Katana

Читатели, знакомые с Katana, будут чувствовать себя комфортно в ASP.NET Core. Фактически Katana — это платформа, от которой ведет свое начало ASP.NET Core. В ней представлены аналогичные шаблоны ПО промежуточного слоя и конвейера для ASP.NET 4.x. ПО промежуточного слоя, разработанное для Katana, можно адаптировать для работы с конвейером ASP.NET Core.

## <a name="common-middleware"></a>Распространенное ПО промежуточного слоя

ASP.NET 4.x включает множество модулей. ASP.NET Core тоже имеет много доступных компонентов ПО промежуточного слоя. В некоторых случаях в ASP.NET Core могут использоваться модули IIS. В других случаях может быть доступно встроенное ПО промежуточного слоя ASP.NET Core.

В следующей таблице приведен список ПО промежуточного слоя и компонентов в ASP.NET Core.

|Модуль                 |Модуль ASP.NET 4.x           |Вариант в ASP.NET Core|
|-----------------------|-----------------------------|-------------------|
|Ошибки HTTP            |`CustomErrorModule`          |[ПО промежуточного слоя для страниц кода состояния](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|Документ по умолчанию       |`DefaultDocumentModule`      |[ПО промежуточного слоя для файлов по умолчанию](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|Просмотр каталогов     |`DirectoryListingModule`     |[ПО промежуточного слоя для просмотра каталогов](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|Динамическое сжатие    |`DynamicCompressionModule`   |[ПО промежуточного слоя для сжатия ответов](/aspnet/core/performance/response-compression)|
|Трассировка неудачно завершенных запросов|`FailedRequestsTracingModule`|[Ведение журналов ASP.NET Core](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|Кэширование файлов           |`FileCacheModule`            |[ПО промежуточного слоя для кэширования ответов](/aspnet/core/performance/caching/middleware)|
|Кэширование HTTP           |`HttpCacheModule`            |[ПО промежуточного слоя для кэширования ответов](/aspnet/core/performance/caching/middleware)|
|Ведение журнала HTTP           |`HttpLoggingModule`          |[Ведение журналов ASP.NET Core](/aspnet/core/fundamentals/logging/index)|
|Перенаправление HTTP       |`HttpRedirectionModule`      |[ПО промежуточного слоя для переопределения URL-адресов](/aspnet/core/fundamentals/url-rewriting)|
|Фильтры ISAPI          |`IsapiFilterModule`          |[ПО промежуточного слоя](/aspnet/core/fundamentals/middleware/index)|
|ISAPI                  |`IsapiModule`                |[ПО промежуточного слоя](/aspnet/core/fundamentals/middleware/index)|
|Фильтрация запросов      |`RequestFilteringModule`     |[Интерфейс IRule ПО промежуточного слоя для переопределения URL-адресов](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|Переопределение URL-адресов&#8224;   |`RewriteModule`              |[ПО промежуточного слоя для переопределения URL-адресов](/aspnet/core/fundamentals/url-rewriting)|
|Статическое сжатие     |`StaticCompressionModule`    |[ПО промежуточного слоя для сжатия ответов](/aspnet/core/performance/response-compression)|
|Статическое содержимое         |`StaticFileModule`           |[ПО промежуточного слоя для статических файлов](/aspnet/core/fundamentals/static-files)|
|Авторизация URL-адреса      |`UrlAuthorizationModule`     |[Идентификация ASP.NET Core](/aspnet/core/security/authentication/identity)|

Этот список не является исчерпывающим, но может дать представление о соответствии, существующем между этими двумя платформами. Более подробный список см. в разделе [Модули IIS с ASP.NET Core](/aspnet/core/host-and-deploy/iis/modules).

## <a name="custom-middleware"></a>Пользовательское ПО промежуточного слоя

Встроенное ПО промежуточного слоя может не обрабатывать все сценарии, необходимые для приложения. В таких случаях имеет смысл создать собственное ПО промежуточного слоя. Существует много способов определения ПО промежуточного слоя, самым простым из которых является обычный делегат. Рассмотрим следующее ПО промежуточного слоя, которое принимает запрос языка и региональных параметров из строки запроса:

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

ПО промежуточного слоя можно также определить как класс, либо путем реализации интерфейса `IMiddleware`, либо с помощью следующего соглашения ПО промежуточного слоя. Дополнительные сведения см. в разделе [Создание пользовательского ПО промежуточного слоя ASP.NET Core](/aspnet/core/fundamentals/middleware/write).

>[!div class="step-by-step"]
>[Назад](data.md)
>[Вперед](config.md)
