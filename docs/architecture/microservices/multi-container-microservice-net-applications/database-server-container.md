---
title: Использование сервера баз данных, работающего в качестве контейнера
description: Изучите важность использования сервера базы данных, работающего в качестве контейнера, только для разработки. Не для рабочей среды.
ms.date: 01/13/2021
ms.openlocfilehash: 1292bf37e3baaeb6284f6fba15b4bc7c9c17b4a7
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188742"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="b0d42-104">Использование сервера баз данных, работающего в качестве контейнера</span><span class="sxs-lookup"><span data-stu-id="b0d42-104">Use a database server running as a container</span></span>

<span data-ttu-id="b0d42-105">Базы данных (SQL Server, PostgreSQL, MySQL и т. д.) можно размещать на обычных отдельных серверах, локальных кластерах или службах PaaS в облаке, например Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="b0d42-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="b0d42-106">Но в средах разработки и тестирования удобнее использовать базы данных в виде контейнеров — так у вас нет внешней зависимости, и вы можете запустить все приложение по команде `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="b0d42-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="b0d42-107">При размещении баз данных в контейнерах легче проводить интеграционные тесты, ведь база данных запускается в контейнере и всегда заполняется одинаковыми демонстрационными данными, так что тестирование становится более предсказуемым.</span><span class="sxs-lookup"><span data-stu-id="b0d42-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="b0d42-108">SQL Server, запущенный в качестве контейнера с базой данных для микрослужб</span><span class="sxs-lookup"><span data-stu-id="b0d42-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="b0d42-109">В eShopOnContainers существует контейнер с именем `sqldata`, определенный в файле [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml), который запускает SQL Server для экземпляра Linux со всеми базами данных на SQL Server, необходимыми для микрослужб.</span><span class="sxs-lookup"><span data-stu-id="b0d42-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="b0d42-110">Ключевой точкой микрослужб является то, что каждая микрослужба владеет связанными данными, поэтому она должна иметь собственную базу данных.</span><span class="sxs-lookup"><span data-stu-id="b0d42-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="b0d42-111">Однако базы данных могут находиться где угодно.</span><span class="sxs-lookup"><span data-stu-id="b0d42-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="b0d42-112">В этом случае все они находятся в одном контейнере, чтобы не усложнять требования к памяти Docker.</span><span class="sxs-lookup"><span data-stu-id="b0d42-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="b0d42-113">Помните, что это решение является хорошим для разработки и, возможно, тестирования, но не для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="b0d42-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="b0d42-114">Контейнер SQL Server в примере приложения настроен со следующим кодом YAML в файле docker-compose.yml, который выполняется по команде `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="b0d42-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="b0d42-115">Обратите внимание, что код YAML содержит консолидированные сведения о конфигурации из общего файла docker-compose.yml и файла docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="b0d42-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="b0d42-116">(В обычной ситуации вы отделяете параметры среды от базовой или статической информации, связанной с образом SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="b0d42-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="b0d42-117">Аналогичным образом, вместо `docker-compose` используйте следующую команду `docker run` для запуска контейнера:</span><span class="sxs-lookup"><span data-stu-id="b0d42-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="b0d42-118">Но если вы развертываете приложение с несколькими контейнерами, например eShopOnContainers, удобнее использовать команду `docker-compose up`, чтобы развернуть все необходимые контейнеры для приложения.</span><span class="sxs-lookup"><span data-stu-id="b0d42-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="b0d42-119">Когда вы запускаете этот контейнер SQL Server впервые, он инициализирует SQL Server с помощью указанного вами пароля.</span><span class="sxs-lookup"><span data-stu-id="b0d42-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="b0d42-120">После запуска SQL Server в качестве контейнера вы можете обновить базу данных через обычное подключение SQL, например SQL Server Management Studio, Visual Studio или код C\#.</span><span class="sxs-lookup"><span data-stu-id="b0d42-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="b0d42-121">Приложение eShopOnContainers инициализирует каждую базу данных микрослужбы, заполняя ее демонстрационными данными при запуске, как описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="b0d42-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="b0d42-122">Использовать SQL Server в качестве контейнера удобно не только для демоверсии, где у вас может не быть доступа к экземпляру SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0d42-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="b0d42-123">Это решение также отлично подходит для среды разработки и тестирования, где вы можете легко запустить интеграционные тесты из чистого образа SQL Server с известными данными, присвоив новые демонстрационные данные.</span><span class="sxs-lookup"><span data-stu-id="b0d42-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b0d42-124">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="b0d42-124">Additional resources</span></span>

