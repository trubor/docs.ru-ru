---
title: Стандартный блок ДАПР Publishing & Subscribe
description: Описание ДАПР Publishing & Subscribe, а также способы его применения
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 4cb249bafc8241eb54153be2605c33d0a3adb619
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604688"
---
# <a name="the-dapr-publish--subscribe-building-block"></a><span data-ttu-id="95889-103">Стандартный блок ДАПР Publishing & Subscribe</span><span class="sxs-lookup"><span data-stu-id="95889-103">The Dapr publish & subscribe building block</span></span>

<span data-ttu-id="95889-104">[Шаблон публикации-подписки](/azure/architecture/patterns/publisher-subscriber) (часто называется "Pub/republish") — это хорошо известная и широко используемая схема обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="95889-104">The [Publish-Subscribe pattern](/azure/architecture/patterns/publisher-subscriber) (often referred to as "pub/sub") is a well-known and widely used messaging pattern.</span></span> <span data-ttu-id="95889-105">Архитекторы часто используют его в распределенных приложениях.</span><span class="sxs-lookup"><span data-stu-id="95889-105">Architects commonly embrace it in distributed applications.</span></span> <span data-ttu-id="95889-106">Однако их реализация может быть сложной.</span><span class="sxs-lookup"><span data-stu-id="95889-106">However, the plumbing to implement it can be complex.</span></span> <span data-ttu-id="95889-107">Часто различия между компонентами различных продуктов обмена сообщениями являются незаметными.</span><span class="sxs-lookup"><span data-stu-id="95889-107">There are often subtle feature differences across different messaging products.</span></span> <span data-ttu-id="95889-108">ДАПР предлагает стандартный блок, который значительно упрощает реализацию функций Pub/подкаталога.</span><span class="sxs-lookup"><span data-stu-id="95889-108">Dapr offers a building block that significantly simplifies implementing pub/sub functionality.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="95889-109">Решение</span><span class="sxs-lookup"><span data-stu-id="95889-109">What it solves</span></span>

