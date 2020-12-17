---
title: Работа с данными в приложениях ASP.NET Core
description: Разработка современных веб-приложений с помощью ASP.NET Core и Azure | Работа с данными в приложениях ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 9d85d700ecb8d6cbe7afd8d3c724f499ee5fed71
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851260"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="c99b7-103">Работа с данными в приложениях ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c99b7-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="c99b7-104">"Данные — это самый ценный ресурс, который намного переживет сами системы".</span><span class="sxs-lookup"><span data-stu-id="c99b7-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="c99b7-105">Тим Бернерс-Ли (Tim Berners-Lee)</span><span class="sxs-lookup"><span data-stu-id="c99b7-105">Tim Berners-Lee</span></span>

<span data-ttu-id="c99b7-106">Доступ к данным является одной из важнейших составляющих практически любой программы.</span><span class="sxs-lookup"><span data-stu-id="c99b7-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="c99b7-107">ASP.NET Core поддерживает широкий спектр способов доступа к данным, включая Entity Framework Core (и Entity Framework 6), и может работать с любыми платформами доступа к данным .NET.</span><span class="sxs-lookup"><span data-stu-id="c99b7-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="c99b7-108">Выбор используемой платформы доступа к данным зависит от потребностей приложения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="c99b7-109">Абстрагируя выбор такой платформы от проектов ядра приложения и пользовательского интерфейса, а также инкапсулируя детали реализации в инфраструктуре, можно создавать слабо связанное приложение с расширенными возможностями для тестирования.</span><span class="sxs-lookup"><span data-stu-id="c99b7-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="c99b7-110">Entity Framework Core (для реляционных баз данных)</span><span class="sxs-lookup"><span data-stu-id="c99b7-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="c99b7-111">Если вы создаете новое приложение ASP.NET Core для работы с реляционными данными, рекомендуется выбирать Entity Framework Core (EF Core) для доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="c99b7-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="c99b7-112">EF Core является объектно-реляционным модулем сопоставления (O/RM), который позволяет разработчикам .NET обеспечивать двустороннюю сохраняемость объектов во взаимодействии с источником данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="c99b7-113">Это устраняет необходимость в большей части кода для доступа к данным, который разработчикам обычно приходится писать.</span><span class="sxs-lookup"><span data-stu-id="c99b7-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="c99b7-114">Как и ASP.NET Core, платформа EF Core была переработана, чтобы обеспечить поддержку модульных кроссплатформенных приложений.</span><span class="sxs-lookup"><span data-stu-id="c99b7-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="c99b7-115">Она добавляется в приложение в виде пакета NuGet, настраивается в классе Startup и используется для обработки запросов посредством внедрения зависимостей в тот момент, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="c99b7-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="c99b7-116">Чтобы использовать EF Core с базой данных SQL Server, выполните следующую команду dotnet CLI:</span><span class="sxs-lookup"><span data-stu-id="c99b7-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="c99b7-117">Чтобы добавить поддержку источника данных в памяти для тестирования, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c99b7-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="c99b7-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="c99b7-118">The DbContext</span></span>

<span data-ttu-id="c99b7-119">Для работы с EF Core вам потребуется подкласс <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="c99b7-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="c99b7-120">Этот класс содержит свойства, представляющие коллекцию сущностей, с которыми будет работать ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="c99b7-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="c99b7-121">Пример приложения eShopOnWeb содержит CatalogContext с коллекциями товаров, брендов и типов:</span><span class="sxs-lookup"><span data-stu-id="c99b7-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="c99b7-122">Ваш класс DbContext должен иметь конструктор, который принимает DbContextOptions и передает этот аргумент в базовый класс DbContext.</span><span class="sxs-lookup"><span data-stu-id="c99b7-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="c99b7-123">Если в вашем приложении используется только один класс DbContext, вы можете передавать экземпляр DbContextOptions. Но при наличии нескольких таких классов вам нужно использовать универсальный тип DbContextOptions\<T>, передавая ваш тип DbContext в качестве универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="c99b7-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="c99b7-124">Настройка EF Core</span><span class="sxs-lookup"><span data-stu-id="c99b7-124">Configuring EF Core</span></span>

<span data-ttu-id="c99b7-125">В приложении ASP.NET Core настройка EF Core обычно осуществляется в методе ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="c99b7-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="c99b7-126">EF Core использует DbContextOptionsBuilder, который поддерживает несколько полезных методов расширения, позволяющих оптимизировать его конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="c99b7-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="c99b7-127">Чтобы настроить метод CatalogContext для использования базы данных SQL Server со строкой подключения, определенной в конфигурации, необходимо добавить следующий код в ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="c99b7-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="c99b7-128">Чтобы использовать выполняющуюся в памяти базу данных:</span><span class="sxs-lookup"><span data-stu-id="c99b7-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="c99b7-129">После установки EF Core, создания дочернего типа DbContext и его настройки в методе ConfigureServices вы можете использовать EF Core.</span><span class="sxs-lookup"><span data-stu-id="c99b7-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="c99b7-130">Вы можете запросить экземпляр вашего типа DbContext в любой службе, где он необходим, и начать работу с хранимыми сущностями с помощью LINQ так, как если бы они были обычными коллекциями.</span><span class="sxs-lookup"><span data-stu-id="c99b7-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="c99b7-131">EF Core автоматически преобразует выражения LINQ в запросы SQL для хранения и извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="c99b7-132">Чтобы просмотреть выполнение запросов EF Core, настройте ведение журналов как минимум на уровне информационных сообщений, как показано на рис. 8-1.</span><span class="sxs-lookup"><span data-stu-id="c99b7-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![Ведение журналов запросов EF Core на консоль](./media/image8-1.png)

<span data-ttu-id="c99b7-134">**Рис. 8-1**.</span><span class="sxs-lookup"><span data-stu-id="c99b7-134">**Figure 8-1**.</span></span> <span data-ttu-id="c99b7-135">Ведение журналов запросов EF Core на консоль</span><span class="sxs-lookup"><span data-stu-id="c99b7-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="c99b7-136">Получение и сохранение данных</span><span class="sxs-lookup"><span data-stu-id="c99b7-136">Fetching and storing Data</span></span>

