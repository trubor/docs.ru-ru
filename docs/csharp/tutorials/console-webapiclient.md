---
title: Создание клиента REST с использованием .NET Core
description: В этом руководстве описаны некоторые возможности .NET Core и языка C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: a8490efbc954ca585a2a0fa9d571191095a4b24c
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "98024981"
---
# <a name="rest-client"></a><span data-ttu-id="4e2a9-103">Клиент REST</span><span class="sxs-lookup"><span data-stu-id="4e2a9-103">REST client</span></span>

<span data-ttu-id="4e2a9-104">Это руководство раскроет для вас некоторые возможности .NET Core и языка C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="4e2a9-105">Вы познакомитесь со следующими аспектами:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-105">You'll learn:</span></span>

* <span data-ttu-id="4e2a9-106">Общие сведения о .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="4e2a9-107">обзор возможностей языка C#;</span><span class="sxs-lookup"><span data-stu-id="4e2a9-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="4e2a9-108">управление зависимостями с помощью NuGet;</span><span class="sxs-lookup"><span data-stu-id="4e2a9-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="4e2a9-109">взаимодействие по протоколу HTTP;</span><span class="sxs-lookup"><span data-stu-id="4e2a9-109">HTTP Communications</span></span>
* <span data-ttu-id="4e2a9-110">обработка информации в формате JSON;</span><span class="sxs-lookup"><span data-stu-id="4e2a9-110">Processing JSON information</span></span>
* <span data-ttu-id="4e2a9-111">управление конфигурацией с помощью атрибутов.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="4e2a9-112">Вам предстоит создать приложение, которое отправляет запросы HTTP к службе REST на GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-112">You'll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="4e2a9-113">Вы будете считывать данные в формате JSON и преобразовывать полученный пакет JSON в объекты C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="4e2a9-114">И наконец, вы увидите примеры работы с объектами C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="4e2a9-115">В этом руководстве описано множество функций.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-115">There are many features in this tutorial.</span></span> <span data-ttu-id="4e2a9-116">Попробуем собрать их по одному.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-116">Let's build them one by one.</span></span>

<span data-ttu-id="4e2a9-117">Если вы хотите работать с [готовым примером кода](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) для этой статьи, можете скачать его.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this article, you can download it.</span></span> <span data-ttu-id="4e2a9-118">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e2a9-119">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4e2a9-119">Prerequisites</span></span>

<span data-ttu-id="4e2a9-120">Компьютер должен быть настроен для запуска .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-120">You'll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="4e2a9-121">Инструкции по установке см. на странице [скачиваемых файлов .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="4e2a9-122">Это приложение можно запустить в ОС Windows, Linux, macOS или в контейнере Docker.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-122">You can run this application on Windows, Linux, or macOS, or in a Docker container.</span></span>
<span data-ttu-id="4e2a9-123">Вам потребуется редактор кода, но вы можете выбрать любой привычный для вас.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-123">You'll need to install your favorite code editor.</span></span> <span data-ttu-id="4e2a9-124">В примерах ниже используется кроссплатформенный редактор [Visual Studio Code](https://code.visualstudio.com/) с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="4e2a9-125">Вы можете заменить его на любое другое средство, с которым вам удобно работать.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="4e2a9-126">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="4e2a9-126">Create the Application</span></span>

