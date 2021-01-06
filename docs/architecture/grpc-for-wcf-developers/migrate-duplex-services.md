---
title: Перенос служб дуплексной службы WCF в gRPC-gRPC для разработчиков WCF
description: Узнайте, как перенести различные формы служб дуплексной службы WCF в gRPC Streaming Services.
ms.date: 12/15/2020
ms.openlocfilehash: 4741e5ad5c12fa358853381d4f2c286add14f8f5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938030"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="f8195-103">Перенос дуплексных служб WCF в gRPC</span><span class="sxs-lookup"><span data-stu-id="f8195-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="f8195-104">Теперь, когда у вас есть смысл основных концепций, в этом разделе вы узнаете о более сложных *потоковых* gRPC службах.</span><span class="sxs-lookup"><span data-stu-id="f8195-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="f8195-105">Существует несколько способов использования дуплексных служб в Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8195-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f8195-106">Некоторые службы инициируются клиентом, а затем потоковая передача данных с сервера.</span><span class="sxs-lookup"><span data-stu-id="f8195-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="f8195-107">Другие Дуплексные службы могут содержать более интерактивное двустороннее взаимодействие, например классический калькулятор в документации по WCF.</span><span class="sxs-lookup"><span data-stu-id="f8195-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="f8195-108">В этой главе вы получите две возможные реализации биржевых средств WCF и перенесите их в gRPC: один использует потоковую передачу RPC на сервере и другой, использующий двунаправленный потоковую передачу RPC.</span><span class="sxs-lookup"><span data-stu-id="f8195-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="f8195-109">Потоковая передача RPC сервера</span><span class="sxs-lookup"><span data-stu-id="f8195-109">Server streaming RPC</span></span>

<span data-ttu-id="f8195-110">В [примере решения WCF симплестокктиккер](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), симплестоккприцетиккер, существует дуплексная служба, для которой клиент запускает подключение со списком стандартных символов, а сервер использует *интерфейс обратного вызова* для отправки обновлений по мере их появления.</span><span class="sxs-lookup"><span data-stu-id="f8195-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="f8195-111">Клиент реализует этот интерфейс для реагирования на вызовы с сервера.</span><span class="sxs-lookup"><span data-stu-id="f8195-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="f8195-112">Решение WCF</span><span class="sxs-lookup"><span data-stu-id="f8195-112">The WCF solution</span></span>

<span data-ttu-id="f8195-113">Решение WCF реализовано как локально размещенный сервер NET. TCP в .NET Framework 4. консольное приложение *x* .</span><span class="sxs-lookup"><span data-stu-id="f8195-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="f8195-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="f8195-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="f8195-115">Служба имеет один метод без типа возвращаемого значения, так как он использует интерфейс обратного вызова `ISimpleStockTickerCallback` для отправки данных клиенту в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="f8195-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="f8195-116">Интерфейс обратного вызова</span><span class="sxs-lookup"><span data-stu-id="f8195-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="f8195-117">Реализации этих интерфейсов можно найти в решении, а также с фиктивными внешними зависимостями для предоставления тестовых данных.</span><span class="sxs-lookup"><span data-stu-id="f8195-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="f8195-118">Потоковая передача gRPC</span><span class="sxs-lookup"><span data-stu-id="f8195-118">gRPC streaming</span></span>

