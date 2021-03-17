---
title: Стандартный блок привязок ДАПР
description: Описание стандартного блока привязок, его функций, преимуществ и способов применения
author: edwinvw
ms.date: 02/17/2021
ms.openlocfilehash: d6f8b2aa90b15e5b9cd7b5c29938660d1b2907e9
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623958"
---
# <a name="the-dapr-bindings-building-block"></a><span data-ttu-id="9b341-103">Стандартный блок привязок ДАПР</span><span class="sxs-lookup"><span data-stu-id="9b341-103">The Dapr bindings building block</span></span>

<span data-ttu-id="9b341-104">Облачные предложения *,* такие как функции Azure и AWS лямбда-выражения, имеют широкое внедрение в пространстве распределенной архитектуры.</span><span class="sxs-lookup"><span data-stu-id="9b341-104">Cloud-based *serverless* offerings, such as Azure Functions and AWS Lambda, have gained wide adoption across the distributed architecture space.</span></span> <span data-ttu-id="9b341-105">Помимо многих преимуществ, они позволяют микрослужбам *управлять событиями* или *вызывать события во* внешней системе, разрешающей базовые трудности и связанные с ними проблемы.</span><span class="sxs-lookup"><span data-stu-id="9b341-105">Among many benefits, they enable a microservice to *handle events from* or *invoke events in* an external system - abstracting away the underlying complexity and plumbing concerns.</span></span> <span data-ttu-id="9b341-106">Внешние ресурсы — это многие из них: хранилища данных, системы сообщений и веб-ресурсы на разных платформах и поставщиках.</span><span class="sxs-lookup"><span data-stu-id="9b341-106">External resources are many: They include datastores, message systems, and web resources, across different platforms and vendors.</span></span> <span data-ttu-id="9b341-107">[Стандартный блок привязок ДАПР](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) предоставляет эти же возможности привязки ресурсов в прибывают приложений ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-107">The [Dapr bindings building block](https://docs.dapr.io/developing-applications/building-blocks/bindings/bindings-overview/) brings these same resource binding capabilities to the doorstep of your Dapr applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="9b341-108">Решение</span><span class="sxs-lookup"><span data-stu-id="9b341-108">What it solves</span></span>

<span data-ttu-id="9b341-109">Привязки ресурсов ДАПР позволяют службам интегрировать бизнес-операции во внешних ресурсах за пределами немедленного приложения.</span><span class="sxs-lookup"><span data-stu-id="9b341-109">Dapr resource bindings enable your services to integrate business operations across external resources outside of the immediate application.</span></span> <span data-ttu-id="9b341-110">Событие внешней системы может активировать операцию в службе, передавая контекстные сведения.</span><span class="sxs-lookup"><span data-stu-id="9b341-110">An event from an external system could trigger an operation in your service passing in contextual information.</span></span> <span data-ttu-id="9b341-111">Затем служба может расширить операцию, активируя событие в другой внешней системе, передавая контекстные полезные данные.</span><span class="sxs-lookup"><span data-stu-id="9b341-111">Your service could then expand the operation by triggering an event in another external system, passing in contextual payload information.</span></span> <span data-ttu-id="9b341-112">Служба взаимодействует без связи или осведомленности о внешнем ресурсе.</span><span class="sxs-lookup"><span data-stu-id="9b341-112">Your service communicates without coupling or awareness of the external resource.</span></span> <span data-ttu-id="9b341-113">Эти коммуникации инкапсулируются внутри предварительно определенных компонентов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-113">The plumbing is encapsulated inside pre-defined Dapr components.</span></span> <span data-ttu-id="9b341-114">Используемый компонент ДАПР можно легко поменять местами во время выполнения без изменения кода.</span><span class="sxs-lookup"><span data-stu-id="9b341-114">The Dapr component to use can be easily swapped at runtime without code changes.</span></span>

<span data-ttu-id="9b341-115">Рассмотрим, например, учетную запись Twitter, которая запускает событие каждый раз, когда пользователь твитет ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="9b341-115">Consider, for example, a Twitter account that triggers an event whenever a user tweets a keyword.</span></span> <span data-ttu-id="9b341-116">Служба предоставляет обработчик событий, который получает и обрабатывает твит.</span><span class="sxs-lookup"><span data-stu-id="9b341-116">Your service exposes an event handler that receives and processes the tweet.</span></span> <span data-ttu-id="9b341-117">После завершения служба активирует событие, вызывающее внешнюю службу Twilio.</span><span class="sxs-lookup"><span data-stu-id="9b341-117">Once complete, your service triggers an event that invokes an external Twilio service.</span></span> <span data-ttu-id="9b341-118">Twilio отправляет сообщение SMS, содержащее твит.</span><span class="sxs-lookup"><span data-stu-id="9b341-118">Twilio sends an SMS message that includes the tweet.</span></span> <span data-ttu-id="9b341-119">На рис. 8-1 показана концептуальная архитектура этой операции.</span><span class="sxs-lookup"><span data-stu-id="9b341-119">Figure 8-1 show the conceptual architecture of this operation.</span></span>

