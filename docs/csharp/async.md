---
title: Асинхронное программирование на C#
description: Сведения о модели асинхронного программирования на уровне языка C#, которая реализуется в .NET Core.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: bb333e5eb5dfadb1ff7a1fac64627b74bca8d981
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637264"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="88871-103">Асинхронное программирование</span><span class="sxs-lookup"><span data-stu-id="88871-103">Asynchronous programming</span></span>

<span data-ttu-id="88871-104">Для решения задач, связанных с вводом-выводом (например, запрос данных из сети, доступ к базе данных или чтение и запись в файловой системе), желательно использовать асинхронное программирование.</span><span class="sxs-lookup"><span data-stu-id="88871-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="88871-105">Если у вас есть код, ограниченный ресурсами процессора, например выполняющий сложные вычисления, то это также подходящий сценарий для асинхронного программирования.</span><span class="sxs-lookup"><span data-stu-id="88871-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="88871-106">В C# есть модель асинхронного программирования, реализованная на уровне языка, которая позволяет легко писать асинхронный код, не прибегая к обратным вызовам или библиотекам, которые поддерживают асинхронность.</span><span class="sxs-lookup"><span data-stu-id="88871-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="88871-107">Она строится на принципах [асинхронной модели на основе задач (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="88871-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="88871-108">Обзор асинхронной модели</span><span class="sxs-lookup"><span data-stu-id="88871-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="88871-109">В основе асинхронного программирования лежат объекты `Task` и `Task<T>`, которые моделируют асинхронные операции.</span><span class="sxs-lookup"><span data-stu-id="88871-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="88871-110">Они поддерживаются ключевыми словами `async` и `await`.</span><span class="sxs-lookup"><span data-stu-id="88871-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="88871-111">В большинстве случаев модель достаточно проста.</span><span class="sxs-lookup"><span data-stu-id="88871-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="88871-112">В коде, ограниченном производительностью ввода-вывода, выполняйте await для операции, которая возвращает `Task` или `Task<T>`, внутри метода `async`.</span><span class="sxs-lookup"><span data-stu-id="88871-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="88871-113">В коде, ограниченном ресурсами процессора, выполняйте await для операции, которая запускается в фоновом потоке методом <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88871-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="88871-114">Именно с помощью ключевого слова `await` творится вся магия.</span><span class="sxs-lookup"><span data-stu-id="88871-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="88871-115">Оно передает управление вызывающему объекту метода, который выполнил `await`, позволяя, таким образом, пользовательскому интерфейсу или службе отвечать на запросы.</span><span class="sxs-lookup"><span data-stu-id="88871-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="88871-116">Хотя [существуют и другие способы](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) реализации асинхронного кода, кроме `async` и `await`, в этой статье рассматриваются только конструкции уровня языка.</span><span class="sxs-lookup"><span data-stu-id="88871-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="88871-117">Пример кода, ограниченного производительностью ввода-вывода: скачивание данных из веб-службы</span><span class="sxs-lookup"><span data-stu-id="88871-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="88871-118">Предположим, вам нужно скачать некоторые данные из веб-службы по нажатию кнопки, не блокируя поток пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="88871-118">You may need to download some data from a web service when a button is pressed but don't want to block the UI thread.</span></span> <span data-ttu-id="88871-119">Это можно сделать так:</span><span class="sxs-lookup"><span data-stu-id="88871-119">It can be accomplished like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="88871-120">В этом коде намерение (скачивание данных в асинхронном режиме) выражается без запутанных операций с объектами `Task`.</span><span class="sxs-lookup"><span data-stu-id="88871-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="88871-121">Пример кода, ограниченного ресурсами процессора: выполнение вычислений для игры</span><span class="sxs-lookup"><span data-stu-id="88871-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="88871-122">Предположим, вы разрабатываете игру для мобильных устройств, в которой при нажатии кнопки может наноситься урон множеству противников на экране.</span><span class="sxs-lookup"><span data-stu-id="88871-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="88871-123">Расчет урона может потреблять много ресурсов. Если производить его в потоке пользовательского интерфейса, то на это время игра может приостанавливаться!</span><span class="sxs-lookup"><span data-stu-id="88871-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="88871-124">Оптимальный способ — запустить фоновый поток, который выполняет задачу с помощью `Task.Run`, а затем ожидать ее результат с помощью `await`.</span><span class="sxs-lookup"><span data-stu-id="88871-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="88871-125">Это обеспечит плавность работы пользовательского интерфейса в процессе вычисления.</span><span class="sxs-lookup"><span data-stu-id="88871-125">This allows the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="88871-126">В этом коде четко выражается назначение события нажатия кнопки, фоновым потоком не требуется управлять вручную, и он выполняется без блокировки.</span><span class="sxs-lookup"><span data-stu-id="88871-126">This code clearly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="88871-127">Что происходит на внутреннем уровне</span><span class="sxs-lookup"><span data-stu-id="88871-127">What happens under the covers</span></span>