<span data-ttu-id="c99b7-137">Чтобы извлечь данные из EF Core, необходимо обратиться к соответствующему свойству и использовать LINQ для фильтрации результатов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="c99b7-138">Также можно использовать LINQ для выполнения проекции (преобразования результата из одного типа в другой).</span><span class="sxs-lookup"><span data-stu-id="c99b7-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="c99b7-139">В следующем примере извлекается CatalogBrands с упорядочением по имени, затем осуществляется фильтровка по свойству Enabled, после чего выполняется проекция в тип SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="c99b7-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="c99b7-140">В приведенном выше примере важно добавить вызов ToListAsync, чтобы выполнить запрос немедленно.</span><span class="sxs-lookup"><span data-stu-id="c99b7-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="c99b7-141">В противном случае инструкция назначит IQueryable\<SelectListItem> для brandItems, и выполнение не будет начато, пока не будет выполнено перечисление.</span><span class="sxs-lookup"><span data-stu-id="c99b7-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="c99b7-142">Возврат результатов IQueryable из методов имеет свои преимущества и недостатки.</span><span class="sxs-lookup"><span data-stu-id="c99b7-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="c99b7-143">Такой подход позволяет осуществлять дальнейшие изменения запроса, который будет создавать EF Core, но также может привести к ошибке, которая проявится только во время выполнения при добавлении операций в запрос, который EF Core не сможет преобразовать.</span><span class="sxs-lookup"><span data-stu-id="c99b7-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="c99b7-144">Как правило, более безопасный подход подразумевает передачу любых фильтров в метод, осуществляющий доступ к данным, с последующим возвратом размещаемой в памяти коллекции (например, List\<T>) в виде результата.</span><span class="sxs-lookup"><span data-stu-id="c99b7-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="c99b7-145">EF Core отслеживает изменения сущностей, которые получаются из хранилища сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="c99b7-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="c99b7-146">Чтобы сохранить изменения в отслеживаемой сущности, достаточно вызвать метод SaveChanges для DbContext и убедиться, что это тот же экземпляр DbContext, который использовался при получении сущности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="c99b7-147">Добавление и удаление сущностей осуществляется непосредственно с помощью свойства DbSet, опять таки, посредством вызова метода SaveChanges для выполнения команд базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="c99b7-148">В следующем примере показано добавление, обновление и удаление сущностей из хранилища сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="c99b7-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="c99b7-149">EF Core поддерживает как синхронные, так и асинхронные методы получения и сохранения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="c99b7-150">В веб-приложениях рекомендуется использовать шаблон async/await для асинхронных методов. В этом случае потоки веб-сервера не блокируются на время ожидания завершения операций доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="c99b7-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="c99b7-151">Получение связанных данных</span><span class="sxs-lookup"><span data-stu-id="c99b7-151">Fetching related data</span></span>

<span data-ttu-id="c99b7-152">При получении сущностей EF Core заполняет все свойства, которые хранятся в базе данных непосредственно с этой сущностью.</span><span class="sxs-lookup"><span data-stu-id="c99b7-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="c99b7-153">Свойства навигации, например списки связанных сущностей, не заполняются и могут получать значения null.</span><span class="sxs-lookup"><span data-stu-id="c99b7-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="c99b7-154">Этот процесс гарантирует, что EF Core не будет извлекать объем данных больше необходимого, что особенно важно для веб-приложений, которые должны быстро обрабатывать запросы и возвращать ответы эффективным способом.</span><span class="sxs-lookup"><span data-stu-id="c99b7-154">This process ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="c99b7-155">Чтобы включить отношение с сущностью, используя _безотложную загрузку_, необходимо указать свойство, используя метод расширения Include для запроса, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="c99b7-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="c99b7-156">С помощью ThenInclude можно включить несколько отношений, а также вложенные отношения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="c99b7-157">EF Core выполнит один запрос для извлечения результирующего набора сущностей.</span><span class="sxs-lookup"><span data-stu-id="c99b7-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="c99b7-158">Кроме того, вы можете включить свойства навигации, передав строку с разделением "." в метод расширения `.Include()` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c99b7-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="c99b7-159">Помимо инкапсуляции логики фильтрации, эта спецификация может указывать форму возвращаемых данных, включая свойства, которые следует заполнить.</span><span class="sxs-lookup"><span data-stu-id="c99b7-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="c99b7-160">Пример приложения eShopOnWeb содержит несколько спецификаций, которые демонстрируют сведения об инкапсулирующей безотложной загрузке в спецификации.</span><span class="sxs-lookup"><span data-stu-id="c99b7-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="c99b7-161">Вы видите, как спецификация используется в рамках запроса:</span><span class="sxs-lookup"><span data-stu-id="c99b7-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="c99b7-162">Также для загрузки связанных данных можно использовать _явную загрузку_.</span><span class="sxs-lookup"><span data-stu-id="c99b7-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="c99b7-163">Явная загрузка позволяет загружать дополнительные данные в уже извлеченную сущность.</span><span class="sxs-lookup"><span data-stu-id="c99b7-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="c99b7-164">Так как для этого требуется отдельный запрос к базе данных, такой подход не рекомендуется для веб-приложений, в которых необходимо свести к минимуму число обращений к базе данных в рамках одного запроса.</span><span class="sxs-lookup"><span data-stu-id="c99b7-164">Since this approach involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="c99b7-165">_Отложенная загрузка_ позволяет автоматически загружать данные в тот момент, когда на них ссылается приложение.</span><span class="sxs-lookup"><span data-stu-id="c99b7-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="c99b7-166">В EF Core добавлена поддержка отложенной загрузки в версии 2.1.</span><span class="sxs-lookup"><span data-stu-id="c99b7-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="c99b7-167">Отложенная загрузка не включена по умолчанию и требует установки `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="c99b7-168">Как и явная загрузка, отложенная загрузка обычно отключена для веб-приложений, так как ее использование приведет к дополнительным запросам к базе данных в пределах каждого веб-запроса.</span><span class="sxs-lookup"><span data-stu-id="c99b7-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="c99b7-169">К сожалению, издержки, связанные с отложенной загрузкой, часто трудно заметить во время разработки, когда задержка маленькая и для тестирования используются небольшие наборы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when the latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="c99b7-170">Но в рабочей среде с большим количеством пользователей, данных и задержек запросы к базе данных могут приводить к снижению производительности для веб-приложений, где активно используется отложенная загрузка.</span><span class="sxs-lookup"><span data-stu-id="c99b7-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="c99b7-171">Предотвращение отложенной загрузки сущностей в веб-приложениях</span><span class="sxs-lookup"><span data-stu-id="c99b7-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="c99b7-172">Инкапсуляция данных</span><span class="sxs-lookup"><span data-stu-id="c99b7-172">Encapsulating data</span></span>