![Входная привязка](media/bindings/bindings-architecture.png)

<span data-ttu-id="9b341-121">**Рис. 8-1**.</span><span class="sxs-lookup"><span data-stu-id="9b341-121">**Figure 8-1**.</span></span> <span data-ttu-id="9b341-122">Концептуальная архитектура привязки ресурсов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-122">Conceptual architecture of a Dapr resource binding.</span></span>

<span data-ttu-id="9b341-123">На первый взгляд поведение привязки ресурсов может показаться похожим на [шаблон публикации или подписки](publish-subscribe.md) , описанный ранее в этой книге.</span><span class="sxs-lookup"><span data-stu-id="9b341-123">At first glance, resource binding behavior may appear similar to the [Publish/Subscribe pattern](publish-subscribe.md) described earlier in this book.</span></span> <span data-ttu-id="9b341-124">Хотя они имеют сходство, существуют различия.</span><span class="sxs-lookup"><span data-stu-id="9b341-124">While they share similarities, there are differences.</span></span> <span data-ttu-id="9b341-125">Публикация/подписка фокусируется на асинхронной связи между ДАПР Services.</span><span class="sxs-lookup"><span data-stu-id="9b341-125">Publish/subscribe focuses on asynchronous communication between Dapr services.</span></span> <span data-ttu-id="9b341-126">Привязка ресурсов имеет намного более широкие области.</span><span class="sxs-lookup"><span data-stu-id="9b341-126">Resource binding has a much wider scope.</span></span> <span data-ttu-id="9b341-127">В нем основное внимание уделяется взаимодействию системы на разных платформах программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="9b341-127">It focuses on system interoperability across software platforms.</span></span> <span data-ttu-id="9b341-128">Обмен данными между разнородными приложениями, хранилищами данных и службами за пределами приложения микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="9b341-128">Exchanging information between disparate applications, datastores, and services outside your microservice application.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="9b341-129">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="9b341-129">How it works</span></span>

<span data-ttu-id="9b341-130">Привязка ресурса ДАПР начинается с файла конфигурации компонента.</span><span class="sxs-lookup"><span data-stu-id="9b341-130">Dapr resource binding starts with a component configuration file.</span></span> <span data-ttu-id="9b341-131">Этот файл YAML описывает тип ресурса, с которым будет осуществляться привязка, и его параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9b341-131">This YAML file describes the type of resource to which you'll bind along with its configuration settings.</span></span> <span data-ttu-id="9b341-132">После настройки Служба может получить события от ресурса или события триггера.</span><span class="sxs-lookup"><span data-stu-id="9b341-132">Once configured, your service can receive events from the resource or trigger events on it.</span></span>

> [!NOTE]
> <span data-ttu-id="9b341-133">Конфигурации привязки представлены подробно далее в разделе *компоненты* .</span><span class="sxs-lookup"><span data-stu-id="9b341-133">Binding configurations are presented in detail later in the *Components* section.</span></span>

### <a name="input-bindings"></a><span data-ttu-id="9b341-134">Входные привязки</span><span class="sxs-lookup"><span data-stu-id="9b341-134">Input bindings</span></span>

<span data-ttu-id="9b341-135">Входные привязки активируют код с входящими событиями из внешних ресурсов.</span><span class="sxs-lookup"><span data-stu-id="9b341-135">Input bindings trigger your code with incoming events from external resources.</span></span> <span data-ttu-id="9b341-136">Чтобы получить события и данные, необходимо зарегистрировать общедоступную конечную точку из службы, которая станет *обработчиком событий*.</span><span class="sxs-lookup"><span data-stu-id="9b341-136">To receive events and data, you register a public endpoint from your service that becomes the *event handler*.</span></span> <span data-ttu-id="9b341-137">На рис. 8-2 показан поток:</span><span class="sxs-lookup"><span data-stu-id="9b341-137">Figure 8-2 shows the flow:</span></span>

![Поток привязки ввода ДАПР](media/bindings/input-binding-flow.png)

<span data-ttu-id="9b341-139">**Рис. 8-2**.</span><span class="sxs-lookup"><span data-stu-id="9b341-139">**Figure 8-2**.</span></span> <span data-ttu-id="9b341-140">Поток привязки ввода ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-140">Dapr input binding flow.</span></span>

<span data-ttu-id="9b341-141">На рис. 8,2 описаны действия по получению событий из внешней учетной записи Twitter.</span><span class="sxs-lookup"><span data-stu-id="9b341-141">Figure 8.2 describes the steps for receiving events from an external Twitter account:</span></span>