<span data-ttu-id="88871-128">Выполнение асинхронных операций связано со множеством моментов.</span><span class="sxs-lookup"><span data-stu-id="88871-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="88871-129">Если вы хотите знать внутренние принципы работы объектов `Task` и `Task<T>`, прочтите статью [Подробный обзор асинхронного программирования](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="88871-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="88871-130">С точки зрения C#, компилятор преобразовывает код в конечный автомат, который контролирует такие моменты, как передача выполнения при достижении `await` и возобновление выполнения после завершения фонового задания.</span><span class="sxs-lookup"><span data-stu-id="88871-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="88871-131">Если вас интересует теория, это реализация [модели асинхронности на основе обещаний](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="88871-131">For the theoretically inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="88871-132">Ключевые моменты для понимания</span><span class="sxs-lookup"><span data-stu-id="88871-132">Key pieces to understand</span></span>

* <span data-ttu-id="88871-133">Асинхронный код можно использовать как при ограниченной производительности ввода-вывода, так и при ограниченных ресурсах процессора, но по-разному в каждом случае.</span><span class="sxs-lookup"><span data-stu-id="88871-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="88871-134">В асинхронном коде используются конструкции `Task<T>` и `Task`, которые служат для моделирования задач, выполняемых в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="88871-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="88871-135">Ключевое слово `async` делает метод асинхронным, что позволяет использовать в его теле ключевое слово `await`.</span><span class="sxs-lookup"><span data-stu-id="88871-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="88871-136">Когда применяется ключевое слово `await`, оно приостанавливает выполнение вызывающего метода и передает управление обратно вызывающему объекту, пока не будет завершена ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="88871-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="88871-137">`await` можно использовать только внутри асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="88871-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="88871-138">Различия задач, ограниченных ресурсами процессора и производительностью ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="88871-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="88871-139">В первых двух примерах этого руководства было показано, как можно использовать `async` и `await` для выполнения задач, ограниченных производительностью ввода-вывода и ресурсами процессора.</span><span class="sxs-lookup"><span data-stu-id="88871-139">The first two examples of this guide showed how you could use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="88871-140">Крайне важно уметь идентифицировать такие задачи, так как они могут существенно повлиять на производительность кода и привести к неправильному использованию некоторых конструкций.</span><span class="sxs-lookup"><span data-stu-id="88871-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="88871-141">Перед написанием любого кода нужно ответить на два вопроса.</span><span class="sxs-lookup"><span data-stu-id="88871-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="88871-142">Будет ли код "ожидать" чего-либо, например данных из базы данных?</span><span class="sxs-lookup"><span data-stu-id="88871-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="88871-143">Если ответ утвердительный, то ваша задача **ограничена производительностью ввода-вывода**.</span><span class="sxs-lookup"><span data-stu-id="88871-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="88871-144">Будет ли код выполнять сложные вычисления?</span><span class="sxs-lookup"><span data-stu-id="88871-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="88871-145">Если ответ утвердительный, то задача **ограничена ресурсами процессора**.</span><span class="sxs-lookup"><span data-stu-id="88871-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="88871-146">Если ваша задача **ограничена производительностью ввода-вывода**, используйте `async` и `await` *без* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="88871-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="88871-147">Библиотеку параллельных задач использовать *не следует*.</span><span class="sxs-lookup"><span data-stu-id="88871-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="88871-148">Причина этого указана в статье [Подробный обзор асинхронного программирования](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="88871-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="88871-149">Если ваша задача **ограничена ресурсами процессора** и вам важна скорость реагирования, используйте `async` и `await`, но перенесите выполнение задачи в дополнительный поток, у которого *есть* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="88871-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="88871-150">Если к задаче применим параллелизм, рассмотрите возможность использования [библиотеки параллельных задач](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="88871-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="88871-151">Кроме того, всегда следует оценивать выполнение кода.</span><span class="sxs-lookup"><span data-stu-id="88871-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="88871-152">Например, затраты на выполнение задачи, ограниченной ресурсами процессора, могут оказаться не столь высокими, как накладные расходы, связанные с переключениями контекста при многопоточности.</span><span class="sxs-lookup"><span data-stu-id="88871-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="88871-153">Каждый вариант имеет свои недостатки, поэтому следует выбрать наиболее компромиссный вариант в вашей ситуации.</span><span class="sxs-lookup"><span data-stu-id="88871-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="88871-154">Дополнительные примеры</span><span class="sxs-lookup"><span data-stu-id="88871-154">More examples</span></span>

<span data-ttu-id="88871-155">В приведенных ниже примерах демонстрируются различные способы написания асинхронного кода на C#.</span><span class="sxs-lookup"><span data-stu-id="88871-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="88871-156">Они охватывают несколько сценариев, с которыми вы можете столкнуться.</span><span class="sxs-lookup"><span data-stu-id="88871-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="88871-157">Извлечение данных из сети</span><span class="sxs-lookup"><span data-stu-id="88871-157">Extract data from a network</span></span>

<span data-ttu-id="88871-158">Этот фрагмент кода скачивает код HTML с главной страницы сайта <https://dotnetfoundation.org> и подсчитывает в нем число вхождений строки ".NET".</span><span class="sxs-lookup"><span data-stu-id="88871-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="88871-159">С помощью ASP.NET он определяет метод контроллера веб-API, который выполняет эту задачу и возвращает число.</span><span class="sxs-lookup"><span data-stu-id="88871-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="88871-160">Если вы планируете проанализировать HTML в рабочем коде, не используйте регулярные выражения.</span><span class="sxs-lookup"><span data-stu-id="88871-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="88871-161">Используйте библиотеку анализа.</span><span class="sxs-lookup"><span data-stu-id="88871-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="88871-162">Вот аналогичный код для универсального приложения для Windows, который выполняет ту же задачу при нажатии кнопки:</span><span class="sxs-lookup"><span data-stu-id="88871-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="88871-163">Ожидание выполнения нескольких задач</span><span class="sxs-lookup"><span data-stu-id="88871-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="88871-164">Может возникнуть ситуация, когда несколько фрагментов данных должны извлекаться одновременно.</span><span class="sxs-lookup"><span data-stu-id="88871-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="88871-165">API-интерфейс `Task` содержит два метода, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, которые позволяют писать асинхронный код, выполняющий неблокирующее ожидание нескольких фоновых заданий.</span><span class="sxs-lookup"><span data-stu-id="88871-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="88871-166">В этом примере показано, как можно получить данные `User` для набора `userId`.</span><span class="sxs-lookup"><span data-stu-id="88871-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="88871-167">Вот более лаконичный вариант этого кода, написанный с использованием LINQ:</span><span class="sxs-lookup"><span data-stu-id="88871-167">Here's another way to write this more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="88871-168">Хотя размер кода будет меньше, соблюдайте осторожность при использовании LINQ в сочетании с асинхронным кодом.</span><span class="sxs-lookup"><span data-stu-id="88871-168">Although it's less code, use caution when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="88871-169">Так как в LINQ используется отложенное выполнение, асинхронные вызовы будут выполняться не немедленно, как в цикле `foreach`, если только вы не производите принудительную итерацию созданной последовательности с помощью вызова `.ToList()` или `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="88871-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="88871-170">Важные сведения и советы</span><span class="sxs-lookup"><span data-stu-id="88871-170">Important info and advice</span></span>

<span data-ttu-id="88871-171">При создании асинхронного кода необходимо учитывать ряд моментов, которые позволят избежать непредвиденного поведения.</span><span class="sxs-lookup"><span data-stu-id="88871-171">With async programming, there are some details to keep in mind that can prevent unexpected behavior.</span></span>

* <span data-ttu-id="88871-172">**В методах `async` должно присутствовать ключевое слово** `await` **. В противном случае результат не будет получен.**</span><span class="sxs-lookup"><span data-stu-id="88871-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="88871-173">Это важно помнить.</span><span class="sxs-lookup"><span data-stu-id="88871-173">This is important to keep in mind.</span></span> <span data-ttu-id="88871-174">Если в теле метода `async` не используется ключевое слово `await`, компилятор C# выдаст предупреждение, но код скомпилируется и будет выполняться, как обычный метод.</span><span class="sxs-lookup"><span data-stu-id="88871-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="88871-175">Это крайне неэффективно, так как созданный компилятором C# конечный автомат для асинхронного метода не будет выполнять никакой работы.</span><span class="sxs-lookup"><span data-stu-id="88871-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="88871-176">**К имени каждого создаваемого асинхронного метода следует добавлять суффикс Async.**</span><span class="sxs-lookup"><span data-stu-id="88871-176">**Add "Async" as the suffix of every async method name you write.**</span></span>

  <span data-ttu-id="88871-177">Это соглашение применяется в .NET для удобной дифференциации синхронных и асинхронных методов.</span><span class="sxs-lookup"><span data-stu-id="88871-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="88871-178">Это не всегда применимо к некоторым методам, которые не вызываются в коде явным образом (например, к обработчикам событий или методам веб-контроллеров).</span><span class="sxs-lookup"><span data-stu-id="88871-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="88871-179">Так как они не вызываются в коде явно, требования к их именованию не так строги.</span><span class="sxs-lookup"><span data-stu-id="88871-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="88871-180">`async void` **следует использовать только для обработчиков событий.**</span><span class="sxs-lookup"><span data-stu-id="88871-180">`async void` **should only be used for event handlers.**</span></span>

  <span data-ttu-id="88871-181">`async void` — это единственный способ обеспечить работу асинхронных обработчиков событий, так как у событий нет типов возвращаемых значений (поэтому они не могут использовать `Task` и `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="88871-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="88871-182">Любые иные способы применения `async void` не предусмотрены моделью TAP и могут создавать указанные ниже проблемы.</span><span class="sxs-lookup"><span data-stu-id="88871-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  * <span data-ttu-id="88871-183">Исключения, вызываемые в методе `async void`, невозможно перехватывать вне этого метода.</span><span class="sxs-lookup"><span data-stu-id="88871-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
  * <span data-ttu-id="88871-184">Методы `async void` очень трудно тестировать.</span><span class="sxs-lookup"><span data-stu-id="88871-184">`async void` methods are difficult to test.</span></span>
  * <span data-ttu-id="88871-185">Методы `async void` могут иметь негативные побочные эффекты, если вызывающий объект не ожидает, что они будут асинхронными.</span><span class="sxs-lookup"><span data-stu-id="88871-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="88871-186">**Будьте осторожны при использовании асинхронных лямбда-выражений в выражениях LINQ**</span><span class="sxs-lookup"><span data-stu-id="88871-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

  <span data-ttu-id="88871-187">Для лямбда-выражений в LINQ применяется отложенное выполнение. Это означает, что код может выполняться в произвольный момент, когда вы этого не ожидаете.</span><span class="sxs-lookup"><span data-stu-id="88871-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="88871-188">Неправильное использование блокирующих задач при этом может привести к взаимоблокировке.</span><span class="sxs-lookup"><span data-stu-id="88871-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="88871-189">Кроме того, вложение такого асинхронного кода может усложнить анализ выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="88871-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="88871-190">Асинхронное выполнение и LINQ — эффективные средства, но использовать их следует с максимальной осторожностью и ясным пониманием того, что вы делаете.</span><span class="sxs-lookup"><span data-stu-id="88871-190">Async and LINQ are powerful but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="88871-191">**При написании кода ожидание задач следует реализовывать без блокирования**</span><span class="sxs-lookup"><span data-stu-id="88871-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

  <span data-ttu-id="88871-192">Блокирование текущего потока для ожидания завершения `Task` может привести к взаимоблокировкам и блокированию потоков контекста, что потребует более сложной обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="88871-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads and can require more complex error-handling.</span></span> <span data-ttu-id="88871-193">В приведенной ниже таблице даются рекомендации по реализации ожидания задач без блокировки.</span><span class="sxs-lookup"><span data-stu-id="88871-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

  | <span data-ttu-id="88871-194">Рекомендуемый способ</span><span class="sxs-lookup"><span data-stu-id="88871-194">Use this...</span></span>          | <span data-ttu-id="88871-195">Нерекомендуемый способ</span><span class="sxs-lookup"><span data-stu-id="88871-195">Instead of this...</span></span>           | <span data-ttu-id="88871-196">Задача</span><span class="sxs-lookup"><span data-stu-id="88871-196">When wishing to do this...</span></span>                 |
  |----------------------|------------------------------|--------------------------------------------|
  | `await`              | <span data-ttu-id="88871-197">`Task.Wait` или `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="88871-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="88871-198">Получение результата фоновой задачи</span><span class="sxs-lookup"><span data-stu-id="88871-198">Retrieving the result of a background task</span></span> |
  | `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="88871-199">Ожидание завершения выполнения любой задачи</span><span class="sxs-lookup"><span data-stu-id="88871-199">Waiting for any task to complete</span></span>           |
  | `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="88871-200">Ожидание завершения выполнения всех задач</span><span class="sxs-lookup"><span data-stu-id="88871-200">Waiting for all tasks to complete</span></span>          |
  | `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="88871-201">Ожидание в течение заданного времени</span><span class="sxs-lookup"><span data-stu-id="88871-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="88871-202">**Рекомендуется использовать** `ValueTask` **во всех возможных случаях**</span><span class="sxs-lookup"><span data-stu-id="88871-202">**Consider using** `ValueTask` **where possible**</span></span>

  <span data-ttu-id="88871-203">В некоторых случаях возврат объекта `Task` из асинхронных методов может вызывать сложности.</span><span class="sxs-lookup"><span data-stu-id="88871-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="88871-204">`Task` — это тип ссылки, поэтому его применение означает распределение объекта.</span><span class="sxs-lookup"><span data-stu-id="88871-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="88871-205">В случаях, когда метод с модификатором `async` возвращает кэшированный результат или завершается синхронно, лишние распределения могут вызывать серьезные потери времени при выполнении фрагментов кода, зависящих от производительности.</span><span class="sxs-lookup"><span data-stu-id="88871-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="88871-206">Эта проблема встает серьезно, если распределения происходят в коротких циклах.</span><span class="sxs-lookup"><span data-stu-id="88871-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="88871-207">Дополнительные сведения см. в разделе [Обобщенные асинхронные типы возвращаемых значений](whats-new/csharp-7.md#generalized-async-return-types).</span><span class="sxs-lookup"><span data-stu-id="88871-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="88871-208">**Рекомендуется использовать** `ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="88871-208">**Consider using** `ConfigureAwait(false)`</span></span>

  <span data-ttu-id="88871-209">Часто возникает вопрос: "Когда же нужно использовать метод <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType>?"</span><span class="sxs-lookup"><span data-stu-id="88871-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="88871-210">Этот метод позволяет экземпляру `Task` настроить ожидающий объект.</span><span class="sxs-lookup"><span data-stu-id="88871-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="88871-211">Это важный элемент, неправильная настройка которого может привести к снижению производительности и даже к взаимоблокировкам.</span><span class="sxs-lookup"><span data-stu-id="88871-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="88871-212">Дополнительные сведения о `ConfigureAwait` см. в [статье с вопросами и ответами по ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span><span class="sxs-lookup"><span data-stu-id="88871-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="88871-213">**Пишите код с менее строгим отслеживанием состояния**</span><span class="sxs-lookup"><span data-stu-id="88871-213">**Write less stateful code**</span></span>

  <span data-ttu-id="88871-214">Старайтесь, чтобы выполнение кода не зависело от состояния глобальных объектов или выполнения определенных методов.</span><span class="sxs-lookup"><span data-stu-id="88871-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="88871-215">Оно должно зависеть только от возвращаемых методами значений.</span><span class="sxs-lookup"><span data-stu-id="88871-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="88871-216">Почему?</span><span class="sxs-lookup"><span data-stu-id="88871-216">Why?</span></span>

  * <span data-ttu-id="88871-217">Код будет проще анализировать.</span><span class="sxs-lookup"><span data-stu-id="88871-217">Code will be easier to reason about.</span></span>
  * <span data-ttu-id="88871-218">Код будет проще тестировать.</span><span class="sxs-lookup"><span data-stu-id="88871-218">Code will be easier to test.</span></span>
  * <span data-ttu-id="88871-219">Гораздо проще будет сочетать асинхронный и синхронный код.</span><span class="sxs-lookup"><span data-stu-id="88871-219">Mixing async and synchronous code is far simpler.</span></span>
  * <span data-ttu-id="88871-220">Как правило, можно полностью избежать состояний гонки.</span><span class="sxs-lookup"><span data-stu-id="88871-220">Race conditions can typically be avoided altogether.</span></span>
  * <span data-ttu-id="88871-221">Зависимость от возвращаемых значений упрощает согласование асинхронного кода.</span><span class="sxs-lookup"><span data-stu-id="88871-221">Depending on return values makes coordinating async code simple.</span></span>
  * <span data-ttu-id="88871-222">Дополнительным преимуществом является то, что такой код хорошо работает с внедрением зависимостей.</span><span class="sxs-lookup"><span data-stu-id="88871-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="88871-223">Следует стремиться к достижению полной или почти полной [ссылочной прозрачности](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) в коде.</span><span class="sxs-lookup"><span data-stu-id="88871-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="88871-224">Результатом будет предсказуемость базы кода, а также ее пригодность для тестирования и обслуживания.</span><span class="sxs-lookup"><span data-stu-id="88871-224">Doing so will result in a predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="88871-225">Другие источники</span><span class="sxs-lookup"><span data-stu-id="88871-225">Other resources</span></span>

* <span data-ttu-id="88871-226">В статье [Подробный обзор асинхронного программирования](../standard/async-in-depth.md) приводятся дополнительные сведения о принципах работы задач.</span><span class="sxs-lookup"><span data-stu-id="88871-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* <span data-ttu-id="88871-227">[Асинхронная модель программирования задач (C#)](./programming-guide/concepts/async/task-asynchronous-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="88871-227">[The Task asynchronous programming model (C#)](./programming-guide/concepts/async/task-asynchronous-programming-model.md).</span></span>
* <span data-ttu-id="88871-228">Эпизод [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) (Шесть важных советов по асинхронному программированию) с Лусианом Вышиком (Lucian Wischik) — это отличный ресурс по асинхронному программированию.</span><span class="sxs-lookup"><span data-stu-id="88871-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) is a wonderful resource for async programming.</span></span>