<span data-ttu-id="c99b7-173">EF Core поддерживает несколько функций, которые позволяют модели правильно инкапсулировать свое состояние.</span><span class="sxs-lookup"><span data-stu-id="c99b7-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="c99b7-174">Распространенной проблемой моделей предметной области является то, что они предоставляют свойства навигации коллекции как общедоступные типы списка.</span><span class="sxs-lookup"><span data-stu-id="c99b7-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="c99b7-175">Таким образом, любой участник совместной работы может управлять содержимым этих типов в коллекции. В результате могут обходиться важные бизнес-правила, связанные с коллекцией, из-за чего объект может оказаться в недопустимом состоянии.</span><span class="sxs-lookup"><span data-stu-id="c99b7-175">This problem allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="c99b7-176">Чтобы решить эту проблему, рекомендуется разрешать доступ к связанным коллекциям только для чтения и явно предоставлять методы, которые определяют возможные способы работы клиентов с этими коллекциями, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c99b7-176">The solution to this problem is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="c99b7-177">Этот тип сущности не предоставляет открытое свойство `List` или `ICollection`, но вместо этого предоставляет тип `IReadOnlyCollection`, который создает оболочку для базового типа списка.</span><span class="sxs-lookup"><span data-stu-id="c99b7-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="c99b7-178">При использовании этого шаблона можно указать для Entity Framework Core использовать резервное поле следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c99b7-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="c99b7-179">Еще один способ улучшить модель предметной области — использовать объекты значений для типов, которым не хватает удостоверений и которые различаются только по своим свойствам.</span><span class="sxs-lookup"><span data-stu-id="c99b7-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="c99b7-180">Использование таких типов в качестве свойств сущностей может помочь сохранить логику, присущую объекту значения, и избежать повторяющуюся логику между несколькими сущностями, использующими одну концепцию.</span><span class="sxs-lookup"><span data-stu-id="c99b7-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="c99b7-181">В Entity Framework Core можно сохранить объекты значений в той же таблице, что и сущность-владелец, настроив тип в качестве принадлежащей сущности следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c99b7-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="c99b7-182">В этом примере свойство `ShipToAddress` принадлежит типу `Address`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="c99b7-183">`Address` является объектом значения с несколькими свойствами, такими как `Street` и `City`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="c99b7-184">EF Core сопоставляет объект `Order` со своей таблицей, по одному столбцу на свойство `Address`, вставляя перед именем каждого столбца имя свойства.</span><span class="sxs-lookup"><span data-stu-id="c99b7-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="c99b7-185">В этом примере таблица `Order` должна включать такие столбцы, как `ShipToAddress_Street` и `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="c99b7-186">При необходимости собственные типы можно также хранить в отдельных таблицах.</span><span class="sxs-lookup"><span data-stu-id="c99b7-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="c99b7-187">Узнайте больше о [поддержке сущностей в EF Core](/ef/core/modeling/owned-entities).</span><span class="sxs-lookup"><span data-stu-id="c99b7-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="c99b7-188">Устойчивые подключения</span><span class="sxs-lookup"><span data-stu-id="c99b7-188">Resilient connections</span></span>