1. <span data-ttu-id="9b341-142">ДАПР расширения считывает файл конфигурации привязки и подписывается на событие, указанное для внешнего ресурса.</span><span class="sxs-lookup"><span data-stu-id="9b341-142">The Dapr sidecar reads the binding configuration file and subscribes to the event specified for the external resource.</span></span> <span data-ttu-id="9b341-143">В этом примере источником события является учетная запись Twitter.</span><span class="sxs-lookup"><span data-stu-id="9b341-143">In the example, the event source is a Twitter account.</span></span>
1. <span data-ttu-id="9b341-144">Когда соответствующий твит публикуется в Twitter, компонент привязки, выполняющийся в ДАПР расширения, выбирает его и активирует событие.</span><span class="sxs-lookup"><span data-stu-id="9b341-144">When a matching Tweet is published on Twitter, the binding component running in the Dapr sidecar picks it up and triggers an event.</span></span>
1. <span data-ttu-id="9b341-145">ДАПР расширения вызывает конечную точку (то есть обработчик событий), настроенную для привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-145">The Dapr sidecar invokes the endpoint (that is, event handler) configured for the binding.</span></span> <span data-ttu-id="9b341-146">В этом примере служба прослушивает HTTP-запрос POST на `/tweet` конечной точке через порт 6000.</span><span class="sxs-lookup"><span data-stu-id="9b341-146">In the example, the service listens for an HTTP POST on the `/tweet` endpoint on port 6000.</span></span> <span data-ttu-id="9b341-147">Так как это операция HTTP POST, полезные данные JSON для события передаются в тексте запроса.</span><span class="sxs-lookup"><span data-stu-id="9b341-147">Because it's an HTTP POST operation, the JSON payload for the event is passed in the request body.</span></span>
1. <span data-ttu-id="9b341-148">После обработки события служба возвращает код состояния HTTP `200 OK` .</span><span class="sxs-lookup"><span data-stu-id="9b341-148">After handling the event, the service returns an HTTP status code `200 OK`.</span></span>

<span data-ttu-id="9b341-149">Следующий контроллер ASP.NET Core предоставляет пример обработки события, запускаемого привязкой Twitter:</span><span class="sxs-lookup"><span data-stu-id="9b341-149">The following ASP.NET Core controller provides an example of handling an event triggered by the Twitter binding:</span></span>

```csharp
[ApiController]
public class SomeController : ControllerBase
{
    public class TwitterTweet
    {
        [JsonPropertyName("id_str")]
        public string ID {get; set; }

        [JsonPropertyName("text")]
        public string Text {get; set; }
    }

    [HttpPost("/tweet")]
    public ActionResult Post(TwitterTweet tweet)
    {
        // Handle tweet
        Console.WriteLine("Tweet received: {0}: {1}", tweet.ID, tweet.Text);

        // ...

        // Acknowledge message
        return Ok();
    }
}
```

<span data-ttu-id="9b341-150">Если операция должна возвращать ошибку, возвращается соответствующий код состояния HTTP уровня 400 или 500.</span><span class="sxs-lookup"><span data-stu-id="9b341-150">If the operation should error, you would return the appropriate 400 or 500 level HTTP status code.</span></span> <span data-ttu-id="9b341-151">Для привязок, которые имеют гарантии *по крайней мере однократной доставки* , ДАПР расширения будет повторять триггер.</span><span class="sxs-lookup"><span data-stu-id="9b341-151">For bindings that feature *at-least-once-delivery* guarantees, the Dapr sidecar will retry the trigger.</span></span> <span data-ttu-id="9b341-152">Ознакомьтесь с [ДАПР документацией по привязкам ресурсов] [1], чтобы узнать, предлагают ли они гарантии доставки *по крайней мере один* раз или *ровно один раз* .</span><span class="sxs-lookup"><span data-stu-id="9b341-152">Check out [Dapr documentation for resource bindings][1] to see whether they offer *at-least-once* or *exactly-once* delivery guarantees.</span></span>

### <a name="output-bindings"></a><span data-ttu-id="9b341-153">Выходные привязки</span><span class="sxs-lookup"><span data-stu-id="9b341-153">Output bindings</span></span>

<span data-ttu-id="9b341-154">ДАПР также включает возможности *выходной привязки* .</span><span class="sxs-lookup"><span data-stu-id="9b341-154">Dapr also includes *output binding* capabilities.</span></span> <span data-ttu-id="9b341-155">Они позволяют службе активировать событие, вызывающее внешний ресурс.</span><span class="sxs-lookup"><span data-stu-id="9b341-155">They enable your service to trigger an event that invokes an external resource.</span></span> <span data-ttu-id="9b341-156">Опять же, сначала нужно настроить файл конфигурации привязки YAML, описывающий выходную привязку.</span><span class="sxs-lookup"><span data-stu-id="9b341-156">Again, you start by configuring a binding configuration YAML file that describes the output binding.</span></span> <span data-ttu-id="9b341-157">После этого вы активируете событие, которое вызывает API привязок в ДАПР расширения приложения.</span><span class="sxs-lookup"><span data-stu-id="9b341-157">Once in place, you trigger an event that invokes the bindings API on the Dapr sidecar of your application.</span></span> <span data-ttu-id="9b341-158">На рисунке 8-3 показан поток выходной привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-158">Figure 8-3 shows the flow of an output binding:</span></span>