<span data-ttu-id="4e2a9-127">Первым шагом является создание нового приложения.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-127">The first step is to create a new application.</span></span> <span data-ttu-id="4e2a9-128">Откройте командную строку и создайте новый каталог для приложения.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="4e2a9-129">Перейдите в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-129">Make that the current directory.</span></span> <span data-ttu-id="4e2a9-130">Введите следующую команду в окне консоли:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="4e2a9-131">Эта команда создает начальный набор файлов для базового приложения Hello World.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="4e2a9-132">Имя проекта — "WebAPIClient".</span><span class="sxs-lookup"><span data-stu-id="4e2a9-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="4e2a9-133">Так как это новый проект, зависимостей нет на месте.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="4e2a9-134">При первом запуске будет скачана платформа .NET Core, установлен сертификат разработки и запущен диспетчер пакетов NuGet для восстановления отсутствующих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="4e2a9-135">Прежде чем вносить изменения, перейдите в каталог "WebAPIClient" с помощью команды `cd` и введите `dotnet run` ([см. примечание](#dotnet-restore-note)) в командной строке, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-135">Before you start making modifications, `cd` into the "WebAPIClient" directory and type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="4e2a9-136">`dotnet run` автоматически выполняет `dotnet restore` при отсутствии зависимостей в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="4e2a9-137">Он также выполнит `dotnet build`, если приложение необходимо пересобрать.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="4e2a9-138">После первоначальной настройки будет достаточно запуска `dotnet restore` или `dotnet build`, когда это имеет смысл для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="4e2a9-139">Добавление новых зависимостей</span><span class="sxs-lookup"><span data-stu-id="4e2a9-139">Adding New Dependencies</span></span>

<span data-ttu-id="4e2a9-140">Одна из важнейших миссий .NET Core — снизить размер установки .NET.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="4e2a9-141">Если для каких-то задач приложению нужны дополнительные библиотеки, добавляйте их в качестве зависимостей в файл проекта C# (\*.csproj).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="4e2a9-142">В нашем примере нужно добавить пакет `System.Runtime.Serialization.Json`, чтобы приложение могло обрабатывать ответы JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="4e2a9-143">Для этого приложения понадобится пакет `System.Runtime.Serialization.Json`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="4e2a9-144">Добавьте его в свой проект, запустив следующую команду [.NET CLI](../../core/tools/dotnet-add-package.md):</span><span class="sxs-lookup"><span data-stu-id="4e2a9-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="4e2a9-145">Выполнение веб-запросов</span><span class="sxs-lookup"><span data-stu-id="4e2a9-145">Making Web Requests</span></span>

