---
title: Реализация шины событий с помощью RabbitMQ для среды разработки или тестирования
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Использование RabbitMQ для реализации сообщений шины событий для событий интеграции для сред разработки или тестирования.
ms.date: 01/13/2021
ms.openlocfilehash: b67b6cf92ac2c29b9eff07c2c9603206e42968a3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258082"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Реализация шины событий с помощью RabbitMQ для среды разработки или тестирования

Начать следует с того, что если вы создаете пользовательскую шину событий на основе RabbitMQ в контейнере, как это делается в приложении eShopOnContainers, ее следует использовать только в средах разработки и тестирования. Не применяйте ее в рабочей среде, если только вы не разрабатываете ее в рамках служебной шины, готовой к развертыванию в рабочей среде. Простая пользовательская шина событий может быть лишена многих критически важных для рабочей среды возможностей, которыми обладают коммерческие служебные шины.

Одна из пользовательских реализаций шины событий в eShopOnContainers по сути представляет собой библиотеку, использующую API RabbitMQ. (Существует и еще одна реализация на основе Служебной шины Azure.)

Реализация шины событий с помощью RabbitMQ позволяет микрослужбам подписываться на события, публиковать и принимать их, как показано на рисунке 6–21.

![Схема, на которой показан API RabbitMQ между отправителем и получателем сообщений.](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**Рис. 6–21.** Реализация шины событий на основе RabbitMQ

RabbitMQ выступает в роли посредника между издателем сообщения и подписчиками и обрабатывает распространение. В коде класс EventBusRabbitMQ реализует универсальный интерфейс IEventBus. Для этого применяется внедрение зависимостей, что позволяет переходить от этой версии для разработки и тестирования к рабочей версии.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

Реализация образца шины событий для разработки и тестирования на основе RabbitMQ представляет собой стандартный код. Она должна обрабатывать подключение к серверу RabbitMQ и предоставлять код для публикации события сообщения в очередях. Кроме того, должен быть реализован словарь коллекций, содержащий обработчики событий интеграции для каждого типа событий. Для каждого из этих типов событий могут применяться разные способы создания экземпляра и подписки для каждой микрослужбы-получателя, как показано на рисунке 6–21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Реализация простого метода публикации с помощью RabbitMQ

Следующий код является ***упрощенной*** версией реализации шины событий для RabbitMQ, демонстрирующей весь сценарий. Вам необязательно обрабатывать подключение таким образом. Чтобы увидеть полную реализацию, просмотрите фактический код в репозитории [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs).

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

[Реальный код](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) метода Publish в приложении eShopOnContainers улучшен с помощью политики повтора [Polly](https://github.com/App-vNext/Polly), которая пытается выполнить задачу повторно несколько раз, если контейнер RabbitMQ не готов. Это может произойти, если контейнеры запускаются с помощью docker-compose. Например, контейнер RabbitMQ может запускаться медленнее других.

Как было сказано ранее, в RabbitMQ возможно множество конфигураций, поэтому этот код следует использовать только в средах разработки и тестирования.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Реализация кода подписки с помощью интерфейса API RabbitMQ

Так же как и в случае с кодом публикации, приведенный ниже код представляет собой часть упрощенной реализации шины событий для RabbitMQ. Изменять его также обычно не нужно, если его не требуется улучшить.

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

С каждым типом событий связан канал для получения событий из RabbitMQ. Для каждого канала и типа событий может быть столько обработчиков событий, сколько требуется.

Метод Subscribe принимает объект IIntegrationEventHandler, который похож на метод обратного вызова в текущей микрослужбе, а также связанный с ним объект IntegrationEvent. Затем добавляется обработчик событий в список обработчиков событий, которые может иметь каждый тип событий интеграции в клиентской микрослужбе. Если код клиента еще не подписался на событие, для данного типа событий создается канал, который позволяет получать события из RabbitMQ принудительным образом, когда они публикуются из любой другой службы.

Как упоминалось выше, шина событий, реализованная в eShopOnContainers, предназначена только для образовательных целей, так как она обрабатывает только основные сценарии и не готова к рабочей среде.

Сведения о рабочих сценариях просмотрите в дополнительных ресурсах о RabbitMQ и разделе [Реализация связи на основе событий между микрослужбами](./integration-event-based-microservice-communications.md#additional-resources).

## <a name="additional-resources"></a>Дополнительные ресурсы

Готовое к работе решение с поддержкой RabbitMQ.

- **EasyNetQ** — клиент API .NET для RabbitMQ с открытым кодом \
  <https://easynetq.com/>

- **MassTransit** \
  <https://masstransit-project.com/>
  
- **Rebus** — служебная шина .NET с открытым кодом <https://github.com/rebus-org/Rebus>

> [!div class="step-by-step"]
> [Назад](integration-event-based-microservice-communications.md)
> [Вперед](subscribe-events.md)