![Поток привязки выходных данных ДАПР](media/bindings/output-binding-flow.png)

<span data-ttu-id="9b341-160">**Рис. 8-3**.</span><span class="sxs-lookup"><span data-stu-id="9b341-160">**Figure 8-3**.</span></span> <span data-ttu-id="9b341-161">Поток привязки выходных данных ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-161">Dapr output binding flow.</span></span>

1. <span data-ttu-id="9b341-162">ДАПР расширения считывает файл конфигурации привязки со сведениями о том, как подключиться к внешнему ресурсу.</span><span class="sxs-lookup"><span data-stu-id="9b341-162">The Dapr sidecar reads the binding configuration file with the information on how to connect to the external resource.</span></span> <span data-ttu-id="9b341-163">В этом примере внешний ресурс является Twilio учетной записью SMS.</span><span class="sxs-lookup"><span data-stu-id="9b341-163">In the example, the external resource is a Twilio SMS account.</span></span>
1. <span data-ttu-id="9b341-164">Приложение вызывает `/v1.0/bindings/sms` конечную точку в ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="9b341-164">Your application invokes the `/v1.0/bindings/sms` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="9b341-165">В этом случае для вызова API используется HTTP-запрос POST.</span><span class="sxs-lookup"><span data-stu-id="9b341-165">In this case, it uses an HTTP POST to invoke the API.</span></span> <span data-ttu-id="9b341-166">Также можно использовать gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b341-166">It's also possible to use gRPC.</span></span>
1. <span data-ttu-id="9b341-167">Компонент привязки, выполняющийся в ДАПР расширения, вызывает внешнюю систему обмена сообщениями для отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="9b341-167">The binding component running in the Dapr sidecar calls the external messaging system to send the message.</span></span> <span data-ttu-id="9b341-168">Сообщение будет содержать полезные данные, переданные в запрос POST.</span><span class="sxs-lookup"><span data-stu-id="9b341-168">The message will contain the payload passed in the POST request.</span></span>

<span data-ttu-id="9b341-169">Например, можно вызвать выходную привязку, вызвав API ДАПР, используя фигурную скобку:</span><span class="sxs-lookup"><span data-stu-id="9b341-169">As an example, you can invoke an output binding by invoking the Dapr API using curl:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/bindings/sms \
  -H "Content-Type: application/json" \
  -d '{
        "data": "Welcome to this awesome service",
        "metadata": {
          "toNumber": "555-3277"
        },
        "operation": "create"
      }'