<span data-ttu-id="c99b7-189">Внешние ресурсы, например базы данных SQL, время от времени могут быть недоступны.</span><span class="sxs-lookup"><span data-stu-id="c99b7-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="c99b7-190">Если ресурс временно недоступен, приложение может использовать логику повторных попыток, чтобы избежать возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="c99b7-191">Такой подход часто называют _устойчивостью подключений_.</span><span class="sxs-lookup"><span data-stu-id="c99b7-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="c99b7-192">Вы можете реализовать собственную логику [повторных попыток с экспоненциальной выдержкой](/azure/architecture/patterns/retry), при которой приложение пытается повторить операцию с экспоненциально растущим временем ожидания, пока не будет достигнуто максимальное число повторных попыток.</span><span class="sxs-lookup"><span data-stu-id="c99b7-192">You can implement your [own retry with exponential backoff](/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="c99b7-193">В этом методе учитывается, что облачные ресурсы могут периодически становиться недоступными на несколько секунд по разным причинам, что может приводить к неудачному завершению некоторых запросов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in the failure of some requests.</span></span>

<span data-ttu-id="c99b7-194">Для баз данных Azure SQL платформа Entity Framework Core уже предоставляет логику устойчивости и повторного выполнения при подключении к внутренним базам данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="c99b7-195">Но вам необходимо применить стратегию выполнения Entity Framework к каждому подключению DbContext, если вы хотите иметь устойчивое подключение к EF Core.</span><span class="sxs-lookup"><span data-stu-id="c99b7-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="c99b7-196">Например, следующий код на уровне подключения к EF Core обеспечивает устойчивое SQL-подключение, которое устанавливается повторно при сбое.</span><span class="sxs-lookup"><span data-stu-id="c99b7-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="c99b7-197">Стратегии выполнения и явные транзакции с использованием BeginTransaction и нескольких DbContext</span><span class="sxs-lookup"><span data-stu-id="c99b7-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="c99b7-198">Если в подключениях к EF Core включены повторные попытки, каждая операция, выполняемая с помощью EF Core, будет предпринимать повторные попытки.</span><span class="sxs-lookup"><span data-stu-id="c99b7-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="c99b7-199">Каждый запрос и каждый вызов к SaveChanges будет повторяться снова как единица в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="c99b7-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="c99b7-200">Но если код запускает транзакцию с помощью BeginTransaction, вы сами определяете группу операций, которые должны рассматриваться как единица, — все содержимое транзакции можно будет откатить в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="c99b7-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="c99b7-201">Если вы попытаетесь выполнить эту транзакцию при использовании стратегии выполнения EF (политика повтора) и включаете несколько вызовов SaveChanges из нескольких DbContext в транзакции, отобразится следующее исключение.</span><span class="sxs-lookup"><span data-stu-id="c99b7-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="c99b7-202">"System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions" (System.InvalidOperationException: настроенная стратегия выполнения SqlServerRetryingExecutionStrategy не поддерживает запуск транзакций пользователем).</span><span class="sxs-lookup"><span data-stu-id="c99b7-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="c99b7-203">Используйте стратегию выполнения, возвращенную 'DbContext.Database.CreateExecutionStrategy()', чтобы выполнить все операции в транзакции как повторяемую единицу.</span><span class="sxs-lookup"><span data-stu-id="c99b7-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="c99b7-204">Необходимо вручную вызвать стратегию выполнения EF с делегатом, который представляет все, что должно быть выполнено.</span><span class="sxs-lookup"><span data-stu-id="c99b7-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="c99b7-205">В случае временного сбоя стратегия выполнения будет снова вызывать делегат.</span><span class="sxs-lookup"><span data-stu-id="c99b7-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="c99b7-206">В следующем примере кода показано, как реализовать этот подход:</span><span class="sxs-lookup"><span data-stu-id="c99b7-206">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="c99b7-207">Первый DbContext — это \_catalogContext, а второй DbContext находится в объекте \_integrationEventLogService.</span><span class="sxs-lookup"><span data-stu-id="c99b7-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="c99b7-208">Наконец, действие фиксации выполняется в нескольких DbContext с помощью стратегии выполнения EF.</span><span class="sxs-lookup"><span data-stu-id="c99b7-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="c99b7-209">Ссылки — получение Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="c99b7-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="c99b7-210">**Документация по EF Core**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="c99b7-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="c99b7-211">**EF Core. Связанные данные**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="c99b7-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="c99b7-212">**Avoid Lazy Loading Entities in ASP.NET Applications**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications> (Предотвращение отложенной загрузки сущностей в приложениях ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="c99b7-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="c99b7-213">EF Core или микро-ORM?</span><span class="sxs-lookup"><span data-stu-id="c99b7-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="c99b7-214">EF Core хорошо подходит для управления сохраняемостью и по большей части инкапсулирует детали базы данных, освобождая от труда разработчиков приложения. Но это средство — не единственный вариант.</span><span class="sxs-lookup"><span data-stu-id="c99b7-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="c99b7-215">Популярное альтернативное решение с открытым кодом — [Dapper](https://github.com/StackExchange/Dapper), который также называется микро-ORM.</span><span class="sxs-lookup"><span data-stu-id="c99b7-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="c99b7-216">Микро-ORM — это упрощенное средство сопоставления объектов со структурами данных, обладающее сокращенным набором функции.</span><span class="sxs-lookup"><span data-stu-id="c99b7-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="c99b7-217">Основной задачей Dapper является оптимизация производительности при проектировании, а не полная инкапсуляция базовых запросов, которые используются для извлечения и обновления данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="c99b7-218">Поскольку это средство не абстрагирует SQL от разработчика, Dapper является более низкоуровневым инструментом, позволяя разработчикам создавать точные запросы, которые они хотят использовать для конкретных операций доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="c99b7-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="c99b7-219">EF Core может предложить две существенных функциональных возможности, которые отличают эту платформу Dapper, но при этом приводят к снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="c99b7-220">Первая из них — это преобразование выражений LINQ в SQL.</span><span class="sxs-lookup"><span data-stu-id="c99b7-220">The first is the translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="c99b7-221">Эти преобразования кэшируются, однако даже в этом случае при их первом выполнении производительность снижается.</span><span class="sxs-lookup"><span data-stu-id="c99b7-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="c99b7-222">Вторая возможность — отслеживание изменений сущностей, что позволяет создавать эффективные операторы обновления.</span><span class="sxs-lookup"><span data-stu-id="c99b7-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="c99b7-223">Такое поведение можно отключить для конкретных запросов с помощью расширения <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A>.</span><span class="sxs-lookup"><span data-stu-id="c99b7-223">This behavior can be turned off for specific queries by using the <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> extension.</span></span> <span data-ttu-id="c99b7-224">EF Core также создает эффективные SQL-запросы, которые крайне эффективны и в любом случае приемлемы с точки зрения производительности. Однако если вам требуется детальный контроль над тем, какой в точности запрос выполняется, вы также можете передать настраиваемый SQL (или выполнить хранимую процедуру) с помощью EF Core.</span><span class="sxs-lookup"><span data-stu-id="c99b7-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="c99b7-225">В такой ситуации Dapper по-прежнему, хотя и незначительно, превосходит EF Core в отношении производительности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="c99b7-226">Джули Лерман (Julie Lerman) приводит некоторые данные по производительности в статье MSDN [Dapper, Entity Framework и гибридные приложения](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps) за май 2016 г.</span><span class="sxs-lookup"><span data-stu-id="c99b7-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="c99b7-227">Дополнительные данные по тестированию производительности для различных методов доступа к данным можно найти на [сайте Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="c99b7-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="c99b7-228">Чтобы ознакомиться с различиями в синтаксисе между Dapper и EF Core, рассмотрите следующие две версии одного и того же метода, извлекающего список элементов:</span><span class="sxs-lookup"><span data-stu-id="c99b7-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="c99b7-229">Для построения более сложных графов объектов с помощью Dapper вам потребуется написать связанные запросы самостоятельно (в отличие от EF Core, где для этого используется Include).</span><span class="sxs-lookup"><span data-stu-id="c99b7-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="c99b7-230">Эта функциональная возможность поддерживается разными вариантами синтаксиса, в том числе с помощью функции множественного сопоставления, которая позволяет сопоставлять отдельные строки с несколькими сопоставленными объектами.</span><span class="sxs-lookup"><span data-stu-id="c99b7-230">This functionality is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="c99b7-231">Например, для класса Post со свойством Owner типа User следующий SQL-код будет возвращать все необходимые данные:</span><span class="sxs-lookup"><span data-stu-id="c99b7-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="c99b7-232">Каждая возвращаемая строка будет включать данные User и Post.</span><span class="sxs-lookup"><span data-stu-id="c99b7-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="c99b7-233">Поскольку данные User должны быть присоединены к данным Post посредством свойства Owner, используется следующая функция:</span><span class="sxs-lookup"><span data-stu-id="c99b7-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="c99b7-234">Полный код, возвращающий коллекцию элементов Post, свойства Owner которых будут заполнены соответствующими данными User, будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c99b7-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="c99b7-235">Dapper обеспечивает более низкий уровень инкапсуляции, в связи с чем разработчики должны знать больше о том, как хранятся их данные, как эффективно выполнять запросы к ним, а также о том, как писать дополнительный код для их получения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="c99b7-236">Если модель изменяется вместо создания новой миграции (еще одна функция EF Core) и (или) обновления данных сопоставления в одном месте в DbContext, необходимо обновить каждый затрагиваемый запрос.</span><span class="sxs-lookup"><span data-stu-id="c99b7-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="c99b7-237">Для таких запросов не гарантируется время компиляции. Поэтому они могут завершиться сбоем во время выполнения при любых изменениях в модели или базе данных. Это значительно усложняет своевременное выявление ошибок.</span><span class="sxs-lookup"><span data-stu-id="c99b7-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="c99b7-238">Тем не менее эти недостатки Dapper компенсирует крайне высокой производительностью.</span><span class="sxs-lookup"><span data-stu-id="c99b7-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="c99b7-239">Для большинства приложений и большинства компонентов практически любых приложений EF Core предлагает приемлемый уровень производительности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="c99b7-240">Таким образом, преимущества в удобстве для разработчика в большинстве случаев перевешивают возможное снижение производительности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="c99b7-241">Для запросов, эффективность которых может быть повышена за счет кэширования, фактический запрос выполняется крайне редко, в связи с чем эти относительно небольшие различия в производительности обработки запросов теряют значимость.</span><span class="sxs-lookup"><span data-stu-id="c99b7-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="c99b7-242">SQL или NoSQL</span><span class="sxs-lookup"><span data-stu-id="c99b7-242">SQL or NoSQL</span></span>

<span data-ttu-id="c99b7-243">Реляционные базы данных, такие как SQL Server, традиционно занимают львиную долю рынка решений для хранения постоянных данных, однако они также не являются единственным решением.</span><span class="sxs-lookup"><span data-stu-id="c99b7-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="c99b7-244">Такие базы данных NoSQL, как [MongoDB](https://www.mongodb.com/what-is-mongodb), предлагают другой подход к хранению объектов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="c99b7-245">Вместо сопоставления объектов с таблицами и строками выполняется сериализация всего графа объектов с сохранением результата.</span><span class="sxs-lookup"><span data-stu-id="c99b7-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="c99b7-246">Преимущества такого подхода, как минимум на начальной стадии, заключаются в простоте и производительности.</span><span class="sxs-lookup"><span data-stu-id="c99b7-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="c99b7-247">Проще хранить один сериализованный объект с ключом, чем разбивать его на множество таблиц, связанных различными отношениями, и обновлять строки, которые могли быть изменены с момента последнего получения объекта из базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="c99b7-248">Аналогичным образом, получение и десериализация одного объекта из основанного на ключах хранилища, как правило, выполняется значительно быстрее и проще, чем сложные объединения или множественные запросы к базе данных, необходимые для полного воссоздания объекта на основе реляционной базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="c99b7-249">Отсутствие блокировок, транзакций или фиксированной схемы также обеспечивает высокую степень пригодности баз данных NoSQL для масштабирования на множестве компьютеров для поддержки очень крупных наборов данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="c99b7-250">С другой стороны, базы данных NoSQL имеют свои недостатки.</span><span class="sxs-lookup"><span data-stu-id="c99b7-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="c99b7-251">Для обеспечения согласованности и предотвращения дублирования данных в реляционных базах данных применяется нормализация.</span><span class="sxs-lookup"><span data-stu-id="c99b7-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="c99b7-252">Это позволяет уменьшить общий размер базы данных и гарантировать немедленную доступность обновлений общих данных на уровне всей базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-252">This approach reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="c99b7-253">В реляционной базе данных таблица Address может ссылаться на таблицу Country по идентификатору. Таким образом, при изменении названия страны или региона записи адресов будут использовать обновленные данные и не потребуют отдельного обновления.</span><span class="sxs-lookup"><span data-stu-id="c99b7-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="c99b7-254">Тем не менее в базе данных NoSQL таблица Address и связанная с ней таблица Country могут быть сериализованы в составе множества хранимых объектов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-254">However, in a NoSQL database, Address, and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="c99b7-255">В таких случаях при изменении названия страны или региона потребуется обновить все такие объекты, а не одну строку.</span><span class="sxs-lookup"><span data-stu-id="c99b7-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="c99b7-256">Реляционные базы данных также гарантируют реляционную целостность посредством применения правил, например внешних ключей.</span><span class="sxs-lookup"><span data-stu-id="c99b7-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="c99b7-257">Базы данных NoSQL, как правило, не реализуют такие ограничения для данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="c99b7-258">Также с базами данных NoSQL связаны трудности при управлении версиями.</span><span class="sxs-lookup"><span data-stu-id="c99b7-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="c99b7-259">При изменении свойств объекта может быть невозможна десериализация объекта на основе хранимых предыдущих версий.</span><span class="sxs-lookup"><span data-stu-id="c99b7-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="c99b7-260">Таким образом, все существующие объекты, у которых есть сериализованная (предыдущая) версия, должны быть обновлены в соответствии с новой схемой.</span><span class="sxs-lookup"><span data-stu-id="c99b7-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="c99b7-261">Такой подход не имеет принципиальных различий с реляционными базами данных, в которых изменение схемы иногда требует обновления скриптов или сопоставления обновлений.</span><span class="sxs-lookup"><span data-stu-id="c99b7-261">This approach is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="c99b7-262">Тем не менее для баз данных NoSQL число изменяемых записей зачастую намного больше из-за большего объема дублированных данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="c99b7-263">В базах данных NoSQL может храниться несколько версий объектов, что в некоторых реляционных базах данных обычно не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c99b7-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="c99b7-264">Однако в данном случае в коде приложения необходимо учитывать существование предыдущих версий объектов, что увеличивает сложность.</span><span class="sxs-lookup"><span data-stu-id="c99b7-264">However, in this case, your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="c99b7-265">В базах данных NoSQL, как правило, не применяется концепция [ACID](https://en.wikipedia.org/wiki/ACID) (атомарность, согласованность, изолированность, устойчивость), в связи с чем они превосходят реляционные базы данных в отношении производительности и масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="c99b7-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="c99b7-266">Такие базы данных хорошо подходят для очень больших наборов данных и объектов, которые неэффективно хранить в нормализованных табличных структурах.</span><span class="sxs-lookup"><span data-stu-id="c99b7-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="c99b7-267">При этом нет никаких ограничений на использование преимуществ как реляционных баз, так и баз данных NoSQL, в рамках одного приложения в тех случаях, где это необходимо.</span><span class="sxs-lookup"><span data-stu-id="c99b7-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="c99b7-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="c99b7-268">Azure Cosmos DB</span></span>

<span data-ttu-id="c99b7-269">Azure Cosmos DB — это полностью управляемая служба баз данных NoSQL, которая предлагает облачное хранилище данных без схемы.</span><span class="sxs-lookup"><span data-stu-id="c99b7-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="c99b7-270">Cosmos DB обеспечивает высокую прогнозируемую производительность, высокую доступность, эластичную масштабируемость и возможность глобального распределения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="c99b7-271">Несмотря на то, что это база данных NoSQL, разработчики могут использовать все хорошо знакомые возможности SQL-запросов к данным JSON.</span><span class="sxs-lookup"><span data-stu-id="c99b7-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="c99b7-272">Все ресурсы в Azure Cosmos DB хранятся в виде документов JSON.</span><span class="sxs-lookup"><span data-stu-id="c99b7-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="c99b7-273">Ресурсы управляются в виде _элементов_ (документы, содержащие метаданные) и _веб-каналов_, которые представляют собой коллекции элементов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="c99b7-274">На рис. 8-2 показаны связи между разными ресурсами Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="c99b7-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Иерархические связи между ресурсами в Azure Cosmos DB (база данных JSON NoSQL)](./media/image8-2.png)

<span data-ttu-id="c99b7-276">**Рис. 8-2.**</span><span class="sxs-lookup"><span data-stu-id="c99b7-276">**Figure 8-2.**</span></span> <span data-ttu-id="c99b7-277">Организация ресурсов Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="c99b7-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="c99b7-278">Язык запросов Azure Cosmos DB — это простой, но мощный интерфейс для создания запросов документов JSON.</span><span class="sxs-lookup"><span data-stu-id="c99b7-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="c99b7-279">Этот язык поддерживает подмножество грамматических конструкций SQL ANSI и реализует углубленную интеграцию объектов, массивов, возможностей конструирования объектов и вызова функций JavaScript.</span><span class="sxs-lookup"><span data-stu-id="c99b7-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="c99b7-280">**Ссылки. Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="c99b7-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="c99b7-281">Основные сведения об Azure Cosmos DB <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="c99b7-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="c99b7-282">Другие варианты сохраняемости</span><span class="sxs-lookup"><span data-stu-id="c99b7-282">Other persistence options</span></span>

<span data-ttu-id="c99b7-283">В дополнение к реляционным и NoSQL вариантам хранения, в приложениях ASP.NET Core можно использовать облачное масштабируемое хранилище Azure для хранения данных и файлов в различных форматах.</span><span class="sxs-lookup"><span data-stu-id="c99b7-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="c99b7-284">Хранилище Azure обеспечивает высокую степень масштабируемости, позволяя начать с хранения небольших объемов данных и при необходимости увеличить объем хранилища до сотен терабайт.</span><span class="sxs-lookup"><span data-stu-id="c99b7-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="c99b7-285">Хранилище Azure поддерживает четыре вида данных:</span><span class="sxs-lookup"><span data-stu-id="c99b7-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="c99b7-286">Хранилище BLOB-объектов для хранения неструктурированных текстовых или двоичных данных, которое также называется хранилищем объектов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="c99b7-287">Хранилище таблиц для структурированных наборов данных, доступных по ключам строк.</span><span class="sxs-lookup"><span data-stu-id="c99b7-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="c99b7-288">Хранилище очередей для надежного обмена сообщениями на основе очередей.</span><span class="sxs-lookup"><span data-stu-id="c99b7-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="c99b7-289">Хранилище файлов для совместного доступа к файлам между виртуальными машинами Azure и локальными приложениями.</span><span class="sxs-lookup"><span data-stu-id="c99b7-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="c99b7-290">**Ссылки — хранилище Azure**</span><span class="sxs-lookup"><span data-stu-id="c99b7-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="c99b7-291">Общие сведения о службе хранилища Azure <https://docs.microsoft.com/azure/storage/common/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="c99b7-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/common/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="c99b7-292">Кэширование</span><span class="sxs-lookup"><span data-stu-id="c99b7-292">Caching</span></span>

<span data-ttu-id="c99b7-293">В веб-приложениях каждый веб-запрос должен быть выполнен в максимально короткое время.</span><span class="sxs-lookup"><span data-stu-id="c99b7-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="c99b7-294">Одним из способов добиться этого является ограничение числа внешних вызовов, которые сервер должен выполнить для обработки запроса.</span><span class="sxs-lookup"><span data-stu-id="c99b7-294">One way to achieve this functionality is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="c99b7-295">Процесс кэширования предусматривает сохранение копии данных на сервере (или в другом хранилище данных, запросы к которому выполняются более эффективно по сравнению с источником данных).</span><span class="sxs-lookup"><span data-stu-id="c99b7-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="c99b7-296">Веб-приложения, в особенности традиционные многостраничные веб-приложения, для каждого запроса должны осуществлять полное построение пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c99b7-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="c99b7-297">При этом в пользовательских запросах, следующих друг за другом, часто выполняются одни и те же запросы к базе данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-297">This approach frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="c99b7-298">В большинстве случаев эти данные редко изменяются, поэтому не имеет практического смысла постоянно запрашивать их из базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="c99b7-299">ASP.NET Core поддерживает кэширование ответов для кэширования страниц целиком, а также кэширование данных, благодаря которому обеспечивается более детальная реализация кэширования.</span><span class="sxs-lookup"><span data-stu-id="c99b7-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="c99b7-300">При реализации кэширования важно учитывать необходимость разделения задач.</span><span class="sxs-lookup"><span data-stu-id="c99b7-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="c99b7-301">Рекомендуется избегать кэширования логики в логике доступа к данным или в пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="c99b7-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="c99b7-302">Вместо этого следует инкапсулировать кэширование в собственных классах и использовать конфигурацию для управления ее поведением.</span><span class="sxs-lookup"><span data-stu-id="c99b7-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="c99b7-303">Такой подход соответствует принципам открытости/закрытости и персональной ответственности, позволяя управлять использованием кэширования в приложении по мере его расширения.</span><span class="sxs-lookup"><span data-stu-id="c99b7-303">This approach follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="c99b7-304">Кэширование ответов в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c99b7-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="c99b7-305">ASP.NET Core поддерживает два уровня кэширования ответов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="c99b7-306">На первом уровне на сервере ничего не кэшируется, однако добавляются заголовки HTTP с инструкциями по кэшированию ответов для клиентов и прокси-серверов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="c99b7-307">Это реализуется путем добавления атрибута ResponseCache в отдельные контроллеры или действия:</span><span class="sxs-lookup"><span data-stu-id="c99b7-307">This functionality is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="c99b7-308">В предыдущем примере к ответу будет добавлен следующий заголовок, предписывающий клиентам кэшировать результат до 60 секунд.</span><span class="sxs-lookup"><span data-stu-id="c99b7-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="c99b7-309">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="c99b7-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="c99b7-310">Чтобы добавить в приложение кэширование в памяти на стороне сервера, необходимо сослаться на пакет NuGet Microsoft.AspNetCore.ResponseCaching и добавить ПО промежуточного слоя для кэширования ответов.</span><span class="sxs-lookup"><span data-stu-id="c99b7-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="c99b7-311">ПО промежуточного слоя настраивается в методах ConfigureServices и Configure в классе Startup:</span><span class="sxs-lookup"><span data-stu-id="c99b7-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="c99b7-312">ПО промежуточного слоя для кэширования ответов будет автоматически кэшировать ответы на основе набора условий, которые при необходимости можно настроить.</span><span class="sxs-lookup"><span data-stu-id="c99b7-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="c99b7-313">По умолчанию кэшируются только ответы 200 (OK) на запросы, выполненные с помощью методов GET или HEAD.</span><span class="sxs-lookup"><span data-stu-id="c99b7-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="c99b7-314">Кроме того, запросы должны иметь ответ Cache-Control: открытый заголовок и не могут включать заголовки для Authorization или Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="c99b7-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="c99b7-315">См. [полный перечень условий кэширования, применяемых ПО промежуточного уровня для кэширования ответов](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="c99b7-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="c99b7-316">Кэширование данных</span><span class="sxs-lookup"><span data-stu-id="c99b7-316">Data caching</span></span>

<span data-ttu-id="c99b7-317">Вместо кэширования полных веб-ответов или в дополнение к нему вы можете кэшировать результаты отдельных запросов данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="c99b7-318">Для этого вы можете использовать кэширование в памяти на веб-сервере или [распределенный кэш](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="c99b7-318">For this functionality, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="c99b7-319">В этом разделе демонстрируется, как реализовать кэширование в памяти.</span><span class="sxs-lookup"><span data-stu-id="c99b7-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="c99b7-320">Поддержка кэширования в памяти (или распределенного кэша) добавляется в ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="c99b7-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="c99b7-321">Также не забудьте добавить пакет Microsoft.Extensions.Caching.Memory NuGet.</span><span class="sxs-lookup"><span data-stu-id="c99b7-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="c99b7-322">После добавления службы вы выполняете запрос IMemoryCache посредством внедрения зависимостей каждый раз, когда вам требуется доступ к кэшу.</span><span class="sxs-lookup"><span data-stu-id="c99b7-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="c99b7-323">В этом примере служба CachedCatalogService использует конструктивный шаблон прокси-сервера (или декоратора), предоставляя альтернативную реализацию ICatalogService, которая управляет доступом к базовой реализации CatalogService или дополняет ее поведение.</span><span class="sxs-lookup"><span data-stu-id="c99b7-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="c99b7-324">Чтобы настроить в приложении использование кэшированной версии службы и при этом разрешить службе получать экземпляр CatalogService, который требуется в ее конструкторе, необходимо добавить в ConfigureServices следующий код:</span><span class="sxs-lookup"><span data-stu-id="c99b7-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following lines in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="c99b7-325">После этого вызовы базы данных для получения данных каталога будут выполняться только один раз в минуту, а не при каждом запросе.</span><span class="sxs-lookup"><span data-stu-id="c99b7-325">With this code in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="c99b7-326">В зависимости от объема трафика на сайте это может повлиять на число запросов к базе данных и среднее время загрузки домашней страницы, которое сейчас зависит от всех трех запросов, предоставляемых этой службой.</span><span class="sxs-lookup"><span data-stu-id="c99b7-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="c99b7-327">При использовании кэширования возникает проблема _устаревших данных_, то есть данных, которые были изменены в источнике, но для которых в кэше хранится устаревшая версия.</span><span class="sxs-lookup"><span data-stu-id="c99b7-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="c99b7-328">Самый простой способ устранить эту проблему заключается в сокращении продолжительности кэширования, так как в приложениях с высоким уровнем загрузки увеличение продолжительности кэширования данных дает минимальные преимущества.</span><span class="sxs-lookup"><span data-stu-id="c99b7-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is a limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="c99b7-329">Рассмотрим страницу, которая выполняет 1 запрос к базе данных, который повторяется 10 раз в секунду.</span><span class="sxs-lookup"><span data-stu-id="c99b7-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="c99b7-330">Если эта страница будет кэшироваться 1 раз в минуту, число запросов к базе данных за минуту уменьшится с 600 до 1, то есть на 99,8 %.</span><span class="sxs-lookup"><span data-stu-id="c99b7-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="c99b7-331">Если вместо этого задать продолжительность кэширования в 1 час, число запросов сократится на 99,997 %, однако при этом значительно увеличится вероятность получения устаревших данных и их потенциальный "возраст".</span><span class="sxs-lookup"><span data-stu-id="c99b7-331">If instead the cache duration was made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="c99b7-332">Другой подход заключается в упреждающем удалении записей кэша при обновлении данных, которые они содержат.</span><span class="sxs-lookup"><span data-stu-id="c99b7-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="c99b7-333">Любую отдельную запись можно удалить по ее ключу:</span><span class="sxs-lookup"><span data-stu-id="c99b7-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="c99b7-334">Если в вашем приложении предоставляются функции обновления кэшируемых записей, вы можете удалять соответствующие записи кэша в коде, который выполняет обновления.</span><span class="sxs-lookup"><span data-stu-id="c99b7-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="c99b7-335">В некоторых случаях от конкретного набора данных может зависеть множество различных записей.</span><span class="sxs-lookup"><span data-stu-id="c99b7-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="c99b7-336">В таких ситуациях рекомендуется создать зависимости между записями кэша с помощью CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="c99b7-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="c99b7-337">Используя CancellationChangeToken, вы можете одновременно завершить срок действия нескольких записей, аннулировав этот маркер.</span><span class="sxs-lookup"><span data-stu-id="c99b7-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="c99b7-338">Кэширование может значительно повысить производительность веб-страниц, которые постоянно запрашивают одни и те же значения из базы данных.</span><span class="sxs-lookup"><span data-stu-id="c99b7-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="c99b7-339">Обязательно измеряйте производительность доступа к данным и страниц перед применением кэширования и используйте кэширование только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="c99b7-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="c99b7-340">Кэширование потребляет ресурсы памяти веб-сервера и увеличивает сложность приложения, поэтому очень важно не внедрять оптимизацию с помощью этой методики преждевременно.</span><span class="sxs-lookup"><span data-stu-id="c99b7-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

## <a name="getting-data-to-no-locblazor-no-locwebassembly-apps"></a><span data-ttu-id="c99b7-341">Получение данных для приложений Blazor WebAssembly</span><span class="sxs-lookup"><span data-stu-id="c99b7-341">Getting data to Blazor WebAssembly apps</span></span>

<span data-ttu-id="c99b7-342">При создании приложений, использующих Blazor Server, можно использовать Entity Framework и другие технологии прямого доступа к данным, как описано выше в этой главе.</span><span class="sxs-lookup"><span data-stu-id="c99b7-342">If you're building apps that use Blazor Server, you can use Entity Framework and other direct data access technologies as they've been discussed thus far in this chapter.</span></span> <span data-ttu-id="c99b7-343">Однако при создании приложений Blazor WebAssembly, таких как другие платформы SPA, потребуется другая стратегия доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="c99b7-343">However, when building Blazor WebAssembly apps, like other SPA frameworks, you will need a different strategy for data access.</span></span> <span data-ttu-id="c99b7-344">Как правило, эти приложения обращаются к данным и взаимодействуют с сервером через конечные точки веб-API.</span><span class="sxs-lookup"><span data-stu-id="c99b7-344">Typically, these applications access data and interact with the server through web API endpoints.</span></span>

<span data-ttu-id="c99b7-345">Если данные или операции выполняются с учетом секрета, обязательно ознакомьтесь с разделом о безопасности в [предыдущей главе](develop-asp-net-core-mvc-apps.md) и защитите свои интерфейсы API от несанкционированного доступа.</span><span class="sxs-lookup"><span data-stu-id="c99b7-345">If the data or operations being performed are sensitive, be sure to review the section on security in the [previous chapter](develop-asp-net-core-mvc-apps.md) and protect your APIs against unauthorized access.</span></span>

<span data-ttu-id="c99b7-346">Пример приложения Blazor WebAssembly можно найти в [эталонном приложении eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) в проекте BlazorAdmin.</span><span class="sxs-lookup"><span data-stu-id="c99b7-346">You'll find an example of a Blazor WebAssembly app in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb), in the BlazorAdmin project.</span></span> <span data-ttu-id="c99b7-347">Этот проект размещается в веб-проекте eShopOnWeb и позволяет пользователям в группе "Администраторы" управлять элементами в хранилище.</span><span class="sxs-lookup"><span data-stu-id="c99b7-347">This project is hosted within the eShopOnWeb Web project, and allows users in the Administrators group to manage the items in the store.</span></span> <span data-ttu-id="c99b7-348">Снимок экрана приложения представлен на рисунке 8-3.</span><span class="sxs-lookup"><span data-stu-id="c99b7-348">You can see a screenshot of the application in Figure 8-3.</span></span>

![Снимок экрана администратора каталога eShopOnWeb](./media/image8-3.jpg)

<span data-ttu-id="c99b7-350">**Рис. 8-3**.</span><span class="sxs-lookup"><span data-stu-id="c99b7-350">**Figure 8-3.**</span></span> <span data-ttu-id="c99b7-351">Снимок экрана администратора каталога eShopOnWeb.</span><span class="sxs-lookup"><span data-stu-id="c99b7-351">eShopOnWeb Catalog Admin Screenshot.</span></span>

<span data-ttu-id="c99b7-352">При выборке данных из веб-API в приложении Blazor WebAssembly вы просто используете экземпляр `HttpClient` как в любом приложении .NET.</span><span class="sxs-lookup"><span data-stu-id="c99b7-352">When fetching data from web APIs within a Blazor WebAssembly app, you just use an instance of `HttpClient` as you would in any .NET application.</span></span> <span data-ttu-id="c99b7-353">Основные этапы — создание запроса на отправку (если это необходимо, обычно для запросов POST или PUT), ожидание запроса, проверка кода состояния и десериализация ответа.</span><span class="sxs-lookup"><span data-stu-id="c99b7-353">The basic steps involved are to create the request to send (if necessary, usually for POST or PUT requests), await the request itself, verify the status code, and deserialize the response.</span></span> <span data-ttu-id="c99b7-354">Если вы собираетесь делать много запросов к определенному набору API, рекомендуется инкапсулировать их и настроить базовый адрес `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-354">If you're going to make many requests to a given set of APIs, it's a good idea to encapsulate your APIs and configure the `HttpClient` base address centrally.</span></span> <span data-ttu-id="c99b7-355">Таким образом, если необходимо изменить любой из этих параметров между средами, можно внести изменения только в одном месте.</span><span class="sxs-lookup"><span data-stu-id="c99b7-355">This way, if you need to adjust any of these settings between environments, you can make the changes in just one place.</span></span> <span data-ttu-id="c99b7-356">Необходимо добавить поддержку для этой службы в `Program.Main`:</span><span class="sxs-lookup"><span data-stu-id="c99b7-356">You should add support for this service in your `Program.Main`:</span></span>

```csharp
builder.Services.AddScoped(sp =>
    new HttpClient
    {
        BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
    });
```

<span data-ttu-id="c99b7-357">Если необходимо безопасно получить доступ к службам, необходимо получить доступ к безопасному маркеру и настроить `HttpClient` для передачи этого маркера в качестве заголовка проверки подлинности с каждым запросом:</span><span class="sxs-lookup"><span data-stu-id="c99b7-357">If you need to access services securely, you should access a secure token and configure the `HttpClient` to pass this token as an Authentication header with every request:</span></span>

```csharp
_httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", token);
```

<span data-ttu-id="c99b7-358">Это можно сделать из любого компонента, в который внедрен `HttpClient`, при условии, что `HttpClient` не был добавлен в службы приложения с временем существования `Transient`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-358">This activity can be done from any component that has the `HttpClient` injected into it, provided that `HttpClient` wasn't added to the application's services with a `Transient` lifetime.</span></span> <span data-ttu-id="c99b7-359">Каждая ссылка на `HttpClient` в приложении ссылается на один и тот же экземпляр, поэтому изменения в одном компоненте проходят через все приложение.</span><span class="sxs-lookup"><span data-stu-id="c99b7-359">Every reference to `HttpClient` in the application references the same instance, so changes to it in one component flow through the entire application.</span></span> <span data-ttu-id="c99b7-360">Хорошим местом для выполнения этой проверки подлинности (а затем указания маркера) является общий компонент, такой как основная навигация по сайту.</span><span class="sxs-lookup"><span data-stu-id="c99b7-360">A good place to perform this authentication check (followed by specifying the token) is in a shared component like the main navigation for the site.</span></span> <span data-ttu-id="c99b7-361">Дополнительные сведения об этом подходе см. в проекте `BlazorAdmin` [эталонного приложения ShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="c99b7-361">Learn more about this approach in the `BlazorAdmin` project in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

<span data-ttu-id="c99b7-362">Одним из преимуществ Blazor WebAssembly перед традиционными одностраничными приложениями JavaScript является то, что не нужно синхронизировать копии объектов передачи данных (DTO).</span><span class="sxs-lookup"><span data-stu-id="c99b7-362">One benefit of Blazor WebAssembly over traditional JavaScript SPAs is that you don't need to keep to copies of your data transfer objects(DTOs) synchronized.</span></span> <span data-ttu-id="c99b7-363">Проект Blazor WebAssembly и проект веб-API могут совместно использовать одни и те же DTO в одном общем проекте.</span><span class="sxs-lookup"><span data-stu-id="c99b7-363">Your Blazor WebAssembly project and your web API project can both share the same DTOs in a common shared project.</span></span> <span data-ttu-id="c99b7-364">Это устраняет некоторые проблемы, связанные с разработкой одностраничных приложений.</span><span class="sxs-lookup"><span data-stu-id="c99b7-364">This approach eliminates some of the friction involved in developing SPAs.</span></span>

<span data-ttu-id="c99b7-365">Чтобы быстро получить данные из конечной точки API, можно использовать встроенный вспомогательный метод `GetFromJsonAsync`.</span><span class="sxs-lookup"><span data-stu-id="c99b7-365">To quickly get data from an API endpoint, you can use the built-in helper method, `GetFromJsonAsync`.</span></span> <span data-ttu-id="c99b7-366">Существуют аналогичные методы для POST, PUT и т. д. Ниже показано, как получить класс CatalogItem из конечной точки API с помощью настроенного `HttpClient` в приложении Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="c99b7-366">There are similar methods for POST, PUT, etc. The following shows how to get a CatalogItem from an API endpoint using a configured `HttpClient` in a Blazor WebAssembly app:</span></span>

```csharp
var item = await _httpClient.GetFromJsonAsync<CatalogItem>($"catalog-items/{id}");
```

<span data-ttu-id="c99b7-367">После получения необходимых данных вы обычно отслеживаете изменения локально.</span><span class="sxs-lookup"><span data-stu-id="c99b7-367">Once you have the data you need, you'll typically track changes locally.</span></span> <span data-ttu-id="c99b7-368">Если требуется внести обновления в серверное хранилище данных, вызовите дополнительные веб-API.</span><span class="sxs-lookup"><span data-stu-id="c99b7-368">When you want to make updates to the backend data store, you'll call additional web APIs for this purpose.</span></span>

<span data-ttu-id="c99b7-369">**Ссылки — данныеBlazor**</span><span class="sxs-lookup"><span data-stu-id="c99b7-369">**References – Blazor Data**</span></span>

- <span data-ttu-id="c99b7-370">Вызов веб-API из ASP.NET Core Blazor</span><span class="sxs-lookup"><span data-stu-id="c99b7-370">Call a web API from ASP.NET Core Blazor</span></span>
  <https://docs.microsoft.com/aspnet/core/blazor/call-web-api>

>[!div class="step-by-step"]
><span data-ttu-id="c99b7-371">[Назад](develop-asp-net-core-mvc-apps.md)
>[Вперед](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="c99b7-371">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
