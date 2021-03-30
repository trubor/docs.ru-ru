---
title: Подписка на события
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Общие сведения о публикации событий интеграции и подписке на них.
ms.date: 01/13/2021
ms.openlocfilehash: d7b68f5c01c21564724e3a00a048a9fa58bb4fb6
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637377"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="1788a-103">Подписка на события</span><span class="sxs-lookup"><span data-stu-id="1788a-103">Subscribing to events</span></span>

<span data-ttu-id="1788a-104">Первый шаг при использовании шины событий — подписать микрослужбы на события, которые они должны получать.</span><span class="sxs-lookup"><span data-stu-id="1788a-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="1788a-105">Это необходимо сделать для микрослужб-получателей.</span><span class="sxs-lookup"><span data-stu-id="1788a-105">That functionality should be done in the receiver microservices.</span></span>

<span data-ttu-id="1788a-106">В следующем простом коде видно, что должна реализовать каждая микрослужба-получатель при запуске службы (то есть в классе `Startup`), чтобы подписаться на нужные события.</span><span class="sxs-lookup"><span data-stu-id="1788a-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="1788a-107">В этом случае микрослужба `basket-api` должна подписаться на сообщения `ProductPriceChangedIntegrationEvent` и `OrderStartedIntegrationEvent`.</span><span class="sxs-lookup"><span data-stu-id="1788a-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="1788a-108">Например, при подписке на событие `ProductPriceChangedIntegrationEvent` микрослужба корзины узнает об изменении цены товара и уведомляет пользователя об этом изменении, если товар находится в корзине пользователя.</span><span class="sxs-lookup"><span data-stu-id="1788a-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user's basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="1788a-109">После выполнения этого кода микрослужба-подписчик будет ожидать передачи данных по каналам RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="1788a-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="1788a-110">При поступлении сообщения типа ProductPriceChangedIntegrationEvent код вызывает обработчика событий, который передается ему и обрабатывает событие.</span><span class="sxs-lookup"><span data-stu-id="1788a-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="1788a-111">Публикация событий через шину событий</span><span class="sxs-lookup"><span data-stu-id="1788a-111">Publishing events through the event bus</span></span>

<span data-ttu-id="1788a-112">Наконец, отправитель сообщения (исходная микрослужба) публикует события интеграции с кодом, как в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="1788a-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="1788a-113">(Это упрощенный пример, не учитывающий атомарность.) Применяйте аналогичный код в случае, когда событие необходимо распространить по нескольким микрослужбам, обычно сразу после фиксации данных или транзакций из исходной микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="1788a-113">(This approach is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="1788a-114">Сначала объект реализации шины событий (на основе RabbitMQ или служебной шины) будет внедрен в конструктор контроллера, как в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="1788a-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="1788a-115">Затем вы используете его из методов контроллера, например UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="1788a-115">Then you use it from your controller's methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="1788a-116">В этом случае, поскольку источником является простая микрослужба CRUD, этот код помещается прямо в контроллер веб-API.</span><span class="sxs-lookup"><span data-stu-id="1788a-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="1788a-117">В более сложных микрослужбах, например на основе подходов CQRS, это можно реализовать в классе `CommandHandler` в методе `Handle()`.</span><span class="sxs-lookup"><span data-stu-id="1788a-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="1788a-118">Проектирование атомарности и устойчивости при публикации в шине событий</span><span class="sxs-lookup"><span data-stu-id="1788a-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="1788a-119">При публикации событий интеграции с помощью распределенной системы обмена сообщениями, такой как шина событий, вы сталкиваетесь с проблемой атомарного обновления исходной базы данных и публикации события (таким образом, выполняются либо обе операции, либо ни одна из них).</span><span class="sxs-lookup"><span data-stu-id="1788a-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="1788a-120">Например, в упрощенном примере, приведенном выше, код фиксирует данные в базе данных, когда меняется цена продукта, а затем публикует сообщение ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="1788a-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="1788a-121">Сначала может показаться важным, чтобы обе операции выполнялись атомарно.</span><span class="sxs-lookup"><span data-stu-id="1788a-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="1788a-122">Однако при использовании распределенных транзакций с базами данных и брокером сообщений, как в прежних системах, например [очередь сообщений (Майкрософт)](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)), это не рекомендуется по причинам, описанным в [теореме CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="1788a-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)), this approach is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="1788a-123">По сути, вы используете микрослужбы для создания масштабируемых систем с высокой доступностью.</span><span class="sxs-lookup"><span data-stu-id="1788a-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="1788a-124">В упрощенном виде теорема CAP гласит, что невозможно создать (распределенную) базу данных (или микрослужбу, владеющую своей моделью), которая была бы всегда доступной, строго согласованной *и* устойчивой к разделению.</span><span class="sxs-lookup"><span data-stu-id="1788a-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that's continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="1788a-125">Можно выбрать только два свойства из трех.</span><span class="sxs-lookup"><span data-stu-id="1788a-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="1788a-126">В архитектурах на основе микрослужб рекомендуется выбирать доступность и устойчивость в ущерб строгой согласованности.</span><span class="sxs-lookup"><span data-stu-id="1788a-126">In microservices-based architectures, you should choose availability and tolerance, and you should de-emphasize strong consistency.</span></span> <span data-ttu-id="1788a-127">Поэтому в большинстве современных приложений на базе микрослужб вы обычно не используете распределенные транзакции при обмене сообщениями, как вы это делаете при реализации [распределенных транзакций](/previous-versions/windows/desktop/ms681205(v=vs.85)) на основе координатора распределенных транзакций Windows (DTC) с [MSMQ](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1788a-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

