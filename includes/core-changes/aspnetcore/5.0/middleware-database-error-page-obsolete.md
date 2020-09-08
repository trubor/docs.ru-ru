---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811285"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="925d1-101">ПО промежуточного слоя: Страница ошибок базы данных помечена как устаревшая</span><span class="sxs-lookup"><span data-stu-id="925d1-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="925d1-102">[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) и связанные с ним методы расширения были помечены как устаревшие в ASP.NET Core 5.0.</span><span class="sxs-lookup"><span data-stu-id="925d1-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="925d1-103">ПО промежуточного слоя и методы расширения будут удалены в ASP.NET Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="925d1-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="925d1-104">Эти функции вместо этого будут предоставляться `DatabaseDeveloperPageExceptionFilter` и методами расширения.</span><span class="sxs-lookup"><span data-stu-id="925d1-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="925d1-105">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span><span class="sxs-lookup"><span data-stu-id="925d1-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="925d1-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="925d1-106">Version introduced</span></span>

<span data-ttu-id="925d1-107">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="925d1-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="925d1-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="925d1-108">Old behavior</span></span>

<span data-ttu-id="925d1-109">`DatabaseErrorPageMiddleware` и связанные с ним методы расширения не устарели.</span><span class="sxs-lookup"><span data-stu-id="925d1-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="925d1-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="925d1-110">New behavior</span></span>

<span data-ttu-id="925d1-111">`DatabaseErrorPageMiddleware` и связанные с ним методы расширения устарели.</span><span class="sxs-lookup"><span data-stu-id="925d1-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="925d1-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="925d1-112">Reason for change</span></span>

<span data-ttu-id="925d1-113">`DatabaseErrorPageMiddleware` был перенесен в расширяемый API для [страницы со сведениями об исключении для разработчика](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span><span class="sxs-lookup"><span data-stu-id="925d1-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="925d1-114">Дополнительные сведения об расширяемых API см. на странице GitHub [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="925d1-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="925d1-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="925d1-115">Recommended action</span></span>

<span data-ttu-id="925d1-116">Выполните следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="925d1-116">Complete the following steps:</span></span>

1. <span data-ttu-id="925d1-117">Не используйте `DatabaseErrorPageMiddleware` в проектах.</span><span class="sxs-lookup"><span data-stu-id="925d1-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="925d1-118">Например, удалите вызов метода `UseDatabaseErrorPage` из `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="925d1-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="925d1-119">Добавьте в проект страницу со сведениями об исключении для разработчика.</span><span class="sxs-lookup"><span data-stu-id="925d1-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="925d1-120">Например, вызовите метод <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> в `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="925d1-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="925d1-121">Добавьте фильтр исключений страницы со сведениями об исключении для разработчика базы данных в коллекцию служб.</span><span class="sxs-lookup"><span data-stu-id="925d1-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="925d1-122">Например, вызовите метод `AddDatabaseDeveloperPageExceptionFilter` в `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="925d1-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="925d1-123">Категория</span><span class="sxs-lookup"><span data-stu-id="925d1-123">Category</span></span>

<span data-ttu-id="925d1-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="925d1-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="925d1-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="925d1-125">Affected APIs</span></span>

- [<span data-ttu-id="925d1-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="925d1-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="925d1-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="925d1-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->