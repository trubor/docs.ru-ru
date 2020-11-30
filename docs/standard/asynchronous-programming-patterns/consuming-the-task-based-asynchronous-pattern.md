---
title: Использование асинхронного шаблона, основанного на задачах
description: Узнайте, как использовать асинхронную модель на основе задач при работе с асинхронными операциями.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET and TAP
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 312a86f38335f1c16a4286795f04b9a80a9ea03f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678133"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="97fc4-103">Использование асинхронного шаблона, основанного на задачах</span><span class="sxs-lookup"><span data-stu-id="97fc4-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="97fc4-104">При работе асинхронными операциями с использованием асинхронного шаблона, основанного на задачах, можно использовать обратные вызовы для реализации неблокирующего ожидания.</span><span class="sxs-lookup"><span data-stu-id="97fc4-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span> <span data-ttu-id="97fc4-105">Для задач это достигается с помощью таких методов, как <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97fc4-106">Поддержка асинхронных операций на основе языка скрывает обратные вызовы, разрешая асинхронным операциям находиться в режиме ожидания в нормальном потоке управления, а код, созданный компилятором, предоставляет поддержку на том же уровне API.</span><span class="sxs-lookup"><span data-stu-id="97fc4-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="97fc4-107">Приостановление выполнения с помощью Await</span><span class="sxs-lookup"><span data-stu-id="97fc4-107">Suspending Execution with Await</span></span>

