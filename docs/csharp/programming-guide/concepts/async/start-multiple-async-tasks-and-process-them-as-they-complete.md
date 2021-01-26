---
title: Обработка асинхронных задач по мере завершения
description: В этом примере показано, как использовать Task.WhenAny в C# для запуска нескольких задач и обработки их результатов по мере завершения, а не в порядке запуска.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 4cdd35af900863895911ea5c2c9772af362951ec
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615975"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="a44a1-103">Обработка асинхронных задач по мере завершения (C#)</span><span class="sxs-lookup"><span data-stu-id="a44a1-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="a44a1-104">С помощью <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> можно запускать несколько задач одновременно и обрабатывать их по одной по мере завершения, а не в порядке их запуска.</span><span class="sxs-lookup"><span data-stu-id="a44a1-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="a44a1-105">В следующем примере используется запрос для создания коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="a44a1-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="a44a1-106">Каждая задача загружает содержимое указанного веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="a44a1-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="a44a1-107">В каждой итерации цикла while ожидаемый вызов <xref:System.Threading.Tasks.Task.WhenAny%2A> возвращает задачу из коллекции задач, которая первой завершает свою загрузку.</span><span class="sxs-lookup"><span data-stu-id="a44a1-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="a44a1-108">Эта задача удаляется из коллекции и обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="a44a1-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="a44a1-109">Цикл выполняется до тех пор, пока в коллекции еще есть задачи.</span><span class="sxs-lookup"><span data-stu-id="a44a1-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="a44a1-110">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="a44a1-110">Create example application</span></span>

<span data-ttu-id="a44a1-111">Создайте новое консольное приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a44a1-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="a44a1-112">Его можно создать с помощью команды [dotnet new console](../../../../core/tools/dotnet-new.md#console) или в [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a44a1-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="a44a1-113">Откройте файл *Program.cs* в любом редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="a44a1-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="a44a1-114">Замена операторов using</span><span class="sxs-lookup"><span data-stu-id="a44a1-114">Replace using statements</span></span>

<span data-ttu-id="a44a1-115">Замените существующие операторы using следующими объявлениями.</span><span class="sxs-lookup"><span data-stu-id="a44a1-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="a44a1-116">Добавить поля</span><span class="sxs-lookup"><span data-stu-id="a44a1-116">Add fields</span></span>

<span data-ttu-id="a44a1-117">Добавьте в определение класса `Program` следующие два поля.</span><span class="sxs-lookup"><span data-stu-id="a44a1-117">In the `Program` class definition, add the following two fields:</span></span>

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<span data-ttu-id="a44a1-118">`HttpClient` предоставляет возможность отправлять HTTP-запросы и получать HTTP-ответы.</span><span class="sxs-lookup"><span data-stu-id="a44a1-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="a44a1-119">`s_urlList` содержит все URL-адреса, которые планируется обработать приложением.</span><span class="sxs-lookup"><span data-stu-id="a44a1-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="a44a1-120">Обновление точки входа приложения</span><span class="sxs-lookup"><span data-stu-id="a44a1-120">Update application entry point</span></span>

<span data-ttu-id="a44a1-121">Главной точкой входа в консольное приложение является метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="a44a1-122">Замените существующий метод следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="a44a1-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="a44a1-123">Обновленный метод `Main` теперь считается [асинхронным методом main](../../../whats-new/csharp-7.md#async-main), который позволяет использовать асинхронную точку входа в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="a44a1-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="a44a1-124">Он выражается вызовом `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="a44a1-125">Создание метода асинхронного суммирования размеров страниц</span><span class="sxs-lookup"><span data-stu-id="a44a1-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="a44a1-126">Добавьте метод `Main` под методом `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="a44a1-127">Метод начинается с создания экземпляра и запуска <xref:System.Diagnostics.Stopwatch>.</span><span class="sxs-lookup"><span data-stu-id="a44a1-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="a44a1-128">Затем он включает запрос, который при выполнении создает коллекцию задач.</span><span class="sxs-lookup"><span data-stu-id="a44a1-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="a44a1-129">Каждый вызов `ProcessUrlAsync` в следующем коде возвращает <xref:System.Threading.Tasks.Task%601>, где `TResult` — целое число.</span><span class="sxs-lookup"><span data-stu-id="a44a1-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="a44a1-130">Из-за [отложенного выполнения](../../../../standard/linq/deferred-execution-example.md) с помощью LINQ для запуска каждой задачи вызывается <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a44a1-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="a44a1-131">Цикл `while` выполняет следующие действия для каждой задачи в коллекции.</span><span class="sxs-lookup"><span data-stu-id="a44a1-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="a44a1-132">Ожидает вызов `WhenAny` для определения первой задачи в коллекции, чтобы завершить ее загрузку.</span><span class="sxs-lookup"><span data-stu-id="a44a1-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> finishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="a44a1-133">Удаляет эту задачу из коллекции.</span><span class="sxs-lookup"><span data-stu-id="a44a1-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(finishedTask);
    ```

1. <span data-ttu-id="a44a1-134">Ожидает `finishedTask`, возвращаемый при вызове `ProcessUrlAsync`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="a44a1-135">Переменная `finishedTask` представляет собой <xref:System.Threading.Tasks.Task%601>, где `TResult` — целое число.</span><span class="sxs-lookup"><span data-stu-id="a44a1-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="a44a1-136">Задача уже завершена, но она ожидается для получения размера загруженного веб-сайта, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a44a1-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="a44a1-137">В случае сбоя задачи `await` выдаст первое исключение дочернего элемента, хранящееся в `AggregateException`, в отличие от считывания свойства <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, которое выдаст `AggregateException`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="a44a1-138">Добавление метода обработки</span><span class="sxs-lookup"><span data-stu-id="a44a1-138">Add process method</span></span>

<span data-ttu-id="a44a1-139">Добавьте приведенный ниже метод `ProcessUrlAsync` после метода `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="a44a1-140">Для любого заданного URL-адреса метод будет использовать экземпляр `client`, предоставленный для получения ответа в качестве `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="a44a1-141">Длина возвращается после того, как URL-адрес и длина записываются в консоль.</span><span class="sxs-lookup"><span data-stu-id="a44a1-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="a44a1-142">Запустите проект несколько раз и убедитесь, что размеры скачанных файлов не всегда отображаются в одном и том же порядке.</span><span class="sxs-lookup"><span data-stu-id="a44a1-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="a44a1-143">Можно использовать `WhenAny` в цикле, как описано в примере, для решения проблем, которые включают небольшое число задач.</span><span class="sxs-lookup"><span data-stu-id="a44a1-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="a44a1-144">Однако когда требуется обработка большого числа задач, другие методы будут более эффективны.</span><span class="sxs-lookup"><span data-stu-id="a44a1-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="a44a1-145">Дополнительные сведения и примеры см. в разделе [Обработка задач по мере их завершения](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="a44a1-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="a44a1-146">Полный пример</span><span class="sxs-lookup"><span data-stu-id="a44a1-146">Complete example</span></span>

<span data-ttu-id="a44a1-147">Приведенный ниже код — это полный текст файла *Program.cs* для примера.</span><span class="sxs-lookup"><span data-stu-id="a44a1-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="a44a1-148">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a44a1-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="a44a1-149">Асинхронное программирование с использованием ключевых слов Async и Await (C#)</span><span class="sxs-lookup"><span data-stu-id="a44a1-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
