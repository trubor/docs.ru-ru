---
title: Реализация шины событий с помощью RabbitMQ для среды разработки или тестирования
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Использование RabbitMQ для реализации сообщений шины событий для событий интеграции для сред разработки или тестирования.
ms.date: 01/13/2021
ms.openlocfilehash: a1e7d11e376080a03269f202fa6ae24ffeb0f4d2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188085"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="977fe-103">Реализация шины событий с помощью RabbitMQ для среды разработки или тестирования</span><span class="sxs-lookup"><span data-stu-id="977fe-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="977fe-104">Начать следует с того, что если вы создаете пользовательскую шину событий на основе RabbitMQ в контейнере, как это делается в приложении eShopOnContainers, ее следует использовать только в средах разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="977fe-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="977fe-105">Не применяйте ее в рабочей среде, если только вы не разрабатываете ее в рамках служебной шины, готовой к развертыванию в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="977fe-105">Don't use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="977fe-106">Простая пользовательская шина событий может быть лишена многих критически важных для рабочей среды возможностей, которыми обладают коммерческие служебные шины.</span><span class="sxs-lookup"><span data-stu-id="977fe-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="977fe-107">Одна из пользовательских реализаций шины событий в eShopOnContainers по сути представляет собой библиотеку, использующую API RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="977fe-107">One of the event bus custom implementations in eShopOnContainers is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="977fe-108">(Существует и еще одна реализация на основе Служебной шины Azure.)</span><span class="sxs-lookup"><span data-stu-id="977fe-108">(There's another implementation based on Azure Service Bus.)</span></span>

<span data-ttu-id="977fe-109">Реализация шины событий с помощью RabbitMQ позволяет микрослужбам подписываться на события, публиковать и принимать их, как показано на рисунке 6–21.</span><span class="sxs-lookup"><span data-stu-id="977fe-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 6-21.</span></span>

![Схема, на которой показан API RabbitMQ между отправителем и получателем сообщений.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

<span data-ttu-id="977fe-111">**Рис. 6–21.**</span><span class="sxs-lookup"><span data-stu-id="977fe-111">**Figure 6-21.**</span></span> <span data-ttu-id="977fe-112">Реализация шины событий на основе RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="977fe-112">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="977fe-113">RabbitMQ выступает в роли посредника между издателем сообщения и подписчиками и обрабатывает распространение.</span><span class="sxs-lookup"><span data-stu-id="977fe-113">RabbitMQ functions as an intermediary between message publisher and subscribers, to handle distribution.</span></span> <span data-ttu-id="977fe-114">В коде класс EventBusRabbitMQ реализует универсальный интерфейс IEventBus.</span><span class="sxs-lookup"><span data-stu-id="977fe-114">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="977fe-115">Для этого применяется внедрение зависимостей, что позволяет переходить от этой версии для разработки и тестирования к рабочей версии.</span><span class="sxs-lookup"><span data-stu-id="977fe-115">This implementation is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

<span data-ttu-id="977fe-116">Реализация образца шины событий для разработки и тестирования на основе RabbitMQ представляет собой стандартный код.</span><span class="sxs-lookup"><span data-stu-id="977fe-116">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="977fe-117">Она должна обрабатывать подключение к серверу RabbitMQ и предоставлять код для публикации события сообщения в очередях.</span><span class="sxs-lookup"><span data-stu-id="977fe-117">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="977fe-118">Кроме того, должен быть реализован словарь коллекций, содержащий обработчики событий интеграции для каждого типа событий. Для каждого из этих типов событий могут применяться разные способы создания экземпляра и подписки для каждой микрослужбы-получателя, как показано на рисунке 6–21.</span><span class="sxs-lookup"><span data-stu-id="977fe-118">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 6-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="977fe-119">Реализация простого метода публикации с помощью RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="977fe-119">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="977fe-120">Следующий код является \**_упрощенной_* _ версией реализации шины событий для RabbitMQ, демонстрирующей весь сценарий.</span><span class="sxs-lookup"><span data-stu-id="977fe-120">The following code is a \**_simplified_* _ version of an event bus implementation for RabbitMQ, to showcase the whole scenario.</span></span> <span data-ttu-id="977fe-121">Вам необязательно обрабатывать подключение таким образом.</span><span class="sxs-lookup"><span data-stu-id="977fe-121">You don't really handle the connection this way.</span></span> <span data-ttu-id="977fe-122">Чтобы увидеть полную реализацию, просмотрите фактический код в репозитории [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs).</span><span class="sxs-lookup"><span data-stu-id="977fe-122">To see the full implementation, see the actual code in the [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) repository.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

<span data-ttu-id="977fe-123">[Реальный код](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) метода Publish в приложении eShopOnContainers улучшен с помощью политики повтора [Polly](https://github.com/App-vNext/Polly), которая пытается выполнить задачу повторно несколько раз, если контейнер RabbitMQ не готов.</span><span class="sxs-lookup"><span data-stu-id="977fe-123">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task some times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="977fe-124">Это может произойти, если контейнеры запускаются с помощью docker-compose. Например, контейнер RabbitMQ может запускаться медленнее других.</span><span class="sxs-lookup"><span data-stu-id="977fe-124">This scenario can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="977fe-125">Как было сказано ранее, в RabbitMQ возможно множество конфигураций, поэтому этот код следует использовать только в средах разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="977fe-125">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="977fe-126">Реализация кода подписки с помощью интерфейса API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="977fe-126">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="977fe-127">Так же как и в случае с кодом публикации, приведенный ниже код представляет собой часть упрощенной реализации шины событий для RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="977fe-127">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="977fe-128">Изменять его также обычно не нужно, если его не требуется улучшить.</span><span class="sxs-lookup"><span data-stu-id="977fe-128">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

<span data-ttu-id="977fe-129">С каждым типом событий связан канал для получения событий из RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="977fe-129">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="977fe-130">Для каждого канала и типа событий может быть столько обработчиков событий, сколько требуется.</span><span class="sxs-lookup"><span data-stu-id="977fe-130">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="977fe-131">Метод Subscribe принимает объект IIntegrationEventHandler, который похож на метод обратного вызова в текущей микрослужбе, а также связанный с ним объект IntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="977fe-131">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="977fe-132">Затем добавляется обработчик событий в список обработчиков событий, которые может иметь каждый тип событий интеграции в клиентской микрослужбе.</span><span class="sxs-lookup"><span data-stu-id="977fe-132">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="977fe-133">Если код клиента еще не подписался на событие, для данного типа событий создается канал, который позволяет получать события из RabbitMQ принудительным образом, когда они публикуются из любой другой службы.</span><span class="sxs-lookup"><span data-stu-id="977fe-133">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>

<span data-ttu-id="977fe-134">Как упоминалось выше, шина событий, реализованная в eShopOnContainers, предназначена только для образовательных целей, так как она обрабатывает только основные сценарии и не готова к рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="977fe-134">As mentioned above, the event bus implemented in eShopOnContainers has only and educational purpose, since it only handles the main scenarios, so it's not ready for production.</span></span>

<span data-ttu-id="977fe-135">Сведения о рабочих сценариях просмотрите в дополнительных ресурсах о RabbitMQ и разделе [Реализация связи на основе событий между микрослужбами](./integration-event-based-microservice-communications.md#additional-resources).</span><span class="sxs-lookup"><span data-stu-id="977fe-135">For production scenarios check the additional resources below, specific for RabbitMQ, and the [Implementing event-based communication between microservices](./integration-event-based-microservice-communications.md#additional-resources) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="977fe-136">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="977fe-136">Additional resources</span></span>

<span data-ttu-id="977fe-137">Готовое к работе решение с поддержкой RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="977fe-137">A production-ready solution with support for RabbitMQ.</span></span>

- <span data-ttu-id="977fe-138">_ \*EasyNetQ\*\* — клиент API .NET для RabbitMQ с открытым кодом </span><span class="sxs-lookup"><span data-stu-id="977fe-138">_ *EasyNetQ*\* - Open Source .NET API client for RabbitMQ </span></span>\
  <https://easynetq.com/>

- <span data-ttu-id="977fe-139">**MassTransit** </span><span class="sxs-lookup"><span data-stu-id="977fe-139">**MassTransit** </span></span>\
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> <span data-ttu-id="977fe-140">[Назад](integration-event-based-microservice-communications.md)
> [Вперед](subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="977fe-140">[Previous](integration-event-based-microservice-communications.md)
[Next](subscribe-events.md)</span></span>