<span data-ttu-id="1788a-128">Давайте вернемся к начальной проблеме и примеру.</span><span class="sxs-lookup"><span data-stu-id="1788a-128">Let's go back to the initial issue and its example.</span></span> <span data-ttu-id="1788a-129">Если служба аварийно завершает работу после обновления базы данных (в этом случае сразу после строки кода с `_context.SaveChangesAsync()`), но до публикации события интеграции, вся система может утратить согласованность.</span><span class="sxs-lookup"><span data-stu-id="1788a-129">If the service crashes after the database is updated (in this case, right after the line of code with `_context.SaveChangesAsync()`), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="1788a-130">Это может быть критически важным для бизнеса в зависимости от конкретной операции.</span><span class="sxs-lookup"><span data-stu-id="1788a-130">This approach might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="1788a-131">Как уже упоминалось в разделе об архитектуре, существует несколько подходов к решению этой проблемы:</span><span class="sxs-lookup"><span data-stu-id="1788a-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="1788a-132">Использование полной модели [источников событий](/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="1788a-132">Using the full [Event Sourcing pattern](/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="1788a-133">Интеллектуальный анализ данных журнала транзакций.</span><span class="sxs-lookup"><span data-stu-id="1788a-133">Using transaction log mining.</span></span>

- <span data-ttu-id="1788a-134">Использование [шаблона Outbox](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span><span class="sxs-lookup"><span data-stu-id="1788a-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="1788a-135">Это таблица транзакций, в которой хранятся события интеграции (расширяющие локальную транзакцию).</span><span class="sxs-lookup"><span data-stu-id="1788a-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="1788a-136">В этом сценарии одним из лучших, если не *лучшим*, подходом будет использование полного шаблона источников событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="1788a-137">Однако часто вы не можете реализовать полную систему источников событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="1788a-138">Источник событий подразумевает хранение в базе данных о транзакциях только событий в предметной области, а не данных о текущем состоянии.</span><span class="sxs-lookup"><span data-stu-id="1788a-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="1788a-139">Хранить только события в предметной области очень удобно. Например, у вас есть история системы, и вы можете определить состояние системы в любой момент в прошлом.</span><span class="sxs-lookup"><span data-stu-id="1788a-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="1788a-140">Однако реализация полной системы источников событий требует перестройки большей части системы и приводит к другим сложностям и требованиям.</span><span class="sxs-lookup"><span data-stu-id="1788a-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="1788a-141">В частности, придется использовать базу данных, созданную специально для источников событий, например [хранилище событий](https://eventstore.org/), или документоориентированную базу данных, например Azure Cosmos DB, MongoDB, Cassandra, CouchDB или RavenDB.</span><span class="sxs-lookup"><span data-stu-id="1788a-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="1788a-142">Модель источников событий может стать отличным решением этой проблемы, но не самым простым, особенно если вы еще не знакомы с этой концепцией.</span><span class="sxs-lookup"><span data-stu-id="1788a-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="1788a-143">Вариант с анализом журнала транзакций, на первый взгляд, выглядит понятным.</span><span class="sxs-lookup"><span data-stu-id="1788a-143">The option to use transaction log mining initially looks transparent.</span></span> <span data-ttu-id="1788a-144">Но такой подход подразумевает соединение микрослужбы с журналом транзакций реляционной СУБД, например журналом транзакций SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1788a-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="1788a-145">Иногда это нежелательно.</span><span class="sxs-lookup"><span data-stu-id="1788a-145">This approach is probably not desirable.</span></span> <span data-ttu-id="1788a-146">Еще один недостаток заключается в том, что обновления низкого уровня, записанные в журнал транзакций, могут не соответствовать событиям интеграции высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="1788a-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="1788a-147">Это может затруднять реконструирование операций в журнале транзакций.</span><span class="sxs-lookup"><span data-stu-id="1788a-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="1788a-148">В качестве компромисса можно использовать комбинацию таблицы базы данных о транзакциях и упрощенного шаблона источников событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="1788a-149">Например, вы можете использовать состояние "готово к публикации события", которое вы задаете в исходном событии при его фиксации в таблице событий интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-149">You can use a state such as "ready to publish the event," which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="1788a-150">Затем вы пытаетесь опубликовать событие в шине события.</span><span class="sxs-lookup"><span data-stu-id="1788a-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="1788a-151">Если действие публикации события выполняется успешно, вы запускаете еще одну транзакцию в исходной службе и изменяете состояние с "готово к публикации события" на "событие опубликовано".</span><span class="sxs-lookup"><span data-stu-id="1788a-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from "ready to publish the event" to "event already published."</span></span>

<span data-ttu-id="1788a-152">Если действие публикации события в шине событий не выполняется, данные не утратят согласованность в исходной микрослужбе — они останутся в состоянии "готово к публикации события", и это будет согласовываться с остальными службами.</span><span class="sxs-lookup"><span data-stu-id="1788a-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as "ready to publish the event," and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="1788a-153">Вы всегда можете запустить фоновые задания для проверки состояния транзакций или событий интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="1788a-154">Когда задание находит событие в состоянии "готово к публикации события", оно пытается повторно опубликовать событие в шине событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-154">If the job finds an event in the "ready to publish the event" state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="1788a-155">При таком подходе вы сохраняете только события интеграции для каждой исходной микрослужбы и только события, которые вы хотите передать другим микрослужбам или внешним системам.</span><span class="sxs-lookup"><span data-stu-id="1788a-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="1788a-156">В отличие от полной системы источников событий, когда вы также храните все события в предметной области.</span><span class="sxs-lookup"><span data-stu-id="1788a-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="1788a-157">Такой сбалансированный подход — это упрощенная система источников событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="1788a-158">Вам нужен список событий интеграции с их текущим состоянием ("готово к публикации" или "опубликовано").</span><span class="sxs-lookup"><span data-stu-id="1788a-158">You need a list of integration events with their current state ("ready to publish" versus "published").</span></span> <span data-ttu-id="1788a-159">Но эти состояния нужно применять только к событиям интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="1788a-160">При таком подходе вам не нужно хранить все данные предметной области в виде событий в базе данных о транзакциях, как в полной системе источников событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="1788a-161">Если вы уже используете реляционную базу данных, можете хранить события интеграции в таблице транзакций.</span><span class="sxs-lookup"><span data-stu-id="1788a-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="1788a-162">Чтобы приложение было атомарным, используйте двухэтапный процесс на основе локальных транзакций.</span><span class="sxs-lookup"><span data-stu-id="1788a-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="1788a-163">Фактически, таблица IntegrationEvent хранится в той же базе денных, что и сущности предметной области.</span><span class="sxs-lookup"><span data-stu-id="1788a-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="1788a-164">Эта таблица используется для гарантии атомарности, чтобы вы включали хранимые события интеграции в те же транзакции, которые фиксируются в данных предметной области.</span><span class="sxs-lookup"><span data-stu-id="1788a-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="1788a-165">Пошаговый процесс выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1788a-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="1788a-166">Приложение запускает транзакцию в локальной базе данных.</span><span class="sxs-lookup"><span data-stu-id="1788a-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="1788a-167">Затем оно обновляет состояние сущностей предметной области и вставляет событие в таблицу событий интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="1788a-168">Наконец, оно фиксирует транзакцию. Вы получаете необходимую атомарность и</span><span class="sxs-lookup"><span data-stu-id="1788a-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="1788a-169">публикуете событие каким-либо образом (далее).</span><span class="sxs-lookup"><span data-stu-id="1788a-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="1788a-170">Для выполнения этапов публикации события у вас есть следующие варианты:</span><span class="sxs-lookup"><span data-stu-id="1788a-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="1788a-171">Опубликуйте событие интеграции сразу после фиксации транзакции и используйте другую локальную транзакцию, чтобы отметить события в таблице как опубликованные.</span><span class="sxs-lookup"><span data-stu-id="1788a-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="1788a-172">Затем используйте таблицу просто как объект для отслеживания событий интеграции в случае проблем в удаленных микрослужбах и выполняйте необходимые действия, основываясь на хранящихся событиях интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="1788a-173">Используйте таблицу как очередь.</span><span class="sxs-lookup"><span data-stu-id="1788a-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="1788a-174">Отдельный поток или процесс приложения обращается к таблице событий интеграции, публикует события в шине событий, а затем выполняет местную транзакцию, чтобы отметить события как опубликованные.</span><span class="sxs-lookup"><span data-stu-id="1788a-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="1788a-175">На рисунке 6-22 показана архитектура для первого из этих подходов.</span><span class="sxs-lookup"><span data-stu-id="1788a-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Схема атомарности при публикации без рабочей микрослужбы.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="1788a-177">**Рис. 6-22**.</span><span class="sxs-lookup"><span data-stu-id="1788a-177">**Figure 6-22**.</span></span> <span data-ttu-id="1788a-178">Атомарность при публикации события в шине событий</span><span class="sxs-lookup"><span data-stu-id="1788a-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="1788a-179">В подходе, проиллюстрированном на рисунке 6-22, отсутствует дополнительная рабочая микрослужба, которая проверяет и подтверждает успешную публикацию событий интеграции.</span><span class="sxs-lookup"><span data-stu-id="1788a-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="1788a-180">В случае сбоя эта дополнительная проверяющая микрослужба может считать события из таблицы и опубликовать их повторно, то есть повторить шаг 2.</span><span class="sxs-lookup"><span data-stu-id="1788a-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="1788a-181">При втором подходе вы используете таблицу EventLog в качестве очереди и всегда применяете рабочую микрослужбу для публикации сообщений.</span><span class="sxs-lookup"><span data-stu-id="1788a-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="1788a-182">Подобный процесс показан на рисунке 6-23.</span><span class="sxs-lookup"><span data-stu-id="1788a-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="1788a-183">Здесь изображена дополнительная микрослужба, и таблица является единственным источником при публикации событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Схема атомарности при публикации с рабочей микрослужбой.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="1788a-185">**Рис. 6-23**.</span><span class="sxs-lookup"><span data-stu-id="1788a-185">**Figure 6-23**.</span></span> <span data-ttu-id="1788a-186">Атомарность при публикации события в шине событий с рабочей микрослужбой</span><span class="sxs-lookup"><span data-stu-id="1788a-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="1788a-187">Для простоты в примере приложения eShopOnContainers используется первый подход (без дополнительных процессов или проверяющих микрослужб) и шина событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="1788a-188">Однако пример eShopOnContainers не обрабатывает все возможные случаи сбоев.</span><span class="sxs-lookup"><span data-stu-id="1788a-188">However, the eShopOnContainers sample is not handling all possible failure cases.</span></span> <span data-ttu-id="1788a-189">В реальном приложении, развернутом в облаке, вы должны учитывать факт неизбежности сбоев и реализовывать эту логику проверки и повторной отправки.</span><span class="sxs-lookup"><span data-stu-id="1788a-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="1788a-190">Таблица в качестве очереди эффективнее первого подхода, если эта таблица является единственным источником событий при их публикации (с помощью рабочего процесса) через шину событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="1788a-191">Реализация атомарности при публикации события интеграции через шину событий</span><span class="sxs-lookup"><span data-stu-id="1788a-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="1788a-192">В следующем коде показано, как можно создать одну транзакцию с несколькими объектами DbContext — один контекст связан с исходными обновляемыми данными, а второй — с таблицей IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="1788a-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="1788a-193">Транзакция в приведенном ниже примере кода не будет устойчивой, если при выполнении кода возникнут проблемы с подключением к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1788a-193">The transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="1788a-194">Это может произойти в облачных системах, таких как база данных SQL Azure, которые могут перемещать базы данных между серверами.</span><span class="sxs-lookup"><span data-stu-id="1788a-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="1788a-195">Реализация устойчивых транзакций в нескольких контекстах описана в разделе [Реализация устойчивых SQL-соединений с платформой Entity Framework Core](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md).</span><span class="sxs-lookup"><span data-stu-id="1788a-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="1788a-196">Чтобы было понятнее, в следующем примере показан весь процесс в одном фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="1788a-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="1788a-197">Но в приложении eShopOnContainers для простоты выполнены рефакторинг и разделение этой логики на несколько классов.</span><span class="sxs-lookup"><span data-stu-id="1788a-197">However, the eShopOnContainers implementation is refactored and splits this logic into multiple classes so it's easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate)
{
  var catalogItem =
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id ==
                                                               productToUpdate.Id);
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false;
  IntegrationEvent priceChangedEvent = null;

  if (catalogItem.Price != productToUpdate.Price)
          raiseProductPriceChangedEvent = true;

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price;
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price,
                                                                  oldPrice);
  }
  // Update current product
  catalogItem = productToUpdate;

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent)
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem);
           await _catalogContext.SaveChangesAsync();

           await _integrationEventLogService.SaveEventAsync(priceChangedEvent);

           transaction.Commit();
        }

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

