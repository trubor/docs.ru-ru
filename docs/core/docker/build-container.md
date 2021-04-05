---
title: Руководство "Контейнеризация приложений с помощью Docker"
description: Из этого руководства вы узнаете, как контейнеризировать приложение .NET Core с помощью Docker.
ms.date: 03/22/2021
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0a64743046d31badb10b5240a172b6e47c76d3cc
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027898"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="74d04-103">Учебник. Контейнеризация приложения .NET Core</span><span class="sxs-lookup"><span data-stu-id="74d04-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="74d04-104">Из этого руководства вы узнаете, как контейнеризировать приложение .NET Core с помощью Docker.</span><span class="sxs-lookup"><span data-stu-id="74d04-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="74d04-105">Контейнеры имеют множество функций и преимуществ, таких как неизменяемая инфраструктура, предоставление переносимой архитектуры и обеспечение масштабируемости.</span><span class="sxs-lookup"><span data-stu-id="74d04-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="74d04-106">Этот образ можно использовать для создания контейнеров в вашей локальной среде разработки, частном или общедоступном облаке.</span><span class="sxs-lookup"><span data-stu-id="74d04-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="74d04-107">В этом учебнике рассмотрены следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="74d04-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="74d04-108">создать и опубликовать простое приложение .NET Core;</span><span class="sxs-lookup"><span data-stu-id="74d04-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="74d04-109">создать и настроить Dockerfile для .NET Core;</span><span class="sxs-lookup"><span data-stu-id="74d04-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="74d04-110">Создание образа Docker</span><span class="sxs-lookup"><span data-stu-id="74d04-110">Build a Docker image</span></span>
> - <span data-ttu-id="74d04-111">создать и запустить контейнер Docker.</span><span class="sxs-lookup"><span data-stu-id="74d04-111">Create and run a Docker container</span></span>

<span data-ttu-id="74d04-112">Вы также узнаете о задачах сборки и развертывания контейнера Docker для приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="74d04-113">*Платформа Docker* использует *модуль Docker* для быстрой сборки и упаковки приложений в качестве *образов Docker*.</span><span class="sxs-lookup"><span data-stu-id="74d04-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="74d04-114">Эти образы имеют формат *Dockerfile* и предназначены для развертывания и запуска в многоуровневом контейнере.</span><span class="sxs-lookup"><span data-stu-id="74d04-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="74d04-115">Это руководство **не** относится к приложениям ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="74d04-116">Если вы используете ASP.NET Core, см. руководство по [контейнеризации приложений ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images).</span><span class="sxs-lookup"><span data-stu-id="74d04-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74d04-117">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="74d04-117">Prerequisites</span></span>