```

<span data-ttu-id="9b341-170">Обратите внимание, что HTTP-порт совпадает с используемым расширенияом ДАПР (в данном случае HTTP-портом ДАПР по умолчанию `3500` ).</span><span class="sxs-lookup"><span data-stu-id="9b341-170">Note that the HTTP port is the same as used by the Dapr sidecar (in this case, the default Dapr HTTP port `3500`).</span></span>

<span data-ttu-id="9b341-171">Структура полезных данных (то есть отправленное сообщение) будет отличаться для каждой привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-171">The structure of the payload (that is, message sent) will vary per binding.</span></span> <span data-ttu-id="9b341-172">В приведенном выше примере полезная нагрузка содержит `data` элемент с сообщением.</span><span class="sxs-lookup"><span data-stu-id="9b341-172">In the example above, the payload contains a `data` element with a message.</span></span> <span data-ttu-id="9b341-173">Привязки к другим типам внешних ресурсов могут отличаться, особенно для отправленных метаданных.</span><span class="sxs-lookup"><span data-stu-id="9b341-173">Bindings to other types of external resources can be different, especially for the metadata that is sent.</span></span> <span data-ttu-id="9b341-174">Каждая полезная нагрузка должна также содержать `operation` поле, определяющее операцию, которую будет выполнять привязка.</span><span class="sxs-lookup"><span data-stu-id="9b341-174">Each payload must also contain an `operation` field, that defines the operation the binding will execute.</span></span> <span data-ttu-id="9b341-175">В приведенном выше примере указывается `create` операция, создающая SMS-сообщение.</span><span class="sxs-lookup"><span data-stu-id="9b341-175">The above example specifies a `create` operation that creates the SMS message.</span></span> <span data-ttu-id="9b341-176">К общим операциям относятся:</span><span class="sxs-lookup"><span data-stu-id="9b341-176">Common operations include:</span></span>

- <span data-ttu-id="9b341-177">create</span><span class="sxs-lookup"><span data-stu-id="9b341-177">create</span></span>
- <span data-ttu-id="9b341-178">get</span><span class="sxs-lookup"><span data-stu-id="9b341-178">get</span></span>
- <span data-ttu-id="9b341-179">удалить</span><span class="sxs-lookup"><span data-stu-id="9b341-179">delete</span></span>
- <span data-ttu-id="9b341-180">list</span><span class="sxs-lookup"><span data-stu-id="9b341-180">list</span></span>

<span data-ttu-id="9b341-181">Это может быть автор привязки, который поддерживает привязка.</span><span class="sxs-lookup"><span data-stu-id="9b341-181">It's up to the author of the binding which operations the binding supports.</span></span> <span data-ttu-id="9b341-182">В документации по каждой привязке описаны доступные операции и способы их вызова.</span><span class="sxs-lookup"><span data-stu-id="9b341-182">The documentation for each binding describes the available operations and how to invoke them.</span></span>

## <a name="using-the-dapr-net-sdk"></a><span data-ttu-id="9b341-183">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="9b341-183">Using the Dapr .NET SDK</span></span>

<span data-ttu-id="9b341-184">Пакет SDK для ДАПР для .NET предоставляет поддержку для разработчиков .NET Core на определенном языке.</span><span class="sxs-lookup"><span data-stu-id="9b341-184">The Dapr .NET SDK provides language-specific support for .NET Core developers.</span></span> <span data-ttu-id="9b341-185">В следующем примере вызов `HttpClient.PostAsync()` метода заменяется на `DaprClient.InvokeBindingAsync()` метод.</span><span class="sxs-lookup"><span data-stu-id="9b341-185">In the following example, the call to the `HttpClient.PostAsync()` is replaced with the `DaprClient.InvokeBindingAsync()` method.</span></span> <span data-ttu-id="9b341-186">Этот специализированный метод упрощает вызов настроенной выходной привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-186">This specialized method simplifies invoking a configured output binding:</span></span>

```csharp
private async Task SendSMSAsync([FromServices] DaprClient daprClient)
{
    var message = "Welcome to this awesome service";
    var metadata = new Dictionary<string, string>
    {
      { "toNumber", "555-3277" }
    };
    await daprClient.InvokeBindingAsync("sms", "create", message, metadata);
}
```

<span data-ttu-id="9b341-187">Метод принимает `metadata` `message` значения и.</span><span class="sxs-lookup"><span data-stu-id="9b341-187">The method expects the `metadata` and `message` values.</span></span>

<span data-ttu-id="9b341-188">При использовании для вызова привязки `DaprClient` компонент использует gRPC для вызова API ДАПР в ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="9b341-188">When used to invoke a binding, the `DaprClient` uses gRPC to call the Dapr API on the Dapr sidecar.</span></span>

## <a name="binding-components"></a><span data-ttu-id="9b341-189">Привязка компонентов</span><span class="sxs-lookup"><span data-stu-id="9b341-189">Binding components</span></span>

<span data-ttu-id="9b341-190">На внутреннем ресурсе привязки ресурсов реализуются с помощью компонентов привязки ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-190">Under the hood, resource bindings are implemented with Dapr binding components.</span></span> <span data-ttu-id="9b341-191">Они предоставляются сообществом и пишутся в дороге.</span><span class="sxs-lookup"><span data-stu-id="9b341-191">They're contributed by the community and written in Go.</span></span> <span data-ttu-id="9b341-192">Если необходимо выполнить интеграцию с внешним ресурсом, для которого не существует привязки ДАПР, можно создать его самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="9b341-192">If you need to integrate with an external resource for which no Dapr binding exists yet, you can create it yourself.</span></span> <span data-ttu-id="9b341-193">Чтобы узнать, как можно привязать привязку, ознакомьтесь с [репозиторием ДАПР Components-от участников сообщества](https://github.com/dapr/components-contrib) .</span><span class="sxs-lookup"><span data-stu-id="9b341-193">Check out the [Dapr components-contrib repo](https://github.com/dapr/components-contrib) to see how you can contribute a binding.</span></span>

> [!NOTE]
> <span data-ttu-id="9b341-194">ДАПР и все его компоненты написаны на языке [Golang](https://golang.org/) (Go).</span><span class="sxs-lookup"><span data-stu-id="9b341-194">Dapr and all of its components are written in the [Golang](https://golang.org/) (Go) language.</span></span> <span data-ttu-id="9b341-195">Go считается современной облачной платформой программирования.</span><span class="sxs-lookup"><span data-stu-id="9b341-195">Go is considered a modern, cloud-native programming platform.</span></span>

<span data-ttu-id="9b341-196">Привязки настраиваются с помощью файла конфигурации YAML.</span><span class="sxs-lookup"><span data-stu-id="9b341-196">You configure bindings using a YAML configuration file.</span></span> <span data-ttu-id="9b341-197">Ниже приведен пример конфигурации для привязки Twitter.</span><span class="sxs-lookup"><span data-stu-id="9b341-197">Here's an example configuration for the Twitter binding:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: twitter-mention
  namespace: default
spec:
  type: bindings.twitter
  version: v1
  metadata:
  - name: consumerKey
    value: "****" # twitter api consumer key, required
  - name: consumerSecret
    value: "****" # twitter api consumer secret, required
  - name: accessToken
    value: "****" # twitter api access token, required
  - name: accessSecret
    value: "****" # twitter api access secret, required
  - name: query
    value: "dapr" # your search query, required
```

