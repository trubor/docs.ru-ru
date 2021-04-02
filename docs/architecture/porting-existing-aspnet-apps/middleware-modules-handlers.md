---
title: Сравнение по промежуточного слоя с модулями и обработчиками
description: В этом разделе рассматриваются различия в структуре для приложений ASP.NET, использующих обработчики и модули с ASP.NET Core приложениями, которые определяют по промежуточного слоя для конвейеров обработки запросов.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3bc3c30a1ee988550cca907d7289583161337cb9
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122876"
---
# <a name="compare-middleware-to-modules-and-handlers"></a>Сравнение по промежуточного слоя с модулями и обработчиками

Если существующее приложение ASP.NET MVC или веб-API использует OWIN/Katana, скорее всего, вы уже знакомы с концепцией по промежуточного слоя и переносом их в ASP.NET Core должны быть довольно простыми. Однако большинство приложений ASP.NET полагаются на HTTP-модули и обработчики HTTP, а не по промежуточного слоя. Перенос этих данных в ASP.NET Core требует дополнительных усилий.

## <a name="aspnet-modules-and-handlers"></a>Модули и обработчики ASP.NET

[Модули HTTP и обработчики HTTP](/troubleshoot/aspnet/http-modules-handlers) являются неотъемлемой частью архитектуры ASP.NET. Во время обработки запроса каждый запрос обрабатывается несколькими модулями HTTP (например, модулем проверки подлинности и модулем сеанса) и обрабатывается одним HTTP-обработчиком. После обработки запроса обработчиком запрос передается обратно через HTTP-модули.

Если приложение использует пользовательские модули HTTP или обработчики HTTP, вам потребуется план для их переноса в ASP.NET Core. Наиболее вероятной заменой в ASP.NET Core является по промежуточного слоя.

## <a name="aspnet-core-middleware"></a>По промежуточного слоя ASP.NET Core

ASP.NET Core определяет конвейер запросов в методе каждого приложения `Configure` . Этот конвейер запросов определяет способ обработки входящего запроса приложением, при этом каждый метод в конвейере вызывает следующий метод до завершения метода, а цепочка по *промежуточного слоя* завершается и возвращает резервную копию стека. По промежуточного слоя может быть нацелено на все запросы или может быть настроено на соответствие только определенным запросам в зависимости от запрошенного пути или других факторов. Его можно настроить полностью в `Configure` методе приложения или реализовать в отдельном классе.

Поведение в приложении ASP.NET MVC, использующем модули HTTP, вероятно, лучше всего подходит для [пользовательского по промежуточного слоя](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1). Пользовательские обработчики HTTP можно заменить пользовательскими маршрутами или конечными точками, которые отвечают на один и тот же путь.

## <a name="accessing-httpcontext"></a>Доступ к HttpContext

Многие приложения .NET ссылаются на контекст текущего запроса через `HttpContext.Current` . Этот статический доступ может быть общим источником проблем с тестированием и другим использованием кода за пределами отдельных запросов. При создании ASP.NET Core приложений доступ к текущему HttpContext должен предоставляться как параметр метода по промежуточного слоя, как показано в этом примере:

```csharp
public class Middleware
{
    private readonly RequestDelegate _next;

    public Middleware(RequestDelegate next)
    {
        _next = next;
    }

    public Task Invoke(HttpContext httpContext)
    {
        return _next(httpContext);
    }
}
```

Аналогичным образом ASP.NET Core фильтры передают аргумент контекста их методам, из которых можно получить доступ к текущему объекту HttpContext:

```csharp
public class MyActionFilterAttribute : ActionFilterAttribute
{
    public override void OnResultExecuting(ResultExecutingContext context)
    {
        var headers = context.HttpContext.Request.Headers;
        // do something based on a header

        base.OnResultExecuting(context);
    }
}
```

Если у вас есть компоненты или службы, которым требуется доступ к HttpContext, вместо использования статического вызова, например `HttpContext.Current` , следует использовать внедрение зависимостей конструктора и интерфейс [ихттпконтекстакцессор](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) :

```csharp
public class MyService
{
    private readonly IHttpContextAccessor _httpContextAccessor;

    public MyService(IHttpContextAccessor httpContextAccessor)
    {
        _httpContextAccessor = httpContextAccessor;
    }

    public void DoSomething()
    {
        var currentContext = _httpContextAccessor.HttpContext;
    }
}
```

Этот подход исключает статическое связывание метода с текущим контекстом, предоставляя доступ тестируемым способом.

## <a name="references"></a>Ссылки

- [ASP.NET HTTP-модули и обработчики HTTP](/troubleshoot/aspnet/http-modules-handlers)
- [По промежуточного слоя ASP.NET Core](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
>[Назад](dependency-injection-differences.md)
>[Вперед](configuration-differences.md)