- <span data-ttu-id="b0d42-125">**Запуск образа SQL Server Docker в Linux, Mac или Windows** </span><span class="sxs-lookup"><span data-stu-id="b0d42-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="b0d42-126">**Подключения и запросы к SQL Server на Linux с помощью sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="b0d42-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="b0d42-127">Заполнение тестовыми данными при запуске веб-приложения</span><span class="sxs-lookup"><span data-stu-id="b0d42-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="b0d42-128">Чтобы заполнить базу данных данными при запуске приложения, вы можете добавить код, как указано ниже, в метод `Main` в классе `Program` проекта веб-API:</span><span class="sxs-lookup"><span data-stu-id="b0d42-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="b0d42-129">При применении миграций и заполнении базы данных во время запуска контейнеров существует важная оговорка.</span><span class="sxs-lookup"><span data-stu-id="b0d42-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="b0d42-130">Поскольку сервер базы данных может быть недоступен по каким-либо причинам, вы должны обрабатывать повторные попытки, пока сервер не будет доступен.</span><span class="sxs-lookup"><span data-stu-id="b0d42-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="b0d42-131">Эта логика повторных попыток обрабатывается методом расширения `MigrateDbContext()`, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="b0d42-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```csharp
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="b0d42-132">Следующий код в пользовательском классе CatalogContextSeed заполняет базу данных данными.</span><span class="sxs-lookup"><span data-stu-id="b0d42-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="b0d42-133">При выполнении интеграционных тестов полезно иметь возможность создавать данные, соответствующие тестам.</span><span class="sxs-lookup"><span data-stu-id="b0d42-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="b0d42-134">Возможность создать все с нуля, включая экземпляр SQL Server в контейнере, имеет серьезные преимущества для тестовых сред.</span><span class="sxs-lookup"><span data-stu-id="b0d42-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="b0d42-135">База данных EF Core InMemory и SQL Server, работающий в качестве контейнера</span><span class="sxs-lookup"><span data-stu-id="b0d42-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="b0d42-136">Еще одно удачное решение для выполнения тестов — использовать базы данных Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="b0d42-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="b0d42-137">Вы можете указать эту конфигурацию в методе ConfigureServices в классе Startup в проекте веб-API:</span><span class="sxs-lookup"><span data-stu-id="b0d42-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