<span data-ttu-id="9b341-198">Каждая конфигурация привязки содержит общий `metadata` элемент с `name` `namespace` полем и.</span><span class="sxs-lookup"><span data-stu-id="9b341-198">Each binding configuration contains a general `metadata` element with a `name` and `namespace` field.</span></span> <span data-ttu-id="9b341-199">ДАПР определит конечную точку для вызова службы на основе настроенного `name` поля.</span><span class="sxs-lookup"><span data-stu-id="9b341-199">Dapr will determine the endpoint to invoke your service based upon the configured `name` field.</span></span> <span data-ttu-id="9b341-200">В приведенном выше примере ДАПР вызовет метод, помеченный `/twitter-mention` как в службе при возникновении события.</span><span class="sxs-lookup"><span data-stu-id="9b341-200">In the above example, Dapr will invoke the method annotated with `/twitter-mention` in your service when an event occurs.</span></span>

<span data-ttu-id="9b341-201">В `spec` элементе вы указываете `type` привязку, а также заданную привязку `metadata` .</span><span class="sxs-lookup"><span data-stu-id="9b341-201">In the `spec` element, you specify the `type` of the binding along with binding specific `metadata`.</span></span> <span data-ttu-id="9b341-202">В примере указываются учетные данные для доступа к учетной записи Twitter с помощью API.</span><span class="sxs-lookup"><span data-stu-id="9b341-202">The example specifies credentials for accessing a Twitter account using its API.</span></span> <span data-ttu-id="9b341-203">Метаданные могут различаться между входными и выходными привязками.</span><span class="sxs-lookup"><span data-stu-id="9b341-203">The metadata can differ between input and output bindings.</span></span> <span data-ttu-id="9b341-204">Например, чтобы использовать Twitter в качестве входной привязки, необходимо указать текст для поиска в твитах с помощью `query` поля.</span><span class="sxs-lookup"><span data-stu-id="9b341-204">For example, to use Twitter as an input binding, you need to specify the text to search for in tweets using the `query` field.</span></span> <span data-ttu-id="9b341-205">При каждом отправке соответствующего твита ДАПР расширения будет вызывать `/twitter-mention` конечную точку в службе.</span><span class="sxs-lookup"><span data-stu-id="9b341-205">Every time a matching tweet is sent, the Dapr sidecar will invoke the `/twitter-mention` endpoint on the service.</span></span> <span data-ttu-id="9b341-206">Он также будет доставлять содержимое твита.</span><span class="sxs-lookup"><span data-stu-id="9b341-206">It will also deliver the contents of the tweet.</span></span>

<span data-ttu-id="9b341-207">Привязку можно настроить для ввода, вывода или и того и другого.</span><span class="sxs-lookup"><span data-stu-id="9b341-207">A binding can be configured for input, output, or both.</span></span> <span data-ttu-id="9b341-208">Интересно, что привязка явно не задает входную или выходную конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9b341-208">Interestingly, the binding doesn't explicitly specify input or output configuration.</span></span> <span data-ttu-id="9b341-209">Вместо этого направление выводится при использовании привязки вместе со значениями конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9b341-209">Instead, the direction is inferred by the usage of the binding along with configuration values.</span></span>

<span data-ttu-id="9b341-210">[ДАПР документация по привязкам ресурсов] [1] содержит полный список доступных привязок и их конкретные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9b341-210">The [Dapr documentation for resource bindings][1] provides a complete list of the available bindings and their specific configuration settings.</span></span>

### <a name="cron-binding"></a><span data-ttu-id="9b341-211">Привязка cron</span><span class="sxs-lookup"><span data-stu-id="9b341-211">Cron binding</span></span>

<span data-ttu-id="9b341-212">Обратите особое внимание на привязку cron ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-212">Pay close attention to Dapr's Cron binding.</span></span> <span data-ttu-id="9b341-213">Он не подписывается на события из внешней системы.</span><span class="sxs-lookup"><span data-stu-id="9b341-213">It doesn't subscribe to events from an external system.</span></span> <span data-ttu-id="9b341-214">Вместо этого для запуска приложения в этой привязке используется настраиваемое расписание интервала.</span><span class="sxs-lookup"><span data-stu-id="9b341-214">Instead, this binding uses a configurable interval schedule to trigger your application.</span></span> <span data-ttu-id="9b341-215">Привязка предоставляет простой способ реализации фоновой рабочей роли для пробуждения и выполнения некоторой работы с постоянным интервалом без необходимости реализации бесконечного цикла с настраиваемой задержкой.</span><span class="sxs-lookup"><span data-stu-id="9b341-215">The binding provides a simple way to implement a background worker to wake up and do some work at a regular interval, without the need to implement an endless loop with a configurable delay.</span></span> <span data-ttu-id="9b341-216">Ниже приведен пример конфигурации привязки cron:</span><span class="sxs-lookup"><span data-stu-id="9b341-216">Here's an example of a Cron binding configuration:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: checkOrderBacklog
  namespace: default
