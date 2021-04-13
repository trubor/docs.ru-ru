---
title: 'Критическое изменение. ПО промежуточного слоя: Страница ошибок базы данных помечена как устаревшая'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — ПО промежуточного слоя. Страница ошибок базы данных помечена как устаревшая
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8bc8852d7fb54b0d558342ee3c69085117512a1a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497623"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a>ПО промежуточного слоя: Страница ошибок базы данных помечена как устаревшая

[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) и связанные с ним методы расширения были помечены как устаревшие в ASP.NET Core 5.0. ПО промежуточного слоя и методы расширения будут удалены в ASP.NET Core 6.0. Эти функции вместо этого будут предоставляться `DatabaseDeveloperPageExceptionFilter` и методами расширения.

Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).

## <a name="version-introduced"></a>Представленная версия

5.0 RC 1

## <a name="old-behavior"></a>Старое поведение

`DatabaseErrorPageMiddleware` и связанные с ним методы расширения не устарели.

## <a name="new-behavior"></a>Новое поведение

`DatabaseErrorPageMiddleware` и связанные с ним методы расширения устарели.

## <a name="reason-for-change"></a>Причина изменения

`DatabaseErrorPageMiddleware` был перенесен в расширяемый API для [страницы со сведениями об исключении для разработчика](/aspnet/core/fundamentals/error-handling#developer-exception-page). Дополнительные сведения об расширяемых API см. на странице GitHub [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).

## <a name="recommended-action"></a>Рекомендованное действие

Выполните следующие шаги:

1. Не используйте `DatabaseErrorPageMiddleware` в проектах. Например, удалите вызов метода `UseDatabaseErrorPage` из `Startup.Configure`.

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. Добавьте в проект страницу со сведениями об исключении для разработчика. Например, вызовите метод <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> в `Startup.Configure`.

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. Добавьте пакет NuGet [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) в файл проекта.

1. Добавьте фильтр исключений страницы со сведениями об исключении для разработчика базы данных в коллекцию служб. Например, вызовите метод `AddDatabaseDeveloperPageExceptionFilter` в `Startup.ConfigureServices`.

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a>Затронутые API

- [Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