<span data-ttu-id="f8195-119">Процесс gRPC для обработки данных в режиме реального времени отличается от процесса WCF.</span><span class="sxs-lookup"><span data-stu-id="f8195-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="f8195-120">Вызов от клиента к серверу может создать постоянный поток, который можно отслеживать для сообщений, поступивших асинхронно.</span><span class="sxs-lookup"><span data-stu-id="f8195-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="f8195-121">Несмотря на различие, потоки могут быть более интуитивно понятным способом работы с этими данными и более актуальны в современном программировании, что акцентирует внимание на LINQ, реактивные потоки, функциональное программирование и т. д.</span><span class="sxs-lookup"><span data-stu-id="f8195-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="f8195-122">Определение службы должно иметь два сообщения: одно для запроса и одно для потока.</span><span class="sxs-lookup"><span data-stu-id="f8195-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="f8195-123">Служба возвращает поток `StockTickerUpdate` сообщения с `stream` ключевым словом в его `return` объявлении.</span><span class="sxs-lookup"><span data-stu-id="f8195-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="f8195-124">Рекомендуется добавить `Timestamp` к обновлению, чтобы отобразить точное время изменения цены.</span><span class="sxs-lookup"><span data-stu-id="f8195-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="f8195-125">simple_stock_ticker.</span><span class="sxs-lookup"><span data-stu-id="f8195-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a><span data-ttu-id="f8195-126">Реализация Симплестокктиккер</span><span class="sxs-lookup"><span data-stu-id="f8195-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="f8195-127">Повторно используйте имитацию `StockPriceSubscriber` из проекта WCF, скопировав три класса из `TraderSys.StockMarket` библиотеки классов в новую библиотеку классов .NET Standard в целевом решении.</span><span class="sxs-lookup"><span data-stu-id="f8195-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="f8195-128">Чтобы лучше следовать рекомендациям, добавьте `Factory` тип для создания экземпляров и зарегистрируйте его `IStockPriceSubscriberFactory` с помощью ASP.NET Core служб внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="f8195-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="f8195-129">Реализация фабрики</span><span class="sxs-lookup"><span data-stu-id="f8195-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="register-the-factory"></a><span data-ttu-id="f8195-130">Регистрация фабрики</span><span class="sxs-lookup"><span data-stu-id="f8195-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="f8195-131">Теперь этот класс можно использовать для реализации gRPC `StockTickerService` .</span><span class="sxs-lookup"><span data-stu-id="f8195-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="f8195-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="f8195-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors caused by broken connection, etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="f8195-133">Как видите, хотя объявление в `.proto` файле говорит, что метод возвращает поток `StockTickerUpdate` сообщений, он фактически возвращает `Task` .</span><span class="sxs-lookup"><span data-stu-id="f8195-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="f8195-134">Задание создания потока обрабатывается созданным кодом и библиотеками времени выполнения gRPC, которые предоставляют `IServerStreamWriter<StockTickerUpdate>` поток ответов, готовый к использованию.</span><span class="sxs-lookup"><span data-stu-id="f8195-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="f8195-135">В отличие от двусторонней службы WCF, где экземпляр класса службы хранится в активном состоянии при открытом соединении, служба gRPC использует возвращенную задачу для поддержания активности службы.</span><span class="sxs-lookup"><span data-stu-id="f8195-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="f8195-136">Задача не должна завершаться, пока соединение не будет закрыто.</span><span class="sxs-lookup"><span data-stu-id="f8195-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="f8195-137">Служба может определить, когда клиент закрыл соединение с помощью `CancellationToken` из `ServerCallContext` .</span><span class="sxs-lookup"><span data-stu-id="f8195-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="f8195-138">Простой статический метод, `AwaitCancellation` , используется для создания задачи, которая завершается при отмене маркера.</span><span class="sxs-lookup"><span data-stu-id="f8195-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="f8195-139">В `Subscribe` методе получите `StockPriceSubscriber` и добавьте обработчик событий, записывающий данные в поток ответа.</span><span class="sxs-lookup"><span data-stu-id="f8195-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="f8195-140">Затем дождитесь закрытия соединения, прежде чем сразу же удаляется, `subscriber` чтобы предотвратить попытку записи данных в закрытый поток.</span><span class="sxs-lookup"><span data-stu-id="f8195-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="f8195-141">`WriteUpdateAsync`Метод имеет `try` / `catch` блок для выполнения любых ошибок, которые могут произойти при запись сообщения в поток.</span><span class="sxs-lookup"><span data-stu-id="f8195-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="f8195-142">Это важно в постоянных подключениях по сетям, которые могут быть нарушены в любой миллисекунде, как намеренно, так и из-за сбоя в любом месте.</span><span class="sxs-lookup"><span data-stu-id="f8195-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="f8195-143">Использование Стокктиккерсервице из клиентского приложения</span><span class="sxs-lookup"><span data-stu-id="f8195-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="f8195-144">Выполните те же действия из предыдущего раздела, чтобы создать общую библиотеку классов клиента из `.proto` файла.</span><span class="sxs-lookup"><span data-stu-id="f8195-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="f8195-145">В этом примере имеется консольное приложение .NET, которое демонстрирует использование клиента.</span><span class="sxs-lookup"><span data-stu-id="f8195-145">In the sample, there's a .NET console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="f8195-146">Пример Program.cs</span><span class="sxs-lookup"><span data-stu-id="f8195-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="f8195-147">В этом случае `Subscribe` метод созданного клиента не является асинхронным.</span><span class="sxs-lookup"><span data-stu-id="f8195-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="f8195-148">Поток создается и пригоден к использованию, так как его `MoveNext` метод асинхронен и первый раз его вызов не завершается до тех пор, пока соединение не будет активно.</span><span class="sxs-lookup"><span data-stu-id="f8195-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="f8195-149">Поток передается асинхронному `DisplayAsync` методу.</span><span class="sxs-lookup"><span data-stu-id="f8195-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="f8195-150">Затем приложение ожидает нажатия пользователем клавиши, а затем отменяет `DisplayAsync` метод и ожидает завершения задачи перед выходом.</span><span class="sxs-lookup"><span data-stu-id="f8195-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="f8195-151">Этот код использует новый `using` синтаксис объявления C# 8 для удаления потока и канала при `Main` выходе из метода.</span><span class="sxs-lookup"><span data-stu-id="f8195-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="f8195-152">Это небольшое изменение, но хорошо, что сокращает отступы и пустые строки.</span><span class="sxs-lookup"><span data-stu-id="f8195-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="f8195-153">Использование потока</span><span class="sxs-lookup"><span data-stu-id="f8195-153">Consume the stream</span></span>