spec:
  type: bindings.cron
  version: v1
  metadata:
  - name: schedule
    value: "@every 30m"
```

<span data-ttu-id="9b341-217">В этом примере ДАПР активирует службу, вызывая `/checkOrderBacklog` конечную точку каждые 30 минут.</span><span class="sxs-lookup"><span data-stu-id="9b341-217">In this example, Dapr triggers a service by invoking the `/checkOrderBacklog` endpoint every 30 minutes.</span></span> <span data-ttu-id="9b341-218">Для указания значения можно использовать несколько шаблонов `schedule` .</span><span class="sxs-lookup"><span data-stu-id="9b341-218">There are several patterns available for specifying the `schedule` value.</span></span> <span data-ttu-id="9b341-219">Дополнительные сведения см. в [документации по привязке cron](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/).</span><span class="sxs-lookup"><span data-stu-id="9b341-219">For more information, see the [Cron binding documentation](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/cron/).</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="9b341-220">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="9b341-220">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="9b341-221">Сопутствующее эталонное приложение Ешопондапр реализует пример выходной привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-221">The accompanying eShopOnDapr reference application implements an output binding example.</span></span> <span data-ttu-id="9b341-222">Он запускает привязку ДАПР [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) для отправки пользователю сообщения электронной почты при помещении нового заказа.</span><span class="sxs-lookup"><span data-stu-id="9b341-222">It triggers the Dapr [SendGrid](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/sendgrid/) binding to send a user an email when a new order is placed.</span></span> <span data-ttu-id="9b341-223">Эту привязку можно найти в `eshop-email.yaml` файле в папке Components:</span><span class="sxs-lookup"><span data-stu-id="9b341-223">You can find this binding in the `eshop-email.yaml` file in the components folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: sendmail
  namespace: eshop
spec:
  type: bindings.twilio.sendgrid
  version: v1
  metadata:
  - name: apiKey
    secretKeyRef:
      name: sendGridAPIKey
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="9b341-224">В этой конфигурации используется компонент привязки [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) .</span><span class="sxs-lookup"><span data-stu-id="9b341-224">This configuration uses the [Twilio SendGrid](https://github.com/dapr/components-contrib/tree/master/bindings/twilio) binding component.</span></span> <span data-ttu-id="9b341-225">Обратите внимание, что ключ API для подключения к службе использует ссылку на секрет ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-225">Note how the API key for connecting to the service consumes a Dapr secret reference.</span></span> <span data-ttu-id="9b341-226">Этот подход обеспечивает хранение секретов за пределами файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9b341-226">This approach keeps secrets outside of the configuration file.</span></span> <span data-ttu-id="9b341-227">Дополнительные сведения о секретах ДАПР см. в [разделе секреты стандартного блока](secrets.md) .</span><span class="sxs-lookup"><span data-stu-id="9b341-227">Read the [secrets building block chapter](secrets.md) to learn more about Dapr secrets.</span></span>

<span data-ttu-id="9b341-228">Конфигурация привязки указывает компонент привязки, который можно вызвать с помощью `/sendmail` конечной точки в ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="9b341-228">The binding configuration specifies a binding component that can be invoked using the `/sendmail` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="9b341-229">Ниже приведен фрагмент кода, в котором отправляется сообщение электронной почты при каждом запуске заказа:</span><span class="sxs-lookup"><span data-stu-id="9b341-229">Here's a code snippet in which an email is sent whenever an order is started:</span></span>

```csharp
public Task Handle(OrderStartedDomainEvent notification, CancellationToken cancellationToken)
{
    var string message = CreateEmailBody(notification);
    var metadata = new Dictionary<string, string>
    {
        {"emailFrom", "eShopOn@dapr.io"},
        {"emailTo", notification.UserName},
        {"subject", $"Your eShopOnDapr order #{notification.Order.Id}"}
    };
    return _daprClient.InvokeBindingAsync("sendmail", "create", message, metadata, cancellationToken);
}
```

<span data-ttu-id="9b341-230">Как видно в этом примере, `message` содержит текст сообщения.</span><span class="sxs-lookup"><span data-stu-id="9b341-230">As you can see in this example, `message` contains the message body.</span></span> <span data-ttu-id="9b341-231">`CreateEmailBody`Метод просто форматирует строку с текстом текста.</span><span class="sxs-lookup"><span data-stu-id="9b341-231">The `CreateEmailBody` method simply formats a string with the body text.</span></span> <span data-ttu-id="9b341-232">`metadata`Указывает отправителя, получателя и тему сообщения электронной почты.</span><span class="sxs-lookup"><span data-stu-id="9b341-232">The `metadata` specifies the email sender, recipient, and the subject for the email message.</span></span> <span data-ttu-id="9b341-233">Если эти значения являются статическими, они также могут быть включены в поля метаданных в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9b341-233">If these values are static, they can also be included in the metadata fields in the configuration file.</span></span> <span data-ttu-id="9b341-234">Имя вызываемой привязки — `sendmail` , а операция — `create` .</span><span class="sxs-lookup"><span data-stu-id="9b341-234">The name of the binding to invoke is `sendmail` and the operation is `create`.</span></span>

## <a name="summary"></a><span data-ttu-id="9b341-235">Итоги</span><span class="sxs-lookup"><span data-stu-id="9b341-235">Summary</span></span>

<span data-ttu-id="9b341-236">Привязки ресурсов ДАПР позволяют интегрироваться с различными внешними ресурсами и системами без зависимости от их библиотек или пакетов SDK.</span><span class="sxs-lookup"><span data-stu-id="9b341-236">Dapr resource bindings enable you to integrate with different external resources and systems without taking dependencies on their libraries or SDKs.</span></span> <span data-ttu-id="9b341-237">Эти внешние системы не обязательно должны быть системами обмена сообщениями, такими как служебная шина или брокер сообщений.</span><span class="sxs-lookup"><span data-stu-id="9b341-237">These external systems don't necessarily have to be messaging systems like a service bus or message broker.</span></span> <span data-ttu-id="9b341-238">Также существуют привязки для хранилищ данных и веб-ресурсов, таких как Twitter или SendGrid.</span><span class="sxs-lookup"><span data-stu-id="9b341-238">Bindings also exist for datastores and web resources like Twitter or SendGrid.</span></span>

<span data-ttu-id="9b341-239">Входные привязки (или триггеры) реагируют на события, происходящие во внешней системе.</span><span class="sxs-lookup"><span data-stu-id="9b341-239">Input bindings (or triggers) react to events occurring in an external system.</span></span> <span data-ttu-id="9b341-240">Они вызывают общедоступные конечные точки HTTP, предварительно настроенные в приложении.</span><span class="sxs-lookup"><span data-stu-id="9b341-240">They invoke the public HTTP endpoints pre-configured in your application.</span></span> <span data-ttu-id="9b341-241">ДАПР использует имя привязки в конфигурации, чтобы определить конечную точку для вызова в приложении.</span><span class="sxs-lookup"><span data-stu-id="9b341-241">Dapr uses the name of the binding in the configuration to determine the endpoint to call in your application.</span></span>

<span data-ttu-id="9b341-242">Выходные привязки будут отсылать сообщения во внешнюю систему.</span><span class="sxs-lookup"><span data-stu-id="9b341-242">Output bindings will send messages to an external system.</span></span> <span data-ttu-id="9b341-243">Вы активируете выходную привязку, выполняя HTTP-запрос POST к `/v1.0/bindings/<binding-name>` конечной точке на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="9b341-243">You trigger an output binding by doing an HTTP POST on the `/v1.0/bindings/<binding-name>` endpoint on the Dapr sidecar.</span></span> <span data-ttu-id="9b341-244">Для вызова привязки можно также использовать gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b341-244">You can also use gRPC to invoke the binding.</span></span> <span data-ttu-id="9b341-245">Пакет SDK для .NET предлагает `InvokeBindingAsync` метод для вызова привязок ДАПР с помощью gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b341-245">The .NET SDK offers a `InvokeBindingAsync` method to invoke Dapr bindings using gRPC.</span></span>

<span data-ttu-id="9b341-246">Вы реализуете привязку с помощью компонента ДАПР.</span><span class="sxs-lookup"><span data-stu-id="9b341-246">You implement a binding with a Dapr component.</span></span> <span data-ttu-id="9b341-247">Эти компоненты предоставляются сообществом.</span><span class="sxs-lookup"><span data-stu-id="9b341-247">These components are contributed by the community.</span></span> <span data-ttu-id="9b341-248">Конфигурация каждого компонента привязки имеет метаданные, характерные для внешней системы, которая является абстрактной.</span><span class="sxs-lookup"><span data-stu-id="9b341-248">Each binding component's configuration has metadata that is specific for the external system it abstracts.</span></span> <span data-ttu-id="9b341-249">Кроме того, поддерживаемые ею команды и структура полезных данных будут отличаться для каждого компонента привязки.</span><span class="sxs-lookup"><span data-stu-id="9b341-249">Also, the commands it supports and the structure of the payload will differ per binding component.</span></span>

### <a name="references"></a><span data-ttu-id="9b341-250">Ссылки</span><span class="sxs-lookup"><span data-stu-id="9b341-250">References</span></span>

- [<span data-ttu-id="9b341-251">Документация по ДАПР для привязок ресурсов</span><span class="sxs-lookup"><span data-stu-id="9b341-251">Dapr documentation for resource bindings</span></span>](https://docs.dapr.io/operations/components/setup-bindings/supported-bindings/)

>[!div class="step-by-step"]
><span data-ttu-id="9b341-252">[Назад](publish-subscribe.md)
>[Вперед](observability.md)</span><span class="sxs-lookup"><span data-stu-id="9b341-252">[Previous](publish-subscribe.md)
[Next](observability.md)</span></span>
