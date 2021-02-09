---
title: Отмена списка задач (C#)
description: Узнайте, как использовать токены отмены для подачи запроса на отмену в список задач.
ms.date: 02/03/2021
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 532c61ab6499583620ba2ee5c710c58f7886f89d
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585745"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="8adb9-103">Отмена списка задач (C#)</span><span class="sxs-lookup"><span data-stu-id="8adb9-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="8adb9-104">Вы можете отменить асинхронное консольное приложение, если не хотите дожидаться его завершения.</span><span class="sxs-lookup"><span data-stu-id="8adb9-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="8adb9-105">Выполнив код в приведенных ниже примерах, вы сможете добавить в приложение возможность отмены, загружающую содержимое списка веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="8adb9-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="8adb9-106">Можно отменить множество задач, связав экземпляр <xref:System.Threading.CancellationTokenSource> с каждой задачей.</span><span class="sxs-lookup"><span data-stu-id="8adb9-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="8adb9-107">В этом случае нажатие клавиши <kbd>ВВОД</kbd> отменяет сразу все незавершенные задачи.</span><span class="sxs-lookup"><span data-stu-id="8adb9-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="8adb9-108">Темы, рассматриваемые в этом руководстве:</span><span class="sxs-lookup"><span data-stu-id="8adb9-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8adb9-109">Создание консольного приложения .NET</span><span class="sxs-lookup"><span data-stu-id="8adb9-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="8adb9-110">Создание асинхронного приложения, поддерживающего отмену</span><span class="sxs-lookup"><span data-stu-id="8adb9-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="8adb9-111">Демонстрация отмены сигнализации</span><span class="sxs-lookup"><span data-stu-id="8adb9-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8adb9-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8adb9-112">Prerequisites</span></span>

<span data-ttu-id="8adb9-113">Для работы с данным учебником требуется следующее:</span><span class="sxs-lookup"><span data-stu-id="8adb9-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="8adb9-114">Пакет SDK для .NET 5.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="8adb9-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="8adb9-115">Интегрированная среда разработки (IDE)</span><span class="sxs-lookup"><span data-stu-id="8adb9-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="8adb9-116">Мы рекомендуем Visual Studio, Visual Studio Code или Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="8adb9-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="8adb9-117">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="8adb9-117">Create example application</span></span>

<span data-ttu-id="8adb9-118">Создайте новое консольное приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8adb9-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="8adb9-119">Его можно создать с помощью команды [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) или в [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="8adb9-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="8adb9-120">Откройте файл *Program.cs* в любом редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="8adb9-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="8adb9-121">Замена операторов using</span><span class="sxs-lookup"><span data-stu-id="8adb9-121">Replace using statements</span></span>

<span data-ttu-id="8adb9-122">Замените существующие операторы using следующими объявлениями.</span><span class="sxs-lookup"><span data-stu-id="8adb9-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="8adb9-123">Добавить поля</span><span class="sxs-lookup"><span data-stu-id="8adb9-123">Add fields</span></span>

<span data-ttu-id="8adb9-124">В определении класса `Program` добавьте следующие три поля.</span><span class="sxs-lookup"><span data-stu-id="8adb9-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<span data-ttu-id="8adb9-125"><xref:System.Threading.CancellationTokenSource> используется для сигнализации запрошенной отмены <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="8adb9-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="8adb9-126">`HttpClient` предоставляет возможность отправлять HTTP-запросы и получать HTTP-ответы.</span><span class="sxs-lookup"><span data-stu-id="8adb9-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="8adb9-127">`s_urlList` содержит все URL-адреса, которые планируется обработать приложением.</span><span class="sxs-lookup"><span data-stu-id="8adb9-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="8adb9-128">Обновление точки входа приложения</span><span class="sxs-lookup"><span data-stu-id="8adb9-128">Update application entry point</span></span>

<span data-ttu-id="8adb9-129">Главной точкой входа в консольное приложение является метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="8adb9-130">Замените существующий метод следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="8adb9-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="8adb9-131">Обновленный метод `Main` теперь считается [асинхронным методом main](../../../whats-new/csharp-7.md#async-main), который позволяет использовать асинхронную точку входа в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="8adb9-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="8adb9-132">Он записывает в консоль несколько сообщений с инструкциями, а затем объявляет экземпляр <xref:System.Threading.Tasks.Task> с именем `cancelTask`, который будет считывать нажатия клавиш в консоли.</span><span class="sxs-lookup"><span data-stu-id="8adb9-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="8adb9-133">Если нажата клавиша <kbd>ВВОД</kbd>, выполняется вызов <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8adb9-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="8adb9-134">Это приведет к отмене сигнала.</span><span class="sxs-lookup"><span data-stu-id="8adb9-134">This will signal cancellation.</span></span> <span data-ttu-id="8adb9-135">Затем переменная `sumPageSizesTask` назначается методом `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="8adb9-136">Затем обе задачи передаются в <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, что будет продолжено после завершения любой из этих задач.</span><span class="sxs-lookup"><span data-stu-id="8adb9-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="8adb9-137">Создание метода асинхронного суммирования размеров страниц</span><span class="sxs-lookup"><span data-stu-id="8adb9-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="8adb9-138">Добавьте метод `Main` под методом `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="8adb9-139">Метод начинается с создания экземпляра и запуска <xref:System.Diagnostics.Stopwatch>.</span><span class="sxs-lookup"><span data-stu-id="8adb9-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="8adb9-140">Затем он просматривает каждый URL-адрес в `s_urlList` и вызывает `ProcessUrlAsync`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="8adb9-141">При каждой итерации в метод `ProcessUrlAsync` передается `s_cts.Token`, а код возвращает <xref:System.Threading.Tasks.Task%601>, где `TResult` является целым числом.</span><span class="sxs-lookup"><span data-stu-id="8adb9-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="8adb9-142">Добавление метода обработки</span><span class="sxs-lookup"><span data-stu-id="8adb9-142">Add process method</span></span>

<span data-ttu-id="8adb9-143">Добавьте приведенный ниже метод `ProcessUrlAsync` после метода `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="8adb9-144">Для любого заданного URL-адреса метод будет использовать экземпляр `client`, предоставленный для получения ответа в качестве `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="8adb9-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="8adb9-145"><xref:System.Threading.CancellationToken> экземпляр передается в методы <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> и <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8adb9-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8adb9-146">`token` используется для регистрации запрошенной отмены.</span><span class="sxs-lookup"><span data-stu-id="8adb9-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="8adb9-147">Длина возвращается после того, как URL-адрес и длина записываются в консоль.</span><span class="sxs-lookup"><span data-stu-id="8adb9-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="8adb9-148">Пример выходных данных приложения</span><span class="sxs-lookup"><span data-stu-id="8adb9-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="8adb9-149">Полный пример</span><span class="sxs-lookup"><span data-stu-id="8adb9-149">Complete example</span></span>

<span data-ttu-id="8adb9-150">Приведенный ниже код — это полный текст файла *Program.cs* для примера.</span><span class="sxs-lookup"><span data-stu-id="8adb9-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="8adb9-151">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8adb9-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="8adb9-152">Асинхронное программирование с использованием ключевых слов Async и Await (C#)</span><span class="sxs-lookup"><span data-stu-id="8adb9-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="8adb9-153">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="8adb9-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8adb9-154">Отмена асинхронных задач после определенного периода времени (C#)</span><span class="sxs-lookup"><span data-stu-id="8adb9-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