<span data-ttu-id="b0d42-138">Но есть одна сложность.</span><span class="sxs-lookup"><span data-stu-id="b0d42-138">There is an important catch, though.</span></span> <span data-ttu-id="b0d42-139">База данных, выполняющаяся в памяти, не поддерживает многие ограничения, относящиеся к определенной базе данных.</span><span class="sxs-lookup"><span data-stu-id="b0d42-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="b0d42-140">Например, вы можете добавить уникальный индекс в столбец в модели EF Core и написать тест для базы данных, выполняющейся в памяти, чтобы проверить, что она не позволяет вам добавлять дублирующие значения.</span><span class="sxs-lookup"><span data-stu-id="b0d42-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="b0d42-141">Но при использовании базы данных, выполняющейся в памяти, вы не можете обрабатывать уникальные индексы в столбце.</span><span class="sxs-lookup"><span data-stu-id="b0d42-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="b0d42-142">Таким образом, базы данных, выполняющиеся в памяти, ведут себя не так, как реальные базы данных SQL Server, — они не эмулируют ограничения, присущие базе данных.</span><span class="sxs-lookup"><span data-stu-id="b0d42-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="b0d42-143">Тем не менее выполняющаяся в памяти база данных подходит для тестирования и создания прототипов.</span><span class="sxs-lookup"><span data-stu-id="b0d42-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="b0d42-144">Но если вы хотите создать точные интеграционные тесты, которые учитывают поведение определенной базы данных, используйте реальную базу данных, например SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0d42-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="b0d42-145">Для этих целей лучше всего использовать SQL Server в контейнере, поскольку результат будет более точным, чем в базе данных EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="b0d42-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="b0d42-146">Использование службы кэша Redis в контейнере</span><span class="sxs-lookup"><span data-stu-id="b0d42-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="b0d42-147">Вы можете запустить Redis в контейнере, особенно для разработки и тестирования, а также подтверждения концепции.</span><span class="sxs-lookup"><span data-stu-id="b0d42-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="b0d42-148">Это удобное решение, поскольку все ваши зависимости будут выполняться в контейнерах — не только на локальных компьютерах для разработки, но и в тестовых средах в конвейерах непрерывной интеграции или поставки.</span><span class="sxs-lookup"><span data-stu-id="b0d42-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="b0d42-149">Но если вы используете Redis в рабочей среде, лучше найти решение с более высоким уровнем доступности, например Redis Microsoft Azure, которое работает как PaaS (платформа как услуга).</span><span class="sxs-lookup"><span data-stu-id="b0d42-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="b0d42-150">В коде достаточно изменить строки подключения.</span><span class="sxs-lookup"><span data-stu-id="b0d42-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="b0d42-151">Redis предоставляет образ Docker с Redis.</span><span class="sxs-lookup"><span data-stu-id="b0d42-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="b0d42-152">Этот образ доступен в центре Docker по URL-адресу:</span><span class="sxs-lookup"><span data-stu-id="b0d42-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="b0d42-153">Вы можете запустить контейнер Docker Redis напрямую, выполнив следующую команду Docker CLI в командной строке:</span><span class="sxs-lookup"><span data-stu-id="b0d42-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="b0d42-154">Образ Redis включает expose:6379 (порт, используемый Redis), поэтому при стандартном связывании контейнеров он будет автоматически доступен связанным контейнерам.</span><span class="sxs-lookup"><span data-stu-id="b0d42-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="b0d42-155">В eShopOnContainers микрослужба `basket-api`использует кэш Redis как контейнер.</span><span class="sxs-lookup"><span data-stu-id="b0d42-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="b0d42-156">Этот контейнер `basketdata` определяется как часть файла *docker-compose.yml* с несколькими контейнерами, как показано в примере:</span><span class="sxs-lookup"><span data-stu-id="b0d42-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="b0d42-157">Этот код в docker-compose.yml определяет контейнер с именем `basketdata` на основе образа redis и внутренней публикации порта 6379.</span><span class="sxs-lookup"><span data-stu-id="b0d42-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="b0d42-158">Такая конфигурация означает, что он будет доступен только из других контейнеров, работающих на узле Docker.</span><span class="sxs-lookup"><span data-stu-id="b0d42-158">This configuration means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="b0d42-159">Наконец, в файле *docker-compose.override.yml* микрослужба `basket-api` для примера приложения eShopOnContainers определяет строку подключения, используемую для этого контейнера Redis:</span><span class="sxs-lookup"><span data-stu-id="b0d42-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="b0d42-160">Как упоминалось ранее, имя микрослужбы `basketdata` разрешается с помощью DNS внутренней сети Docker.</span><span class="sxs-lookup"><span data-stu-id="b0d42-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b0d42-161">[Назад](multi-container-applications-docker-compose.md)
>[Вперед](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="b0d42-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