<span data-ttu-id="97fc4-108">Для асинхронного ожидания объектов <xref:System.Threading.Tasks.Task> и <xref:System.Threading.Tasks.Task%601> можно использовать ключевое слово [await](../../csharp/language-reference/operators/await.md) (в C#) и [оператор Await](../../visual-basic/language-reference/operators/await-operator.md) (в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="97fc4-108">You can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="97fc4-109">Когда вы ожидаете <xref:System.Threading.Tasks.Task>, выражение `await` имеет тип `void`.</span><span class="sxs-lookup"><span data-stu-id="97fc4-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="97fc4-110">Когда вы ожидаете <xref:System.Threading.Tasks.Task%601>, выражение `await` имеет тип `TResult`.</span><span class="sxs-lookup"><span data-stu-id="97fc4-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="97fc4-111">Выражение `await` должно находиться в теле асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="97fc4-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="97fc4-112">(Эти возможности языка были представлены в .NET Framework 4.5.)</span><span class="sxs-lookup"><span data-stu-id="97fc4-112">(These language features were introduced in .NET Framework 4.5.)</span></span>

 <span data-ttu-id="97fc4-113">На самом деле функция ожидания реализуется с помощью установки обратного вызова для задачи с помощью продолжения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="97fc4-114">Этот обратный вызов возобновляет асинхронный методы в точке остановки.</span><span class="sxs-lookup"><span data-stu-id="97fc4-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="97fc4-115">При возобновлении асинхронного метода, если ожидаемая операция была завершена успешно и имела тип <xref:System.Threading.Tasks.Task%601>, возвращается ее значение `TResult`.</span><span class="sxs-lookup"><span data-stu-id="97fc4-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="97fc4-116">Если ожидаемая операция <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> завершилась с состоянием <xref:System.Threading.Tasks.TaskStatus.Canceled>, создается исключение <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="97fc4-117">Если ожидаемая операция <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> завершилась с состоянием <xref:System.Threading.Tasks.TaskStatus.Faulted>, создается вызвавшее эту проблему исключение.</span><span class="sxs-lookup"><span data-stu-id="97fc4-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="97fc4-118">`Task` может завершиться с ошибкой из-за нескольких исключений, но распространяется только одно из этих исключений.</span><span class="sxs-lookup"><span data-stu-id="97fc4-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="97fc4-119">Тем не менее, свойство <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> возвращает исключение <xref:System.AggregateException> с полным списком ошибок.</span><span class="sxs-lookup"><span data-stu-id="97fc4-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="97fc4-120">Если контекст синхронизации (объект <xref:System.Threading.SynchronizationContext>) связан с потоком, который во время приостановки выполнял асинхронный метод (например, если свойство <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> имеет значение, отличное от `null`), асинхронный метод возобновляется в том же контексте синхронизации, для чего вызывается метод <xref:System.Threading.SynchronizationContext.Post%2A> этого контекста.</span><span class="sxs-lookup"><span data-stu-id="97fc4-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="97fc4-121">В противном случае он полагается на планировщик задач (объект <xref:System.Threading.Tasks.TaskScheduler>), который использовался в момент приостановки.</span><span class="sxs-lookup"><span data-stu-id="97fc4-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="97fc4-122">Обычно это планировщик по умолчанию (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), который нацелен на пул потоков.</span><span class="sxs-lookup"><span data-stu-id="97fc4-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="97fc4-123">Этот планировщик задач определяет, следует ли возобновить приостановленную асинхронную операцию в тот момент, в который она была завершена, или следует ли запланировать возобновление.</span><span class="sxs-lookup"><span data-stu-id="97fc4-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="97fc4-124">Планировщик по умолчанию обычно разрешает продолжение выполнения в потоке, который был завершен операцией.</span><span class="sxs-lookup"><span data-stu-id="97fc4-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="97fc4-125">При вызове асинхронного метода он синхронно выполняет тело функции до первого выражения await для ожидаемого экземпляра, которое еще не было завершено, и в этот момент управление передается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="97fc4-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="97fc4-126">Если асинхронный метод не возвращает `void`, в качестве представления текущего вычисления возвращается объект <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="97fc4-127">В асинхронном методе, который возвращает значение, отличное от void, при обнаружении выражения return или при достижении окончания метода задача завершается в конечном состоянии <xref:System.Threading.Tasks.TaskStatus.RanToCompletion>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="97fc4-128">Если асинхронный метод теряет управление из-за необработанного исключения, задача завершается в состоянии <xref:System.Threading.Tasks.TaskStatus.Faulted>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="97fc4-129">Если же это исключение является <xref:System.OperationCanceledException>, задача завершается в состоянии <xref:System.Threading.Tasks.TaskStatus.Canceled>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="97fc4-130">Таким образом, результат или исключение в конечном счете будут сформированы.</span><span class="sxs-lookup"><span data-stu-id="97fc4-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="97fc4-131">Существует несколько важных вариантов такого поведения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="97fc4-132">Для повышения производительности, если к моменту ожидания задачи оказывается, что задача уже завершена, то управление не освобождается и функция продолжает выполнение.</span><span class="sxs-lookup"><span data-stu-id="97fc4-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="97fc4-133">Кроме того, возврат к исходному контексту не всегда желателен, и такое поведение можно изменить. Подробное описание приведено в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="97fc4-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="97fc4-134">Настройка приостановки и возобновления с помощью Yield и ConfigureAwait</span><span class="sxs-lookup"><span data-stu-id="97fc4-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>

 <span data-ttu-id="97fc4-135">Существуют методы, которые позволяют получить больший контроль над выполнением асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="97fc4-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="97fc4-136">Например, вы можете использовать метод <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> для внедрения точки приостановки в асинхронный метод:</span><span class="sxs-lookup"><span data-stu-id="97fc4-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="97fc4-137">Это аналогично асинхронному размещению или планированию возврата в текущий контекст.</span><span class="sxs-lookup"><span data-stu-id="97fc4-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="97fc4-138">Также можно использовать метод <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> для более точного контроля над приостановкой и возобновлением в асинхронном методе.</span><span class="sxs-lookup"><span data-stu-id="97fc4-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="97fc4-139">Как упоминалось ранее, по умолчанию текущий контекст записывается в момент приостановки асинхронного метода и используется для вызова продолжения асинхронного метода при возобновлении.</span><span class="sxs-lookup"><span data-stu-id="97fc4-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="97fc4-140">Во многих случаях это именно то поведение, к которому вы стремитесь.</span><span class="sxs-lookup"><span data-stu-id="97fc4-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="97fc4-141">В других случаях можно не заботиться о контексте продолжения. Для повышения производительности нужно избегать подобного размещения обратно в исходный контекст.</span><span class="sxs-lookup"><span data-stu-id="97fc4-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="97fc4-142">Для этого воспользуйтесь методом <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType>, чтобы сообщить операции await о том, что перехватывать и возобновлять контекст не нужно, и вместо этого необходимо продолжить выполнение в той точке, в которой завершилась ожидаемая асинхронная операция.</span><span class="sxs-lookup"><span data-stu-id="97fc4-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="97fc4-143">Отмена асинхронной операции</span><span class="sxs-lookup"><span data-stu-id="97fc4-143">Canceling an Asynchronous Operation</span></span>

<span data-ttu-id="97fc4-144">Начиная с .NET Framework 4, методы TAP, которые поддерживают отмену, предоставляют по крайней мере одну перегрузку, которая принимает токен отмены (объект <xref:System.Threading.CancellationToken>).</span><span class="sxs-lookup"><span data-stu-id="97fc4-144">Starting with .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="97fc4-145">Маркер отмены создается с помощью источника маркеров отмены (объект <xref:System.Threading.CancellationTokenSource>).</span><span class="sxs-lookup"><span data-stu-id="97fc4-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="97fc4-146">Свойство <xref:System.Threading.CancellationTokenSource.Token%2A> источника возвращает маркер отмены, который будет передаваться при вызове метода <xref:System.Threading.CancellationTokenSource.Cancel%2A> источника.</span><span class="sxs-lookup"><span data-stu-id="97fc4-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="97fc4-147">Например, если вы хотите скачать одну веб-страницу и при этом иметь возможность отменить операцию, создайте объект <xref:System.Threading.CancellationTokenSource>, передайте его маркер методу TAP и вызовите метод источника <xref:System.Threading.CancellationTokenSource.Cancel%2A>, когда нужно будет отменить операцию.</span><span class="sxs-lookup"><span data-stu-id="97fc4-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="97fc4-148">Чтобы отменить несколько асинхронных вызовов, можно передать один и тот же маркер всем вызовам.</span><span class="sxs-lookup"><span data-stu-id="97fc4-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="97fc4-149">Также можно передать один и тот же маркер выбранному подмножеству операций.</span><span class="sxs-lookup"><span data-stu-id="97fc4-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="97fc4-150">Запрос на отмену может быть запущен из любого потока.</span><span class="sxs-lookup"><span data-stu-id="97fc4-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="97fc4-151">Значение <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> можно передать любому методу, который принимает маркер отмены. Это будет означать, что отмена никогда не будет запрашиваться.</span><span class="sxs-lookup"><span data-stu-id="97fc4-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="97fc4-152">В результате свойство <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> будет возвращать `false`, и вызываемый метод сможет принять меры для оптимизации.</span><span class="sxs-lookup"><span data-stu-id="97fc4-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="97fc4-153">Для тестирования также можно передать маркер отмены, для которого уже была выполнена отмена. Этот маркер инициализируется с помощью конструктора, который принимает логическое значение, означающее, следует ли запустить маркер в уже отмененном или неотменяемом состоянии.</span><span class="sxs-lookup"><span data-stu-id="97fc4-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="97fc4-154">У такого подхода к отмене есть несколько преимуществ.</span><span class="sxs-lookup"><span data-stu-id="97fc4-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="97fc4-155">Один и тот же маркер отмены можно передать в любое количество асинхронных и синхронных операций.</span><span class="sxs-lookup"><span data-stu-id="97fc4-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="97fc4-156">Один и тот же запрос отмены можно распространить на любое количество прослушивателей.</span><span class="sxs-lookup"><span data-stu-id="97fc4-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="97fc4-157">Разработчик асинхронного интерфейса API имеет полный контроль над тем, можно ли разрешить запрос отмены и когда ее можно применить.</span><span class="sxs-lookup"><span data-stu-id="97fc4-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="97fc4-158">Код, который использует этот интерфейс API, может выборочно определять асинхронные вызовы, на которые будут распространены запросы отмены.</span><span class="sxs-lookup"><span data-stu-id="97fc4-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="97fc4-159">Наблюдение за ходом выполнения</span><span class="sxs-lookup"><span data-stu-id="97fc4-159">Monitoring Progress</span></span>

 <span data-ttu-id="97fc4-160">Некоторые асинхронные методы предоставляют сведения о ходе выполнения с помощью интерфейса хода выполнения, который передается в асинхронный метод.</span><span class="sxs-lookup"><span data-stu-id="97fc4-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="97fc4-161">Например, рассмотрим функцию, которая асинхронно скачивает строку текста, одновременно обновляя сведения о ходе скачивания, которые включают долю уже скачанной части строки в процентах ко всей строке.</span><span class="sxs-lookup"><span data-stu-id="97fc4-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="97fc4-162">Этот метод можно использовать в приложении WPF следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97fc4-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>

## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="97fc4-163">Использование внутренних блоков объединения задач</span><span class="sxs-lookup"><span data-stu-id="97fc4-163">Using the Built-in Task-based Combinators</span></span>

 <span data-ttu-id="97fc4-164">В пространстве имен <xref:System.Threading.Tasks> предусмотрено несколько способов объединять задачи и работать с ними.</span><span class="sxs-lookup"><span data-stu-id="97fc4-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="97fc4-165">Task.Run</span><span class="sxs-lookup"><span data-stu-id="97fc4-165">Task.Run</span></span>

 <span data-ttu-id="97fc4-166">Класс <xref:System.Threading.Tasks.Task> содержит несколько методов <xref:System.Threading.Tasks.Task.Run%2A>, которые позволяют легко разгрузить задачи в формате <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601> в пул потоков, например так:</span><span class="sxs-lookup"><span data-stu-id="97fc4-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="97fc4-167">Некоторые из этих методов <xref:System.Threading.Tasks.Task.Run%2A>, например перегрузка <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, являются ссылкой на метод <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="97fc4-168">Другие перегрузки, например <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, позволяют использовать await в разгруженных задачах, например так:</span><span class="sxs-lookup"><span data-stu-id="97fc4-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="97fc4-169">Эти перегрузки логически эквивалентны вызову метода <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> в сочетании с методом расширения <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>из библиотеки параллельных задач.</span><span class="sxs-lookup"><span data-stu-id="97fc4-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="97fc4-170">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="97fc4-170">Task.FromResult</span></span>

 <span data-ttu-id="97fc4-171">Используйте метод <xref:System.Threading.Tasks.Task.FromResult%2A> в ситуациях, когда данные уже могут быть доступны и их достаточно возвратить в <xref:System.Threading.Tasks.Task%601> из метода, возвращающего задачу.</span><span class="sxs-lookup"><span data-stu-id="97fc4-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="97fc4-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="97fc4-172">Task.WhenAll</span></span>

 <span data-ttu-id="97fc4-173">Используйте метод <xref:System.Threading.Tasks.Task.WhenAll%2A> для асинхронного ожидания нескольких асинхронных операций, которые представлены в виде задач.</span><span class="sxs-lookup"><span data-stu-id="97fc4-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="97fc4-174">У этого метода есть несколько перегрузок, которые поддерживают набор неуниверсальных задач или неоднородный набор универсальных задач (например, асинхронное ожидание нескольких операций, возвращающих void, или асинхронное ожидание несколько методов, возвращающих значение (при этом эти значения могут быть разных типов)), а также поддерживают единый набор универсальных задач (например, асинхронное ожидание нескольких методов, которые возвращают `TResult`).</span><span class="sxs-lookup"><span data-stu-id="97fc4-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="97fc4-175">Предположим, что вы хотите отправить сообщения по электронной почте нескольким клиентам.</span><span class="sxs-lookup"><span data-stu-id="97fc4-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="97fc4-176">Отправку сообщений можно перекрывать, чтобы не ожидать завершения отправки одного сообщения перед отправкой следующего.</span><span class="sxs-lookup"><span data-stu-id="97fc4-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="97fc4-177">Также можно узнать, были ли выполнены операции отправки и возникли ли ошибки.</span><span class="sxs-lookup"><span data-stu-id="97fc4-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="97fc4-178">Этот код не обрабатывает возможные исключения явным образом, но позволяет им распространяться из метода `await` на задачу, полученную от <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="97fc4-179">Для обработки исключений можно использовать следующий код.</span><span class="sxs-lookup"><span data-stu-id="97fc4-179">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="97fc4-180">В этом случае при сбое любой асинхронной операции все исключения объединяются в одно исключение <xref:System.AggregateException>, которое сохраняется в <xref:System.Threading.Tasks.Task>, возвращаемом из метода <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="97fc4-181">Однако с помощью ключевого слова `await` распространяется только одно из этих исключений.</span><span class="sxs-lookup"><span data-stu-id="97fc4-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="97fc4-182">Если вы хотите изучить все исключения, можно переписать предыдущий код следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97fc4-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="97fc4-183">Рассмотрим в качестве примера асинхронную загрузку нескольких файлов из Интернета.</span><span class="sxs-lookup"><span data-stu-id="97fc4-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="97fc4-184">В этом случае все асинхронные операции имеют результаты одного типа, и к этим результатам легко получить доступ.</span><span class="sxs-lookup"><span data-stu-id="97fc4-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="97fc4-185">Можно использовать те же способы обработки исключений, которые были рассмотрены в предыдущем сценарии с возвратом void.</span><span class="sxs-lookup"><span data-stu-id="97fc4-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="97fc4-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="97fc4-186">Task.WhenAny</span></span>

 <span data-ttu-id="97fc4-187">Используйте метод <xref:System.Threading.Tasks.Task.WhenAny%2A> для асинхронного ожидания завершения одной из нескольких асинхронных операций, которые представлены в виде задач.</span><span class="sxs-lookup"><span data-stu-id="97fc4-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="97fc4-188">Этот метод допускает четыре основных варианта использования.</span><span class="sxs-lookup"><span data-stu-id="97fc4-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="97fc4-189">Избыточность:  многократный запуск одной операции и выбор первой завершенной операции (например, обращение к нескольким веб-сервисам котировок акций с целью получить один результат и выбор операции, которая завершилась первой).</span><span class="sxs-lookup"><span data-stu-id="97fc4-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="97fc4-190">Чередование:  запуск и ожидание завершения нескольких операций, но обработка операций по мере выполнения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="97fc4-191">Регулирование:  добавление новых операций по мере завершения предыдущих.</span><span class="sxs-lookup"><span data-stu-id="97fc4-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="97fc4-192">Это расширение сценария с чередованием.</span><span class="sxs-lookup"><span data-stu-id="97fc4-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="97fc4-193">Ранняя остановка:  например, операция, представленная задачей t1, может сгруппироваться в задачу <xref:System.Threading.Tasks.Task.WhenAny%2A> с другой задачей t2, после чего можно ожидать задачу <xref:System.Threading.Tasks.Task.WhenAny%2A>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="97fc4-194">Например, задача t2 может представлять завершение ожидания, отмену или другой сигнал, требующий завершения задачи <xref:System.Threading.Tasks.Task.WhenAny%2A> до завершения задачи t1.</span><span class="sxs-lookup"><span data-stu-id="97fc4-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="97fc4-195">Избыточность</span><span class="sxs-lookup"><span data-stu-id="97fc4-195">Redundancy</span></span>

 <span data-ttu-id="97fc4-196">Рассмотрим случай, когда вам требуется принять решение о необходимости покупки акций.</span><span class="sxs-lookup"><span data-stu-id="97fc4-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="97fc4-197">Существует несколько стандартных веб-служб с рекомендациями по покупке акций, которым вы доверяете, но в зависимости от ежедневной нагрузки каждая из этих служб иногда может работать медленно.</span><span class="sxs-lookup"><span data-stu-id="97fc4-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="97fc4-198">Для получения уведомлений о завершении любой операции можно использовать метод <xref:System.Threading.Tasks.Task.WhenAny%2A>:</span><span class="sxs-lookup"><span data-stu-id="97fc4-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="97fc4-199">В отличие от <xref:System.Threading.Tasks.Task.WhenAll%2A>, который возвращает распакованные результаты всех успешно выполненных задач, <xref:System.Threading.Tasks.Task.WhenAny%2A> возвращает завершенную задачу.</span><span class="sxs-lookup"><span data-stu-id="97fc4-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="97fc4-200">Если задача завершилась сбоем, важно знать, что она завершилась сбоем, а если она завершилась успешно, важно знать, с какой задачей связано возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="97fc4-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="97fc4-201">Поэтому необходимо получить доступ к результату, возвращаемому задачей, или продолжить ожидание, как показано в данном примере.</span><span class="sxs-lookup"><span data-stu-id="97fc4-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="97fc4-202">Как и в случае с <xref:System.Threading.Tasks.Task.WhenAll%2A>, необходимо поддерживать исключения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="97fc4-203">Так как вы получаете управление от завершенной задачи, вы можете подождать, пока не будут распространены ошибки для возвращенной задачи и `try/catch` их соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="97fc4-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="97fc4-204">Кроме того, даже если первая задача завершается успешно, следующие задачи могут завершиться сбоем.</span><span class="sxs-lookup"><span data-stu-id="97fc4-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="97fc4-205">В этом случае есть несколько вариантов обработки исключений:  можно ждать, пока не завершатся все задачи, используя метод <xref:System.Threading.Tasks.Task.WhenAll%2A>, или решить, что все исключения важны и должны быть записаны в журнал.</span><span class="sxs-lookup"><span data-stu-id="97fc4-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="97fc4-206">В этом случае используется продолжение для получения уведомлений об успешном завершении задач.</span><span class="sxs-lookup"><span data-stu-id="97fc4-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="97fc4-207">или</span><span class="sxs-lookup"><span data-stu-id="97fc4-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="97fc4-208">или даже:</span><span class="sxs-lookup"><span data-stu-id="97fc4-208">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="97fc4-209">Наконец, вы можете отменить все остальные операции.</span><span class="sxs-lookup"><span data-stu-id="97fc4-209">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="97fc4-210">Чередование</span><span class="sxs-lookup"><span data-stu-id="97fc4-210">Interleaving</span></span>

 <span data-ttu-id="97fc4-211">Рассмотрим ситуацию, в которой вы загружаете изображения из Интернета и обрабатываете каждое изображение (например, добавляете изображение в элемент управления пользовательского интерфейса).</span><span class="sxs-lookup"><span data-stu-id="97fc4-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="97fc4-212">Обработка изображений выполняется последовательно в потоке пользовательского интерфейса, но скачивать их следует по возможности параллельно.</span><span class="sxs-lookup"><span data-stu-id="97fc4-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="97fc4-213">Кроме того, для добавления изображений в пользовательский интерфейс не стоит ждать, пока все они будут скачаны.</span><span class="sxs-lookup"><span data-stu-id="97fc4-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="97fc4-214">Вместо этого лучше добавлять каждое изображение после его скачивания.</span><span class="sxs-lookup"><span data-stu-id="97fc4-214">Instead, you want to add them as they complete.</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="97fc4-215">Также вы можете применить чередование к сценарию, который подразумевает интенсивную вычислительную обработку пула загруженных изображений <xref:System.Threading.ThreadPool>, например так:</span><span class="sxs-lookup"><span data-stu-id="97fc4-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="97fc4-216">Регулирование</span><span class="sxs-lookup"><span data-stu-id="97fc4-216">Throttling</span></span>

 <span data-ttu-id="97fc4-217">Рассмотрим пример с чередованием с тем исключением, что на этот раз пользователь загружает так много изображений, что загрузку необходимо регулировать; например, вы можете ограничить максимальное количество параллельных загрузок.</span><span class="sxs-lookup"><span data-stu-id="97fc4-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="97fc4-218">Для этого можно запустить подмножество асинхронных операций.</span><span class="sxs-lookup"><span data-stu-id="97fc4-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="97fc4-219">По завершении операций можно запускать дополнительные операции, которые займут их место.</span><span class="sxs-lookup"><span data-stu-id="97fc4-219">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="97fc4-220">Ранняя остановка</span><span class="sxs-lookup"><span data-stu-id="97fc4-220">Early Bailout</span></span>

 <span data-ttu-id="97fc4-221">Рассмотрим, что вы асинхронно ожидаете завершения операции и одновременно отвечаете на запрос отмены пользователя (например, если пользователь нажал кнопку "Отмена").</span><span class="sxs-lookup"><span data-stu-id="97fc4-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="97fc4-222">Этот сценарий иллюстрируется в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="97fc4-222">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="97fc4-223">В этой реализации сразу же после отмены загрузки отображается пользовательский интерфейс, но базовые асинхронные операции не отменяются.</span><span class="sxs-lookup"><span data-stu-id="97fc4-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="97fc4-224">В качестве альтернативы можно отменить ожидающие операции после отмены скачивания, но не отображать пользовательский интерфейс, пока операции на самом деле не завершатся (возможно, из-за раннего завершения, вызванного запросом отмены).</span><span class="sxs-lookup"><span data-stu-id="97fc4-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="97fc4-225">Еще один пример ранней остановки предполагает использование метода <xref:System.Threading.Tasks.Task.WhenAny%2A> в сочетании с методом <xref:System.Threading.Tasks.Task.Delay%2A>, как описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="97fc4-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="97fc4-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="97fc4-226">Task.Delay</span></span>

 <span data-ttu-id="97fc4-227">Метод <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> позволяет приостановить выполнение асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="97fc4-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="97fc4-228">Это удобно для реализации различных функций, включая создание циклов опроса и задержку обработки ввода пользователя на заданный период времени.</span><span class="sxs-lookup"><span data-stu-id="97fc4-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="97fc4-229">Метод <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> также можно использовать в сочетании с <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> для ограничения времени ожидания await.</span><span class="sxs-lookup"><span data-stu-id="97fc4-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="97fc4-230">Если на выполнение задачи, которая является частью большой асинхронной операции (например, веб-служба ASP.NET), требуется слишком много времени, то это может негативно сказаться на всей операции, особенно если это приведет к неудачному завершению операции.</span><span class="sxs-lookup"><span data-stu-id="97fc4-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="97fc4-231">Поэтому важно иметь возможность задавать время ожидания для асинхронных операций.</span><span class="sxs-lookup"><span data-stu-id="97fc4-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="97fc4-232">Синхронные методы <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> принимают значения времени ожидания, а соответствующий метод <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> и ранее упомянутый <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> — нет.</span><span class="sxs-lookup"><span data-stu-id="97fc4-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="97fc4-233">Вместо этого вы можете совместно использовать <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> для ограничения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="97fc4-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="97fc4-234">Например, предположим, что вы хотите загрузить приложение и отключить пользовательский интерфейс на время загрузки.</span><span class="sxs-lookup"><span data-stu-id="97fc4-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="97fc4-235">Однако если загрузка занимает слишком много времени, вы можете отменить загрузку и вернуться в пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="97fc4-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="97fc4-236">Это же применимо и скачиванию нескольких файлов, так как <xref:System.Threading.Tasks.Task.WhenAll%2A> возвращает задачу:</span><span class="sxs-lookup"><span data-stu-id="97fc4-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads.Result) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="97fc4-237">Создание блоков объединения на основе задач</span><span class="sxs-lookup"><span data-stu-id="97fc4-237">Building Task-based Combinators</span></span>

 <span data-ttu-id="97fc4-238">Поскольку задача может полностью представлять асинхронную операцию и предоставляет синхронные и асинхронные функции для соединения с операцией, получения ее результатов и т. д., то вы можете создавать полезные библиотеки блоков объединения, которые объединяют задачи для создания шаблонов большего размера.</span><span class="sxs-lookup"><span data-stu-id="97fc4-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span> <span data-ttu-id="97fc4-239">Как уже обсуждалось в предыдущем разделе, в .NET есть несколько встроенных блоков объединения, но вы можете создать и собственные.</span><span class="sxs-lookup"><span data-stu-id="97fc4-239">As discussed in the previous section, .NET includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="97fc4-240">В следующих разделах приведено несколько примеров возможных методов и типов блоков объединения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="97fc4-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="97fc4-241">RetryOnFault</span></span>

 <span data-ttu-id="97fc4-242">Во многих ситуациях может потребоваться повторить операцию, если предыдущая попытка завершилась неудачно.</span><span class="sxs-lookup"><span data-stu-id="97fc4-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="97fc4-243">Для решения этой задачи в синхронном коде можно использовать вспомогательный метод, например `RetryOnFault` в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97fc4-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="97fc4-244">Вы можете создать почти такой же вспомогательный метод для асинхронных операций, которые реализованы в TAP и таким образом вернуть задачи.</span><span class="sxs-lookup"><span data-stu-id="97fc4-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="97fc4-245">Этот блок объединения также можно использовать для анализа повторных попыток в логике приложения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="97fc4-246">Функцию `RetryOnFault` можно улучшить.</span><span class="sxs-lookup"><span data-stu-id="97fc4-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="97fc4-247">Например, функция может принимать другой `Func<Task>`, который будет вызываться между повторными попытками, чтобы определить, когда операцию нужно повторить.</span><span class="sxs-lookup"><span data-stu-id="97fc4-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="97fc4-248">Чтобы подождать одну секунду перед повтором операции, эту функцию можно использовать следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97fc4-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="97fc4-249">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="97fc4-249">NeedOnlyOne</span></span>

 <span data-ttu-id="97fc4-250">В некоторых случаях для повышения задержки и вероятности успешного завершения операции можно воспользоваться преимуществами избыточности.</span><span class="sxs-lookup"><span data-stu-id="97fc4-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="97fc4-251">Рассмотрим несколько веб-служб, которые предоставляют котировки акций в разное время дня, и каждая служба обеспечивает различный уровень качества и время отклика.</span><span class="sxs-lookup"><span data-stu-id="97fc4-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="97fc4-252">Чтобы справиться с неравномерным характером поступления данных, вы можете отправлять запросы ко всем веб-службам и при получении ответа от одной из веб-служб отменять оставшиеся запросы.</span><span class="sxs-lookup"><span data-stu-id="97fc4-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="97fc4-253">Вы можете реализовать вспомогательную функцию для более удобной реализации этого распространенного шаблона с запуском нескольких операций, ожидания завершения любой операции и последующей отмены остальных.</span><span class="sxs-lookup"><span data-stu-id="97fc4-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="97fc4-254">Функция `NeedOnlyOne` в следующем примере иллюстрирует этот сценарий.</span><span class="sxs-lookup"><span data-stu-id="97fc4-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="97fc4-255">Затем можно использовать эту функцию следующим образом.</span><span class="sxs-lookup"><span data-stu-id="97fc4-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="97fc4-256">Операции с чередованием</span><span class="sxs-lookup"><span data-stu-id="97fc4-256">Interleaved Operations</span></span>

 <span data-ttu-id="97fc4-257">При использовании метода <xref:System.Threading.Tasks.Task.WhenAny%2A> для поддержки сценария чередования при работе с большими наборами задач существует потенциальная проблема производительности.</span><span class="sxs-lookup"><span data-stu-id="97fc4-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="97fc4-258">Каждый вызов <xref:System.Threading.Tasks.Task.WhenAny%2A> приводит к регистрации продолжения в каждой задаче.</span><span class="sxs-lookup"><span data-stu-id="97fc4-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="97fc4-259">Для N задач это приводит к созданию O(N<sup>2</sup>) продолжений в течение времени существования операции чередования.</span><span class="sxs-lookup"><span data-stu-id="97fc4-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="97fc4-260">При работе с большим набором задач можно использовать комбинатор (`Interleaved` в следующем примере), чтобы решить проблему производительности:</span><span class="sxs-lookup"><span data-stu-id="97fc4-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="97fc4-261">Затем с помощью блоков объединения можно объединять результаты задач по мере их завершения.</span><span class="sxs-lookup"><span data-stu-id="97fc4-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="97fc4-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="97fc4-262">WhenAllOrFirstException</span></span>

 <span data-ttu-id="97fc4-263">В некоторых сценариях распределения и объединения вы можете ожидать, пока одна из задач в наборе не завершится сбоем, в этом случае ожидание прекращается, так как выдается исключение.</span><span class="sxs-lookup"><span data-stu-id="97fc4-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="97fc4-264">Для этого можно использовать такой блок объединения как `WhenAllOrFirstException`, как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="97fc4-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="97fc4-265">Создание структур данных на основе задач</span><span class="sxs-lookup"><span data-stu-id="97fc4-265">Building Task-based Data Structures</span></span>

 <span data-ttu-id="97fc4-266">Кроме возможности создавать блоки объединения на основе задач, <xref:System.Threading.Tasks.Task> и <xref:System.Threading.Tasks.Task%601> имеют структуру данных, которая представляет результаты асинхронной операции и необходимую синхронизацию для объединения, что делает их эффективным инструментом для создания пользовательских структур данных для асинхронных сценариев.</span><span class="sxs-lookup"><span data-stu-id="97fc4-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="97fc4-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="97fc4-267">AsyncCache</span></span>

 <span data-ttu-id="97fc4-268">Одним из важных аспектов задачи является то, что ее можно передать нескольким потребителям, каждый из которых может ожидать ее, регистрировать продолжения для этой задачи, получать ее результат или исключения (для <xref:System.Threading.Tasks.Task%601>) и т. д.</span><span class="sxs-lookup"><span data-stu-id="97fc4-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="97fc4-269">Благодаря этому <xref:System.Threading.Tasks.Task> и <xref:System.Threading.Tasks.Task%601> идеально подходят для асинхронной инфраструктуры кэширования.</span><span class="sxs-lookup"><span data-stu-id="97fc4-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="97fc4-270">Ниже приведен пример небольшого, но мощного асинхронного кэша, созданного на основе <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="97fc4-271">Класс [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) в качестве делегата своего конструктора принимает функцию, которая принимает `TKey` и возвращает <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="97fc4-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="97fc4-272">Ранее запрошенные из кэша значения хранятся во внутреннем словаре, и `AsyncCache` гарантирует, что для одного ключа создается только одна задача, даже при одновременном доступе к кэшу.</span><span class="sxs-lookup"><span data-stu-id="97fc4-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="97fc4-273">Например, можно создать кэш для загруженных веб-страниц.</span><span class="sxs-lookup"><span data-stu-id="97fc4-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="97fc4-274">Затем можно использовать этот кэш в асинхронных методах каждый раз, когда вам потребуется содержимое какой-либо веб-страницы.</span><span class="sxs-lookup"><span data-stu-id="97fc4-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="97fc4-275">Класс `AsyncCache` гарантирует, что будет скачано минимальное число страниц, и кэширует результаты.</span><span class="sxs-lookup"><span data-stu-id="97fc4-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="97fc4-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="97fc4-276">AsyncProducerConsumerCollection</span></span>

 <span data-ttu-id="97fc4-277">Задачи также можно использовать для создания структур данных для координации асинхронных действий.</span><span class="sxs-lookup"><span data-stu-id="97fc4-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="97fc4-278">Рассмотрим один из классических шаблонов параллельных систем: производитель/потребитель.</span><span class="sxs-lookup"><span data-stu-id="97fc4-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="97fc4-279">В этой схеме производители создают данные, которые используются потребителями и производители и потребители могут работать параллельно.</span><span class="sxs-lookup"><span data-stu-id="97fc4-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="97fc4-280">Например, потребитель обрабатывает элемент 1, который ранее был создан производителем, который в это же время создает элемент 2.</span><span class="sxs-lookup"><span data-stu-id="97fc4-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="97fc4-281">Для схемы "производитель/потребитель" в любом случае потребуется некоторая структура данных, в которой будут храниться объекты, создаваемые производителем. Эта структура необходима для того, чтобы потребитель мог узнать о новых данных и получить их, когда они будут доступны.</span><span class="sxs-lookup"><span data-stu-id="97fc4-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="97fc4-282">Вот простая структура данных на основе задач, которая позволяет использовать асинхронные методы в качестве производителей и потребителей.</span><span class="sxs-lookup"><span data-stu-id="97fc4-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="97fc4-283">С этой структурой данных на месте можно написать следующий код.</span><span class="sxs-lookup"><span data-stu-id="97fc4-283">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="97fc4-284">Пространство имен <xref:System.Threading.Tasks.Dataflow> включает также тип <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>, который можно использовать аналогичным образом, но не создавая пользовательский тип коллекции:</span><span class="sxs-lookup"><span data-stu-id="97fc4-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="97fc4-285">Пространство имен <xref:System.Threading.Tasks.Dataflow> доступно в виде пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="97fc4-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available as a NuGet package.</span></span> <span data-ttu-id="97fc4-286">Чтобы установить сборку, которая содержит пространство имен <xref:System.Threading.Tasks.Dataflow>, откройте проект в Visual Studio, в меню "Проект" выберите пункт **Управление пакетами NuGet** и найдите в Интернете пакет `System.Threading.Tasks.Dataflow`.</span><span class="sxs-lookup"><span data-stu-id="97fc4-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the `System.Threading.Tasks.Dataflow` package.</span></span>

## <a name="see-also"></a><span data-ttu-id="97fc4-287">См. также</span><span class="sxs-lookup"><span data-stu-id="97fc4-287">See also</span></span>

- <span data-ttu-id="97fc4-288">[Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md) (Асинхронный шаблон, основанный на задачах (TAP))</span><span class="sxs-lookup"><span data-stu-id="97fc4-288">[Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md)</span></span>
- [<span data-ttu-id="97fc4-289">Реализация асинхронной модели на основе задач</span><span class="sxs-lookup"><span data-stu-id="97fc4-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="97fc4-290">Взаимодействие с другими асинхронными шаблонами и типами</span><span class="sxs-lookup"><span data-stu-id="97fc4-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
