---
title: Реализация операций чтения и запросов в микрослужбе CQRS
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Реализация стороны запросов CQRS в микрослужбе заказов в eShopOnContainers с помощью Dapper.
ms.date: 01/13/2021
ms.openlocfilehash: 047fc3893dcaf72a17d29f5560c928879757d024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188924"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="62981-103">Реализация операций чтения и запросов в микрослужбе CQRS</span><span class="sxs-lookup"><span data-stu-id="62981-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="62981-104">При выполнении операций чтения и запросов микрослужба заказов в примере приложения eShopOnContainers реализует запросы независимо от модели проблемно-ориентированного программирования (DDD) и области транзакций.</span><span class="sxs-lookup"><span data-stu-id="62981-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="62981-105">Это было сделано, главным образом, потому, что требования к запросам и транзакциям значительно отличаются.</span><span class="sxs-lookup"><span data-stu-id="62981-105">This implementation was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="62981-106">Операции записи выполняют транзакции, которые должны соответствовать логике предметной области.</span><span class="sxs-lookup"><span data-stu-id="62981-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="62981-107">Запросы, с другой стороны, являются идемпотентными, их можно отделить от правил предметной области.</span><span class="sxs-lookup"><span data-stu-id="62981-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="62981-108">Это простой подход, как показано на рис. 7-3.</span><span class="sxs-lookup"><span data-stu-id="62981-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="62981-109">API-интерфейс реализуется контроллерами веб-API с помощью любой инфраструктуры, например микро-ORM (средство объектно-реляционного отображения), такого как Dapper, и возвращения динамических ViewModel, в зависимости от потребностей приложения пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="62981-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Схема, на которой в общем показана сторона запросов в упрощенной микрослужбе CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="62981-111">**Рис. 7-3**.</span><span class="sxs-lookup"><span data-stu-id="62981-111">**Figure 7-3**.</span></span> <span data-ttu-id="62981-112">Самый простой метод запросов в микрослужбе CQRS</span><span class="sxs-lookup"><span data-stu-id="62981-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="62981-113">Самый простой вариант для стороны запросов в упрощенном подходе CQRS можно реализовать путем запросов базы данных с помощью Micro-ORM, например Dapper, для возврата динамических ViewModel.</span><span class="sxs-lookup"><span data-stu-id="62981-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="62981-114">Определения запроса обращаются к базе данных и возвращают динамическую ViewModel, которая создается в режиме реального времени для каждого запроса.</span><span class="sxs-lookup"><span data-stu-id="62981-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="62981-115">Поскольку запросы идемпотентны, они не меняют данные, сколько бы раз вы ни выполняли запрос.</span><span class="sxs-lookup"><span data-stu-id="62981-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="62981-116">Значит, вам не нужно ограничиваться шаблоном DDD, используемым на стороне транзакций, например статистическими выражениями и другими шаблонами. Поэтому запросы отделены от области транзакций.</span><span class="sxs-lookup"><span data-stu-id="62981-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="62981-117">Вы запрашиваете у базы данных необходимые для пользовательского интерфейса данные и получаете динамические ViewModel, которые не нужно статически определять нигде, кроме самих инструкций SQL (для ViewModel нет классов).</span><span class="sxs-lookup"><span data-stu-id="62981-117">You query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="62981-118">Это простой подход, поэтому код на стороне запросов (например, код, использующий микро-ORM, вроде [Dapper](https://github.com/StackExchange/Dapper)) можно реализовать [в том же проекте веб-API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="62981-118">Since this approach is simple, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="62981-119">Это показано на рисунке 7-4.</span><span class="sxs-lookup"><span data-stu-id="62981-119">Figure 7-4 shows this approach.</span></span> <span data-ttu-id="62981-120">Запросы определяются в проекте микрослужбы **Ordering.API** в решении eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="62981-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Снимок экрана: папка Queries в проекте Ordering.API.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="62981-122">**Рис. 7-4**.</span><span class="sxs-lookup"><span data-stu-id="62981-122">**Figure 7-4**.</span></span> <span data-ttu-id="62981-123">Запросы в микрослужбе заказов в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="62981-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="62981-124">Использование моделей представления, специально созданных для клиентских приложений, независимо от ограничений модели предметной области</span><span class="sxs-lookup"><span data-stu-id="62981-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="62981-125">Поскольку запросы выполняются для получения данных, необходимых клиентским приложениям, можно создать тип возвращаемого значения специально для клиентов на основе данных, возвращаемых запросами.</span><span class="sxs-lookup"><span data-stu-id="62981-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="62981-126">Эти модели, или объекты передачи данных (DTO), называются ViewModel.</span><span class="sxs-lookup"><span data-stu-id="62981-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="62981-127">Возвращаемые данные (ViewModel) могут быть результатом объединения данных из нескольких сущностей или таблиц в базе данных или даже нескольких статистических выражений, определенных в модели предметной области для области транзакций.</span><span class="sxs-lookup"><span data-stu-id="62981-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="62981-128">В этом случае, так как вы создаете запросы независимо от модели предметной области, границы и ограничения статистических выражений игнорируются, и вы можете обратиться к любой нужной таблице или столбцу.</span><span class="sxs-lookup"><span data-stu-id="62981-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="62981-129">Такой подход обеспечивает большую гибкость и производительность для разработчиков, создающих или обновляющих запросы.</span><span class="sxs-lookup"><span data-stu-id="62981-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="62981-130">ViewModels могут быть статическими типами, определенными в классах (как реализовано в микрослужбе заказов).</span><span class="sxs-lookup"><span data-stu-id="62981-130">The ViewModels can be static types defined in classes (as is implemented in the ordering microservice).</span></span> <span data-ttu-id="62981-131">Они также могут создаваться динамически в зависимости от выполненных запросов, что удобно для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="62981-131">Or they can be created dynamically based on the queries performed, which is agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="62981-132">Использование Dapper в качестве микро-ORM для выполнения запросов</span><span class="sxs-lookup"><span data-stu-id="62981-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="62981-133">Для запросов вы можете использовать любой микро-ORM, Entity Framework Core или даже просто ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="62981-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="62981-134">В примере приложения eShopOnContainers Dapper выбран для микрослужбы заказов как хороший пример популярного микро-ORM.</span><span class="sxs-lookup"><span data-stu-id="62981-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="62981-135">Он может выполнять обычные SQL-запросы с высокой производительностью благодаря легкости платформы.</span><span class="sxs-lookup"><span data-stu-id="62981-135">It can run plain SQL queries with great performance, because it's a light framework.</span></span> <span data-ttu-id="62981-136">С помощью Dapper вы можете написать SQL-запрос, который обратится к нескольким таблицам и соединит их.</span><span class="sxs-lookup"><span data-stu-id="62981-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="62981-137">Dapper — это проект с открытым кодом (изначально созданный Сэмом Сэффроном), который является частью стандартных блоков, используемых в [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="62981-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="62981-138">Чтобы использовать Dapper, просто установите его с помощью [пакета Dapper NuGet](https://www.nuget.org/packages/Dapper), как показано на рисунке:</span><span class="sxs-lookup"><span data-stu-id="62981-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Снимок экрана: пакет Dapper в представлении пакетов NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="62981-140">Затем добавьте директиву `using`, чтобы у кода был доступ к методам расширения Dapper.</span><span class="sxs-lookup"><span data-stu-id="62981-140">You also need to add a `using` directive so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="62981-141">При добавлении Dapper в код вы напрямую используете класс <xref:System.Data.SqlClient.SqlConnection>, доступный в пространстве имен <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="62981-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="62981-142">Метод QueryAsync и другие методы расширения, которые расширяют класс <xref:System.Data.SqlClient.SqlConnection>, — это прямой и эффективный способ выполнения запросов.</span><span class="sxs-lookup"><span data-stu-id="62981-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="62981-143">Динамические и статические модели ViewModel</span><span class="sxs-lookup"><span data-stu-id="62981-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="62981-144">Когда модели представления возвращаются с сервера в клиентские приложения, их можно представить себе в виде объектов передачи данных (DTO), которые могут отличаться для внутренних сущностей предметной области в вашей модели сущностей, поскольку модели представления хранят данные так, как это необходимо клиентскому приложению.</span><span class="sxs-lookup"><span data-stu-id="62981-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="62981-145">Поэтому во многих случаях вы можете объединять данные из нескольких сущностей предметной области и составлять модели ViewModel в точном соответствии с требованиями клиентского приложения.</span><span class="sxs-lookup"><span data-stu-id="62981-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="62981-146">Эти ViewModel или DTO могут быть определены явным образом (в виде классов-владельцев данных), как и представленный выше класс `OrderSummary`.</span><span class="sxs-lookup"><span data-stu-id="62981-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes), like the `OrderSummary` class shown in a later code snippet.</span></span> <span data-ttu-id="62981-147">Вы также можете просто вернуть динамические ViewModel или DTO на основе атрибутов, полученных из запросов в виде динамических типов.</span><span class="sxs-lookup"><span data-stu-id="62981-147">Or, you could just return dynamic ViewModels or dynamic DTOs based on the attributes returned by your queries as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="62981-148">ViewModel как динамический тип</span><span class="sxs-lookup"><span data-stu-id="62981-148">ViewModel as dynamic type</span></span>

<span data-ttu-id="62981-149">Как показано в следующем коде, `ViewModel` можно получить напрямую с помощью запросов, вернув *динамический* тип, который внутренне основан на атрибутах, возвращенных запросом.</span><span class="sxs-lookup"><span data-stu-id="62981-149">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="62981-150">Это означает, что подмножество атрибутов, которое будет возвращено, основано на самом запросе.</span><span class="sxs-lookup"><span data-stu-id="62981-150">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="62981-151">Поэтому, если вы добавляете в запрос или соединение новый столбец, данные динамически добавляются к возвращаемой `ViewModel`.</span><span class="sxs-lookup"><span data-stu-id="62981-151">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="62981-152">Важно отметить, что при использовании динамического типа возвращенная коллекция данных динамически собирается в виде ViewModel.</span><span class="sxs-lookup"><span data-stu-id="62981-152">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="62981-153">**Преимущества.** При этом подходе можно реже менять статические классы ViewModel при обновлении SQL-предложения запроса, что очень удобно при написании кода. Это простой метод, позволяющий быстро приспособиться к изменениям в будущем.</span><span class="sxs-lookup"><span data-stu-id="62981-153">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="62981-154">**Недостатки.** В долгосрочной перспективе использование динамических типов может негативно отразиться на ясности и повлиять на совместимость службы с клиентскими приложениями.</span><span class="sxs-lookup"><span data-stu-id="62981-154">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="62981-155">Кроме того, ПО промежуточного слоя, например Swashbuckle, не может предоставить тот же уровень документации для типов возвращаемого значения, если вы используете динамические типы.</span><span class="sxs-lookup"><span data-stu-id="62981-155">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="62981-156">ViewModel как предопределенные классы объектов передачи данных</span><span class="sxs-lookup"><span data-stu-id="62981-156">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="62981-157">**Преимущества.** Предопределенные статические классы ViewModel (например, "контракты") на основе явных классов объектов передачи данных лучше подходят для общедоступных API-интерфейсов, а также для долгосрочных микрослужб, даже если они используются только в том же самом приложении.</span><span class="sxs-lookup"><span data-stu-id="62981-157">**Pros**: Having static, predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long-term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="62981-158">Если вы хотите указать типы ответов для Swagger, необходимо использовать явные классы объектов передачи данных в качестве типа возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="62981-158">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="62981-159">Таким образом, с помощью предопределенных классов объектов передачи данных вы сможете получить больше сведений из Swagger.</span><span class="sxs-lookup"><span data-stu-id="62981-159">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="62981-160">Так вы сможете улучшить документацию по API и совместимость при использовании API.</span><span class="sxs-lookup"><span data-stu-id="62981-160">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="62981-161">**Недостатки.** Как уже упоминалось, при обновлении кода будет сложнее обновить классы объектов передачи данных.</span><span class="sxs-lookup"><span data-stu-id="62981-161">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="62981-162">*Совет, основанный на нашем опыте.* В запросах, реализованных микрослужбой заказов в контейнерах eShopOnContainer, мы начали разработку, используя динамические модели ViewModel, так как это удобно на ранних этапах разработки.</span><span class="sxs-lookup"><span data-stu-id="62981-162">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was straightforward and agile on the early development stages.</span></span> <span data-ttu-id="62981-163">Но после стабилизации разработки мы выполнили рефакторинг API и использовали статические или предопределенные объекты передачи данных для ViewModel, так как микрослужбам удобнее знать явные типы объектов передачи данных и использовать их как "контракты".</span><span class="sxs-lookup"><span data-stu-id="62981-163">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="62981-164">В следующем примере показано, как запрос возвращает данные с помощью явного класса объекта передачи данных ViewModel: класса OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="62981-164">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="62981-165">Описания типов ответов веб-API</span><span class="sxs-lookup"><span data-stu-id="62981-165">Describe response types of Web APIs</span></span>

<span data-ttu-id="62981-166">Разработчиков, использующих веб-интерфейсов API и микрослужбы, в первую очередь волнуют возвращаемые данные, а именно: типы ответов и коды ошибок (если они не стандартны).</span><span class="sxs-lookup"><span data-stu-id="62981-166">Developers consuming web APIs and microservices are most concerned with what is returned—specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="62981-167">Типы ответов обрабатываются в XML-комментариях и заметках к данным.</span><span class="sxs-lookup"><span data-stu-id="62981-167">The response types are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="62981-168">Без правильной документации в пользовательском интерфейсе Swagger потребителю не хватает знаний о том, какой тип значений возвращается или что могут вернуть HTTP-коды.</span><span class="sxs-lookup"><span data-stu-id="62981-168">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="62981-169">Проблему можно решить, если добавить <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, чтобы Swashbuckle создал больше информации о модели возврата и возвращенных значениях API, как в примере кода:</span><span class="sxs-lookup"><span data-stu-id="62981-169">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="62981-170">Однако атрибут `ProducesResponseType` не может использовать динамический тип. Он требует явный тип, как объект передачи данных ViewModel `OrderSummary`, показанный в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="62981-170">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="62981-171">Это еще одна причина, по которой явные типы возвращаемого значения лучше динамических в долгосрочной перспективе.</span><span class="sxs-lookup"><span data-stu-id="62981-171">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="62981-172">При использовании атрибута `ProducesResponseType` вы также можете указать ожидаемый результат в отношении возможных ошибок и кодов HTTP, например 200, 400 и т. д.</span><span class="sxs-lookup"><span data-stu-id="62981-172">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome regarding possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="62981-173">На следующем рисунке показано, как пользовательский интерфейс Swagger отображает сведения ResponseType.</span><span class="sxs-lookup"><span data-stu-id="62981-173">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Снимок экрана: страница пользовательского интерфейса Swagger для Ordering API.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="62981-175">**Рис. 7-5**.</span><span class="sxs-lookup"><span data-stu-id="62981-175">**Figure 7-5**.</span></span> <span data-ttu-id="62981-176">Пользовательский интерфейс Swagger, отображающий типы ответов и возможные коды состояния HTTP в веб-API</span><span class="sxs-lookup"><span data-stu-id="62981-176">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="62981-177">На рисунке выше показан пример значений на базе типов ViewModel и коды состояния HTTP, которые могут возвращаться.</span><span class="sxs-lookup"><span data-stu-id="62981-177">The image shows some example values based on the ViewModel types and the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="62981-178">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="62981-178">Additional resources</span></span>

- <span data-ttu-id="62981-179">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="62981-179">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="62981-180">**Julie Lerman (Джули Лерман). Точки данных — Dapper, Entity Framework и гибридные приложения (статья в журнале MSDN)**</span><span class="sxs-lookup"><span data-stu-id="62981-180">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="62981-181">**Страницы справки по веб-API ASP.NET Core с использованием Swagger**</span><span class="sxs-lookup"><span data-stu-id="62981-181">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="62981-182">[Назад](eshoponcontainers-cqrs-ddd-microservice.md)
>[Вперед](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="62981-182">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