<span data-ttu-id="95889-110">Основное преимущество шаблона Publish-Subscribe — **слабая** связь, которая иногда называется [временной](/azure/architecture/guide/technology-choices/messaging#decoupling)разсоединением.</span><span class="sxs-lookup"><span data-stu-id="95889-110">The primary advantage of the Publish-Subscribe pattern is **loose coupling**, sometimes referred to as [temporal decoupling](/azure/architecture/guide/technology-choices/messaging#decoupling).</span></span> <span data-ttu-id="95889-111">Шаблон отделяет службы, отправляющие сообщения ( **Издатели**) от служб, которые используют сообщения ( **Подписчики**).</span><span class="sxs-lookup"><span data-stu-id="95889-111">The pattern decouples services that send messages (the **publishers**) from services that consume messages (the **subscribers**).</span></span> <span data-ttu-id="95889-112">Как издатели, так и подписчики не знают друг о друга. они зависят от централизованного **брокера сообщений** , который распространяет сообщения.</span><span class="sxs-lookup"><span data-stu-id="95889-112">Both publishers and subscribers are unaware of each other - both are dependent on a centralized **message broker** that distributes the messages.</span></span>

<span data-ttu-id="95889-113">На рис. 7-1 показана высокоуровневая архитектура шаблона публикации и подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="95889-113">Figure 7-1 shows the high-level architecture of the pub/sub pattern.</span></span>

![Шаблон публикации и подпапки](./media/publish-subscribe/pub-sub-pattern.png)

<span data-ttu-id="95889-115">**Рис. 7-1**.</span><span class="sxs-lookup"><span data-stu-id="95889-115">**Figure 7-1**.</span></span> <span data-ttu-id="95889-116">Шаблон публикации и подпапки.</span><span class="sxs-lookup"><span data-stu-id="95889-116">The pub/sub pattern.</span></span>

<span data-ttu-id="95889-117">На предыдущем рисунке обратите внимание на шаги шаблона:</span><span class="sxs-lookup"><span data-stu-id="95889-117">From the previous figure, note the steps of the pattern:</span></span>

1. <span data-ttu-id="95889-118">Издатели отправляют сообщения в брокер сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-118">Publishers send messages to the message broker.</span></span>
1. <span data-ttu-id="95889-119">Подписчики привязываются к подписке в брокере сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-119">Subscribers bind to a subscription on the message broker.</span></span>
1. <span data-ttu-id="95889-120">Брокер сообщений пересылает копию сообщения заинтересованным подпискам.</span><span class="sxs-lookup"><span data-stu-id="95889-120">The message broker forwards a copy of the message to interested subscriptions.</span></span>
1. <span data-ttu-id="95889-121">Подписчики используют сообщения из своих подписок.</span><span class="sxs-lookup"><span data-stu-id="95889-121">Subscribers consume messages from their subscriptions.</span></span>

<span data-ttu-id="95889-122">Большинство брокеров сообщений инкапсулируют механизм очередей, который может сохранять сообщения после получения.</span><span class="sxs-lookup"><span data-stu-id="95889-122">Most message brokers encapsulate a queueing mechanism that can persist messages once received.</span></span> <span data-ttu-id="95889-123">С его помощью брокер сообщений гарантирует **устойчивость** , сохранив сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-123">With it, the message broker guarantees **durability** by storing the message.</span></span> <span data-ttu-id="95889-124">Подписчики не должны быть доступны немедленно или даже в режиме в сети, когда издатель отправляет сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-124">Subscribers don't need to be immediately available or even online when a publisher sends a message.</span></span> <span data-ttu-id="95889-125">После получения доступа подписчик получает и обрабатывает сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-125">Once available, the subscriber receives and processes the message.</span></span>  <span data-ttu-id="95889-126">ДАПР гарантирует как **минимум одну** семантику доставки сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-126">Dapr guarantees **At-Least-Once** semantics for message delivery.</span></span> <span data-ttu-id="95889-127">После публикации сообщения оно будет доставлено хотя бы одному заинтересованному подписчику.</span><span class="sxs-lookup"><span data-stu-id="95889-127">Once a message is published, it will be delivered at least once to any interested subscriber.</span></span>

 > <span data-ttu-id="95889-128">Если служба может обработать сообщение только один раз, необходимо предоставить [проверку идемпотентности](/azure/architecture/microservices/design/api-design#idempotent-operations) , чтобы убедиться, что одно и то же сообщение не обрабатывается несколько раз.</span><span class="sxs-lookup"><span data-stu-id="95889-128">If your service can only process a message once, you'll need to provide an [idempotency check](/azure/architecture/microservices/design/api-design#idempotent-operations) to ensure that the same message is not processed multiple times.</span></span> <span data-ttu-id="95889-129">Хотя такую логику можно закодировать, некоторые брокеры сообщений, например служебная шина Azure, предоставляют встроенные возможности обмена сообщениями об *обнаружении дубликатов* .</span><span class="sxs-lookup"><span data-stu-id="95889-129">While such logic can be coded, some message brokers, such as Azure Service Bus, provide built-in *duplicate detection* messaging capabilities.</span></span>

<span data-ttu-id="95889-130">Доступно несколько продуктов брокера сообщений — как коммерческих, так и с открытым кодом.</span><span class="sxs-lookup"><span data-stu-id="95889-130">There are several message broker products available - both commercially and open-source.</span></span> <span data-ttu-id="95889-131">У каждого есть свои преимущества и недостатки.</span><span class="sxs-lookup"><span data-stu-id="95889-131">Each has advantages and drawbacks.</span></span> <span data-ttu-id="95889-132">Ваше задание должно соответствовать требованиям к системе для соответствующего брокера.</span><span class="sxs-lookup"><span data-stu-id="95889-132">Your job is to match your system requirements to the appropriate broker.</span></span> <span data-ttu-id="95889-133">После выбора рекомендуется отделить приложение от коммуникаций брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-133">Once selected, it's a best practice to decouple your application from message broker plumbing.</span></span> <span data-ttu-id="95889-134">Эту функциональность можно реализовать, заключив брокер внутрь *абстракции*.</span><span class="sxs-lookup"><span data-stu-id="95889-134">You achieve this functionality by wrapping the broker inside an *abstraction*.</span></span> <span data-ttu-id="95889-135">Абстракция инкапсулирует механизм обмена сообщениями и предоставляет в код универсальные операции публикации и подмножества.</span><span class="sxs-lookup"><span data-stu-id="95889-135">The abstraction encapsulates the message plumbing and exposes generic pub/sub operations to your code.</span></span> <span data-ttu-id="95889-136">Код взаимодействует с абстракцией, а не с реальным посредником сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-136">Your code communicates with the abstraction, not the actual message broker.</span></span> <span data-ttu-id="95889-137">При разумном принятии решения вам придется писать и поддерживать абстракцию и ее базовую реализацию.</span><span class="sxs-lookup"><span data-stu-id="95889-137">While a wise decision, you'll have to write and maintain the abstraction and its underlying implementation.</span></span> <span data-ttu-id="95889-138">Этот подход требует использования пользовательского кода, который может быть сложным, повторяющимися и подверженным ошибкам.</span><span class="sxs-lookup"><span data-stu-id="95889-138">This approach requires custom code that can be complex, repetitive, and error-prone.</span></span>

<span data-ttu-id="95889-139">Стандартный блок ДАПР Publish & подписки предоставляет абстракцию и реализацию сообщения.</span><span class="sxs-lookup"><span data-stu-id="95889-139">The Dapr publish & subscribe building block provides the messaging abstraction and implementation out-of-the-box.</span></span> <span data-ttu-id="95889-140">Пользовательский код, который пришлось бы писать, является предварительно созданным и инкапсулированным в стандартном блоке ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-140">The custom code you would have had to write is prebuilt and encapsulated inside the Dapr building block.</span></span> <span data-ttu-id="95889-141">Выполняется привязка к нему и его использование.</span><span class="sxs-lookup"><span data-stu-id="95889-141">You bind to it and consume it.</span></span> <span data-ttu-id="95889-142">Вместо написания кода для обмена сообщениями вы и ваша команда сосредоточены на создании бизнес-функций, которые расширяют ценность для клиентов.</span><span class="sxs-lookup"><span data-stu-id="95889-142">Instead of writing messaging plumbing code, you and your team focus on creating business functionality that adds value to your customers.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="95889-143">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="95889-143">How it works</span></span>

<span data-ttu-id="95889-144">Стандартный блок ДАПР Publish & Subscribe предоставляет платформу API, не зависящую от платформы, для отправки и получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-144">The Dapr publish & subscribe building block provides a platform-agnostic API framework to send and receive messages.</span></span> <span data-ttu-id="95889-145">Ваши службы публикуют сообщения в именованном [разделе](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions).</span><span class="sxs-lookup"><span data-stu-id="95889-145">Your services publish messages to a named [topic](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions#topics-and-subscriptions).</span></span> <span data-ttu-id="95889-146">Ваши службы подписываются на тему для использования сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-146">Your services subscribe to a topic to consume messages.</span></span>

<span data-ttu-id="95889-147">Служба вызывает API Pub/подпрограммы на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="95889-147">The service calls the pub/sub API on the Dapr sidecar.</span></span> <span data-ttu-id="95889-148">Затем расширения обращается к предварительно определенному компоненту ДАПР Pub/подразделу, который инкапсулирует конкретный продукт брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-148">The sidecar then makes calls into a pre-defined Dapr pub/sub component that encapsulates a specific message broker product.</span></span> <span data-ttu-id="95889-149">На рисунке 7-2 показан стек сообщений ДАПР Pub/подразделов.</span><span class="sxs-lookup"><span data-stu-id="95889-149">Figure 7-2 shows the Dapr pub/sub messaging stack.</span></span>

![Стек публикации и поддерева](./media/publish-subscribe/pub-sub-buildingblock.png)

<span data-ttu-id="95889-151">**Рис. 7-2**.</span><span class="sxs-lookup"><span data-stu-id="95889-151">**Figure 7-2**.</span></span> <span data-ttu-id="95889-152">Стек Pub/ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-152">The Dapr pub/sub stack.</span></span>

<span data-ttu-id="95889-153">Стандартный блок ДАПР Publish & Subscribe может вызываться множеством способов.</span><span class="sxs-lookup"><span data-stu-id="95889-153">The Dapr publish & subscribe building block can be invoked in many ways.</span></span>

<span data-ttu-id="95889-154">На самом низком уровне любая платформа программирования может вызывать Стандартный блок по протоколу HTTP или gRPC с помощью **собственного API ДАПР**.</span><span class="sxs-lookup"><span data-stu-id="95889-154">At the lowest level, any programming platform can invoke the building block over HTTP or gRPC using the **Dapr native API**.</span></span> <span data-ttu-id="95889-155">Чтобы опубликовать сообщение, необходимо выполнить следующий вызов API:</span><span class="sxs-lookup"><span data-stu-id="95889-155">To publish a message, you make the following API call:</span></span>

``` http
http://localhost:<dapr-port>/v1.0/publish/<pub-sub-name>/<topic>
```

<span data-ttu-id="95889-156">Существует несколько ДАПР сегментов URL-адресов в приведенном выше вызове:</span><span class="sxs-lookup"><span data-stu-id="95889-156">There are several Dapr specific URL segments in the above call:</span></span>

- <span data-ttu-id="95889-157">`<dapr-port>` предоставляет номер порта, на котором прослушивается расширения ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-157">`<dapr-port>` provides the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="95889-158">`<pub-sub-name>` предоставляет имя выбранного компонента ДАПР Pub/подтипа.</span><span class="sxs-lookup"><span data-stu-id="95889-158">`<pub-sub-name>` provides the name of the selected Dapr pub/sub component.</span></span>
- <span data-ttu-id="95889-159">`<topic>` предоставляет имя раздела, в который публикуется сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-159">`<topic>` provides the name of the topic to which the message is published.</span></span>

<span data-ttu-id="95889-160">С помощью *инструмента командной строки* для публикации сообщения можно попробовать выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="95889-160">Using the *curl* command-line tool to publish a message, you can try it out:</span></span>

``` curl
curl -X POST http://localhost:3500/v1.0/publish/pubsub/newOrder \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1234", "productId": "5678", "amount": 2 }'
```

<span data-ttu-id="95889-161">Вы получаете сообщения, подписавшись на раздел.</span><span class="sxs-lookup"><span data-stu-id="95889-161">You receive messages by subscribing to a topic.</span></span> <span data-ttu-id="95889-162">При запуске среда выполнения ДАПР будет вызывать приложение на известной конечной точке для обнаружения и создания необходимых подписок:</span><span class="sxs-lookup"><span data-stu-id="95889-162">At startup, the Dapr runtime will call the application on a well-known endpoint to identify and create the required subscriptions:</span></span>

``` http
http://localhost:<appPort>/dapr/subscribe
```

- <span data-ttu-id="95889-163">`<appPort>` информирует ДАПР расширения порта, на котором приложение прослушивается.</span><span class="sxs-lookup"><span data-stu-id="95889-163">`<appPort>` informs the Dapr sidecar of the port upon which the application is listening.</span></span>

<span data-ttu-id="95889-164">Эту конечную точку можно реализовать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="95889-164">You can implement this endpoint yourself.</span></span> <span data-ttu-id="95889-165">Но ДАПР предоставляет более интуитивно понятные способы реализации.</span><span class="sxs-lookup"><span data-stu-id="95889-165">But Dapr provides more intuitive ways of implementing it.</span></span> <span data-ttu-id="95889-166">Эта функция будет устранена далее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="95889-166">We'll address this functionality later in this chapter.</span></span>

<span data-ttu-id="95889-167">Ответ вызова содержит список разделов, на которые будут подписываться приложения.</span><span class="sxs-lookup"><span data-stu-id="95889-167">The response from the call contains a list of topics to which the applications will subscribe.</span></span> <span data-ttu-id="95889-168">Каждый из них включает конечную точку, которая вызывается, когда раздел получает сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-168">Each includes an endpoint to call when the topic receives a message.</span></span> <span data-ttu-id="95889-169">Вот пример ответа:</span><span class="sxs-lookup"><span data-stu-id="95889-169">Here's an example of a response:</span></span>

```json
[
  {
    "pubsubname": "pubsub",
    "topic": "newOrder",
    "route": "/orders"
  },
  {
    "pubsubname": "pubsub",
    "topic": "newProduct",
    "route": "/productCatalog/products"
  }
]
```

<span data-ttu-id="95889-170">В ответе JSON можно увидеть, что приложение хочет подписываться на разделы `newOrder` и `newProduct` .</span><span class="sxs-lookup"><span data-stu-id="95889-170">In the JSON response, you can see the application wants to subscribe to topics `newOrder` and `newProduct`.</span></span> <span data-ttu-id="95889-171">Он регистрирует конечные точки `/orders` и `/productCatalog/products` для каждого, соответственно.</span><span class="sxs-lookup"><span data-stu-id="95889-171">It registers the endpoints `/orders` and `/productCatalog/products` for each, respectively.</span></span> <span data-ttu-id="95889-172">Для обеих подписок приложение привязывается к компоненту ДАПР с именем `pubsub` .</span><span class="sxs-lookup"><span data-stu-id="95889-172">For both subscriptions, the application is binding to the Dapr component named `pubsub`.</span></span>

<span data-ttu-id="95889-173">На рис. 7-3 представлен поток примера.</span><span class="sxs-lookup"><span data-stu-id="95889-173">Figure 7-3 presents the flow of the example.</span></span>

![Пример потока публикации и подсистемы с помощью ДАПР](media/publish-subscribe/pub-sub-flow.png)

<span data-ttu-id="95889-175">**Рис. 7-3**.</span><span class="sxs-lookup"><span data-stu-id="95889-175">**Figure 7-3**.</span></span> <span data-ttu-id="95889-176">поток Pub/с ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-176">pub/sub flow with Dapr.</span></span>

<span data-ttu-id="95889-177">На предыдущем рисунке обратите внимание на последовательность:</span><span class="sxs-lookup"><span data-stu-id="95889-177">From the previous figure, note the flow:</span></span>

1. <span data-ttu-id="95889-178">ДАПР расширения для службы B вызывает `/dapr/subscribe` конечную точку из службы b (потребителя).</span><span class="sxs-lookup"><span data-stu-id="95889-178">The Dapr sidecar for Service B calls the `/dapr/subscribe` endpoint from Service B (the consumer).</span></span> <span data-ttu-id="95889-179">Служба реагирует на подписки, которые необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="95889-179">The service responds with the subscriptions it wants to create.</span></span>
1. <span data-ttu-id="95889-180">ДАПР расширения для службы B создает запрошенные подписки на брокере сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-180">The Dapr sidecar for Service B creates the requested subscriptions on the message broker.</span></span>
1. <span data-ttu-id="95889-181">Служба а публикует сообщение в `/v1.0/publish/<pub-sub-name>/<topic>` конечной точке в службе ДАПР A расширения.</span><span class="sxs-lookup"><span data-stu-id="95889-181">Service A publishes a message at the `/v1.0/publish/<pub-sub-name>/<topic>` endpoint on the Dapr Service A sidecar.</span></span>
1. <span data-ttu-id="95889-182">Служба A расширения публикует сообщение в брокер сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-182">The Service A sidecar publishes the message to the message broker.</span></span>
1. <span data-ttu-id="95889-183">Брокер сообщений отправляет копию сообщения в службу B расширения.</span><span class="sxs-lookup"><span data-stu-id="95889-183">The message broker sends a copy of the message to the Service B sidecar.</span></span>
1. <span data-ttu-id="95889-184">Служба B расширения вызывает конечную точку, соответствующую подписке (в данном случае `/orders` ), в службе б. Служба реагирует на код состояния HTTP, `200 OK` поэтому расширения будет рассматривать сообщение как обработанное успешно.</span><span class="sxs-lookup"><span data-stu-id="95889-184">The Service B sidecar calls the endpoint corresponding to the subscription (in this case `/orders`) on Service B. The service responds with an HTTP status-code `200 OK` so the sidecar will consider the message as being handled successfully.</span></span>

<span data-ttu-id="95889-185">В этом примере сообщение обработано успешно.</span><span class="sxs-lookup"><span data-stu-id="95889-185">In the example, the message is handled successfully.</span></span> <span data-ttu-id="95889-186">Но если что-то пошло не так, когда служба б обрабатывает запрос, она может использовать ответ, чтобы указать, что должно происходить с сообщением.</span><span class="sxs-lookup"><span data-stu-id="95889-186">But if something goes wrong while Service B is handling the request, it can use the response to specify what needs to happen with the message.</span></span> <span data-ttu-id="95889-187">Когда он возвращает код состояния HTTP `404` , регистрируется ошибка и сообщение удаляется.</span><span class="sxs-lookup"><span data-stu-id="95889-187">When it returns an HTTP status-code `404`, an error is logged and the message is dropped.</span></span> <span data-ttu-id="95889-188">При наличии любого другого кода состояния `200` `404` , который больше или, предупреждение регистрируется и сообщение повторяется.</span><span class="sxs-lookup"><span data-stu-id="95889-188">With any other status-code than `200` or `404`, a warning is logged and the message is retried.</span></span> <span data-ttu-id="95889-189">Кроме того, служба б может явно указать, что должно происходить с сообщением, включив полезные данные JSON в текст ответа:</span><span class="sxs-lookup"><span data-stu-id="95889-189">Alternatively, Service B can explicitly specify what needs to happen with the message by including a JSON payload in the body of the response:</span></span>

```json
{
  "status": "<status>"
}
```

<span data-ttu-id="95889-190">Доступные значения приведены в следующей таблице `status` .</span><span class="sxs-lookup"><span data-stu-id="95889-190">The following table shows the available `status` values:</span></span>

| <span data-ttu-id="95889-191">Состояние</span><span class="sxs-lookup"><span data-stu-id="95889-191">Status</span></span>           | <span data-ttu-id="95889-192">Действие</span><span class="sxs-lookup"><span data-stu-id="95889-192">Action</span></span>                                                       |
| ---------------- | ------------------------------------------------------------ |
| <span data-ttu-id="95889-193">УСПЕШНОЕ ЗАВЕРШЕНИЕ</span><span class="sxs-lookup"><span data-stu-id="95889-193">SUCCESS</span></span>          | <span data-ttu-id="95889-194">Сообщение считается обработанным успешно и удалено.</span><span class="sxs-lookup"><span data-stu-id="95889-194">The message is considered as processed successfully and dropped.</span></span> |
| <span data-ttu-id="95889-195">ПОВТОРИТЬ</span><span class="sxs-lookup"><span data-stu-id="95889-195">RETRY</span></span>            | <span data-ttu-id="95889-196">Сообщение повторяется.</span><span class="sxs-lookup"><span data-stu-id="95889-196">The message is retried.</span></span>                                      |
| <span data-ttu-id="95889-197">DROP</span><span class="sxs-lookup"><span data-stu-id="95889-197">DROP</span></span>             | <span data-ttu-id="95889-198">В журнал заносится предупреждение и сообщение удаляется.</span><span class="sxs-lookup"><span data-stu-id="95889-198">A warning is logged and the message is dropped.</span></span>              |
| <span data-ttu-id="95889-199">Любое другое состояние</span><span class="sxs-lookup"><span data-stu-id="95889-199">Any other status</span></span> | <span data-ttu-id="95889-200">Сообщение повторяется.</span><span class="sxs-lookup"><span data-stu-id="95889-200">The message is retried.</span></span>                                      |

### <a name="competing-consumers"></a><span data-ttu-id="95889-201">Конкурирующие потребители</span><span class="sxs-lookup"><span data-stu-id="95889-201">Competing consumers</span></span>

<span data-ttu-id="95889-202">При масштабировании приложения, которое подписывается на раздел, необходимо работать с конкурирующими потребителями.</span><span class="sxs-lookup"><span data-stu-id="95889-202">When scaling out an application that subscribes to a topic, you have to deal with competing consumers.</span></span> <span data-ttu-id="95889-203">Только один экземпляр приложения должен работать с сообщением, отправленным в раздел.</span><span class="sxs-lookup"><span data-stu-id="95889-203">Only one application instance should handle a message sent to the topic.</span></span> <span data-ttu-id="95889-204">К счастью, ДАПР обрабатывает эту проблему.</span><span class="sxs-lookup"><span data-stu-id="95889-204">Luckily, Dapr handles that problem.</span></span> <span data-ttu-id="95889-205">Когда несколько экземпляров службы с одним и тем же идентификатором приложения подписываются на раздел, ДАПР доставляет каждое сообщение только одному из них.</span><span class="sxs-lookup"><span data-stu-id="95889-205">When multiple instances of a service with the same application-id subscribe to a topic, Dapr delivers each message to only one of them.</span></span>

### <a name="sdks"></a><span data-ttu-id="95889-206">Пакеты SDK</span><span class="sxs-lookup"><span data-stu-id="95889-206">SDKs</span></span>

<span data-ttu-id="95889-207">Выполнение HTTP-вызовов к собственным ДАПР API-интерфейсам занимает много времени и является абстрактным.</span><span class="sxs-lookup"><span data-stu-id="95889-207">Making HTTP calls to the native Dapr APIs is time-consuming and abstract.</span></span> <span data-ttu-id="95889-208">Вызовы разрабатываются на уровне HTTP, и вам нужно будет решить такие проблемы, как сериализация и коды ответов HTTP.</span><span class="sxs-lookup"><span data-stu-id="95889-208">Your calls are crafted at the HTTP level, and you'll need to handle plumbing concerns such as serialization and HTTP response codes.</span></span> <span data-ttu-id="95889-209">К счастью, существует более интуитивно понятный способ.</span><span class="sxs-lookup"><span data-stu-id="95889-209">Fortunately, there's a more intuitive way.</span></span> <span data-ttu-id="95889-210">ДАПР предоставляет несколько пакетов SDK для конкретных языков для популярных платформ разработки.</span><span class="sxs-lookup"><span data-stu-id="95889-210">Dapr provides several language-specific SDKs for popular development platforms.</span></span> <span data-ttu-id="95889-211">На момент написания этой статьи доступны Node.js, Python, .NET, Java и JavaScript.</span><span class="sxs-lookup"><span data-stu-id="95889-211">At the time of this writing, Go, Node.js, Python, .NET, Java, and JavaScript are available.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="95889-212">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="95889-212">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="95889-213">Для разработчиков .NET [пакет SDK для ДАПР .NET](https://www.nuget.org/packages/Dapr.Client) предоставляет более эффективный способ работы с ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-213">For .NET Developers, the [Dapr .NET SDK](https://www.nuget.org/packages/Dapr.Client) provides a more productive way of working with Dapr.</span></span> <span data-ttu-id="95889-214">Пакет SDK предоставляет `DaprClient` класс, с помощью которого можно напрямую вызывать функции ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-214">The SDK exposes a `DaprClient` class through which you can directly invoke Dapr functionality.</span></span> <span data-ttu-id="95889-215">Он интуитивно понятен и удобен в использовании.</span><span class="sxs-lookup"><span data-stu-id="95889-215">It's intuitive and easy to use.</span></span>

<span data-ttu-id="95889-216">Чтобы опубликовать сообщение, объект `DaprClient` предоставляет `PublishEventAsync` метод.</span><span class="sxs-lookup"><span data-stu-id="95889-216">To publish a message, the `DaprClient` exposes a `PublishEventAsync` method.</span></span>

```csharp
var data = new OrderData
{
  orderId = "123456",
  productId = "67890",
  amount = 2
};

var daprClient = new DaprClientBuilder().Build();

await daprClient.PublishEventAsync<OrderData>("pubsub", "newOrder", data);
```

- <span data-ttu-id="95889-217">Первым аргументом `pubsub` является имя компонента ДАПР, предоставляющего реализацию брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-217">The first argument `pubsub` is the name of the Dapr component that provides the message broker implementation.</span></span> <span data-ttu-id="95889-218">Далее в этой главе мы будем обращаться к компонентам.</span><span class="sxs-lookup"><span data-stu-id="95889-218">We'll address components later in this chapter.</span></span>
- <span data-ttu-id="95889-219">Второй аргумент `neworder` предоставляет имя раздела, в который отправляется сообщение.</span><span class="sxs-lookup"><span data-stu-id="95889-219">The second argument `neworder` provides the name of the topic to send the message to.</span></span>
- <span data-ttu-id="95889-220">Третьим аргументом является полезная нагрузка сообщения.</span><span class="sxs-lookup"><span data-stu-id="95889-220">The third argument is the payload of the message.</span></span>
- <span data-ttu-id="95889-221">Тип .NET сообщения можно указать с помощью параметра универсального типа метода.</span><span class="sxs-lookup"><span data-stu-id="95889-221">You can specify the .NET type of the message using the generic type parameter of the method.</span></span>

<span data-ttu-id="95889-222">Чтобы получить сообщения, необходимо привязать конечную точку к подписке для зарегистрированного раздела.</span><span class="sxs-lookup"><span data-stu-id="95889-222">To receive messages, you bind an endpoint to a subscription for a registered topic.</span></span> <span data-ttu-id="95889-223">Библиотека AspNetCore для ДАПР делает это тривиальным.</span><span class="sxs-lookup"><span data-stu-id="95889-223">The AspNetCore library for Dapr makes this trivial.</span></span> <span data-ttu-id="95889-224">Предположим, например, что у вас есть метод действия WebAPI ASP.NET, имеющий право `CreateOrder` :</span><span class="sxs-lookup"><span data-stu-id="95889-224">Assume, for example, that you have an existing ASP.NET WebAPI action method entitled `CreateOrder`:</span></span>

```csharp
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

 > <span data-ttu-id="95889-225">Чтобы использовать интеграцию с ДАПР ASP.NET Core, необходимо добавить ссылку на пакет NuGet [ДАПР. AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) в проекте.</span><span class="sxs-lookup"><span data-stu-id="95889-225">You must add a reference to the [Dapr.AspNetCore](https://www.nuget.org/packages/Dapr.AspNetCore) NuGet package in your project to consume the Dapr ASP.NET Core integration.</span></span>

<span data-ttu-id="95889-226">Чтобы привязать этот метод действия к разделу, необходимо снабдить его `Topic` атрибутом:</span><span class="sxs-lookup"><span data-stu-id="95889-226">To bind this action method to a topic, you decorate it with the `Topic` attribute:</span></span>

```csharp
[Topic("pubsub", "newOrder")]
[HttpPost("/orders")]
public async Task<ActionResult> CreateOrder(Order order)
```

<span data-ttu-id="95889-227">Вы указываете два ключевых элемента с помощью этого атрибута:</span><span class="sxs-lookup"><span data-stu-id="95889-227">You specify two key elements with this attribute:</span></span>

- <span data-ttu-id="95889-228">Целевой компонент ДАПР Pub/подкаталог (в данном случае `pubsub` ).</span><span class="sxs-lookup"><span data-stu-id="95889-228">The Dapr pub/sub component to target (in this case `pubsub`).</span></span>
- <span data-ttu-id="95889-229">Раздел, на который подписывается (в данном случае `newOrder` ).</span><span class="sxs-lookup"><span data-stu-id="95889-229">The topic to subscribe to (in this case `newOrder`).</span></span>

<span data-ttu-id="95889-230">Затем ДАПР вызывает этот метод действия, когда он получает сообщения для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="95889-230">Dapr then invokes that action method as it receives messages for that topic.</span></span>

<span data-ttu-id="95889-231">Также необходимо включить ASP.NET Core для использования ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-231">You'll also need to enable ASP.NET Core to use Dapr.</span></span> <span data-ttu-id="95889-232">Пакет SDK для ДАПР .NET предоставляет несколько методов расширения, которые могут быть вызваны в `Startup` классе.</span><span class="sxs-lookup"><span data-stu-id="95889-232">The Dapr .NET SDK provides several extension methods that can be invoked in the `Startup` class.</span></span>

<span data-ttu-id="95889-233">В `ConfigureServices` методе необходимо добавить следующий метод расширения:</span><span class="sxs-lookup"><span data-stu-id="95889-233">In the `ConfigureServices` method, you must add the following extension method:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // ...
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="95889-234">Добавление `AddDapr` метода расширения в `AddControllers` метод Extension регистрирует необходимые службы для интеграции ДАПР в конвейер MVC.</span><span class="sxs-lookup"><span data-stu-id="95889-234">Appending the `AddDapr` extension-method to the `AddControllers` extension-method registers the necessary services to integrate Dapr into the MVC pipeline.</span></span> <span data-ttu-id="95889-235">Он также регистрирует `DaprClient` экземпляр в контейнере внедрения зависимостей, который затем может быть внедрен в любую службу.</span><span class="sxs-lookup"><span data-stu-id="95889-235">It also registers a `DaprClient` instance into the dependency injection container, which then can be injected anywhere into your service.</span></span>

<span data-ttu-id="95889-236">В `Configure` методе необходимо добавить следующие компоненты по промежуточного слоя для включения ДАПР:</span><span class="sxs-lookup"><span data-stu-id="95889-236">In the `Configure` method, you must add the following middleware components to enable Dapr:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // ...
    app.UseCloudEvents();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapSubscribeHandler();
        // ...
    });
}
```

<span data-ttu-id="95889-237">Вызов добавляет по `UseCloudEvents` промежуточного слоя **клаудевентс** в конвейер по промежуточного слоя ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="95889-237">The call to `UseCloudEvents` adds **CloudEvents** middleware into to the ASP.NET Core middleware pipeline.</span></span> <span data-ttu-id="95889-238">Это по промежуточного слоя будет распаковывать запросы, использующие структурированный формат Клаудевентс, поэтому метод получения может считывать полезные данные события напрямую.</span><span class="sxs-lookup"><span data-stu-id="95889-238">This middleware will unwrap requests that use the CloudEvents structured format, so the receiving method can read the event payload directly.</span></span>

> <span data-ttu-id="95889-239">[Клаудевентс](https://cloudevents.io/) — это стандартизированный формат обмена сообщениями, предоставляющий общий способ описания сведений о событиях на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="95889-239">[CloudEvents](https://cloudevents.io/) is a standardized messaging format, providing a common way to describe event information across platforms.</span></span> <span data-ttu-id="95889-240">ДАПР охватывает Клаудевентс.</span><span class="sxs-lookup"><span data-stu-id="95889-240">Dapr embraces CloudEvents.</span></span> <span data-ttu-id="95889-241">Дополнительные сведения о Клаудевентс см. в [спецификации клаудевентс](https://github.com/cloudevents/spec/tree/v1.0).</span><span class="sxs-lookup"><span data-stu-id="95889-241">For more information about CloudEvents, see the [cloudevents specification](https://github.com/cloudevents/spec/tree/v1.0).</span></span>

<span data-ttu-id="95889-242">При вызове `MapSubscribeHandler` в конфигурации маршрутизации конечной точки в приложение будет добавлена конечная точка подписки ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-242">The call to `MapSubscribeHandler` in the endpoint routing configuration will add a Dapr subscribe endpoint to the application.</span></span> <span data-ttu-id="95889-243">Эта конечная точка будет отвечать на запросы `/dapr/subscribe` .</span><span class="sxs-lookup"><span data-stu-id="95889-243">This endpoint will respond to requests on `/dapr/subscribe`.</span></span> <span data-ttu-id="95889-244">При вызове этой конечной точки он автоматически находит все методы действий WebAPI, снабженные `Topic` атрибутом, и указывает ДАПР создать для них подписки.</span><span class="sxs-lookup"><span data-stu-id="95889-244">When this endpoint is called, it will automatically find all WebAPI action methods decorated with the `Topic` attribute and instruct Dapr to create subscriptions for them.</span></span>

## <a name="pubsub-components"></a><span data-ttu-id="95889-245">Компоненты публикации и подраздела</span><span class="sxs-lookup"><span data-stu-id="95889-245">Pub/sub components</span></span>

<span data-ttu-id="95889-246">[Компоненты Pub/](https://github.com/dapr/components-contrib/tree/master/pubsub) поддапр обработают фактический транспорт сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-246">Dapr [pub/sub components](https://github.com/dapr/components-contrib/tree/master/pubsub) handle the actual transport of the messages.</span></span> <span data-ttu-id="95889-247">Доступны несколько.</span><span class="sxs-lookup"><span data-stu-id="95889-247">Several are available.</span></span> <span data-ttu-id="95889-248">Каждый из них инкапсулирует конкретный продукт брокера сообщений для реализации функции Pub/подтипа.</span><span class="sxs-lookup"><span data-stu-id="95889-248">Each encapsulates a specific message broker product to implement the pub/sub functionality.</span></span> <span data-ttu-id="95889-249">На момент написания статьи были доступны следующие компоненты публикации и подкаталогов:</span><span class="sxs-lookup"><span data-stu-id="95889-249">At the time of writing, the following pub/sub components were available:</span></span>

- <span data-ttu-id="95889-250">Apache Kafka</span><span class="sxs-lookup"><span data-stu-id="95889-250">Apache Kafka</span></span>
- <span data-ttu-id="95889-251">Центры событий Azure</span><span class="sxs-lookup"><span data-stu-id="95889-251">Azure Event Hubs</span></span>
- <span data-ttu-id="95889-252">Azure Service Bus</span><span class="sxs-lookup"><span data-stu-id="95889-252">Azure Service Bus</span></span>
- <span data-ttu-id="95889-253">AWS SNS/СКС</span><span class="sxs-lookup"><span data-stu-id="95889-253">AWS SNS/SQS</span></span>
- <span data-ttu-id="95889-254">ОБЕСПЕЧИТЬ Pub/Re-in</span><span class="sxs-lookup"><span data-stu-id="95889-254">GCP Pub/Sub</span></span>
- <span data-ttu-id="95889-255">хазелкаст</span><span class="sxs-lookup"><span data-stu-id="95889-255">Hazelcast</span></span>
- <span data-ttu-id="95889-256">MQTT</span><span class="sxs-lookup"><span data-stu-id="95889-256">MQTT</span></span>
- <span data-ttu-id="95889-257">NATS</span><span class="sxs-lookup"><span data-stu-id="95889-257">NATS</span></span>
- <span data-ttu-id="95889-258">пулсар</span><span class="sxs-lookup"><span data-stu-id="95889-258">Pulsar</span></span>
- <span data-ttu-id="95889-259">RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="95889-259">RabbitMQ</span></span>
- <span data-ttu-id="95889-260">Потоки Redis</span><span class="sxs-lookup"><span data-stu-id="95889-260">Redis Streams</span></span>

> [!NOTE]
> <span data-ttu-id="95889-261">В облачном стеке Azure доступны обе функции: обмен сообщениями (служебная шина Azure) и потоковая передача событий (концентратор событий Azure).</span><span class="sxs-lookup"><span data-stu-id="95889-261">The Azure cloud stack has both messaging functionality (Azure Service Bus) and event streaming (Azure Event Hub) availability.</span></span>

<span data-ttu-id="95889-262">Эти компоненты создаются сообществом в [репозитории Component-от участников сообщества на сайте GitHub](https://github.com/dapr/components-contrib/tree/master/pubsub).</span><span class="sxs-lookup"><span data-stu-id="95889-262">These components are created by the community in a [component-contrib repository on GitHub](https://github.com/dapr/components-contrib/tree/master/pubsub).</span></span> <span data-ttu-id="95889-263">Вы можете написать собственный компонент ДАПР для брокера сообщений, который еще не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="95889-263">You're encouraged to write your own Dapr component for a message broker that isn't yet supported.</span></span>

### <a name="configure-pubsub-components"></a><span data-ttu-id="95889-264">Настройка компонентов публикации и подразделов</span><span class="sxs-lookup"><span data-stu-id="95889-264">Configure pub/sub components</span></span>

<span data-ttu-id="95889-265">С помощью файла конфигурации ДАПР можно указать компоненты публикации и подсистемы, которые будут использоваться.</span><span class="sxs-lookup"><span data-stu-id="95889-265">Using a Dapr configuration file, you can specify the pub/sub component(s) to use.</span></span> <span data-ttu-id="95889-266">Эта конфигурация содержит несколько полей.</span><span class="sxs-lookup"><span data-stu-id="95889-266">This configuration contains several fields.</span></span> <span data-ttu-id="95889-267">В этом `name` поле указывается компонент Pub/подсистемы, который вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="95889-267">The `name` field specifies the pub/sub component that you want to use.</span></span> <span data-ttu-id="95889-268">При отправке или получении сообщения необходимо указать это имя (как было показано ранее в `PublishEventAsync` сигнатуре метода).</span><span class="sxs-lookup"><span data-stu-id="95889-268">When sending or receiving a message, you need to specify this name (as you saw earlier in the `PublishEventAsync` method signature).</span></span>

<span data-ttu-id="95889-269">Ниже приведен пример файла конфигурации ДАПР для настройки компонента брокера сообщений RabbitMQ:</span><span class="sxs-lookup"><span data-stu-id="95889-269">Below you see an example of a Dapr configuration file for configuring a RabbitMQ message broker component:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub-rq
spec:
  type: pubsub.rabbitmq
  version: v1
  metadata:
  - name: host
    value: "amqp://localhost:5672"
  - name: durable
    value: true
```

<span data-ttu-id="95889-270">В этом примере можно увидеть, что в блоке можно указать любую конфигурацию брокера сообщений `metadata` .</span><span class="sxs-lookup"><span data-stu-id="95889-270">In this example, you can see that you can specify any message broker-specific configuration in the `metadata` block.</span></span> <span data-ttu-id="95889-271">В этом случае RabbitMQ настроен для создания устойчивых очередей.</span><span class="sxs-lookup"><span data-stu-id="95889-271">In this case, RabbitMQ is configured to create durable queues.</span></span> <span data-ttu-id="95889-272">Но у компонента RabbitMQ больше параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="95889-272">But the RabbitMQ component has more configuration options.</span></span> <span data-ttu-id="95889-273">Каждая конфигурация компонентов будет иметь собственный набор возможных полей.</span><span class="sxs-lookup"><span data-stu-id="95889-273">Each of the components' configuration will have its own set of possible fields.</span></span> <span data-ttu-id="95889-274">Можно прочитать, какие поля доступны в документации по каждому [компоненту Pub/подтип](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/).</span><span class="sxs-lookup"><span data-stu-id="95889-274">You can read which fields are available in the documentation of each [pub/sub component](https://docs.dapr.io/operations/components/setup-pubsub/supported-pubsub/).</span></span>

<span data-ttu-id="95889-275">Рядом с программным способом подписки на раздел кода ДАПР Pub/поддает также декларативный способ подписки на раздел.</span><span class="sxs-lookup"><span data-stu-id="95889-275">Next to the programmatic way of subscribing to a topic from code, Dapr pub/sub also provides a declarative way of subscribing to a topic.</span></span> <span data-ttu-id="95889-276">Этот подход удаляет зависимость ДАПР из кода приложения.</span><span class="sxs-lookup"><span data-stu-id="95889-276">This approach removes the Dapr dependency from the application code.</span></span> <span data-ttu-id="95889-277">Таким образом, оно также позволяет существующему приложению подписываться на разделы без внесения изменений в код.</span><span class="sxs-lookup"><span data-stu-id="95889-277">Therefore, it also enables an existing application to subscribe to topics without any changes to the code.</span></span> <span data-ttu-id="95889-278">В следующем примере показан файл конфигурации ДАПР для настройки подписки.</span><span class="sxs-lookup"><span data-stu-id="95889-278">The following example shows a Dapr configuration file for configuring a subscription:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Subscription
metadata:
  name: newOrder-subscription
spec:
  pubsubname: pubsub
  topic: newOrder
  route: /orders
scopes:
- ServiceB
- ServiceC
```

<span data-ttu-id="95889-279">Необходимо указать несколько элементов с каждой подпиской:</span><span class="sxs-lookup"><span data-stu-id="95889-279">You have to specify several elements with every subscription:</span></span>

- <span data-ttu-id="95889-280">Имя подкомпонента ДАПР Pub/подтипа, который вы хотите использовать (в данном случае `pubsub` ).</span><span class="sxs-lookup"><span data-stu-id="95889-280">The name of the Dapr pub/sub component you want to use (in this case `pubsub`).</span></span>
- <span data-ttu-id="95889-281">Имя раздела для подписки (в данном случае `newOrder` ).</span><span class="sxs-lookup"><span data-stu-id="95889-281">The name of the topic to subscribe to (in this case `newOrder`).</span></span>
- <span data-ttu-id="95889-282">Операция API, которая должна вызываться для этого раздела (в данном случае `/orders` ).</span><span class="sxs-lookup"><span data-stu-id="95889-282">The API operation that needs to be called for this topic (in this case `/orders`).</span></span>
- <span data-ttu-id="95889-283">В [области](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) можно указать, какие службы могут публиковать и подписываться на раздел.</span><span class="sxs-lookup"><span data-stu-id="95889-283">The [scope](https://docs.dapr.io/developing-applications/building-blocks/pubsub/pubsub-scopes/) can specify which services can publish and subscribe to a topic.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="95889-284">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="95889-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="95889-285">Сопутствующее приложение [ешопондапр](https://github.com/dotnet-architecture/eShopOnDapr) предоставляет комплексную эталонную архитектуру для создания приложения микрослужб, реализующего ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-285">The accompanying [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) app provides an end-to-end reference architecture for constructing a microservices application implementing Dapr.</span></span> <span data-ttu-id="95889-286">Ешопондапр — это эволюция широко популярного [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) приложения, созданного несколько лет назад.</span><span class="sxs-lookup"><span data-stu-id="95889-286">eShopOnDapr is an evolution of the widely popular [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) app, created several years ago.</span></span> <span data-ttu-id="95889-287">В обеих версиях используется шаблон публикации и поддела для обмена [событиями интеграции](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) между микрослужбами.</span><span class="sxs-lookup"><span data-stu-id="95889-287">Both versions use the pub/sub pattern for communicating [integration events](https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/#integration-events) across microservices.</span></span> <span data-ttu-id="95889-288">К событиям интеграции относятся:</span><span class="sxs-lookup"><span data-stu-id="95889-288">Integration events include:</span></span>

- <span data-ttu-id="95889-289">Когда пользователь извлекает корзину покупок.</span><span class="sxs-lookup"><span data-stu-id="95889-289">When a user checks-out a shopping basket.</span></span>
- <span data-ttu-id="95889-290">При успешном платеже заказа.</span><span class="sxs-lookup"><span data-stu-id="95889-290">When a payment for an order has succeeded.</span></span>
- <span data-ttu-id="95889-291">По истечении периода отсрочки покупки.</span><span class="sxs-lookup"><span data-stu-id="95889-291">When the grace-period of a purchase has expired.</span></span>

<span data-ttu-id="95889-292">События в eShopOnContainers основаны на следующем `IEventBus` интерфейсе:</span><span class="sxs-lookup"><span data-stu-id="95889-292">Eventing in eShopOnContainers is based on the following `IEventBus` interface:</span></span>

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent integrationEvent);

    void Subscribe<T, THandler>()
        where TEvent : IntegrationEvent
        where THandler : IIntegrationEventHandler<T>;
}
```

<span data-ttu-id="95889-293">Конкретные реализации этого интерфейса существуют в eShopOnContainers как для RabbitMQ, так и для служебной шины Azure.</span><span class="sxs-lookup"><span data-stu-id="95889-293">Concrete implementations of this interface exist in eShopOnContainers for both RabbitMQ and Azure Service Bus.</span></span> <span data-ttu-id="95889-294">Каждая реализация включает в себя большой объем пользовательского коммуникационного кода, который был сложным для понимания и сложно поддерживать.</span><span class="sxs-lookup"><span data-stu-id="95889-294">Each implementation included a great deal of custom plumbing code that was complex to understand and difficult to maintain.</span></span>

<span data-ttu-id="95889-295">Более новая Ешопондапр значительно упрощает поведение публикации и подменю с помощью ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-295">The newer eShopOnDapr significantly simplifies pub/sub behavior by using Dapr.</span></span> <span data-ttu-id="95889-296">Например, `IEventBus` интерфейс был уменьшен до одного метода:</span><span class="sxs-lookup"><span data-stu-id="95889-296">For example, the `IEventBus` interface was reduced to a single method:</span></span>

```csharp
public interface IEventBus
{
    Task PublishAsync(IntegrationEvent integrationEvent);
}
```

### <a name="publish-events"></a><span data-ttu-id="95889-297">Публикация событий</span><span class="sxs-lookup"><span data-stu-id="95889-297">Publish events</span></span>

<span data-ttu-id="95889-298">В обновленном Ешопондапр одна `DaprEventBus` реализация может поддерживать любой брокер сообщений, поддерживаемый ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-298">In the updated eShopOnDapr, a single `DaprEventBus` implementation can support any Dapr-supported message broker.</span></span> <span data-ttu-id="95889-299">В следующем блоке кода показан упрощенный метод публикации.</span><span class="sxs-lookup"><span data-stu-id="95889-299">The following code block shows the simplified Publish method.</span></span> <span data-ttu-id="95889-300">Обратите внимание, что `PublishAsync` метод использует клиент ДАПР для публикации события:</span><span class="sxs-lookup"><span data-stu-id="95889-300">Note how the `PublishAsync` method uses the Dapr client to publish an event:</span></span>

```csharp
public class DaprEventBus : IEventBus
{
    private const string PubSubName = "pubsub";

    private readonly DaprClient _daprClient;
    private readonly ILogger<DaprEventBus> _logger;

    public DaprEventBus(DaprClient daprClient, ILogger<DaprEventBus> logger)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task PublishAsync(IntegrationEvent integrationEvent)
    {
        var topicName = integrationEvent.GetType().Name;

        // Dapr uses System.Text.Json which does not support serialization of a
        // polymorphic type hierarchy by default. Using object as the type
        // parameter causes all properties to be serialized.
        await _daprClient.PublishEventAsync<object>(PubSubName, topicName, integrationEvent);
    }
}
```

<span data-ttu-id="95889-301">Как видно в фрагменте кода, имя раздела является производным от имени типа события.</span><span class="sxs-lookup"><span data-stu-id="95889-301">As you can see in the code snippet, the topic name is derived from event type's name.</span></span> <span data-ttu-id="95889-302">Так как все службы Ешоп используют `IEventBus` абстракцию, модернизация ДАПР *не требует изменений* в коде приложения магистрали.</span><span class="sxs-lookup"><span data-stu-id="95889-302">Because all eShop services use the `IEventBus` abstraction, retrofitting Dapr required *absolutely no change* to the mainline application code.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95889-303">Пакет SDK ДАПР использует `System.Text.Json` для сериализации и десериализации сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-303">The Dapr SDK uses `System.Text.Json` to serialize/deserialize messages.</span></span> <span data-ttu-id="95889-304">Однако `System.Text.Json` по умолчанию не Сериализует свойства производных классов.</span><span class="sxs-lookup"><span data-stu-id="95889-304">However, `System.Text.Json` doesn't serialize properties of derived classes by default.</span></span> <span data-ttu-id="95889-305">В коде Ешоп событие иногда явно объявляется как `IntegrationEvent` , базовым классом для событий интеграции.</span><span class="sxs-lookup"><span data-stu-id="95889-305">In the eShop code, an event is sometimes explicitly declared as an `IntegrationEvent`, the base class for integration events.</span></span> <span data-ttu-id="95889-306">Это делается потому, что конкретный тип события определяется динамически во время выполнения на основе бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="95889-306">This is done because the concrete event type is determined dynamically at run time based on business logic.</span></span> <span data-ttu-id="95889-307">В результате событие сериализуется с использованием сведений о типе базового класса, а не производного класса.</span><span class="sxs-lookup"><span data-stu-id="95889-307">As a result, the event is serialized using the type information of the base class and not the derived class.</span></span> <span data-ttu-id="95889-308">Чтобы принудительно `System.Text.Json` сериализовать все свойства производного класса в этом случае, код использует в `object` качестве параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="95889-308">To force `System.Text.Json` to serialize all properties of the derived class in this case, the code uses `object` as the generic type parameter.</span></span> <span data-ttu-id="95889-309">Дополнительные сведения см. в [документации по .NET](../../standard/serialization/system-text-json-polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="95889-309">For more information, see the [.NET documentation](../../standard/serialization/system-text-json-polymorphism.md).</span></span>

<span data-ttu-id="95889-310">С помощью ДАПР код инфраструктуры **значительно упрощен**.</span><span class="sxs-lookup"><span data-stu-id="95889-310">With Dapr, the infrastructure code is **dramatically simplified**.</span></span> <span data-ttu-id="95889-311">Не нужно различать различные брокеры сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-311">It doesn't need to distinguish between the different message brokers.</span></span> <span data-ttu-id="95889-312">ДАПР предоставляет эту абстракцию.</span><span class="sxs-lookup"><span data-stu-id="95889-312">Dapr provides this abstraction for you.</span></span> <span data-ttu-id="95889-313">При необходимости можно легко поменять местами брокеры сообщений или настроить несколько компонентов брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-313">And if needed, you can easily swap out message brokers or configure multiple message broker components.</span></span>

### <a name="subscribe-to-events"></a><span data-ttu-id="95889-314">Оформление подписки на события</span><span class="sxs-lookup"><span data-stu-id="95889-314">Subscribe to events</span></span>

<span data-ttu-id="95889-315">Предыдущее приложение eShopOnContainers содержит *SubscriptionManagers* для поддержки реализации подписки для каждого брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-315">The earlier eShopOnContainers app contains *SubscriptionManagers* to handle the subscription implementation for each message broker.</span></span> <span data-ttu-id="95889-316">Каждый диспетчер содержит сложный код брокера сообщений для обработки событий подписки.</span><span class="sxs-lookup"><span data-stu-id="95889-316">Each manager contains complex message broker-specific code for handling subscription events.</span></span> <span data-ttu-id="95889-317">Для получения событий каждая служба должна явным образом зарегистрировать обработчик для каждого типа события.</span><span class="sxs-lookup"><span data-stu-id="95889-317">To receive events, each service has to explicitly register a handler for each event-type.</span></span>

<span data-ttu-id="95889-318">Ешопондапр упрощает работу с подписками на события с помощью библиотек ASP.NET Core ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-318">eShopOnDapr streamlines the plumbing for event subscriptions by using Dapr ASP.NET Core libraries.</span></span> <span data-ttu-id="95889-319">Каждое событие обрабатывается методом действия в контроллере.</span><span class="sxs-lookup"><span data-stu-id="95889-319">Each event is handled by an action method in the controller.</span></span> <span data-ttu-id="95889-320">Атрибут добавляет к `Topic` методу действия имя соответствующего раздела для подписки.</span><span class="sxs-lookup"><span data-stu-id="95889-320">A `Topic` attribute decorates the action method with the name of the corresponding topic to subscribe to.</span></span> <span data-ttu-id="95889-321">Ниже приведен фрагмент кода, взятый из `PaymentService` :</span><span class="sxs-lookup"><span data-stu-id="95889-321">Here's a code snippet taken from the `PaymentService`:</span></span>

```csharp
[Route("api/v1/[controller]")]
[ApiController]
public class IntegrationEventController : ControllerBase
{
    private const string DAPR_PUBSUB_NAME = "pubsub";

    private readonly IServiceProvider _serviceProvider;

    public IntegrationEventController(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    [HttpPost("OrderStatusChangedToValidated")]
    [Topic(DAPR_PUBSUB_NAME, "OrderStatusChangedToValidatedIntegrationEvent")]
    public async Task OrderStarted(OrderStatusChangedToValidatedIntegrationEvent integrationEvent)
    {
        var handler = _serviceProvider.GetRequiredService<OrderStatusChangedToValidatedIntegrationEventHandler>();
        await handler.Handle(integrationEvent);
    }
}
```

<span data-ttu-id="95889-322">В `Topic` атрибуте имя типа .NET для события используется в качестве имени раздела.</span><span class="sxs-lookup"><span data-stu-id="95889-322">In the `Topic` attribute, the name of the .NET type of the event is used as the topic name.</span></span> <span data-ttu-id="95889-323">Для обработки события вызывается обработчик событий, который уже существовал в более ранней базе кода eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="95889-323">For handling the event, an event handler that already existed in the earlier eShopOnContainers code base is invoked.</span></span> <span data-ttu-id="95889-324">В предыдущем примере сообщения, полученные из раздела, `OrderStatusChangedToValidatedIntegrationEvent` вызывают существующий `OrderStatusChangedToValidatedIntegrationEventHandler` обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="95889-324">In the previous example, messages received from the `OrderStatusChangedToValidatedIntegrationEvent` topic invoke the existing `OrderStatusChangedToValidatedIntegrationEventHandler` event-handler.</span></span> <span data-ttu-id="95889-325">Поскольку ДАПР реализует базовые коммуникации для подписок и брокеров сообщений, большой объем исходного кода стал устаревшим и был удален из базы кода.</span><span class="sxs-lookup"><span data-stu-id="95889-325">Because Dapr implements the underlying plumbing for subscriptions and message brokers, a large amount of original code became obsolete and was removed from the code-base.</span></span> <span data-ttu-id="95889-326">Большая часть этого кода была сложной для понимания и сложной в обслуживании.</span><span class="sxs-lookup"><span data-stu-id="95889-326">Much of this code was complex to understand and challenging to maintain.</span></span>

### <a name="use-pubsub-components"></a><span data-ttu-id="95889-327">Использование компонентов Pub/подразделов</span><span class="sxs-lookup"><span data-stu-id="95889-327">Use pub/sub components</span></span>

<span data-ttu-id="95889-328">В репозитории Ешопондапр `deployment` Папка содержит файлы для развертывания приложения с использованием различных режимов развертывания: `Docker Compose` и `Kubernetes` .</span><span class="sxs-lookup"><span data-stu-id="95889-328">Within the eShopOnDapr repository, a `deployment` folder contains files for deploying the application using different deployment modes: `Docker Compose` and `Kubernetes`.</span></span> <span data-ttu-id="95889-329">`dapr`Папка существует в каждой из этих папок, где хранится `components` Папка.</span><span class="sxs-lookup"><span data-stu-id="95889-329">A `dapr` folder exists within each of these folders that holds a `components` folder.</span></span> <span data-ttu-id="95889-330">Эта папка содержит файл, `eshop-pubsub.yaml` содержащий конфигурацию компонента ДАПР Pub/подпрограммы, которую приложение будет использовать для публикации и вложенности.</span><span class="sxs-lookup"><span data-stu-id="95889-330">This folder holds a file `eshop-pubsub.yaml` containing the configuration of the Dapr pub/sub component that the application will use for pub/sub behavior.</span></span> <span data-ttu-id="95889-331">Как было показано в предыдущих фрагментах кода, имя используемого компонента публикации и подраздела — `pubsub` .</span><span class="sxs-lookup"><span data-stu-id="95889-331">As you saw in the earlier code snippets, the name of the pub/sub component used is `pubsub`.</span></span> <span data-ttu-id="95889-332">Вот содержимое `eshop-pubsub.yaml` файла в `deployment/compose/dapr/components` папке:</span><span class="sxs-lookup"><span data-stu-id="95889-332">Here's the content of the `eshop-pubsub.yaml` file in the `deployment/compose/dapr/components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: default
spec:
  type: pubsub.nats
  version: v1
  metadata:
  - name: natsURL
    value: nats://demo.nats.io:4222
```

<span data-ttu-id="95889-333">В приведенной выше конфигурации для этого примера указан необходимый [брокер сообщений NAT](https://nats.io/) .</span><span class="sxs-lookup"><span data-stu-id="95889-333">The preceding configuration specifies the desired [NATS message broker](https://nats.io/) for this example.</span></span> <span data-ttu-id="95889-334">Чтобы изменить брокеры сообщений, необходимо настроить другой брокер сообщений, например RabbitMQ или служебную шину Azure, и обновить файл YAML.</span><span class="sxs-lookup"><span data-stu-id="95889-334">To change message brokers, you need only to configure a different message broker, such as RabbitMQ or Azure Service Bus and update the yaml file.</span></span> <span data-ttu-id="95889-335">В ДАПР нет изменений в коде службы магистрали при переключении брокеров сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-335">With Dapr, there are no changes to your mainline service code when switching message brokers.</span></span>

<span data-ttu-id="95889-336">Наконец, вы можете спросить: «Зачем мне нужен несколько брокеров сообщений в приложении?».</span><span class="sxs-lookup"><span data-stu-id="95889-336">Finally, you might ask, "Why would I need multiple message brokers in an application?".</span></span> <span data-ttu-id="95889-337">В большинстве случаев система будет выполнять рабочие нагрузки с различными характеристиками.</span><span class="sxs-lookup"><span data-stu-id="95889-337">Many times a system will handle workloads with different characteristics.</span></span> <span data-ttu-id="95889-338">Одно событие может происходить 10 раз в день, но другое событие происходит 5 000 раз в секунду.</span><span class="sxs-lookup"><span data-stu-id="95889-338">One event may occur 10 times a day, but another event occurs 5,000 times per second.</span></span> <span data-ttu-id="95889-339">Вы можете воспользоваться преимуществами, разбейте трафик сообщений на разные брокеры сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-339">You may benefit by partitioning messaging traffic to different message brokers.</span></span> <span data-ttu-id="95889-340">С помощью ДАПР можно добавить несколько конфигураций компонентов публикации и подраздела, каждый из которых имеет другое имя.</span><span class="sxs-lookup"><span data-stu-id="95889-340">With Dapr, you can add multiple pub/sub component configurations, each with a different name.</span></span>

## <a name="summary"></a><span data-ttu-id="95889-341">Итоги</span><span class="sxs-lookup"><span data-stu-id="95889-341">Summary</span></span>

<span data-ttu-id="95889-342">Шаблон Pub/Re-in позволяет отделить службы в распределенном приложении.</span><span class="sxs-lookup"><span data-stu-id="95889-342">The pub/sub pattern helps you decouple services in a distributed application.</span></span> <span data-ttu-id="95889-343">Стандартный блок ДАПР Publish & Subscribe упрощает реализацию этого поведения в приложении.</span><span class="sxs-lookup"><span data-stu-id="95889-343">The Dapr publish & subscribe building block simplifies implementing this behavior in your application.</span></span>

<span data-ttu-id="95889-344">С помощью ДАПР Pub/Publish можно публиковать сообщения в определенном *разделе*.</span><span class="sxs-lookup"><span data-stu-id="95889-344">Through Dapr pub/sub, you can publish messages to a specific *topic*.</span></span> <span data-ttu-id="95889-345">Кроме того, Стандартный блок запрашивает службу, чтобы определить, на какие разделы следует подписываться.</span><span class="sxs-lookup"><span data-stu-id="95889-345">As well, the building block will query your service to determine which topic(s) to subscribe to.</span></span>

<span data-ttu-id="95889-346">Вы можете использовать ДАПР Pub/подкаталог в собственном формате по протоколу HTTP или с помощью одного из пакетов SDK для конкретного языка, например пакета SDK для .NET для ДАПР.</span><span class="sxs-lookup"><span data-stu-id="95889-346">You can use Dapr pub/sub natively over HTTP or by using one of the language-specific SDKs, such as the .NET SDK for Dapr.</span></span> <span data-ttu-id="95889-347">Пакет SDK для .NET тесно интегрируется с платформой ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="95889-347">The .NET SDK tightly integrates with the ASP.NET core platform.</span></span>

<span data-ttu-id="95889-348">С помощью ДАПР вы можете подключить к приложению поддерживаемый продукт брокера сообщений.</span><span class="sxs-lookup"><span data-stu-id="95889-348">With Dapr, you can plug a supported message broker product into your application.</span></span> <span data-ttu-id="95889-349">Затем можно поменять местами брокеры сообщений, не требуя изменения кода в приложении.</span><span class="sxs-lookup"><span data-stu-id="95889-349">You can then swap message brokers without requiring code changes to your application.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="95889-350">[Назад](service-invocation.md)
> [Вперед](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="95889-350">[Previous](service-invocation.md)
[Next](bindings.md)</span></span>