<span data-ttu-id="1788a-198">После создания события интеграции ProductPriceChangedIntegrationEvent транзакция, хранящая операцию в исходной предметной области (обновление позиции каталога), также включает сохранение события в таблице EventLog.</span><span class="sxs-lookup"><span data-stu-id="1788a-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="1788a-199">В результате получается одна транзакция, и вы всегда можете проверить, были ли отправлены сообщения о событии.</span><span class="sxs-lookup"><span data-stu-id="1788a-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="1788a-200">Таблица журнала событий обновляется атомарно операцией исходной базы данных с помощью локальной транзакции в этой же базе данных.</span><span class="sxs-lookup"><span data-stu-id="1788a-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="1788a-201">Если происходит сбой операции, выдается исключение, и транзакция откатывает выполненную операцию, поддерживая согласованность между операциями предметной области и сообщениями о событии, сохраненными в таблице.</span><span class="sxs-lookup"><span data-stu-id="1788a-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="1788a-202">Получение сообщений из подписок: обработчики событий в микрослужбах-получателях</span><span class="sxs-lookup"><span data-stu-id="1788a-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="1788a-203">Помимо логики подписки на события вам необходимо реализовать внутренний код для обработчиков событий интеграции (например, метод обратного вызова).</span><span class="sxs-lookup"><span data-stu-id="1788a-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="1788a-204">В обработчике событий вы указываете, где будут получаться и обрабатываться сообщения о событиях определенного типа.</span><span class="sxs-lookup"><span data-stu-id="1788a-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="1788a-205">Сначала обработчик событий получает экземпляр события от шины событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="1788a-206">Затем он выполняет поиск компонента, нуждающегося в обработке и связанного с этим событием интеграции, распространяя и сохраняя событие как изменение состояния в микрослужбе-получателе.</span><span class="sxs-lookup"><span data-stu-id="1788a-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="1788a-207">Например если событие ProductPriceChanged инициируется в микрослужбе каталога, оно обрабатывается в микрослужбе корзины и изменяет состояние в этой микрослужбе-получателе, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="1788a-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="1788a-208">Обработчик событий должен проверить, существует ли товар в экземплярах корзины.</span><span class="sxs-lookup"><span data-stu-id="1788a-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="1788a-209">Он также обновляет цену товара в каждой соответствующей позиции строки корзины.</span><span class="sxs-lookup"><span data-stu-id="1788a-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="1788a-210">Наконец, он создает для пользователя предупреждение об изменении цены, как показано на рисунке 6-24.</span><span class="sxs-lookup"><span data-stu-id="1788a-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Снимок экрана: окно браузера с уведомлением об изменении цены в корзине пользователя.](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="1788a-212">**Рис. 6-24**.</span><span class="sxs-lookup"><span data-stu-id="1788a-212">**Figure 6-24**.</span></span> <span data-ttu-id="1788a-213">Отображение изменения цены товара в корзине на основе данных о событиях интеграции</span><span class="sxs-lookup"><span data-stu-id="1788a-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="1788a-214">Идемпотентность в событиях сообщения об обновлении</span><span class="sxs-lookup"><span data-stu-id="1788a-214">Idempotency in update message events</span></span>

<span data-ttu-id="1788a-215">Важный аспект событий сообщения об обновлении заключается в том, что при сбое взаимодействия сообщение должно отправляться повторно.</span><span class="sxs-lookup"><span data-stu-id="1788a-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="1788a-216">В противном случае фоновая задача попытается опубликовать уже опубликованное событие, создавая состояние гонки.</span><span class="sxs-lookup"><span data-stu-id="1788a-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="1788a-217">Убедитесь, что обновления либо являются идемпотентными, любо предоставляют достаточно информации, чтобы вы могли найти дублирующие данные, отменить их и отправить обратно только один ответ.</span><span class="sxs-lookup"><span data-stu-id="1788a-217">Make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="1788a-218">Как отмечалось ранее, идемпотентность означает, что операция может выполняться несколько раз без изменения результатов.</span><span class="sxs-lookup"><span data-stu-id="1788a-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="1788a-219">В среде обмена сообщениями, например при передаче событий, событие является идемпотентным, если его можно доставить несколько раз без изменения результатов для микрослужбы-получателя.</span><span class="sxs-lookup"><span data-stu-id="1788a-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="1788a-220">Это необходимо из-за особенностей самого события или из-за способа обработки событий в системе.</span><span class="sxs-lookup"><span data-stu-id="1788a-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="1788a-221">Идемпотентность сообщений важна в любом приложении, где используется обмен сообщениями, а не только в приложениях с шаблоном шины событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="1788a-222">Пример идемпотентной операции — инструкция SQL, которая вставляет данные в таблицу только в том случае, если этих данных еще нет в таблице.</span><span class="sxs-lookup"><span data-stu-id="1788a-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="1788a-223">Сколько бы раз вы ни выполняли эту инструкцию SQL по вставке, результат не изменится — таблица будет содержать эти данные.</span><span class="sxs-lookup"><span data-stu-id="1788a-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="1788a-224">Такая идемпотентность также может быть необходима при работе с сообщениями, если сообщения могут быть отправлены и, следовательно, обработаны несколько раз.</span><span class="sxs-lookup"><span data-stu-id="1788a-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="1788a-225">Например, если по логике повтора отправитель несколько раз посылает одно и то же сообщение, необходимо обеспечить идемпотентность.</span><span class="sxs-lookup"><span data-stu-id="1788a-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="1788a-226">Вы можете создать идемпотентные сообщения.</span><span class="sxs-lookup"><span data-stu-id="1788a-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="1788a-227">Например, можно создать событие, которое предписывает "установить цену товара 25 рублей" вместо "увеличить цену товара на 5 рублей".</span><span class="sxs-lookup"><span data-stu-id="1788a-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="1788a-228">Первое сообщение можно безопасно обрабатывать сколько угодно раз, результат не изменится.</span><span class="sxs-lookup"><span data-stu-id="1788a-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="1788a-229">Со вторым сообщением будет иначе.</span><span class="sxs-lookup"><span data-stu-id="1788a-229">That is not true for the second message.</span></span> <span data-ttu-id="1788a-230">Но даже в первом случае можно отказаться от обработки первого события, поскольку система уже могла послать обновленное событие изменения цены, и тогда будет изменена уже новая цена.</span><span class="sxs-lookup"><span data-stu-id="1788a-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="1788a-231">Еще один пример — событие выполнения заказа, распространяемое нескольким подписчикам.</span><span class="sxs-lookup"><span data-stu-id="1788a-231">Another example might be an order-completed event that's propagated to multiple subscribers.</span></span> <span data-ttu-id="1788a-232">Приложение должно обновлять сведения о заказах в других системах однократно, даже если существуют дублирующие события сообщений для одного события выполнения заказа.</span><span class="sxs-lookup"><span data-stu-id="1788a-232">The app has to make sure that order information is updated in other systems only once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="1788a-233">У события должен быть какой-то идентификатор, чтобы вы могли создать логику, по которой каждое событие обрабатывается получателем только один раз.</span><span class="sxs-lookup"><span data-stu-id="1788a-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="1788a-234">Иногда обработка сообщений является идемпотентной сама по себе.</span><span class="sxs-lookup"><span data-stu-id="1788a-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="1788a-235">Например, если система создает эскизы изображений, неважно, сколько раз будет обработано сообщение о созданном эскизе, результат неизменен — эскизы созданы.</span><span class="sxs-lookup"><span data-stu-id="1788a-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="1788a-236">С другой стороны, такие операции, как вызов шлюза оплаты для списания средств с кредитной карты, могут быть совсем не идемпотентными.</span><span class="sxs-lookup"><span data-stu-id="1788a-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="1788a-237">В этих случаях необходимо гарантировать, что обработка сообщения несколько раз приведет к ожидаемым результатам.</span><span class="sxs-lookup"><span data-stu-id="1788a-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1788a-238">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="1788a-238">Additional resources</span></span>

- <span data-ttu-id="1788a-239">**Соблюдение идемпотентности сообщений** </span><span class="sxs-lookup"><span data-stu-id="1788a-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="1788a-240">Дедупликация сообщений о событиях интеграции</span><span class="sxs-lookup"><span data-stu-id="1788a-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="1788a-241">Вы можете гарантировать, что события сообщения будут отправлены или обработаны только один раз для подписчика, на разных уровнях.</span><span class="sxs-lookup"><span data-stu-id="1788a-241">You can make sure that message events are sent and processed only once per subscriber at different levels.</span></span> <span data-ttu-id="1788a-242">Например, можно использовать функцию дедупликации в вашей инфраструктуре обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="1788a-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="1788a-243">Или можно применить пользовательскую логику в микрослужбе назначения.</span><span class="sxs-lookup"><span data-stu-id="1788a-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="1788a-244">Лучший вариант — проверки и на уровне транспортировки, и на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="1788a-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="1788a-245">Дедупликация событий сообщения на уровне EventHandler</span><span class="sxs-lookup"><span data-stu-id="1788a-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="1788a-246">Один из способов убедиться, что событие будет обработано получателями только один раз, — применить определенную логику при обработке событий сообщения в обработчиках событий.</span><span class="sxs-lookup"><span data-stu-id="1788a-246">One way to make sure that an event is processed only once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="1788a-247">Например, такой подход используется в приложении eShopOnContainers, как видно в [исходном коде класса UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs), который получает событие интеграции `UserCheckoutAcceptedIntegrationEvent`.</span><span class="sxs-lookup"><span data-stu-id="1788a-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives a `UserCheckoutAcceptedIntegrationEvent` integration event.</span></span> <span data-ttu-id="1788a-248">(В данном случае `CreateOrderCommand` заключается в оболочку `IdentifiedCommand` с использованием `eventMsg.RequestId` в качестве идентификатора, прежде чем отправлять его в обработчик команд.)</span><span class="sxs-lookup"><span data-stu-id="1788a-248">(In this case, the `CreateOrderCommand` is wrapped with an `IdentifiedCommand`, using the `eventMsg.RequestId` as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="1788a-249">Дедупликация сообщений при использовании RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="1788a-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="1788a-250">В случае периодических сбоев в сети сообщения могут дублироваться, и получатель сообщений должен быть готов к обработке повторяющихся сообщений.</span><span class="sxs-lookup"><span data-stu-id="1788a-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="1788a-251">По возможности получатели должны обрабатывать сообщения идемпотентно. Это лучше, чем явная обработка с дедупликацией.</span><span class="sxs-lookup"><span data-stu-id="1788a-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="1788a-252">Согласно [документации RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), если сообщение доставлено получателю, а затем повторно поставлено в очередь (например, оно не было подтверждено до разрыва соединения с получателем), RabbitMQ пометит его как доставляемое повторно, когда оно снова будет доставляться (этому же получателю или другому).</span><span class="sxs-lookup"><span data-stu-id="1788a-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), "If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="1788a-253">Если сообщение имеет метку "доставляется повторно", получатель должен учитывать это, поскольку он мог уже обработать это сообщение.</span><span class="sxs-lookup"><span data-stu-id="1788a-253">If the "redelivered" flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="1788a-254">Но это необязательно. Сообщение могло так и не дойти до получателя после отправки из брокера сообщений, например из-за проблем в сети.</span><span class="sxs-lookup"><span data-stu-id="1788a-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="1788a-255">С другой стороны, если нет метки "доставляется повторно", сообщение гарантированно было отправлено только один раз.</span><span class="sxs-lookup"><span data-stu-id="1788a-255">On the other hand, if the "redelivered" flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="1788a-256">Таким образом, получатель должен дедуплицировать или обрабатывать сообщения идемпотентно только в том случае, если они имеют метку "доставляется повторно".</span><span class="sxs-lookup"><span data-stu-id="1788a-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the "redelivered" flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1788a-257">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="1788a-257">Additional resources</span></span>

- <span data-ttu-id="1788a-258">**Ветвление eShopOnContainers с использованием NServiceBus (Particular Software)**  </span><span class="sxs-lookup"><span data-stu-id="1788a-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="1788a-259">**Обмен сообщениями на основе событий** </span><span class="sxs-lookup"><span data-stu-id="1788a-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="1788a-260">**Джимми Богард (Jimmy Bogard). Рефакторинг для обеспечения отказоустойчивости: оценка взаимозависимости** </span><span class="sxs-lookup"><span data-stu-id="1788a-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="1788a-261">**Канал публикации и подписки** </span><span class="sxs-lookup"><span data-stu-id="1788a-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="1788a-262">**Взаимодействие между ограниченными контекстами** </span><span class="sxs-lookup"><span data-stu-id="1788a-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="1788a-263">**Итоговая согласованность** </span><span class="sxs-lookup"><span data-stu-id="1788a-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="1788a-264">**Филип Браун (Philip Brown). Стратегии интеграции ограниченных контекстов** </span><span class="sxs-lookup"><span data-stu-id="1788a-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="1788a-265">**Крис Ричардсон (Chris Richardson). Разработка транзакционных микрослужб с помощью агрегатов, порождения событий и CQRS. Часть 2** </span><span class="sxs-lookup"><span data-stu-id="1788a-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="1788a-266">**Крис Ричардсон (Chris Richardson). Шаблон порождения событий** </span><span class="sxs-lookup"><span data-stu-id="1788a-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="1788a-267">**Знакомство с порождением событий** </span><span class="sxs-lookup"><span data-stu-id="1788a-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="1788a-268">**База данных хранилища событий**.</span><span class="sxs-lookup"><span data-stu-id="1788a-268">**Event Store database**.</span></span> <span data-ttu-id="1788a-269">Официальный сайт</span><span class="sxs-lookup"><span data-stu-id="1788a-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="1788a-270">**Патрик Номменсен (Patrick Nommensen). Управление данными на основе событий для микрослужб** </span><span class="sxs-lookup"><span data-stu-id="1788a-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="1788a-271">**Теорема CAP** </span><span class="sxs-lookup"><span data-stu-id="1788a-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="1788a-272">**Что такое теорема CAP?**</span><span class="sxs-lookup"><span data-stu-id="1788a-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="1788a-273">**Основные сведения о согласованности данных** </span><span class="sxs-lookup"><span data-stu-id="1788a-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="1788a-274">**Рик Сейлинг (Rick Saling). Теорема CAP: почему в случае с облачными средами и Интернетом все иначе** </span><span class="sxs-lookup"><span data-stu-id="1788a-274">**Rick Saling. The CAP Theorem: Why "Everything is Different" with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="1788a-275">**Эрик Брюер (Eric Brewer). CAP двенадцать лет спустя: Как изменились "правила"**  </span><span class="sxs-lookup"><span data-stu-id="1788a-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="1788a-276">**Служебная шина Azure. Обмен сообщениями через брокер: обнаружение повторений**  </span><span class="sxs-lookup"><span data-stu-id="1788a-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="1788a-277">**Руководство по обеспечению надежности** (документация RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="1788a-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="1788a-278">[Назад](rabbitmq-event-bus-development-test-environment.md)
> [Вперед](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="1788a-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>
