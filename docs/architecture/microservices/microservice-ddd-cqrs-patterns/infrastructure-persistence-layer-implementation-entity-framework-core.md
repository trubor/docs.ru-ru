---
title: Реализация уровня сохраняемости инфраструктуры с помощью Entity Framework Core
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Сведения о реализации уровня сохраняемости инфраструктуры с помощью Entity Framework Core.
ms.date: 01/13/2021
ms.openlocfilehash: 2c7b6dbe2f59a26d33a4842e74aed2b7588bd14d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188898"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="4eb69-103">Реализация уровня сохраняемости инфраструктуры с помощью Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="4eb69-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="4eb69-104">При использовании реляционных баз данных, таких как SQL Server, Oracle или PostgreSQL, рекомендуемый подход заключается в реализации уровня сохраняемости на основе Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="4eb69-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="4eb69-105">EF поддерживает LINQ и предоставляет строго типизированные объекты для вашей модели, а также упрощенную сохраняемость в базу данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="4eb69-106">Entity Framework имеет длинную историю в составе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4eb69-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="4eb69-107">При использовании .NET следует также использовать технологию Entity Framework Core, которая работает в Windows или Linux таким же образом, как .NET.</span><span class="sxs-lookup"><span data-stu-id="4eb69-107">When you use .NET, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET.</span></span> <span data-ttu-id="4eb69-108">EF Core — это полностью переработанная технология Entity Framework, реализованная с гораздо меньшими требованиями по ресурсам и важными улучшениями в производительности.</span><span class="sxs-lookup"><span data-stu-id="4eb69-108">EF Core is a complete rewrite of Entity Framework that's implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="4eb69-109">Знакомство с Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="4eb69-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="4eb69-110">Entity Framework (EF) — это упрощенная, расширяемая и кроссплатформенная версия популярной технологии для доступа к данным Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4eb69-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="4eb69-111">Она появилась в .NET Core в середине 2016 г.</span><span class="sxs-lookup"><span data-stu-id="4eb69-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="4eb69-112">Поскольку общие сведения о EF Core уже доступны в документации Майкрософт, здесь будут просто приведены ссылки на эту информацию.</span><span class="sxs-lookup"><span data-stu-id="4eb69-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4eb69-113">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="4eb69-113">Additional resources</span></span>

- <span data-ttu-id="4eb69-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="4eb69-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="4eb69-115">**Начало работы с ASP.NET Core и Entity Framework Core с использованием Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="4eb69-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="4eb69-116">**Класс DbContext** </span><span class="sxs-lookup"><span data-stu-id="4eb69-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="4eb69-117">**Сравнение EF Core и EF6.x** </span><span class="sxs-lookup"><span data-stu-id="4eb69-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="4eb69-118">Инфраструктура в Entity Framework Core с точки зрения DDD</span><span class="sxs-lookup"><span data-stu-id="4eb69-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="4eb69-119">С точки зрения DDD важной особенностью EF является возможность использования сущностей предметной области POCO, которые в терминологии EF также называются *сущностями code-first*.</span><span class="sxs-lookup"><span data-stu-id="4eb69-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="4eb69-120">При использовании сущностей предметной области POCO ваши классы модели предметной области являются неустойчивыми, следуя принципам [Persistence Ignorance](https://deviq.com/persistence-ignorance/) (независимости сохраняемости) и [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) (независимости инфраструктуры).</span><span class="sxs-lookup"><span data-stu-id="4eb69-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="4eb69-121">В шаблонах DDD вы должны инкапсулировать правила и поведение домена в самом классе сущностей, чтобы он мог управлять инвариантами, проверками и правилами при доступе к любой коллекции.</span><span class="sxs-lookup"><span data-stu-id="4eb69-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="4eb69-122">Таким образом, в DDD не рекомендуется разрешать общий доступ к коллекциям дочерних сущностей или объектов значений.</span><span class="sxs-lookup"><span data-stu-id="4eb69-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="4eb69-123">Вместо этого следует предоставить методы, определяющие, как и когда могут обновляться поля и коллекции свойств, и какое поведение и действия должны осуществляться, когда это происходит.</span><span class="sxs-lookup"><span data-stu-id="4eb69-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="4eb69-124">Начиная с EF Core 1.1, для удовлетворения этих требований DDD можно создавать в своих сущностях простые поля вместо общедоступных свойств.</span><span class="sxs-lookup"><span data-stu-id="4eb69-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="4eb69-125">Если вы не хотите, чтобы поле сущности было доступно извне, можно просто создать атрибут или поле вместо свойства.</span><span class="sxs-lookup"><span data-stu-id="4eb69-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="4eb69-126">Можно также использовать методы задания закрытых свойств.</span><span class="sxs-lookup"><span data-stu-id="4eb69-126">You can also use private property setters.</span></span>