<span data-ttu-id="4e2a9-146">Теперь вы готовы получать данные из Интернета.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="4e2a9-147">В этом приложении вы будете считывать информацию из [API GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="4e2a9-148">Давайте, например, получим информацию о проектах под зонтичным брендом [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="4e2a9-149">Для начала вам нужно составить запрос к API GitHub для получения информации о проектах.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="4e2a9-150">Используемая конечная точка: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="4e2a9-151">Вы будете получать все данные об этих проектах, поэтому используйте запрос HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="4e2a9-152">Браузер также использует запросы HTTP GET, поэтому вы можете указать этот URL-адрес в адресной строке браузера и увидеть, какие сведения вы будете получать и обрабатывать.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="4e2a9-153">Для выполнения веб-запросов используется класс <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="4e2a9-154">Как и все современные API-интерфейсы .NET, <xref:System.Net.Http.HttpClient> поддерживает для API-интерфейсов длительного выполнения только асинхронные методы.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="4e2a9-155">Поэтому вам нужно создать асинхронный метод.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-155">Start by making an async method.</span></span> <span data-ttu-id="4e2a9-156">Реализацию вы будете добавлять постепенно, по мере создания функций приложения.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="4e2a9-157">Сначала откройте файл `program.cs`, расположенный в каталоге проекта, и добавьте в класс `Program` следующий метод:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="4e2a9-158">В верхней части метода `Main` нужно добавить директиву `using`, чтобы компилятор C# распознал тип <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="4e2a9-159">Если сейчас вы выполните сборку проекта, то получите предупреждение для этого метода, поскольку он не содержит ни одного оператора `await`, и поэтому будет выполняться синхронно.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="4e2a9-160">Пока это предупреждение можно игнорировать. Операторы `await` здесь появятся по мере заполнения метода.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="4e2a9-161">Затем измените метод `Main`, чтобы он вызывал метод `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="4e2a9-162">Метод `ProcessRepositories` возвращает задачу, до завершения которой выполнение программы не должно прекращаться.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="4e2a9-163">Поэтому следует изменить сигнатуру `Main`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="4e2a9-164">Добавьте модификатор `async` и измените тип возвращаемого значения на `Task`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="4e2a9-165">Затем в теле метода добавьте вызов к `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="4e2a9-166">Добавьте ключевое слово `await` в этот вызов метода.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="4e2a9-167">Теперь у вас есть программа, которая работает в асинхронном режиме, но не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="4e2a9-168">Давайте улучшим ее.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-168">Let's improve it.</span></span>

<span data-ttu-id="4e2a9-169">Для начала нужен объект, который может извлечь данные из Интернета. Для этого подойдет <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="4e2a9-170">Он будет обрабатывать запрос и ответы на него.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-170">This object handles the request and the responses.</span></span> <span data-ttu-id="4e2a9-171">Создайте один экземпляр этого типа в классе `Program` из файла *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="4e2a9-172">Давайте вернемся к методу `ProcessRepositories` и создадим его первую версию.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="4e2a9-173">Чтобы эта версия успешно компилировалась, нужно добавить две новые директивы `using` в верхней части файла.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="4e2a9-174">Эта первая версия метода выполняет веб-запрос для чтения списка всех репозиториев в организации dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="4e2a9-175">(На сайте GitHub организация .NET Foundation имеет идентификатор `dotnet`.) Первые несколько строк настраивают <xref:System.Net.Http.HttpClient> для этого запроса.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-175">(The GitHub ID for the .NET Foundation is `dotnet`.) The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="4e2a9-176">Сначала мы указываем, что он будет принимать ответы GitHub JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-176">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="4e2a9-177">Они возвращаются в простом формате JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-177">This format is simply JSON.</span></span> <span data-ttu-id="4e2a9-178">Следующая строка добавляет заголовок User Agent ко всем запросам от этого объекта.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-178">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="4e2a9-179">Кодом сервера GitHub проверяет эти два заголовка, и их наличие необходимо для извлечения сведений из GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-179">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="4e2a9-180">Когда вы настроите объект <xref:System.Net.Http.HttpClient>, можно выполнить веб-запрос и получить ответ.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-180">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="4e2a9-181">В первой версии используйте удобный метод <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-181">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="4e2a9-182">Этот метод запускает задачу для выполнения веб-запроса, а при получении результатов запроса он считывает поток ответа и извлекает из него содержимое.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-182">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="4e2a9-183">Текст ответа возвращается в формате <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-183">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="4e2a9-184">Эта строка становится доступна после завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-184">The string is available when the task completes.</span></span>

<span data-ttu-id="4e2a9-185">Последние две строки этого метода ожидают выполнения созданной задачи, а затем выводят ответ в консоль.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-185">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="4e2a9-186">Выполните сборку приложения и запустите его.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-186">Build the app, and run it.</span></span> <span data-ttu-id="4e2a9-187">Предупреждение при сборке теперь не отображается, поскольку в методе `ProcessRepositories` есть оператор `await`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-187">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="4e2a9-188">В ответ вы получите длинный текст в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-188">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="4e2a9-189">Обработка результатов JSON</span><span class="sxs-lookup"><span data-stu-id="4e2a9-189">Processing the JSON Result</span></span>

<span data-ttu-id="4e2a9-190">Сейчас у вас уже есть код, который получает от веб-сервера ответ и отображает текст из этого ответа.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-190">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="4e2a9-191">Теперь давайте преобразуем этот ответ JSON в объекты C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-191">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="4e2a9-192">Класс <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> сериализирует объекты в JSON и десериализирует JSON на объекты.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-192">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="4e2a9-193">Начните с определения класса, представляющего объект JSON `repo`, возвращенный из API GitHub:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-193">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="4e2a9-194">Поместите приведенный выше код в новый файл с именем repo.cs.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-194">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="4e2a9-195">Эта версия класса реализует простейший способ обработки данных JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-195">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="4e2a9-196">Имя класса и имя элемента совпадают с именами, используемыми в пакете JSON, и не соответствуют соглашениям C# об именовании.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-196">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="4e2a9-197">Чтобы исправить это, мы позже добавим некоторые атрибуты конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-197">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="4e2a9-198">Этот класс демонстрирует еще одну важную возможность сериализации и десериализации JSON — не все поля в пакете JSON входят в этот класс.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-198">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="4e2a9-199">Сериализатор JSON просто игнорирует информацию, которая не входит в используемый тип класса.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-199">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="4e2a9-200">Такое поведение позволяет легко создавать типы, работающие с любым подмножеством полей из пакета JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-200">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="4e2a9-201">Теперь давайте выполним десериализацию созданного типа.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-201">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="4e2a9-202">Теперь вызовите сериализатор для преобразования пакета JSON в объекты C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-202">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="4e2a9-203">В методе `ProcessRepositories` замените вызов <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> следующими строками.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-203">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="4e2a9-204">Вы используете новое пространство имён, поэтому его также нужно добавить в верхней части файла:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-204">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="4e2a9-205">Обратите внимание, что теперь вы используете <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> вместо <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-205">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="4e2a9-206">Сериализатор использует в качестве источника поток, а не строку.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-206">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="4e2a9-207">Рассмотрим несколько функций языка C#, которые используются во второй строке предыдущего фрагмента кода.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-207">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="4e2a9-208">Первый аргумент <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> является выражением `await`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-208">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="4e2a9-209">(Два других параметра являются необязательными и не включены в фрагмент кода.) Выражения await могут использоваться почти в любом месте кода, хотя пока мы их применяли только в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-209">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="4e2a9-210">Метод `Deserialize` является *общим*, что означает, что необходимо предоставить аргументы типа того, какие объекты следует создать из текста JSON.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-210">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="4e2a9-211">В этом примере выполняется десериализация в `List<Repository>`, который является еще одним общим объектом <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-211">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4e2a9-212">Класс `List<>` хранит коллекцию объектов.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-212">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="4e2a9-213">Аргумент типа определяет тип объектов, хранящихся в `List<>`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-213">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="4e2a9-214">Текст JSON представляет набор объектов репозитория, поэтому аргументом типа является `Repository`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-214">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="4e2a9-215">В этом разделе все почти готово.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-215">You're almost done with this section.</span></span> <span data-ttu-id="4e2a9-216">Вы уже преобразовали JSON в объекты C#, и теперь можете отобразить имена всех репозиториев.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-216">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="4e2a9-217">Удалите вот эти строки кода:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-217">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="4e2a9-218">и замените их следующим фрагментом:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-218">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="4e2a9-219">Скомпилируйте и запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-219">Compile and run the application.</span></span> <span data-ttu-id="4e2a9-220">Оно выведет имена всех репозиториев, которые являются частью .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-220">It will print the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="4e2a9-221">Управление сериализацией</span><span class="sxs-lookup"><span data-stu-id="4e2a9-221">Controlling Serialization</span></span>

<span data-ttu-id="4e2a9-222">Прежде чем добавлять дополнительные функции, давайте обратимся к свойству `name` с помощью атрибута `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-222">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="4e2a9-223">В файле repo.cs внесите следующие изменения в объявление `name`:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-223">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="4e2a9-224">Чтобы использовать атрибут `[JsonPropertyName]`, нужно добавить пространство имен <xref:System.Text.Json.Serialization> в директивы `using`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-224">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="4e2a9-225">Это изменение требует также изменить код в файле program.cs, который записывает имя каждого хранилища:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-225">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="4e2a9-226">Выполните `dotnet run`, чтобы проверить правильность сопоставления.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-226">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="4e2a9-227">Результат выполнения должен быть такой же, как прежде.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-227">You should see the same output as before.</span></span>

<span data-ttu-id="4e2a9-228">И еще одно изменение, прежде чем мы начнем добавлять новые функции.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-228">Let's make one more change before adding new features.</span></span> <span data-ttu-id="4e2a9-229">Метод `ProcessRepositories` может выполнять работу в асинхронном режиме и возвращает коллекцию репозиториев.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-229">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="4e2a9-230">Давайте сделаем так, чтобы этот метод возвращал `List<Repository>`, а сегмент кода, который записывает информацию, переместим в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-230">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="4e2a9-231">Измените сигнатуру `ProcessRepositories`, чтобы этот метод возвращал задачу, результатом которой является список объектов `Repository`:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-231">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="4e2a9-232">Теперь мы можем просто возвращать репозитории после обработки ответа JSON:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-232">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="4e2a9-233">Компилятор создает в качестве выходных данных объект `Task<T>`, поскольку этот метод обозначен ключевым словом `async`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-233">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="4e2a9-234">Теперь мы изменим метод `Main` так, чтобы он записывает эти результаты и выводил в консоль имя каждого репозитория.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-234">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="4e2a9-235">Метод `Main` теперь выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-235">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="4e2a9-236">Получение дополнительных сведений</span><span class="sxs-lookup"><span data-stu-id="4e2a9-236">Reading More Information</span></span>

<span data-ttu-id="4e2a9-237">И в завершении нашего руководства мы обработаем еще несколько свойств, содержащихся в пакете JSON, который отправляется из API GitHub.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-237">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="4e2a9-238">Нет смысла обрабатывать всю информацию, но добавление нескольких свойств поможет продемонстрировать еще несколько возможностей языка C#.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-238">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="4e2a9-239">Сначала добавьте еще несколько простых типов в определение класса `Repository`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-239">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="4e2a9-240">Добавьте в этот класс следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-240">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="4e2a9-241">Для этих свойств применяются встроенные преобразования из строкового типа (который используется в пакетах JSON) в целевой тип.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-241">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="4e2a9-242">Возможно, с типом <xref:System.Uri> вы пока не знакомы.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-242">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="4e2a9-243">Он представляет универсальный код ресурса, например URL-адрес, как в нашем примере.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-243">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="4e2a9-244">Если вы используете типы `Uri` и `int`, а пакет JSON содержит данные, для которых невозможно выполнить преобразование в целевой тип, действие сериализации создает исключение.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-244">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="4e2a9-245">Добавив новые типы, включите их в метод `Main`:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-245">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

<span data-ttu-id="4e2a9-246">На последнем этапе мы добавим сведения о последней операции принудительной отправки.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-246">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="4e2a9-247">Эта информация представлена в ответе JSON в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-247">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="4e2a9-248">Этот формат имеет время в формате UTC, поэтому вы получаете значение <xref:System.DateTime>, свойство <xref:System.DateTime.Kind%2A> которого является <xref:System.DateTimeKind.Utc>.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-248">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="4e2a9-249">Если вы предпочитаете дату, представленную в вашем часовом поясе, вам необходимо написать пользовательский метод преобразования.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-249">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="4e2a9-250">Сначала определите свойство `public`, которое будет содержать представление даты и времени в формате UTC в вашем классе `Repository`, а также свойство `LastPush` `readonly`, которое возвращает дату, преобразованную в местное время:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-250">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="4e2a9-251">Давайте подробнее рассмотрим новые конструкции, которые мы только что определили.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-251">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="4e2a9-252">Свойство `LastPush` определяется с помощью *члена, заданного выражением* для метода доступа `get`.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-252">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="4e2a9-253">Метод доступа `set` не существует.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-253">There is no `set` accessor.</span></span> <span data-ttu-id="4e2a9-254">Именно так в C#, пропуская метод доступа `set`, определяется свойство *только для чтения*.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-254">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="4e2a9-255">(Да, вы можете создать в C# даже свойства *только для записи*, но для них трудно найти применение.)</span><span class="sxs-lookup"><span data-stu-id="4e2a9-255">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="4e2a9-256">Вам осталось только добавить одну инструкцию вывода данных в консоль, и можно будет заново собрать и запустить приложение:</span><span class="sxs-lookup"><span data-stu-id="4e2a9-256">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="4e2a9-257">Теперь версия вашего приложения должна совпадать с [полной версией примера](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="4e2a9-257">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="4e2a9-258">Заключение</span><span class="sxs-lookup"><span data-stu-id="4e2a9-258">Conclusion</span></span>

<span data-ttu-id="4e2a9-259">В этом руководстве вы увидели, как правильно выполнять веб-запросы, анализировать результаты и отображать полученные в них свойства.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-259">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="4e2a9-260">Вы также добавили в свой проект несколько новых пакетов в качестве зависимостей.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-260">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="4e2a9-261">Еще вы увидели примеры некоторых функций языка C#, которые поддерживают объектно-ориентированный подход.</span><span class="sxs-lookup"><span data-stu-id="4e2a9-261">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