<span data-ttu-id="74d04-118">Установите следующие необходимые компоненты:</span><span class="sxs-lookup"><span data-stu-id="74d04-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="74d04-119">[Пакет SDK для .NET Core 5.0](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="74d04-119">[.NET Core 5.0 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="74d04-120">Если у вас установлена платформа .NET Core, воспользуйтесь командой `dotnet --info`, чтобы определить версию пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="74d04-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- <span data-ttu-id="74d04-121">[Docker Community Edition](https://www.docker.com/products/docker-desktop).</span><span class="sxs-lookup"><span data-stu-id="74d04-121">[Docker Community Edition](https://www.docker.com/products/docker-desktop)</span></span>
- <span data-ttu-id="74d04-122">Временная рабочая папка для *Dockerfile* и примера приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="74d04-123">В этом руководстве в качестве рабочей папки используется имя *docker-working*.</span><span class="sxs-lookup"><span data-stu-id="74d04-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="74d04-124">Создание приложения .NET Core</span><span class="sxs-lookup"><span data-stu-id="74d04-124">Create .NET Core app</span></span>

<span data-ttu-id="74d04-125">Вам нужно создать приложение .NET Core для выполнения контейнера Docker.</span><span class="sxs-lookup"><span data-stu-id="74d04-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="74d04-126">Откройте терминал, создайте рабочую папку, если вы еще этого не сделали, и войдите в нее.</span><span class="sxs-lookup"><span data-stu-id="74d04-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="74d04-127">Выполните следующую команду в рабочей папке, чтобы создать проект во вложенной папке с именем *app*:</span><span class="sxs-lookup"><span data-stu-id="74d04-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="74d04-128">Дерево папок будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="74d04-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="74d04-129">Команда `dotnet new` создает папку с именем *App* и консольное приложение Hello World.</span><span class="sxs-lookup"><span data-stu-id="74d04-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="74d04-130">Измените каталоги и перейдите в папку *App* из сеанса терминала.</span><span class="sxs-lookup"><span data-stu-id="74d04-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="74d04-131">Используйте команду `dotnet run`, чтобы запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="74d04-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="74d04-132">Приложение запустится и выведет `Hello World!` под командой:</span><span class="sxs-lookup"><span data-stu-id="74d04-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="74d04-133">Шаблон по умолчанию создает приложение, которое выводит текст в терминал и затем завершает работу.</span><span class="sxs-lookup"><span data-stu-id="74d04-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="74d04-134">В этом руководстве описано, как использовать приложение с бесконечным циклом выполнения.</span><span class="sxs-lookup"><span data-stu-id="74d04-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="74d04-135">Откройте файл *Program.cs* в текстовом редакторе.</span><span class="sxs-lookup"><span data-stu-id="74d04-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="74d04-136">Если вы используете Visual Studio Code, в предыдущем сеансе терминала введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="74d04-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="74d04-137">Откроется папка *App*, которая содержит проект в Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="74d04-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="74d04-138">Файл *Program.cs* должен выглядеть как следующий фрагмент кода C#:</span><span class="sxs-lookup"><span data-stu-id="74d04-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="74d04-139">Замените его кодом, который считает числа каждую секунду:</span><span class="sxs-lookup"><span data-stu-id="74d04-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="74d04-140">Сохраните файл и протестируйте программу еще раз с помощью команды `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="74d04-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="74d04-141">Помните, что это приложение выполняется бесконечно.</span><span class="sxs-lookup"><span data-stu-id="74d04-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="74d04-142">Остановите его с помощью команды отмены, нажав клавиши <kbd>CTRL+C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="74d04-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="74d04-143">Ниже представлен пример таких выходных данных:</span><span class="sxs-lookup"><span data-stu-id="74d04-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="74d04-144">Если приложению передать число в командной строке, оно досчитает до такого числа и завершит работу.</span><span class="sxs-lookup"><span data-stu-id="74d04-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="74d04-145">Введите команду `dotnet run -- 5`, чтобы приложение досчитало до пяти.</span><span class="sxs-lookup"><span data-stu-id="74d04-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74d04-146">Все параметры после `--` не передаются команде `dotnet run`, а передаются в приложение.</span><span class="sxs-lookup"><span data-stu-id="74d04-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="74d04-147">Публикация приложения .NET Core</span><span class="sxs-lookup"><span data-stu-id="74d04-147">Publish .NET Core app</span></span>

<span data-ttu-id="74d04-148">Прежде чем добавлять приложение .NET Core в образ Docker, его необходимо опубликовать.</span><span class="sxs-lookup"><span data-stu-id="74d04-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="74d04-149">Рекомендуется, чтобы в контейнере была запущена опубликованная версия приложения.</span><span class="sxs-lookup"><span data-stu-id="74d04-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="74d04-150">Чтобы опубликовать приложение, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="74d04-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="74d04-151">Эта команда компилирует приложение и помещает результат в папку *publish*.</span><span class="sxs-lookup"><span data-stu-id="74d04-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="74d04-152">Путь к папке *publish* из рабочей папки должен быть таким: `.\App\bin\Release\net5.0\publish\`</span><span class="sxs-lookup"><span data-stu-id="74d04-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\net5.0\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="74d04-153">Windows</span><span class="sxs-lookup"><span data-stu-id="74d04-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="74d04-154">Получите список файлов для папки publish из папки *App*, чтобы убедиться, что файл *NetCore.Docker.dll* создан.</span><span class="sxs-lookup"><span data-stu-id="74d04-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\net5.0\publish\

    Directory: C:\Users\dapine\App\bin\Release\net5.0\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="74d04-155">Linux</span><span class="sxs-lookup"><span data-stu-id="74d04-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="74d04-156">Воспользуйтесь командой `ls`, чтобы получить список каталога и проверить, был ли создан файл *NetCore.Docker.dll*.</span><span class="sxs-lookup"><span data-stu-id="74d04-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/net5.0/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="74d04-157">Создание файла Dockerfile</span><span class="sxs-lookup"><span data-stu-id="74d04-157">Create the Dockerfile</span></span>

<span data-ttu-id="74d04-158">Файл *Dockerfile* используется командой `docker build` для создания образа контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="74d04-159">Это текстовый файл с именем *Dockerfile*, не имеющий расширения.</span><span class="sxs-lookup"><span data-stu-id="74d04-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="74d04-160">Создайте файл с именем *Dockerfile* в каталоге, содержащем файл *CSPROJ*, и откройте его в текстовом редакторе.</span><span class="sxs-lookup"><span data-stu-id="74d04-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="74d04-161">В этом учебнике будет использоваться образ среды выполнения ASP.NET Core (который содержит образ среды выполнения .NET Core). Он подходит для консольного приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0
```

> [!NOTE]
> <span data-ttu-id="74d04-162">Образ среды выполнения ASP.NET Core используется намеренно, хотя может использоваться образ `mcr.microsoft.com/dotnet/runtime:5.0`.</span><span class="sxs-lookup"><span data-stu-id="74d04-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/runtime:5.0` image could have been used.</span></span>

<span data-ttu-id="74d04-163">Ключевое слово `FROM` требует полного имени образа контейнера Docker.</span><span class="sxs-lookup"><span data-stu-id="74d04-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="74d04-164">Реестр контейнеров Microsoft (MCR, mcr.microsoft.com) представляет собой коллекцию Docker Hub, в которой размещены общедоступные контейнеры.</span><span class="sxs-lookup"><span data-stu-id="74d04-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="74d04-165">Сегмент `dotnet/core` — это репозиторий контейнеров, а сегмент `aspnet` является именем образа контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="74d04-166">Образ помечается `5.0` для управления версиями.</span><span class="sxs-lookup"><span data-stu-id="74d04-166">The image is tagged with `5.0`, which is used for versioning.</span></span> <span data-ttu-id="74d04-167">Таким образом, `mcr.microsoft.com/dotnet/aspnet:5.0` — это среда выполнения .NET Core 5.0.</span><span class="sxs-lookup"><span data-stu-id="74d04-167">Thus, `mcr.microsoft.com/dotnet/aspnet:5.0` is the .NET Core 5.0 runtime.</span></span> <span data-ttu-id="74d04-168">Убедитесь, что вызываете версию среды выполнения, которая соответствует версии среды выполнения, с которой работает пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="74d04-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="74d04-169">Например, приложение, созданное в предыдущем разделе, использовало пакет SDK для .NET Core 5.0, а базовый образ, указанный в *Dockerfile*, имеет тег **5.0.** .</span><span class="sxs-lookup"><span data-stu-id="74d04-169">For example, the app created in the previous section used the .NET Core 5.0 SDK and the base image referred to in the *Dockerfile* is tagged with **5.0**.</span></span>

<span data-ttu-id="74d04-170">Сохраните файл *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="74d04-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="74d04-171">Структура каталогов рабочей папки должна выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="74d04-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="74d04-172">Некоторые файлы и папки на более глубоком уровне были опущены для экономии места в статье:</span><span class="sxs-lookup"><span data-stu-id="74d04-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──net5.0
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="74d04-173">В терминале выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="74d04-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="74d04-174">Docker обработает все строки файла *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="74d04-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="74d04-175">Символ `.` в команде `docker build` используется, чтобы выполнить с помощью Docker поиск файла *Dockerfile* в текущей папке.</span><span class="sxs-lookup"><span data-stu-id="74d04-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="74d04-176">Эта команда создает образ и локальный репозиторий с именем **counter-image**, который указывает на такой образ.</span><span class="sxs-lookup"><span data-stu-id="74d04-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="74d04-177">После завершения работы этой команды выполните команду `docker images`, чтобы просмотреть список установленных образов:</span><span class="sxs-lookup"><span data-stu-id="74d04-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="74d04-178">Обратите внимание, что два образа имеют одинаковое значение **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="74d04-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="74d04-179">Это связано с тем, что единственная команда в файле *Dockerfile* создает новый образ на основе существующего.</span><span class="sxs-lookup"><span data-stu-id="74d04-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="74d04-180">Добавим в файл *Dockerfile* еще три команды.</span><span class="sxs-lookup"><span data-stu-id="74d04-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="74d04-181">Каждая команда создает новый уровень образа, а последняя команда представляет образ, на который указывает запись в репозитории **counter-image**.</span><span class="sxs-lookup"><span data-stu-id="74d04-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/net5.0/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="74d04-182">Команда `COPY` предписывает Docker скопировать указанную папку на вашем компьютере в папку в контейнере.</span><span class="sxs-lookup"><span data-stu-id="74d04-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="74d04-183">В этом примере папка *publish* копируется в папку с именем *App* в контейнере.</span><span class="sxs-lookup"><span data-stu-id="74d04-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="74d04-184">Команда `WORKDIR` изменяет **текущий каталог** в контейнере на *App*.</span><span class="sxs-lookup"><span data-stu-id="74d04-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="74d04-185">Следующая команда `ENTRYPOINT` используется, чтобы настроить с помощью Docker контейнер для запуска в качестве исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="74d04-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="74d04-186">При запуске контейнера выполняется команда `ENTRYPOINT`.</span><span class="sxs-lookup"><span data-stu-id="74d04-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="74d04-187">После выполнения команды контейнер автоматически остановится.</span><span class="sxs-lookup"><span data-stu-id="74d04-187">When this command ends, the container will automatically stop.</span></span>

> [!TIP]
> <span data-ttu-id="74d04-188">Для повышения безопасности вы можете отказаться от конвейера диагностики.</span><span class="sxs-lookup"><span data-stu-id="74d04-188">For added security, you can opt-out of the diagnostic pipeline.</span></span> <span data-ttu-id="74d04-189">Такой отказ позволяет контейнеру выполняться в режиме только для чтения.</span><span class="sxs-lookup"><span data-stu-id="74d04-189">When you opt-out this allows the container to run as readonly.</span></span> <span data-ttu-id="74d04-190">Для этого укажите переменную среды `COMPlus_EnableDiagnostics` как `0` (непосредственно перед шагом `ENTRYPOINT`).</span><span class="sxs-lookup"><span data-stu-id="74d04-190">In order to do this, specify a `COMPlus_EnableDiagnostics` environment variable as `0` (just before the `ENTRYPOINT` step):</span></span>
>
> ```dockerfile
> ENV COMPlus_EnableDiagnostics=0
> ```

<span data-ttu-id="74d04-191">В окне терминала выполните команду `docker build -t counter-image -f Dockerfile .`, а после ее выполнения — команду `docker images`.</span><span class="sxs-lookup"><span data-stu-id="74d04-191">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/aspnet:5.0
 ---> e6780479db63
Step 2/4 : COPY bin/Release/net5.0/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="74d04-192">Каждая команда в файле *Dockerfile* создает уровень и экземпляр **IMAGE ID**.</span><span class="sxs-lookup"><span data-stu-id="74d04-192">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="74d04-193">Последний экземпляр **IMAGE ID** (ваш идентификатор будет отличаться) имеет значение **cd11c3df9b19**. Теперь вы создадите контейнер на основе этого образа.</span><span class="sxs-lookup"><span data-stu-id="74d04-193">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="74d04-194">Создание контейнера</span><span class="sxs-lookup"><span data-stu-id="74d04-194">Create a container</span></span>

<span data-ttu-id="74d04-195">Теперь, когда у вас есть образ, содержащий приложение, вы можете создать контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-195">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="74d04-196">Контейнер можно создать двумя способами.</span><span class="sxs-lookup"><span data-stu-id="74d04-196">You can create a container in two ways.</span></span> <span data-ttu-id="74d04-197">Сначала создайте остановленный контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-197">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="74d04-198">Команда `docker create` выше создает контейнер на основе образа **counter-image**.</span><span class="sxs-lookup"><span data-stu-id="74d04-198">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="74d04-199">В выходных данных этой команды присутствует **CONTAINER ID** (ваш идентификатор будет отличаться) созданного контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-199">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="74d04-200">Чтобы просмотреть список *всех* контейнеров, воспользуйтесь командой `docker ps -a`:</span><span class="sxs-lookup"><span data-stu-id="74d04-200">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="74d04-201">Управление контейнером</span><span class="sxs-lookup"><span data-stu-id="74d04-201">Manage the container</span></span>

<span data-ttu-id="74d04-202">Контейнер был создан с определенным именем `core-counter`. Для управления контейнером используется это имя.</span><span class="sxs-lookup"><span data-stu-id="74d04-202">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="74d04-203">В следующем примере используется команда `docker start` для запуска контейнера, а затем — команда `docker ps` для отображения только запущенных контейнеров:</span><span class="sxs-lookup"><span data-stu-id="74d04-203">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="74d04-204">Аналогично, команда `docker stop` останавливает контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-204">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="74d04-205">В следующем примере используется команда `docker stop` для остановки контейнера, а затем — команда `docker ps` для подтверждения того, что контейнеры не запущены:</span><span class="sxs-lookup"><span data-stu-id="74d04-205">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="74d04-206">Подключение к контейнеру</span><span class="sxs-lookup"><span data-stu-id="74d04-206">Connect to a container</span></span>

<span data-ttu-id="74d04-207">После запуска контейнера вы можете подключиться к нему, чтобы просмотреть выходные данные.</span><span class="sxs-lookup"><span data-stu-id="74d04-207">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="74d04-208">С помощью команд `docker start` и `docker attach` запустите контейнер и просмотрите поток вывода.</span><span class="sxs-lookup"><span data-stu-id="74d04-208">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="74d04-209">В этом примере команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, используется для отключения от запущенного контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-209">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="74d04-210">Нажатие клавиш завершает процесс в контейнере, если не указано иное, что приведет к остановке контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-210">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="74d04-211">Параметр `--sig-proxy=false` гарантирует, что команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, не остановит процесс в контейнере.</span><span class="sxs-lookup"><span data-stu-id="74d04-211">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="74d04-212">После отключения от контейнера снова подключитесь к нему, чтобы убедиться в том, что он продолжает работать и считать числа.</span><span class="sxs-lookup"><span data-stu-id="74d04-212">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="74d04-213">Удаление контейнера</span><span class="sxs-lookup"><span data-stu-id="74d04-213">Delete a container</span></span>

<span data-ttu-id="74d04-214">В рамках этого руководства предполагается, что вам не нужны контейнеры, которые запущены, но не выполняют полезные действия.</span><span class="sxs-lookup"><span data-stu-id="74d04-214">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="74d04-215">Удалите созданный ранее контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-215">Delete the container you previously created.</span></span> <span data-ttu-id="74d04-216">Если контейнер запущен, остановите его.</span><span class="sxs-lookup"><span data-stu-id="74d04-216">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="74d04-217">В примере ниже выводится список всех контейнеров,</span><span class="sxs-lookup"><span data-stu-id="74d04-217">The following example lists all containers.</span></span> <span data-ttu-id="74d04-218">а затем используется команда `docker rm` для удаления контейнера. После этого выполняется повторная проверка наличия запущенных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="74d04-218">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="74d04-219">Однократный запуск</span><span class="sxs-lookup"><span data-stu-id="74d04-219">Single run</span></span>

<span data-ttu-id="74d04-220">Docker предоставляет единую команду `docker run` для создания и запуска контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-220">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="74d04-221">Она исключает необходимость в поочередном выполнении команд `docker create` и `docker start`.</span><span class="sxs-lookup"><span data-stu-id="74d04-221">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="74d04-222">Вы также можете настроить ее для автоматического удаления контейнера при его остановке.</span><span class="sxs-lookup"><span data-stu-id="74d04-222">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="74d04-223">Например, команда `docker run -it --rm` выполняет две операции. Сначала она автоматически подключается к контейнеру с помощью текущего терминала, а потом, после завершения работы контейнера, удаляет его:</span><span class="sxs-lookup"><span data-stu-id="74d04-223">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="74d04-224">Контейнер также передает параметры в выполнение приложения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-224">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="74d04-225">Чтобы указать приложению .NET Core считать только до 3, передайте 3.</span><span class="sxs-lookup"><span data-stu-id="74d04-225">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="74d04-226">Во время выполнения `docker run -it` команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, остановит процесс, запущенный в контейнере. А это, в свою очередь, приведет к остановке контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-226">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="74d04-227">Так как в команде указан параметр `--rm`, контейнер автоматически удалится после остановки процесса.</span><span class="sxs-lookup"><span data-stu-id="74d04-227">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="74d04-228">Убедитесь, что он больше не существует:</span><span class="sxs-lookup"><span data-stu-id="74d04-228">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="74d04-229">Изменение команды ENTRYPOINT</span><span class="sxs-lookup"><span data-stu-id="74d04-229">Change the ENTRYPOINT</span></span>

<span data-ttu-id="74d04-230">Команда `docker run` также позволяет изменить команду `ENTRYPOINT` из файла *Dockerfile* для запуска другой программы, но только для соответствующего контейнера.</span><span class="sxs-lookup"><span data-stu-id="74d04-230">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="74d04-231">Например, воспользуйтесь указанной ниже командой, чтобы запустить `bash` или `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="74d04-231">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="74d04-232">При необходимости измените команду.</span><span class="sxs-lookup"><span data-stu-id="74d04-232">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="74d04-233">Windows</span><span class="sxs-lookup"><span data-stu-id="74d04-233">Windows</span></span>](#tab/windows)

<span data-ttu-id="74d04-234">В этом примере команда `ENTRYPOINT` изменена на `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="74d04-234">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="74d04-235">Нажав клавиши <kbd>CTRL+C</kbd>, вы можете завершить процесс и остановить контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-235"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="74d04-236">Linux</span><span class="sxs-lookup"><span data-stu-id="74d04-236">Linux</span></span>](#tab/linux)

<span data-ttu-id="74d04-237">В этом примере команда `ENTRYPOINT` изменена на `bash`.</span><span class="sxs-lookup"><span data-stu-id="74d04-237">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="74d04-238">Команда `exit` позволяет завершить процесс и остановить контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-238">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="74d04-239">Основные команды</span><span class="sxs-lookup"><span data-stu-id="74d04-239">Essential commands</span></span>

<span data-ttu-id="74d04-240">В Docker есть множество различных команд, которые создают контейнеры и образы, управляют ими, а также взаимодействуют с ними.</span><span class="sxs-lookup"><span data-stu-id="74d04-240">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="74d04-241">Для управления контейнерами в основном используются такие команды Docker:</span><span class="sxs-lookup"><span data-stu-id="74d04-241">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="74d04-242">docker build</span><span class="sxs-lookup"><span data-stu-id="74d04-242">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="74d04-243">docker run</span><span class="sxs-lookup"><span data-stu-id="74d04-243">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="74d04-244">docker ps</span><span class="sxs-lookup"><span data-stu-id="74d04-244">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="74d04-245">docker stop</span><span class="sxs-lookup"><span data-stu-id="74d04-245">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="74d04-246">docker rm</span><span class="sxs-lookup"><span data-stu-id="74d04-246">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="74d04-247">docker rmi</span><span class="sxs-lookup"><span data-stu-id="74d04-247">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="74d04-248">docker image</span><span class="sxs-lookup"><span data-stu-id="74d04-248">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="74d04-249">Очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="74d04-249">Clean up resources</span></span>

<span data-ttu-id="74d04-250">В этом учебнике описано, как создать контейнеры и образы.</span><span class="sxs-lookup"><span data-stu-id="74d04-250">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="74d04-251">При желании эти ресурсы можно удалить.</span><span class="sxs-lookup"><span data-stu-id="74d04-251">If you want, delete these resources.</span></span> <span data-ttu-id="74d04-252">Ниже представлены команды, которые позволяют сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="74d04-252">Use the following commands to</span></span>

01. <span data-ttu-id="74d04-253">Вывести список всех контейнеров.</span><span class="sxs-lookup"><span data-stu-id="74d04-253">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="74d04-254">Остановить запущенные контейнеры по имени.</span><span class="sxs-lookup"><span data-stu-id="74d04-254">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="74d04-255">Удалить контейнер.</span><span class="sxs-lookup"><span data-stu-id="74d04-255">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="74d04-256">Затем удалите все ненужные образы на компьютере.</span><span class="sxs-lookup"><span data-stu-id="74d04-256">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="74d04-257">Удалите образ, созданный с помощью файла *Dockerfile*, а затем удалите образ .NET Core, на основе которого был создан файл *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="74d04-257">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="74d04-258">Вы можете использовать значение **IMAGE ID** или строку в формате **РЕПОЗИТОРИЙ:МЕТКА**.</span><span class="sxs-lookup"><span data-stu-id="74d04-258">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/aspnet:5.0
```

<span data-ttu-id="74d04-259">С помощью команды `docker images` просмотрите список установленных образов.</span><span class="sxs-lookup"><span data-stu-id="74d04-259">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="74d04-260">Файлы образов могут иметь большой размер.</span><span class="sxs-lookup"><span data-stu-id="74d04-260">Image files can be large.</span></span> <span data-ttu-id="74d04-261">Как правило, удаляются временные контейнеры, созданные в ходе тестирования и разработки приложения.</span><span class="sxs-lookup"><span data-stu-id="74d04-261">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="74d04-262">При этом рекомендуется оставить базовые образы с установленной средой выполнения, если на ее основе вы планируете создавать другие образы.</span><span class="sxs-lookup"><span data-stu-id="74d04-262">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74d04-263">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="74d04-263">Next steps</span></span>

- [<span data-ttu-id="74d04-264">Узнайте, как упаковать в контейнер приложение ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-264">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="74d04-265">Изучите руководство по микрослужбам ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d04-265">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="74d04-266">Узнайте больше о службах Azure, которые поддерживают контейнеры.</span><span class="sxs-lookup"><span data-stu-id="74d04-266">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="74d04-267">Ознакомьтесь с командами Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="74d04-267">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="74d04-268">Изучите инструменты Visual Studio для контейнеров</span><span class="sxs-lookup"><span data-stu-id="74d04-268">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