<span data-ttu-id="4eb69-127">Аналогичным образом, теперь вы можете иметь доступ к коллекциям только на чтение, используя общедоступное свойство, написанное как `IReadOnlyCollection<T>`, которое поддерживается закрытым членом поля для коллекции (например `List<T>`) в вашей сущности, основанной на EF для сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="4eb69-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="4eb69-128">В предыдущих версиях Entity Framework требовалось наличие свойств коллекции для поддержки `ICollection<T>`, что означало, что любой разработчик, использующий родительский класс сущностей, может добавлять или удалять элементы с помощью его коллекций свойств.</span><span class="sxs-lookup"><span data-stu-id="4eb69-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="4eb69-129">Эта возможность противоречила бы рекомендуемым шаблонам в DDD.</span><span class="sxs-lookup"><span data-stu-id="4eb69-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="4eb69-130">Вы можете использовать закрытую коллекцию при предоставлении объекта `IReadOnlyCollection<T>` только для чтения, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="4eb69-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="4eb69-131">Свойство `OrderItems` может быть доступно только для чтения с помощью `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="4eb69-131">The `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="4eb69-132">Этот тип доступен только для чтения, поэтому он защищен от обычных внешних обновлений.</span><span class="sxs-lookup"><span data-stu-id="4eb69-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="4eb69-133">EF Core предоставляет способ сопоставления модели предметной области с физической базой данных без "засорения" этой модели предметной области.</span><span class="sxs-lookup"><span data-stu-id="4eb69-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="4eb69-134">Это чистый код POCO .NET, так как действие сопоставления реализовано на уровне сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="4eb69-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="4eb69-135">В данном действии сопоставления необходимо настроить сопоставление полей с базой данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="4eb69-136">В следующем примере метода `OnModelCreating` из `OrderingContext` и класса `OrderEntityTypeConfiguration` вызов `SetPropertyAccessMode` указывает EF Core на необходимость обратиться к свойству `OrderItems` через его поле.</span><span class="sxs-lookup"><span data-stu-id="4eb69-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="4eb69-137">При использовании полей вместо свойств сущность `OrderItem` сохраняется так же, как если бы она имела свойство `List<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="4eb69-137">When you use fields instead of properties, the `OrderItem` entity is persisted as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="4eb69-138">Однако она предоставляет единственный метод доступа `AddOrderItem` для добавления в заказ новых элементов.</span><span class="sxs-lookup"><span data-stu-id="4eb69-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="4eb69-139">В результате поведение и данные оказываются связаны друг с другом и будут согласованными во всем коде приложения, использующем модель предметной области.</span><span class="sxs-lookup"><span data-stu-id="4eb69-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="4eb69-140">Реализация пользовательских репозиториев с помощью Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="4eb69-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="4eb69-141">На уровне реализации репозиторий является просто классом с кодом сохраняемости данных, координируемым единицей работы (DBContext в EF Core) при выполнении обновлений, как показано в следующем классе:</span><span class="sxs-lookup"><span data-stu-id="4eb69-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using directives...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="4eb69-142">Интерфейс `IBuyerRepository` поступает из уровня модели предметной области как контракт.</span><span class="sxs-lookup"><span data-stu-id="4eb69-142">The `IBuyerRepository` interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="4eb69-143">Однако реализация репозитория выполняется на уровне сохраняемости и инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="4eb69-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="4eb69-144">DbContext EF поступает через конструктор путем внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4eb69-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="4eb69-145">Он совместно используется несколькими репозиториями внутри одной области запроса HTTP благодаря его времени существования по умолчанию (`ServiceLifetime.Scoped`) в контейнере IoC (что также можно явно задать с помощью `services.AddDbContext<>`).</span><span class="sxs-lookup"><span data-stu-id="4eb69-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="4eb69-146">Методы, реализуемые в репозитории (обновления или транзакции по отношению к запросам)</span><span class="sxs-lookup"><span data-stu-id="4eb69-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="4eb69-147">В каждом классе репозитория следует поместить методы сохраняемости, которые обновляют состояние сущностей, содержащихся в связанном с ним агрегате.</span><span class="sxs-lookup"><span data-stu-id="4eb69-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="4eb69-148">Помните, что имеется однозначное соответствие между агрегатом и связанным с ним репозиторием.</span><span class="sxs-lookup"><span data-stu-id="4eb69-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="4eb69-149">Также учитывайте, что корневой объект сущности агрегата может иметь внедренные дочерние сущности в своем графе EF.</span><span class="sxs-lookup"><span data-stu-id="4eb69-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="4eb69-150">Например, покупатель может иметь несколько способов оплаты в виде связанных дочерних сущностей.</span><span class="sxs-lookup"><span data-stu-id="4eb69-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="4eb69-151">Поскольку этот подход для микрослужбы заказов в eShopOnContainers также основан на CQS/CQRS, большинство запросов не реализуется в пользовательских репозиториях.</span><span class="sxs-lookup"><span data-stu-id="4eb69-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="4eb69-152">Разработчики имеют право создавать нужные им запросы и соединения для уровня представления данных без ограничений, установленных агрегатами, пользовательскими репозиториями в агрегатах и DDD в целом.</span><span class="sxs-lookup"><span data-stu-id="4eb69-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="4eb69-153">Большинство пользовательских репозиториев, предлагаемых в данном руководстве, имеют несколько методов обновления или транзакций, но только те методы запросов, которые необходимы для получения обновляемых данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="4eb69-154">Например, репозиторий BuyerRepository реализует метод FindAsync, так как приложению нужно узнать, существует ли конкретный покупатель, прежде чем создавать нового покупателя, связанного с заказом.</span><span class="sxs-lookup"><span data-stu-id="4eb69-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="4eb69-155">Однако реальные методы запросов для получения данных для отправки на уровень представления данных или в клиентские приложения реализуются, как было указано, в запросах CQRS на основе гибких запросов с помощью Dapper.</span><span class="sxs-lookup"><span data-stu-id="4eb69-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="4eb69-156">Применение пользовательского репозитория по сравнению с непосредственным применением DbContext EF</span><span class="sxs-lookup"><span data-stu-id="4eb69-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="4eb69-157">Класс DbContext Entity Framework основан на шаблонах Unit of Work (единицы работы) и Repository (репозитория); его можно использовать непосредственно из кода приложения, например из контроллера MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4eb69-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="4eb69-158">Шаблоны Unit of Work и Repository дают простейший код, как в микрослужбе каталога CRUD в eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4eb69-158">The Unit of Work and Repository patterns result in the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="4eb69-159">В случаях, когда требуется создать максимально простой код, вы можете захотеть напрямую воспользоваться классом DbContext, как делают многие разработчики.</span><span class="sxs-lookup"><span data-stu-id="4eb69-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="4eb69-160">Однако реализация пользовательских репозиториев обеспечивает определенные преимущества при реализации более сложных микрослужб или приложений.</span><span class="sxs-lookup"><span data-stu-id="4eb69-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="4eb69-161">Шаблоны Unit of Work и Repository предназначены для инкапсуляции уровня сохраняемости инфраструктуры, поэтому он отделен от уровней приложения и модели предметной области.</span><span class="sxs-lookup"><span data-stu-id="4eb69-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain-model layers.</span></span> <span data-ttu-id="4eb69-162">Реализация этих шаблонов позволяет упростить использование макетов репозиториев, моделирующих доступ к базе данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="4eb69-163">На рис. 7-18 можно увидеть различия между отсутствием использования репозиториев (с применением класса DbContext EF напрямую) и использованием репозиториев, что упрощает макетирование таких репозиториев.</span><span class="sxs-lookup"><span data-stu-id="4eb69-163">In Figure 7-18, you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories, which makes it easier to mock those repositories.</span></span>

![Схема, на которой показаны компоненты и поток данных в двух репозиториях.](./media/infrastructure-persistence-layer-implementation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="4eb69-165">**Рис. 7-18**.</span><span class="sxs-lookup"><span data-stu-id="4eb69-165">**Figure 7-18**.</span></span> <span data-ttu-id="4eb69-166">Применение пользовательских репозиториев по сравнению с простым DbContext</span><span class="sxs-lookup"><span data-stu-id="4eb69-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="4eb69-167">На рис. 7-18 показано, что применение пользовательского репозитория добавляет уровень абстракции, который может использоваться для упрощения тестирования путем макетирования репозитория.</span><span class="sxs-lookup"><span data-stu-id="4eb69-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="4eb69-168">Существует несколько вариантов макетирования.</span><span class="sxs-lookup"><span data-stu-id="4eb69-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="4eb69-169">Можно макетировать только репозитории или макетировать всю единицу работы.</span><span class="sxs-lookup"><span data-stu-id="4eb69-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="4eb69-170">Как правило, достаточно макетирования только репозиториев, и сложность абстрагирования и макетирования всей единицы работы обычно не требуется.</span><span class="sxs-lookup"><span data-stu-id="4eb69-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="4eb69-171">Позднее, когда мы будем рассматривать уровень приложения, вы увидите, как работает внедрение зависимостей в ASP.NET Core и как оно реализуется при использовании репозиториев.</span><span class="sxs-lookup"><span data-stu-id="4eb69-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="4eb69-172">Короче говоря, пользовательские репозитории позволяют упростить тестирование кода с помощью модульных тестов, на которые не влияет состояние уровня данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="4eb69-173">Если выполняются тесты, которые также обращаются к реальной базе данных через Entity Framework, то это не модульные тесты, а интеграционные тесты, которые выполняются гораздо медленнее.</span><span class="sxs-lookup"><span data-stu-id="4eb69-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="4eb69-174">Если вы использовали DbContext напрямую, вам потребовалось бы выполнить его макетирование или запуск модульных тестов с помощью SQL Server в памяти с прогнозируемыми данными для модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="4eb69-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="4eb69-175">Однако макетирование DbContext или управление фиктивными данными требует больше усилий, чем макетирование на уровне репозитория.</span><span class="sxs-lookup"><span data-stu-id="4eb69-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="4eb69-176">Конечно, вы всегда можете тестировать контроллеры MVC.</span><span class="sxs-lookup"><span data-stu-id="4eb69-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="4eb69-177">Время существования экземпляра IUnitOfWork и DbContext EF в контейнере IoC</span><span class="sxs-lookup"><span data-stu-id="4eb69-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="4eb69-178">Необходимо реализовать общий доступ к объекту `DbContext` (предоставляемому как объект `IUnitOfWork`) из нескольких репозиториев в рамках одной и той же области запроса HTTP.</span><span class="sxs-lookup"><span data-stu-id="4eb69-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="4eb69-179">Например, это может требоваться, когда выполняемая операция должна иметь дело с несколькими агрегаторами, или просто потому, что вы используете несколько экземпляров репозитория.</span><span class="sxs-lookup"><span data-stu-id="4eb69-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="4eb69-180">Также важно упомянуть, что интерфейс `IUnitOfWork` является частью уровня домена, а не типом EF Core.</span><span class="sxs-lookup"><span data-stu-id="4eb69-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="4eb69-181">Для этого время существования службы экземпляра объекта `DbContext` должно быть установлено в значение ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="4eb69-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="4eb69-182">Это время существования по умолчанию при регистрации `DbContext` с помощью `services.AddDbContext` в контейнере IoC из метода ConfigureServices файла `Startup.cs` в проекте веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4eb69-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="4eb69-183">Это проиллюстрировано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4eb69-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="4eb69-184">Режим создания экземпляра DbContext не должен быть настроен как ServiceLifetime.Transient или ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="4eb69-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="4eb69-185">Время существования экземпляра репозитория в контейнере IoC</span><span class="sxs-lookup"><span data-stu-id="4eb69-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="4eb69-186">Аналогичным образом время существования репозитория обычно должно быть задано как scoped — ограниченное областью (InstancePerLifetimeScope в Autofac).</span><span class="sxs-lookup"><span data-stu-id="4eb69-186">In a similar way, repository's lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="4eb69-187">Оно также может быть задано как transient — временное (InstancePerDependency в Autofac), но служба будет более эффективной в отношении памяти при использовании времени существования, ограниченного областью.</span><span class="sxs-lookup"><span data-stu-id="4eb69-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="4eb69-188">Использование для репозитория времени существования singleton может вызвать серьезные проблемы с параллелизмом, если для DbContext установлено время существования scoped (InstancePerLifetimeScope) (время существования по умолчанию для DBContext).</span><span class="sxs-lookup"><span data-stu-id="4eb69-188">Using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4eb69-189">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="4eb69-189">Additional resources</span></span>

- <span data-ttu-id="4eb69-190">**Реализация шаблонов репозитория и единиц работы в приложении ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="4eb69-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="4eb69-191">**Джонатан Аллен (Jonathan Allen). Стратегии реализации для шаблона репозитория в Entity Framework, Dapper и Chain** </span><span class="sxs-lookup"><span data-stu-id="4eb69-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="4eb69-192">**Сезар де ла Торре (Cesar de la Torre). Сравнение времени существования службы контейнеров IoC ASP.NET Core с областями действия экземпляра контейнера IoC Autofac** </span><span class="sxs-lookup"><span data-stu-id="4eb69-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="4eb69-193">Сопоставление таблиц</span><span class="sxs-lookup"><span data-stu-id="4eb69-193">Table mapping</span></span>

<span data-ttu-id="4eb69-194">Сопоставление таблиц определяет таблицы, данные которых должны запрашиваться и сохраняться в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="4eb69-195">Ранее было показано, как сущности предметной области (например, предметная область продуктов или заказов) могут использоваться для создания схемы связанной базы данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="4eb69-196">Технология EF строго построена на концепции *соглашений*.</span><span class="sxs-lookup"><span data-stu-id="4eb69-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="4eb69-197">Соглашения разрешают, например, такие вопросы, как "Каким будет имя таблицы?"</span><span class="sxs-lookup"><span data-stu-id="4eb69-197">Conventions address questions like "What will the name of a table be?"</span></span> <span data-ttu-id="4eb69-198">или "Какое свойство является первичным ключом?"</span><span class="sxs-lookup"><span data-stu-id="4eb69-198">or "What property is the primary key?"</span></span> <span data-ttu-id="4eb69-199">Как правило, соглашения основываются на условных именованиях.</span><span class="sxs-lookup"><span data-stu-id="4eb69-199">Conventions are typically based on conventional names.</span></span> <span data-ttu-id="4eb69-200">Например, первичный ключ обычно является свойством, которое заканчивается на `Id`.</span><span class="sxs-lookup"><span data-stu-id="4eb69-200">For example, it is typical for the primary key to be a property that ends with `Id`.</span></span>

<span data-ttu-id="4eb69-201">По соглашению каждая сущность будет настроена для сопоставления с таблицей с именем, указанным в свойстве `DbSet<TEntity>`, которое предоставляет сущность в производном контексте.</span><span class="sxs-lookup"><span data-stu-id="4eb69-201">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="4eb69-202">Если для конкретной сущности значение свойства `DbSet<TEntity>` не задано, то используется имя класса.</span><span class="sxs-lookup"><span data-stu-id="4eb69-202">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="4eb69-203">Заметки к данным и текучий API</span><span class="sxs-lookup"><span data-stu-id="4eb69-203">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="4eb69-204">Существует множество дополнительных соглашений EF Core, и большинство из них можно изменить с помощью заметок к данным или текучего API, реализованного в методе OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="4eb69-204">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="4eb69-205">Заметки к данным необходимо использовать в самих классах модели сущностей, что является более навязчивым способом с точки зрения DDD.</span><span class="sxs-lookup"><span data-stu-id="4eb69-205">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="4eb69-206">Это связано с тем, что вы засоряете модель заметками к данным, относящимися к базе данных инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="4eb69-206">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="4eb69-207">С другой стороны, текучий API представляет удобный способ изменения большинства соглашений и сопоставлений на уровне инфраструктуры сохраняемости данных; таким образом, модель сущностей будет чистой и отделенной от инфраструктуры сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="4eb69-207">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="4eb69-208">Текучий API и метод OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="4eb69-208">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="4eb69-209">Как уже упоминалось, для изменения соглашений и сопоставлений можно использовать метод OnModelCreating класса DbContext.</span><span class="sxs-lookup"><span data-stu-id="4eb69-209">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="4eb69-210">Микрослужба заказов в eShopOnContainers реализует явное сопоставление и конфигурацию, когда это необходимо, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="4eb69-210">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="4eb69-211">Можно задать все сопоставления текучего API в одном и том же методе `OnModelCreating`, но рекомендуется разбить этот код на несколько классов конфигурации, по одному на сущность, как показано в примере.</span><span class="sxs-lookup"><span data-stu-id="4eb69-211">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="4eb69-212">В первую очередь отдельные классы конфигурации для настройки разных типов сущностей рекомендуется использовать для больших моделей.</span><span class="sxs-lookup"><span data-stu-id="4eb69-212">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="4eb69-213">В примере кода показано несколько явных объявлений и сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="4eb69-213">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="4eb69-214">Однако соглашения EF Core выполняют многие из этих сопоставлений автоматически, так что фактический код, который понадобится в вашем случае, может иметь меньший размер.</span><span class="sxs-lookup"><span data-stu-id="4eb69-214">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="4eb69-215">Алгоритм Hi/Lo в EF Core</span><span class="sxs-lookup"><span data-stu-id="4eb69-215">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="4eb69-216">Интересным аспектом кода в предыдущем примере является применение [алгоритма Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) в качестве стратегии создания ключей.</span><span class="sxs-lookup"><span data-stu-id="4eb69-216">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="4eb69-217">Алгоритм Hi/Lo удобно использовать в тех случаях, когда требуются уникальные ключи перед фиксацией изменений.</span><span class="sxs-lookup"><span data-stu-id="4eb69-217">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="4eb69-218">Вкратце, алгоритм Hi-Lo присваивает строкам таблицы уникальные идентификаторы, которые не зависят от немедленного сохранения строк в базе данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-218">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="4eb69-219">Это позволяет начинать использовать идентификаторы сразу, как это происходит с обычными последовательными идентификаторами базы данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-219">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="4eb69-220">Алгоритм Hi/Lo описывает механизм для получения пакета уникальных идентификаторов из последовательности связанной базы данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-220">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="4eb69-221">Эти идентификаторы являются безопасными для использования, так как база данных гарантирует уникальность, исключая конфликты между пользователями.</span><span class="sxs-lookup"><span data-stu-id="4eb69-221">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="4eb69-222">Этот алгоритм представляет интерес по следующим причинам.</span><span class="sxs-lookup"><span data-stu-id="4eb69-222">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="4eb69-223">Он не нарушает шаблон единицы работы.</span><span class="sxs-lookup"><span data-stu-id="4eb69-223">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="4eb69-224">Он получает идентификаторы последовательности в пакетах, чтобы свести к минимуму количество обращений к базе данных.</span><span class="sxs-lookup"><span data-stu-id="4eb69-224">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="4eb69-225">Он создает удобный для восприятия идентификатор, в отличие от методов, в которых используются идентификаторы GUID.</span><span class="sxs-lookup"><span data-stu-id="4eb69-225">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="4eb69-226">EF Core поддерживает алгоритм [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) с помощью метода `UseHiLo`, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="4eb69-226">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="4eb69-227">Сопоставление полей вместо свойств</span><span class="sxs-lookup"><span data-stu-id="4eb69-227">Map fields instead of properties</span></span>

<span data-ttu-id="4eb69-228">Эта функция, появившаяся в EF Core 1.1, позволяет сопоставлять столбцы с полями напрямую.</span><span class="sxs-lookup"><span data-stu-id="4eb69-228">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="4eb69-229">Теперь существует возможность не использовать свойства в классе сущностей, а просто сопоставлять столбцы таблицы с полями.</span><span class="sxs-lookup"><span data-stu-id="4eb69-229">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="4eb69-230">Эта возможность часто используется в закрытых полях для хранения внутреннего состояния, доступ к которому не должен осуществляться извне сущности.</span><span class="sxs-lookup"><span data-stu-id="4eb69-230">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="4eb69-231">Это можно делать как с отдельными полями, так и с коллекциями, например с `List<>`.</span><span class="sxs-lookup"><span data-stu-id="4eb69-231">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="4eb69-232">Этот момент упоминался ранее, когда мы обсуждали моделирование классов модели предметной области, но здесь можно видеть, как это сопоставление выполняется для конфигурации `PropertyAccessMode.Field`, выделенной в предыдущем коде.</span><span class="sxs-lookup"><span data-stu-id="4eb69-232">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="4eb69-233">Использование теневых свойств в EF Core, скрытых на уровне инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="4eb69-233">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="4eb69-234">Теневые свойства в EF Core — это свойства, которые не существуют в вашей модели классов сущностей.</span><span class="sxs-lookup"><span data-stu-id="4eb69-234">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="4eb69-235">Значения и состояния этих свойств сохраняются только в классе [ChangeTracker](/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) на уровне инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="4eb69-235">The values and states of these properties are maintained purely in the [ChangeTracker](/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="4eb69-236">Реализация шаблона спецификации запроса</span><span class="sxs-lookup"><span data-stu-id="4eb69-236">Implement the Query Specification pattern</span></span>

<span data-ttu-id="4eb69-237">Как говорилось ранее в разделе, посвященном проектированию, шаблон спецификации запроса — это шаблон предметно-ориентированного проектирования, в котором можно поместить определение запроса с дополнительной логикой сортировки и разбиения на страницы.</span><span class="sxs-lookup"><span data-stu-id="4eb69-237">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="4eb69-238">Шаблон спецификации запроса определяет запрос в объекте.</span><span class="sxs-lookup"><span data-stu-id="4eb69-238">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="4eb69-239">Например, чтобы инкапсулировать постраничный запрос, который выполняет поиск некоторых продуктов, вы можете создать спецификацию PagedProduct, которая принимает необходимые входные параметры (номер страницы, размер страницы, фильтр и т. д.).</span><span class="sxs-lookup"><span data-stu-id="4eb69-239">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="4eb69-240">Затем в любом методе репозитория (обычно в перегрузке List()) вы можете принять IQuerySpecification и запустить ожидаемый запрос на основе этой спецификации.</span><span class="sxs-lookup"><span data-stu-id="4eb69-240">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="4eb69-241">Пример универсального интерфейса спецификации приведен в следующем коде из [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="4eb69-241">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="4eb69-242">Реализация базового класса универсальной спецификации выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="4eb69-242">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="4eb69-243">Следующая спецификация загружает одну сущность корзины, заданную идентификатором корзины или идентификатором покупателя, которому принадлежит корзина.</span><span class="sxs-lookup"><span data-stu-id="4eb69-243">The following specification loads a single basket entity given either the basket's ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="4eb69-244">Она будет [безотлагательно загружать](/ef/core/querying/related-data) коллекцию `Items` корзины.</span><span class="sxs-lookup"><span data-stu-id="4eb69-244">It will [eagerly load](/ef/core/querying/related-data) the basket's `Items` collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="4eb69-245">И, наконец, ниже вы видите, как универсальный репозиторий EF может использовать такую спецификацию для фильтрации и безотложной загрузки данных, связанных с типом T заданной сущности.</span><span class="sxs-lookup"><span data-stu-id="4eb69-245">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="4eb69-246">Помимо инкапсуляции логики фильтрации, эта спецификация может указывать форму возвращаемых данных, включая свойства, которые следует заполнить.</span><span class="sxs-lookup"><span data-stu-id="4eb69-246">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="4eb69-247">Хотя не рекомендуется возвращать `IQueryable` из репозитория, совершенно нормально использовать их в репозитории для создания набора результатов.</span><span class="sxs-lookup"><span data-stu-id="4eb69-247">Although we don't recommend returning `IQueryable` from a repository, it's perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="4eb69-248">Вы видели применение этого подхода в методе List выше, где промежуточные выражения `IQueryable` использовались для построения списка Includes запроса перед выполнением запроса с условиями спецификации в последней строке.</span><span class="sxs-lookup"><span data-stu-id="4eb69-248">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query's list of includes before executing the query with the specification's criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4eb69-249">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="4eb69-249">Additional resources</span></span>

- <span data-ttu-id="4eb69-250">**Сопоставление таблиц** </span><span class="sxs-lookup"><span data-stu-id="4eb69-250">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="4eb69-251">**Применение HiLo для создания ключей с использованием Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="4eb69-251">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="4eb69-252">**Резервные поля** </span><span class="sxs-lookup"><span data-stu-id="4eb69-252">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="4eb69-253">**Стив Смит (Steve Smith). Инкапсулированные коллекции в Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="4eb69-253">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="4eb69-254">**Свойства тени** </span><span class="sxs-lookup"><span data-stu-id="4eb69-254">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="4eb69-255">**Шаблон спецификации** </span><span class="sxs-lookup"><span data-stu-id="4eb69-255">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="4eb69-256">[Назад](infrastructure-persistence-layer-design.md)
> [Вперед](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="4eb69-256">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