<span data-ttu-id="f8195-154">WCF использует интерфейсы обратного вызова, чтобы разрешить серверу вызывать методы непосредственно на клиенте.</span><span class="sxs-lookup"><span data-stu-id="f8195-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="f8195-155">потоки gRPC работают по-разному.</span><span class="sxs-lookup"><span data-stu-id="f8195-155">gRPC streams work differently.</span></span> <span data-ttu-id="f8195-156">Клиент проходит по возвращенному потоку и обрабатывает сообщения так, как будто они были возвращены из локального метода, возвращающего `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="f8195-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="f8195-157">`IAsyncStreamReader<T>`Тип работает во многом подобно `IEnumerator<T>` .</span><span class="sxs-lookup"><span data-stu-id="f8195-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="f8195-158">Существует `MoveNext` метод, возвращающий значение true, если есть больше данных, и `Current` свойство, которое возвращает последнее значение.</span><span class="sxs-lookup"><span data-stu-id="f8195-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="f8195-159">Единственное отличие заключается в том, что `MoveNext` метод возвращает, `Task<bool>` а не просто `bool` .</span><span class="sxs-lookup"><span data-stu-id="f8195-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="f8195-160">`ReadAllAsync`Метод расширения создает оболочку для потока в стандартном C# 8 `IAsyncEnumerable` , который можно использовать с новым `await foreach` синтаксисом.</span><span class="sxs-lookup"><span data-stu-id="f8195-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="f8195-161">Для разработчиков, использующих реактивные шаблоны программирования, в разделе, посвященном [клиентским библиотекам](client-libraries.md#iobservable) в конце этой главы, показано, как добавить метод расширения и классы для переноса `IAsyncStreamReader<T>` в `IObservable<T>` .</span><span class="sxs-lookup"><span data-stu-id="f8195-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="f8195-162">Опять же, не забудьте перехватывать исключения из-за возможности сбоя в сети и из-за того <xref:System.OperationCanceledException> , что неизбежно будет вызываться, так как код использует <xref:System.Threading.CancellationToken> для разбиения цикла.</span><span class="sxs-lookup"><span data-stu-id="f8195-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="f8195-163">`RpcException`Тип имеет много полезной информации об ошибках среды выполнения gRPC, включая `StatusCode` .</span><span class="sxs-lookup"><span data-stu-id="f8195-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="f8195-164">Дополнительные сведения см. в разделе [ *Обработка ошибок* в главе 4](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="f8195-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="f8195-165">Двунаправленная потоковая передача</span><span class="sxs-lookup"><span data-stu-id="f8195-165">Bidirectional streaming</span></span>

<span data-ttu-id="f8195-166">Высокодуплексная служба WCF обеспечивает асинхронный обмен сообщениями в режиме реального времени в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="f8195-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="f8195-167">В примере потоковой передачи сервера клиент запускает запрос, а затем получает поток обновлений.</span><span class="sxs-lookup"><span data-stu-id="f8195-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="f8195-168">Более новая версия этой службы позволит клиенту добавлять и удалять акции из списка без необходимости приостанавливаться и создавать новую подписку.</span><span class="sxs-lookup"><span data-stu-id="f8195-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="f8195-169">Эта функциональность реализована в [примере решения фуллстокктиккер](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="f8195-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="f8195-170">`IFullStockTickerService`Интерфейс предоставляет три метода:</span><span class="sxs-lookup"><span data-stu-id="f8195-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="f8195-171">`Subscribe` запускает подключение.</span><span class="sxs-lookup"><span data-stu-id="f8195-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="f8195-172">`AddSymbol` Добавляет символ акции для просмотра.</span><span class="sxs-lookup"><span data-stu-id="f8195-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="f8195-173">`RemoveSymbol` Удаляет символ из наблюдаемого списка.</span><span class="sxs-lookup"><span data-stu-id="f8195-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="f8195-174">Интерфейс обратного вызова остается прежним.</span><span class="sxs-lookup"><span data-stu-id="f8195-174">The callback interface remains the same.</span></span>

<span data-ttu-id="f8195-175">Реализация этого шаблона в gRPC менее проста, так как теперь существует два потока данных с передачей сообщений: от клиента к серверу и от сервера к клиенту.</span><span class="sxs-lookup"><span data-stu-id="f8195-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="f8195-176">Невозможно использовать несколько методов для реализации операций добавления и удаления, но можно передать более одного типа сообщений в одном потоке с помощью `Any` `oneof` ключевого слова Type или, которое было рассмотрено в [главе 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="f8195-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="f8195-177">Если существует конкретный набор допустимых типов, `oneof` лучше всего сделать это.</span><span class="sxs-lookup"><span data-stu-id="f8195-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="f8195-178">Используйте объект `ActionMessage` , который может содержать либо `AddSymbolRequest` `RemoveSymbolRequest` :</span><span class="sxs-lookup"><span data-stu-id="f8195-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="f8195-179">Объявите службу двунаправленной потоковой передачи, которая принимает поток `ActionMessage` сообщений:</span><span class="sxs-lookup"><span data-stu-id="f8195-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="f8195-180">Реализация для этой службы аналогична предыдущему примеру, за исключением того, что первый параметр `Subscribe` метода теперь является `IAsyncStreamReader<ActionMessage>` , который можно использовать для обработки `Add` `Remove` запросов и.</span><span class="sxs-lookup"><span data-stu-id="f8195-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors caused by broken connection, etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="f8195-181">`ActionMessage`Класс, созданный gRPC, гарантирует, что можно установить только одно `Add` из `Remove` свойств и.</span><span class="sxs-lookup"><span data-stu-id="f8195-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="f8195-182">Определить, какой `null` тип сообщения использовать не является допустимым способом, но есть и лучший способ.</span><span class="sxs-lookup"><span data-stu-id="f8195-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="f8195-183">Создание кода также создает `enum ActionOneOfCase` в `ActionMessage` классе, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f8195-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="f8195-184">Свойство `ActionCase` `ActionMessage` объекта может использоваться с `switch` инструкцией для определения того, какое поле задается:</span><span class="sxs-lookup"><span data-stu-id="f8195-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="f8195-185">В `switch` инструкции есть `default` вариант, который регистрирует предупреждение при обнаружении неизвестного `ActionOneOfCase` значения.</span><span class="sxs-lookup"><span data-stu-id="f8195-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="f8195-186">Это может быть полезно для указания того, что клиент использует более позднюю версию файла с `.proto` дополнительными действиями.</span><span class="sxs-lookup"><span data-stu-id="f8195-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="f8195-187">Это одна из причин того, почему использование объекта `switch` лучше, чем тестирование `null` на наличие известных полей.</span><span class="sxs-lookup"><span data-stu-id="f8195-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="f8195-188">Использование Фуллстокктиккерсервице из клиентского приложения</span><span class="sxs-lookup"><span data-stu-id="f8195-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="f8195-189">Существует простое приложение .NET WPF, которое демонстрирует использование этого более сложного клиента.</span><span class="sxs-lookup"><span data-stu-id="f8195-189">There's a simple .NET WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="f8195-190">Полное приложение можно найти на сайте [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="f8195-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="f8195-191">Клиент используется в `MainWindowViewModel` классе, который получает экземпляр `FullStockTicker.FullStockTickerClient` типа из внедрения зависимостей:</span><span class="sxs-lookup"><span data-stu-id="f8195-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="f8195-192">Объект, возвращаемый `client.Subscribe()` методом, теперь является экземпляром типа библиотеки gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>` , который предоставляет `RequestStream` для отправки запросов на сервер и `ResponseStream` для обработки ответов.</span><span class="sxs-lookup"><span data-stu-id="f8195-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="f8195-193">Поток запроса используется из некоторых `ICommand` методов WPF для добавления и удаления символов.</span><span class="sxs-lookup"><span data-stu-id="f8195-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="f8195-194">Для каждой операции задайте соответствующее поле для `ActionMessage` объекта:</span><span class="sxs-lookup"><span data-stu-id="f8195-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="f8195-195">При установке `oneof` значения поля в сообщении автоматически очищаются все поля, которые были заданы ранее.</span><span class="sxs-lookup"><span data-stu-id="f8195-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="f8195-196">Поток ответов обрабатывается в `async` методе.</span><span class="sxs-lookup"><span data-stu-id="f8195-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="f8195-197">`Task`Он возвращается для удаления при закрытии окна:</span><span class="sxs-lookup"><span data-stu-id="f8195-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-cleanup"></a><span data-ttu-id="f8195-198">Очистка клиента</span><span class="sxs-lookup"><span data-stu-id="f8195-198">Client cleanup</span></span>

<span data-ttu-id="f8195-199">Когда окно закрывается и `MainWindowViewModel` удаляется (из `Closed` события `MainWindow` ), рекомендуется правильно ликвидировать `AsyncDuplexStreamingCall` объект.</span><span class="sxs-lookup"><span data-stu-id="f8195-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="f8195-200">В частности, `CompleteAsync` метод `RequestStream` должен вызываться для корректного закрытия потока на сервере.</span><span class="sxs-lookup"><span data-stu-id="f8195-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="f8195-201">В этом примере показан `DisposeAsync` метод из примера модели представления:</span><span class="sxs-lookup"><span data-stu-id="f8195-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="f8195-202">Закрытие потоков запросов позволяет серверу своевременно удалять собственные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="f8195-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="f8195-203">Это повышает эффективность и масштабируемость служб и предотвращает исключения.</span><span class="sxs-lookup"><span data-stu-id="f8195-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f8195-204">[Назад](migrate-request-reply.md)
>[Вперед](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="f8195-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
