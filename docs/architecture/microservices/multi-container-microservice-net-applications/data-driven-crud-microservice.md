---
title: Создание простой микрослужбы CRUD на основе данных
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Общие сведения о создании простой микрослужбы CRUD (управляемой данными) в контексте приложения для микрослужб.
ms.date: 08/14/2020
ms.openlocfilehash: 27c9b331573ff08ea16c756552818df285156282
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739873"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="e8ae9-103">Создание простой микрослужбы CRUD на основе данных</span><span class="sxs-lookup"><span data-stu-id="e8ae9-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="e8ae9-104">В этом разделе показывается создание простой микрослужбы, которая выполняет операции create, read, update и delete (CRUD) в источнике данных.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="e8ae9-105">Разработка простой микрослужбы CRUD</span><span class="sxs-lookup"><span data-stu-id="e8ae9-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="e8ae9-106">С точки зрения проектирования этот тип контейнерной микрослужбы очень прост.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="e8ae9-107">Возможно, решаемая проблема не представляет особой сложности, или реализация является лишь проверкой концепции.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Схема, на которой показан шаблон внутренней структуры простой микрослужбы CRUD.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="e8ae9-109">**Рис. 6-4**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-109">**Figure 6-4**.</span></span> <span data-ttu-id="e8ae9-110">Внутренняя структура простой микрослужбы CRUD</span><span class="sxs-lookup"><span data-stu-id="e8ae9-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="e8ae9-111">Примером простой службы на основе данных такого рода является микрослужба каталога из эталонного приложения eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="e8ae9-112">Служба такого типа реализует все свои функции в одном проекте веб-API ASP.NET Core, который включает классы для своей модели данных, бизнес-логику и код доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="e8ae9-113">Она хранит свои связанные данные в базе данных, работающей в SQL Server (в качестве другого контейнера для целей разработки и тестирования), но это может также быть любой обычный узел SQL Server, как показано на рисунке 6-5.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Схема, на которой показан контейнер микрослужбы CRUD на основе данных.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="e8ae9-115">**Рис. 6-5**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-115">**Figure 6-5**.</span></span> <span data-ttu-id="e8ae9-116">Структура простой микрослужбы CRUD на основе данных</span><span class="sxs-lookup"><span data-stu-id="e8ae9-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="e8ae9-117">На предыдущей схеме показана логическая микрослужба каталога, включающая свою базу данных каталога, которая может находиться на том же или другом узле Docker.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="e8ae9-118">Наличие базы данных на том же узле Docker может быть удобно для разработки, но не подходит для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="e8ae9-119">При разработке такого рода службы требуется только [ASP.NET Core](/aspnet/core/) и ORM или API для доступа к данным, например [Entity Framework Core](/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-119">When you are developing this kind of service, you only need [ASP.NET Core](/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](/ef/core/index).</span></span> <span data-ttu-id="e8ae9-120">Можно также автоматически создать метаданные [Swagger](https://swagger.io/) посредством [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore), чтобы предоставить описание возможностей службы, как показано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="e8ae9-121">Обратите внимание, что запуск сервера базы данных, такого как SQL Server, в контейнере Docker отлично подходит для сред разработки, так как вы можете получить все нужные зависимости в полной готовности без необходимости подготовки базы данных в облаке или локально.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="e8ae9-122">Это очень удобно при выполнении интеграционных тестов.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="e8ae9-123">Однако для рабочих сред запуск сервера базы данных в контейнере не рекомендуется, так как при таком подходе обычно не удается добиться высокой доступности.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="e8ae9-124">Для рабочей среды в Azure рекомендуется использовать базу данных SQL Azure или любую другую технологию базы данных, которая может обеспечить высокий уровень доступности и масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="e8ae9-125">Например, для варианта NoSQL можно выбрать CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="e8ae9-126">Наконец, путем редактирования файлов метаданных Dockerfile и docker-compose.yml можно настроить порядок создания образа этого контейнера — какой базовый образ будет использоваться, а также конструктивные параметры, такие как внутренние и внешние имена и порты TCP.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="e8ae9-127">Реализация простой микрослужбы CRUD в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e8ae9-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="e8ae9-128">Чтобы реализовать простую микрослужбу CRUD с помощью Visual Studio и .NET Core, начните с создания простого проекта веб-API ASP.NET Core (работающего в .NET Core, чтобы его можно было запустить на узле Linux Docker), как показано на рисунке 6-6.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Снимок экрана Visual Studio, на котором показана настройка проекта.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="e8ae9-130">**Рис. 6-6**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-130">**Figure 6-6**.</span></span> <span data-ttu-id="e8ae9-131">Создание проекта веб-API ASP.NET Core в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e8ae9-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="e8ae9-132">Для создания проекта веб-API ASP.NET Core сначала выберите веб-приложение ASP.NET Core и затем тип API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="e8ae9-133">После создания проекта вы можете реализовать свои контроллеры MVC, как это делается в любом другом проекте веб-API, с помощью API Entity Framework или другого API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="e8ae9-134">В новом проекте веб-API видно, что единственная имеющаяся в микрослужбе зависимость — в самом ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="e8ae9-135">Внутренним образом зависимость *Microsoft.AspNetCore.All* ссылается на Entity Framework и многие другие пакеты NuGet .NET Core, как показано на рисунке 6-7.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Снимок экрана VS, на котором показаны зависимости NuGet для Catalog.Api.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="e8ae9-137">**Рис. 6-7**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-137">**Figure 6-7**.</span></span> <span data-ttu-id="e8ae9-138">Зависимости в простой микрослужбе CRUD веб-API</span><span class="sxs-lookup"><span data-stu-id="e8ae9-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="e8ae9-139">Проект API содержит ссылки на пакет NuGet Microsoft.AspNetCore.App, включающий в себя ссылки на все основные пакеты.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-139">The API project includes references to Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="e8ae9-140">Кроме того, он может включать и некоторые другие пакеты.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="e8ae9-141">Реализация служб CRUD веб-API с помощью Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="e8ae9-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="e8ae9-142">Entity Framework (EF) — это упрощенная, расширяемая и кроссплатформенная версия популярной технологии для доступа к данным Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="e8ae9-143">EF Core является объектно-реляционным модулем сопоставления (ORM), который позволяет разработчикам .NET работать с базой данных, используя объекты .NET.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="e8ae9-144">Микрослужба каталога использует EF и поставщик SQL Server, так как его база данных работает в контейнере с образом Docker SQL Server для Linux .</span><span class="sxs-lookup"><span data-stu-id="e8ae9-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="e8ae9-145">Тем не менее база данных может быть развернута в любом SQL Server, например локально в Windows или в базе данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="e8ae9-146">Единственное, что потребуется изменить, — это строку подключения в микрослужбе веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="e8ae9-147">Модель данных</span><span class="sxs-lookup"><span data-stu-id="e8ae9-147">The data model</span></span>

<span data-ttu-id="e8ae9-148">В EF Core доступ к данным осуществляется с помощью модели.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="e8ae9-149">Модель состоит из классов сущностей (модель предметной области) и производного контекста (DbContext), который представляет сеанс взаимодействия с базой данных, позволяя запрашивать и сохранять данные.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="e8ae9-150">Вы можете создать модель из существующей базы данных, вручную написать код модели, соответствующей вашей базе данных, или воспользоваться миграциями EF для создания базы данных из своей модели на базе подхода Code First (что упрощает развитие базы данных по мере изменения модели).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations technique to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="e8ae9-151">Для микрослужбы каталога использовался последний подход.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-151">For the catalog microservice, the last approach has been used.</span></span> <span data-ttu-id="e8ae9-152">Пример класса CatalogItem можно увидеть в следующем примере кода, который представляет простой класс сущностей Plain Old CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="e8ae9-153">Также потребуется DbContext, который представляет сеанс работы с базой данных.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="e8ae9-154">Для микрослужбы каталога класс CatalogContext является производным от базового класса DbContext, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

<span data-ttu-id="e8ae9-155">У вас могут быть дополнительные реализации `DbContext`.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="e8ae9-156">Например, в примере микрослужбы Catalog.API образца имеется второй `DbContext` с именем `CatalogContextSeed`, где он автоматически заполняет демонстрационные данные при первой попытке получения доступа к базе данных.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="e8ae9-157">Этот метод полезен для демонстрационных данных, а также в сценариях автоматических тестов.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="e8ae9-158">В `DbContext` используется метод `OnModelCreating` для настройки сопоставлений сущностей объектов или базы данных, а также других [точек расширяемости EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="e8ae9-159">Запрос данных из контроллеров веб-API</span><span class="sxs-lookup"><span data-stu-id="e8ae9-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="e8ae9-160">Экземпляры классов сущностей обычно извлекаются из базы данных с помощью LINQ, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    }
    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="e8ae9-161">Сохранение данных</span><span class="sxs-lookup"><span data-stu-id="e8ae9-161">Saving data</span></span>

<span data-ttu-id="e8ae9-162">Для создания, удаления и изменения данных в базе данных используются экземпляры классов сущностей.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="e8ae9-163">К своим контроллерам веб-API можно добавить код, как в следующем примере с жестким заданием (макета данных в этом случае).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="e8ae9-164">Внедрение зависимостей в ASP.NET Core и контроллеры веб-API</span><span class="sxs-lookup"><span data-stu-id="e8ae9-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="e8ae9-165">В ASP.NET Core можно использовать внедрение зависимостей (DI) без дополнительной настройки.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="e8ae9-166">Не требуется настраивать сторонний контейнер инверсии управления (IoC), хотя при желании можно включить в инфраструктуру ASP.NET Core свой предпочитаемый контейнер IoC.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="e8ae9-167">В данном случае это означает, что вы можете напрямую внедрить требуемый DBContext EF или дополнительные репозитории с помощью конструктора контроллера.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="e8ae9-168">В упомянутом ранее классе `CatalogController` тип `CatalogContext` (который наследуется от типа `DbContext`) внедряется вместе с другими необходимыми объектами в конструкторе `CatalogController()`.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-168">In the `CatalogController` class mentioned earlier, `CatalogContext` (which inherits from `DbContext`) type is injected along with the other required objects in the `CatalogController()` constructor.</span></span>

<span data-ttu-id="e8ae9-169">Важной конфигурацией для настройки в проекте веб-API является регистрация класса DbContext в контейнере IoC службы.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="e8ae9-170">Обычно это делается в классе `Startup` путем вызова метода `services.AddDbContext<CatalogContext>()` в методе `ConfigureServices()`, как показано в следующем **упрощенном** примере:</span><span class="sxs-lookup"><span data-stu-id="e8ae9-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<CatalogContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...
}
```

### <a name="additional-resources"></a><span data-ttu-id="e8ae9-171">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="e8ae9-171">Additional resources</span></span>

- <span data-ttu-id="e8ae9-172">**Запросы к данным** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="e8ae9-173">**Сохранение данных** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="e8ae9-174">Строка подключения к базе данных и переменные среды, используемые контейнерами Docker</span><span class="sxs-lookup"><span data-stu-id="e8ae9-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="e8ae9-175">Вы можете использовать параметры ASP.NET Core и добавить свойство ConnectionString в файл settings.json, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=[PLACEHOLDER]",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="e8ae9-176">Файл settings.json может иметь значения по умолчанию для свойства ConnectionString или любого другого свойства.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="e8ae9-177">Однако при использовании Docker эти свойства будут переопределяться значениями переменных среды, заданными в файле docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="e8ae9-178">Из файлов docker-compose.yml или docker-compose.override.yml можно инициализировать эти переменные среды, чтобы Docker устанавливал их в качестве переменных среды операционной системы, как показано в следующем файле docker-compose.override.yml (в этом примере строка подключения и другие строки переносятся, но в вашем собственном файле они не будут переноситься).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=[PLACEHOLDER]
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="e8ae9-179">Файлы docker-compose.yml на уровне решения не только более гибкие, чем файлы конфигурации на уровне проекта или микрослужбы, но также и более безопасные, если вы переопределяете переменные среды, объявленные в файлах docker-compose, значениями, установленными из инструментов развертывания, например из задач развертывания Docker в Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="e8ae9-180">Наконец, можно получить это значение из кода с помощью Configuration\["ConnectionString"\], как показано в методе ConfigureServices в предыдущем примере кода.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="e8ae9-181">Однако для рабочей среды вы можете исследовать дополнительные возможности по хранению секретов, таких как строки подключения.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="e8ae9-182">Прекрасным способом управления секретами приложений является использование [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="e8ae9-183">Azure Key Vault обеспечивает хранение и защиту ключей шифрования и секретов, используемых облачными приложениями и службами.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="e8ae9-184">Секрет — это все то, что вы хотите жестко контролировать, например ключи API, строки подключения, пароли и т. п., при этом в число средств такого контроля, *среди прочего*, входит ведение журналов использования, срок действия параметров и управление доступом.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="e8ae9-185">Azure Key Vault позволяет очень детально управлять уровнем использования секретов приложений, не раскрывая их никому постороннему.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="e8ae9-186">Секреты можно даже менять, чтобы повысить уровень безопасности, не нарушая процедуры разработки или эксплуатации.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="e8ae9-187">Чтобы приложения могли использовать Key Vault, они должны быть зарегистрированы в Active Directory организации.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="e8ae9-188">Дополнительные сведения см. в *документации об основных понятиях Key Vault*.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="e8ae9-189">Реализация управления версиями в веб-API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e8ae9-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="e8ae9-190">По мере изменения бизнес-требований может происходить добавление новых коллекций ресурсов, изменение связей между ресурсами и совершенствование структуры данных в ресурсах.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="e8ae9-191">Обновление веб-API для обработки новых требований выполняется относительно просто, однако необходимо учитывать воздействие, которое такие изменения будут оказывать на клиентские приложения, использующие веб-API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="e8ae9-192">Несмотря на то, что разработчик, проектирующий и реализующий веб-API, имеет полный контроль над этим API, у него нет той же степени контроля над клиентскими приложениями, которые могут быть созданы сторонними организациями, работающими удаленно.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third-party organizations operating remotely.</span></span>

<span data-ttu-id="e8ae9-193">Управление версиями позволяет веб-API указать компоненты и ресурсы, которые он предоставляет.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="e8ae9-194">Затем клиентское приложение может отправлять запросы к определенной версии функции или ресурса.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="e8ae9-195">Существует несколько методов реализации управления версиями:</span><span class="sxs-lookup"><span data-stu-id="e8ae9-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="e8ae9-196">управление версиями с помощью URI;</span><span class="sxs-lookup"><span data-stu-id="e8ae9-196">URI versioning</span></span>

- <span data-ttu-id="e8ae9-197">управление версиями с помощью строки запроса;</span><span class="sxs-lookup"><span data-stu-id="e8ae9-197">Query string versioning</span></span>

- <span data-ttu-id="e8ae9-198">управление версиями с помощью заголовка.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-198">Header versioning</span></span>

<span data-ttu-id="e8ae9-199">Проще всего реализовать управление версиями с помощью строки заголовка и URI.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="e8ae9-200">Управление версиями с помощью заголовка — хороший метод.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-200">Header versioning is a good approach.</span></span> <span data-ttu-id="e8ae9-201">Но он не настолько явный и простой, как управление версиями с помощью URI.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-201">However, header versioning is not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="e8ae9-202">Так как управление версиями с помощью URI является самым простым и очевидным методом, в эталонном приложении eShopOnContainers используется именно управление версиями с помощью URI.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="e8ae9-203">При использовании управления версиями с помощью URI, как в эталонном приложении eShopOnContainers, при каждом изменении веб-API или схемы ресурсов в URI для каждого ресурса добавляется номер версии.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="e8ae9-204">Существующие URI должны продолжать работать как и прежде, возвращая ресурсы, которые подходят для схемы, соответствующей запрошенной версии.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="e8ae9-205">Как показано в следующем примере кода, версию можно устанавливать с помощью атрибута Route в контроллере веб-API, что делает версию в URI явной (в данном случае это v1).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="e8ae9-206">Этот механизм управления версиями прост и зависит от сервера, направляющего запрос в соответствующую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="e8ae9-207">Однако для более сложного управления версиями и наиболее подходящего метода при использовании REST следует использовать гиперсредства и реализовать подход [HATEOAS (гипертекст как обработчик состояния приложения)](/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e8ae9-208">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="e8ae9-208">Additional resources</span></span>

- <span data-ttu-id="e8ae9-209">**Скотт Ханселман (Scott Hanselman). Упрощение управления версиями веб-API ASP.NET Core с поддержкой REST** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="e8ae9-210">**Управление версиями веб-API с поддержкой REST** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="e8ae9-211">**Рой Филдинг (Roy Fielding). Управление версиями, гипермедиа и REST** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="e8ae9-212">Создание метаданных описания Swagger из веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e8ae9-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="e8ae9-213">[Swagger](https://swagger.io/) — это распространенная платформа с открытым исходным кодом, поддерживаемая большой экосистемой инструментов, помогающих разрабатывать, собирать, документировать и использовать ваши API RESTful.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="e8ae9-214">Она становится стандартом для домена метаданных описания API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="e8ae9-215">Следует включать метаданные описания Swagger в микрослужбы любого вида — и в микрослужбы на основе данных, и в более сложные предметно-ориентированные микрослужбы (как описывается в следующем разделе).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in the following section).</span></span>

<span data-ttu-id="e8ae9-216">Основу Swagger составляет спецификация Swagger, представляющая собой метаданные описания API в файле JSON или YAML.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="e8ae9-217">Эта спецификация создает контракт RESTful для вашего API, детализируя все его ресурсы и операции как в форме, удобной для восприятия человеком, так и в машинно-распознаваемой форме для упрощения разработки, обнаружения и интеграции.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="e8ae9-218">Спецификация является основой спецификации OpenAPI (OAS) и разрабатывается в открытом, прозрачном, совместно работающем сообществе для стандартизации способа определения интерфейсов RESTful.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="e8ae9-219">Спецификация определяет структуру способа обнаружения службы и понимания ее возможностей.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="e8ae9-220">Дополнительные сведения, включая веб-редактор и примеры спецификаций Swagger от таких компаний, как Spotify, Uber, Slack и Майкрософт, см. на сайте Swagger (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="e8ae9-221">Почему следует использовать Swagger?</span><span class="sxs-lookup"><span data-stu-id="e8ae9-221">Why use Swagger?</span></span>

<span data-ttu-id="e8ae9-222">Ниже перечислены основные причины создания метаданных Swagger для ваших API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="e8ae9-223">**Возможность для других продуктов автоматически использовать и интегрировать ваши API**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="e8ae9-224">Десятки продуктов и [коммерческих инструментов](https://swagger.io/commercial-tools/), а также множество [библиотек и платформ](https://swagger.io/open-source-integrations/) поддерживают Swagger.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="e8ae9-225">Корпорация Майкрософт предоставляет высокоуровневые продукты и инструменты, которые могут автоматически использовать API на основе Swagger, например следующие.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="e8ae9-226">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="e8ae9-227">Вы можете автоматически создавать клиентские классы .NET для вызова Swagger.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="e8ae9-228">Этот инструмент можно использовать из CLI, и он также интегрируется с Visual Studio для упрощения использования через графический интерфейс пользователя.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="e8ae9-229">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="e8ae9-230">Вы можете автоматически [использовать и интегрировать свои API](https://flow.microsoft.com/blog/integrating-custom-api/) в высокоуровневый процесс Microsoft Flow без каких-либо навыков программирования.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="e8ae9-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="e8ae9-232">Вы можете автоматически использовать свои API из [мобильных приложений PowerApps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/), созданных с помощью [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), без каких-либо навыков программирования.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="e8ae9-233">[Приложения логики службы приложений Azure](/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-233">[Azure App Service Logic Apps](/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="e8ae9-234">Вы можете автоматически [использовать и интегрировать свои API в приложение логики службы приложений Azure ](/azure/app-service-logic/app-service-logic-custom-hosted-api) без каких-либо навыков программирования.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-234">You can automatically [use and integrate your API into an Azure App Service Logic App](/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="e8ae9-235">**Возможность автоматического создания документации по API**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="e8ae9-236">При создании крупномасштабных API RESTful, например сложных приложений на основе микрослужб, необходимо обрабатывать много конечных точек с разными моделями данных, используемых в полезной нагрузке запросов и ответов.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="e8ae9-237">Наличие соответствующей документации и надежного обозревателя API, что можно получить с помощью Swagger, является ключом для успеха API и внедрения разработчиками.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="e8ae9-238">Метаданные Swagger используются Microsoft Flow, PowerApps и Azure Logic Apps для понимания, как следует использовать API и подключаться к ним.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="e8ae9-239">Существует несколько способов автоматизировать создание метаданных Swagger для приложений REST API ASP.NET Core в виде функциональных страниц справки API на основе *swagger-ui*.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="e8ae9-240">Вероятно, наиболее известен [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore), который сейчас используется в [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers), и мы рассмотрим его подробнее в этом руководстве. Однако можно также использовать [NSwag](https://github.com/RSuter/NSwag), который может создавать клиенты API Typescript и C\#, а также контроллеры C\# на базе спецификации Swagger или OpenAPI и даже посредством сканирования библиотеки DLL, содержащей контроллеры, с помощью [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="e8ae9-241">Автоматизация создания метаданных Swagger API с помощью пакета NuGet Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="e8ae9-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="e8ae9-242">Создание метаданных Swagger вручную (в файле JSON или YAML) может быть утомительным.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="e8ae9-243">Однако вы можете автоматизировать обнаружение API службами веб-API ASP.NET с помощью [пакета NuGet Swashbuckle](https://aka.ms/swashbuckledotnetcore) для динамического создания метаданных Swagger API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="e8ae9-244">Swashbuckle автоматически создает метаданные Swagger для проектов веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="e8ae9-245">Он поддерживает проекты веб-API ASP.NET Core, классические веб-API ASP.NET и любые разновидности, такие как приложение API Azure, мобильное приложение Azure, микрослужбы Azure Service Fabric на основе ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="e8ae9-246">Он также поддерживает простой веб-API, развертываемый в контейнерах, как в эталонном приложении.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="e8ae9-247">Swashbuckle объединяет обозреватель API и Swagger или [пользовательский интерфейс Swagger](https://github.com/swagger-api/swagger-ui) для обеспечения вашим клиентам API широких возможностей использования обнаружения и документации.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="e8ae9-248">Помимо своей подсистемы создания метаданных Swagger, Swashbuckle также содержит встроенную версию пользовательского интерфейса swagger, которую он будет автоматически обслуживать после установки Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="e8ae9-249">Это означает, что вы можете дополнять свой API отличным пользовательским интерфейсом обнаружения, чтобы помочь разработчикам использовать этот API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="e8ae9-250">Для него требуется совсем немного кода и поддержки, так как он создается автоматически, что позволяет сосредоточиться на построении API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="e8ae9-251">Результат в обозревателе API выглядит подобно показанному на рисунке 6-8.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![Снимок экрана: обозреватель API Swagger, в котором отображается API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="e8ae9-253">**Рис. 6-8**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-253">**Figure 6-8**.</span></span> <span data-ttu-id="e8ae9-254">Обозреватель API Swashbuckle на основе метаданных Swagger — микрослужба каталога eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e8ae9-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="e8ae9-255">Созданная Swashbuckle документация по API пользовательского интерфейса Swagger.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="e8ae9-256">Обозреватель API здесь не самое главное.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="e8ae9-257">При наличии веб-API, который может описать сам себя в метаданных Swagger, ваш API можно без проблем использовать в инструментах на основе Swagger, включая генераторы кода клиентского прокси-класса, предназначенные для многих платформ.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="e8ae9-258">Например, как упоминалось ранее, [AutoRest](https://github.com/Azure/AutoRest) автоматически создает клиентские классы .NET.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="e8ae9-259">Однако доступны также и дополнительные средства, например [swagger-codegen](https://github.com/swagger-api/swagger-codegen), что позволяет автоматически создавать код клиентских библиотек API, заглушки сервера и документацию.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="e8ae9-260">В настоящее время Swashbuckle состоит из пяти независимых внутренних пакетов NuGet в высокоуровневом метапакете [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) для приложений ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level metapackage [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="e8ae9-261">После установки этих пакетов NuGet в проекте веб-API нужно настроить Swagger в классе Startup, как показано в следующем **упрощенном** коде:</span><span class="sxs-lookup"><span data-stu-id="e8ae9-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="e8ae9-262">После этого можно запустить приложение и перейти к следующим конечным точкам пользовательского интерфейса и JSON Swagger, используя URL-адреса, подобные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="e8ae9-263">Вы ранее видели пользовательский интерфейс, созданный Swashbuckle и доступный по URL-адресу, например `http://<your-root-url>/swagger`.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="e8ae9-264">На рисунке 6-9 показано, как можно тестировать любой метод API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Снимок экрана: пользовательский интерфейс Swagger, в котором отображаются доступные средства тестирования.](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="e8ae9-266">**Рис. 6-9**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-266">**Figure 6-9**.</span></span> <span data-ttu-id="e8ae9-267">Тестирование метода API Catalog/Items в пользовательском интерфейсе Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="e8ae9-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="e8ae9-268">В сведениях об API пользовательского интерфейса Swagger приведен пример отклика, который можно использовать для выполнения реального API, что отлично подходит для обнаружения разработчика.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="e8ae9-269">На рисунке 6-10 показаны метаданные JSON Swagger, созданные из микрослужбы eShopOnContainers (именно ее инструменты используют на внутреннем уровне) при запросе `http://<your-root-url>/swagger/v1/swagger.json` с помощью [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="e8ae9-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Снимок экрана: пример пользовательского интерфейса Postman, в котором отображаются метаданные Swagger в формате JSON.](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="e8ae9-271">**Рис. 6-10**.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-271">**Figure 6-10**.</span></span> <span data-ttu-id="e8ae9-272">Метаданные JSON Swagger</span><span class="sxs-lookup"><span data-stu-id="e8ae9-272">Swagger JSON metadata</span></span>

<span data-ttu-id="e8ae9-273">Это так просто.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-273">It is that simple.</span></span> <span data-ttu-id="e8ae9-274">И так как они создаются автоматически, метаданные Swagger будет увеличиваться при добавлении дополнительных функций к вашему API.</span><span class="sxs-lookup"><span data-stu-id="e8ae9-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e8ae9-275">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="e8ae9-275">Additional resources</span></span>

- <span data-ttu-id="e8ae9-276">**Страницы справки по веб-API ASP.NET с использованием Swagger** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="e8ae9-277">**Начало работы с Swashbuckle и ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="e8ae9-278">**Начало работы с NSwag и ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e8ae9-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="e8ae9-279">[Назад](microservice-application-design.md)
> [Вперед](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="e8ae9-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
