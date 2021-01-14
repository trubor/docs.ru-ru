---
title: Рабочий процесс внутреннего цикла разработки для приложений Docker
description: Узнайте о рабочем процессе внутреннего цикла разработки для приложений Docker.
ms.date: 01/06/2021
ms.openlocfilehash: 78c593890d56a6888d4c4ea6752497918222ebee
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970589"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="1e782-103">Рабочий процесс внутреннего цикла разработки для приложений Docker</span><span class="sxs-lookup"><span data-stu-id="1e782-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="1e782-104">Рабочий процесс внутреннего цикла, охватывающий весь цикл DevOps, начинается на компьютере каждого разработчика, где разработчик локально пишет код приложения на предпочитаемых языках и платформах, а затем тестирует его (рис. 4-21).</span><span class="sxs-lookup"><span data-stu-id="1e782-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="1e782-105">Независимо от выбранного языка и платформы этот рабочий процесс имеет одну общую черту:</span><span class="sxs-lookup"><span data-stu-id="1e782-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="1e782-106">В этом конкретном рабочем процессе вы всегда разрабатываете и тестируете контейнеры Docker не в других средах, а локально.</span><span class="sxs-lookup"><span data-stu-id="1e782-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![Схема, показывающая концепцию среды разработки внутреннего цикла](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="1e782-108">**Рис. 4-21**.</span><span class="sxs-lookup"><span data-stu-id="1e782-108">**Figure 4-21**.</span></span> <span data-ttu-id="1e782-109">Контекст внутреннего цикла разработки</span><span class="sxs-lookup"><span data-stu-id="1e782-109">Inner-loop development context</span></span>

<span data-ttu-id="1e782-110">В каждый контейнер или экземпляр образа Docker входят следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="1e782-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="1e782-111">выбранная операционная система (например, Windows или дистрибутив Linux);</span><span class="sxs-lookup"><span data-stu-id="1e782-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="1e782-112">файлы, добавленные разработчиком (например, двоичные файлы приложения);</span><span class="sxs-lookup"><span data-stu-id="1e782-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="1e782-113">конфигурация (например, параметры среды и зависимости);</span><span class="sxs-lookup"><span data-stu-id="1e782-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="1e782-114">инструкции касательно того, какие процессы должны выполняться Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="1e782-115">Рабочий процесс внутреннего цикла разработки на основе Docker можно настроить как процесс (как описано в следующем разделе).</span><span class="sxs-lookup"><span data-stu-id="1e782-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="1e782-116">Учтите, что начальные этапы настройки среды здесь не рассматриваются, так как они выполняются только один раз.</span><span class="sxs-lookup"><span data-stu-id="1e782-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="1e782-117">Создание одного приложения в контейнере Docker с помощью Visual Studio Code и интерфейса командной строки (CLI) Docker</span><span class="sxs-lookup"><span data-stu-id="1e782-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="1e782-118">Приложение состоит из ваших собственных служб и дополнительных библиотек (зависимостей).</span><span class="sxs-lookup"><span data-stu-id="1e782-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="1e782-119">На рис. 4-22 показаны основные шаги, которые обычно необходимо выполнить при сборке приложения Docker, после чего приводится подробное описание каждого из них.</span><span class="sxs-lookup"><span data-stu-id="1e782-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Схема, на которой показаны семь шагов, необходимых для создания контейнерного приложения.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="1e782-121">**Рис. 4-22**.</span><span class="sxs-lookup"><span data-stu-id="1e782-121">**Figure 4-22**.</span></span> <span data-ttu-id="1e782-122">Высокоуровневое представление рабочего процесса для жизненного цикла контейнерных приложений Docker, создаваемых с помощью CLI Docker</span><span class="sxs-lookup"><span data-stu-id="1e782-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="1e782-123">Шаг 1. Начало программирования в Visual Studio Code и создание первого приложения или базовой службы</span><span class="sxs-lookup"><span data-stu-id="1e782-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="1e782-124">Разработка приложения Docker аналогична разработке приложения без Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="1e782-125">Разница заключается в том, что при разработке развертывание и тестирование приложения или служб, работающих в контейнерах Docker, выполняется в локальной среде (например, в Windows или виртуальной машине Linux).</span><span class="sxs-lookup"><span data-stu-id="1e782-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="1e782-126">**Настройка локальной среды**</span><span class="sxs-lookup"><span data-stu-id="1e782-126">**Setting up your local environment**</span></span>

<span data-ttu-id="1e782-127">С помощью последних версий Docker Desktop для Mac и Windows разрабатывать приложения Docker стало еще легче. Настройка очень проста.</span><span class="sxs-lookup"><span data-stu-id="1e782-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="1e782-128">Инструкции по настройке Docker Desktop для Windows см. на странице <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="1e782-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="1e782-129">Инструкции по настройке Docker Desktop для Mac см. на странице <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="1e782-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="1e782-130">Кроме того, вам потребуется редактор кода для разработки приложения с помощью CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="1e782-131">Корпорация Майкрософт предлагает Visual Studio Code, простой редактор кода, который поддерживается в macOS, Windows и Linux. Он предоставляет технологию IntelliSense с [поддержкой множества языков](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python и большинства современных языков), возможность [отладки](https://code.visualstudio.com/Docs/editor/debugging), [интеграцию с Git](https://code.visualstudio.com/Docs/editor/versioncontrol) и [поддержку расширений](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="1e782-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="1e782-132">Это средство отлично подойдет разработчикам, использующим macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="1e782-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="1e782-133">В Windows также можно использовать Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e782-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="1e782-134">Инструкции по установке Visual Studio Code для Windows, macOS или Linux см. на странице <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="1e782-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="1e782-135">Инструкции по настройке Docker для Mac см. на странице <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="1e782-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="1e782-136">Вы можете использовать CLI Docker и писать код в любом редакторе кода, однако Visual Studio Code в сочетании с расширением Docker упрощает создание файлов `Dockerfile` и `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="1e782-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="1e782-137">Вы также можете выполнять задачи и скрипты из интегрированной среды разработки Visual Studio Code для выполнения команд Docker на базе CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="1e782-138">Расширение Docker для VS Code предоставляет следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="1e782-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="1e782-139">автоматическое создание файлов `Dockerfile` и `docker-compose.yml`;</span><span class="sxs-lookup"><span data-stu-id="1e782-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="1e782-140">выделение синтаксических конструкций и подсказки при наведении для файлов `docker-compose.yml` и `Dockerfile`;</span><span class="sxs-lookup"><span data-stu-id="1e782-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="1e782-141">IntelliSense (варианты завершения) для файлов `Dockerfile` и `docker-compose.yml`;</span><span class="sxs-lookup"><span data-stu-id="1e782-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="1e782-142">статический анализ кода (ошибки и предупреждения) для файлов `Dockerfile`;</span><span class="sxs-lookup"><span data-stu-id="1e782-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="1e782-143">интеграция палитры команд (F1) с наиболее часто используемыми командами Docker;</span><span class="sxs-lookup"><span data-stu-id="1e782-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="1e782-144">интеграция в обозреватель для управления образами и контейнерами;</span><span class="sxs-lookup"><span data-stu-id="1e782-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="1e782-145">развертывание образов из DockerHub и реестров контейнеров Azure в службе приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="1e782-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="1e782-146">Чтобы установить расширение Docker, нажмите клавиши CTRL+SHIFT+P, введите `ext install` и выполните команду "Установить расширение", чтобы открыть список расширений в Marketplace.</span><span class="sxs-lookup"><span data-stu-id="1e782-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="1e782-147">Затем введите **docker**, чтобы отфильтровать результаты, и выберите расширение поддержки Docker, как показано на рис. 4-23.</span><span class="sxs-lookup"><span data-stu-id="1e782-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Расширение Docker для VS Code.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="1e782-149">**Рис. 4-23**.</span><span class="sxs-lookup"><span data-stu-id="1e782-149">**Figure 4-23**.</span></span> <span data-ttu-id="1e782-150">Установка расширения Docker в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1e782-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-nodejs-and-ruby"></a><span data-ttu-id="1e782-151">Шаг 2. Создание файла Dockerfile, связанного с существующим образом (обычная ОС или среды разработки, такие как .NET, Node.js и Ruby)</span><span class="sxs-lookup"><span data-stu-id="1e782-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET, Node.js, and Ruby)</span></span>

<span data-ttu-id="1e782-152">Для каждого собираемого образа и каждого развертываемого контейнера требуется файл `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="1e782-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="1e782-153">Если в приложении имеется только одна пользовательская служба, необходим один файл `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="1e782-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="1e782-154">Но если приложение состоит из нескольких служб (как в архитектуре на основе микрослужб), потребуется по одному файлу `Dockerfile` для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="1e782-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="1e782-155">Файл `DockerFile` обычно находится в корневой папке приложения или службы и содержит команды, которые требуются Docker для настройки и запуска приложения или службы.</span><span class="sxs-lookup"><span data-stu-id="1e782-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="1e782-156">Вы можете создать файл `DockerFile` самостоятельно и добавить его в проект вместе с кодом (node.js, .NET и т. д.) или, если у вас нет опыта работы со средой, воспользоваться приведенным ниже советом.</span><span class="sxs-lookup"><span data-stu-id="1e782-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="1e782-157">При использовании файлов `Dockerfile` и `docker-compose.yml`, связанных с контейнерами Docker, можно следовать указаниям, которые предоставляются расширением Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="1e782-158">Вероятно, в дальнейшем вы будете создавать эти файлы, не прибегая к помощи данного средства, но поначалу оно позволяет ускорить обучение.</span><span class="sxs-lookup"><span data-stu-id="1e782-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="1e782-159">На рис. 4-24 приведены шаги по добавлению файлов Docker в проект с помощью расширения Docker для VS Code.</span><span class="sxs-lookup"><span data-stu-id="1e782-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="1e782-160">Откройте палитру команд, введите "**docker**" и нажмите "**Добавить файлы Docker в рабочую область**".</span><span class="sxs-lookup"><span data-stu-id="1e782-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="1e782-161">Выберите платформу приложения (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="1e782-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="1e782-162">Выберите операционную систему (Linux)</span><span class="sxs-lookup"><span data-stu-id="1e782-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="1e782-163">При необходимости включите дополнительные файлы Docker Compose</span><span class="sxs-lookup"><span data-stu-id="1e782-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="1e782-164">Введите порты для публикации (80, 443)</span><span class="sxs-lookup"><span data-stu-id="1e782-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="1e782-165">Выбор проекта</span><span class="sxs-lookup"><span data-stu-id="1e782-165">Select the project</span></span>

![Действия по добавлению файлов Docker с помощью расширения Docker](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="1e782-167">**Рис. 4-24**.</span><span class="sxs-lookup"><span data-stu-id="1e782-167">**Figure 4-24**.</span></span> <span data-ttu-id="1e782-168">Добавление файлов Docker с помощью команды **Добавить файлы Docker в рабочую область**</span><span class="sxs-lookup"><span data-stu-id="1e782-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="1e782-169">При добавлении файла Dockerfile указывается базовый образ Docker, который необходимо использовать (например, `FROM mcr.microsoft.com/dotnet/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="1e782-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/aspnet`).</span></span> <span data-ttu-id="1e782-170">Обычно пользовательский образ создается на основе базового образа, полученного из официального репозитория в [реестре Docker Hub](https://hub.docker.com/) (например, [образа для .NET](https://hub.docker.com/_/microsoft-dotnet/) или [Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="1e782-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET](https://hub.docker.com/_/microsoft-dotnet/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="1e782-171">Эту процедуру необходимо повторить для каждого проекта в приложении.</span><span class="sxs-lookup"><span data-stu-id="1e782-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="1e782-172">Однако после первого запуска расширение будет запрашивать перезапись созданного файла docker-compose.</span><span class="sxs-lookup"><span data-stu-id="1e782-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="1e782-173">На запрос на перезапись нужно отвечать отказом, чтобы расширение создавало отдельные файлы docker-compose, которые затем можно объединить вручную перед выполнением docker-compose.</span><span class="sxs-lookup"><span data-stu-id="1e782-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="1e782-174">**_Использование существующего официального образа Docker_**</span><span class="sxs-lookup"><span data-stu-id="1e782-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="1e782-175">Использование официального репозитория стека языка с номером версии гарантирует, что на всех компьютерах (включая компьютеры для разработки, тестирования и работы) будут доступны одни и те же функции языка.</span><span class="sxs-lookup"><span data-stu-id="1e782-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="1e782-176">Вот пример файла Dockerfile для контейнера .NET:</span><span class="sxs-lookup"><span data-stu-id="1e782-176">The following is a sample DockerFile for a .NET container:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="1e782-177">В этом случае образ основан на версии 5.0 официального образа Docker ASP.NET Core (мультиархитектурного, для Linux и Windows), что следует из строки `FROM mcr.microsoft.com/dotnet/aspnet:5.0`.</span><span class="sxs-lookup"><span data-stu-id="1e782-177">In this case, the image is based on version 5.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/aspnet:5.0`.</span></span> <span data-ttu-id="1e782-178">(Дополнительные сведения по этой теме см. на страницах [Образ Docker ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet/) и [Образ Docker .NET](https://hub.docker.com/_/microsoft-dotnet/).)</span><span class="sxs-lookup"><span data-stu-id="1e782-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-aspnet/) page and the [.NET Docker Image](https://hub.docker.com/_/microsoft-dotnet/) page).</span></span>

<span data-ttu-id="1e782-179">Кроме того, в файле Dockerfile можно указать, что средство Docker должно прослушивать порт TCP, который будет использоваться во время выполнения (например, порт 80 или 443).</span><span class="sxs-lookup"><span data-stu-id="1e782-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="1e782-180">В Dockerfile можно задать дополнительные параметры конфигурации, в зависимости от используемого языка и платформы.</span><span class="sxs-lookup"><span data-stu-id="1e782-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="1e782-181">Например, строка `ENTRYPOINT` со значением `["dotnet", "WebMvcApplication.dll"]` указывает Docker запускать приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="1e782-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET application.</span></span> <span data-ttu-id="1e782-182">Если для создания и запуска приложения .NET используется пакет SDK и .NET CLI (`dotnet CLI`), этот параметр будет другим.</span><span class="sxs-lookup"><span data-stu-id="1e782-182">If you're using the SDK and the .NET CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="1e782-183">Ключевой момент здесь заключается в том, что строка ENTRYPOINT и другие параметры зависят от языка и платформы, выбранных для приложения.</span><span class="sxs-lookup"><span data-stu-id="1e782-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="1e782-184">Дополнительные сведения о создании образов Docker для приложений .NET см. на странице <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="1e782-184">For more information about building Docker images for .NET applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="1e782-185">Дополнительные сведения о создании собственных образов см. на странице <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="1e782-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="1e782-186">**Использование репозиториев мультиархитектурных образов**</span><span class="sxs-lookup"><span data-stu-id="1e782-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="1e782-187">В репозитории могут содержаться варианты одного и того же образа для разных платформ, например образ Linux и образ Windows.</span><span class="sxs-lookup"><span data-stu-id="1e782-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="1e782-188">Это позволяет поставщикам, таким как Майкрософт, которые создают базовые образы, создать один репозиторий для охвата нескольких платформ (т. е. Windows и Linux).</span><span class="sxs-lookup"><span data-stu-id="1e782-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="1e782-189">Например, репозиторий [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) в реестре Docker Hub обеспечивает поддержку Linux и Windows Nano Server при использовании одного и того же имени образа.</span><span class="sxs-lookup"><span data-stu-id="1e782-189">For example, the [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="1e782-190">При запросе образа [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) с узла Windows извлекается вариант для Windows, а при запросе образа с тем же именем с узла Linux — вариант для Linux.</span><span class="sxs-lookup"><span data-stu-id="1e782-190">Pulling the [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="1e782-191">**_Создание базового образа с нуля_**</span><span class="sxs-lookup"><span data-stu-id="1e782-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="1e782-192">Вы можете создать собственный базовый образ Docker с нуля, как описано в этой [статье](https://docs.docker.com/engine/userguide/eng-image/baseimages/).</span><span class="sxs-lookup"><span data-stu-id="1e782-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="1e782-193">Этот сценарий, вероятно, будет не самым лучшим для тех, кто только начинает работать с Docker, но если вы хотите задать определенные биты базового образа, это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="1e782-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="1e782-194">Шаг 3. Создание пользовательских образов Docker и внедрение в них собственных служб</span><span class="sxs-lookup"><span data-stu-id="1e782-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="1e782-195">Для каждой пользовательской службы в приложении необходимо создать связанный образ.</span><span class="sxs-lookup"><span data-stu-id="1e782-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="1e782-196">Если приложение состоит из одной службы или веб-приложения, достаточно одного образа.</span><span class="sxs-lookup"><span data-stu-id="1e782-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="1e782-197">В рамках "рабочего процесса внешнего цикла DevOps" образы создаются автоматическим процессом сборки при отправке исходного кода в репозиторий Git (непрерывная интеграция), поэтому образы будут создаваться в этой глобальной среде из вашего исходного кода.</span><span class="sxs-lookup"><span data-stu-id="1e782-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="1e782-198">Однако перед переходом к этому внешнему циклу необходимо убедиться в том, что приложение Docker действительно работает правильно, чтобы в систему управления версиями (Git и т. д.) не передавался неправильно работающий код.</span><span class="sxs-lookup"><span data-stu-id="1e782-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="1e782-199">Поэтому каждый разработчик должен вначале полностью выполнить внутренний цикл, чтобы провести тестирование локально, прежде чем отправлять в систему управления версиями полностью готовую функцию или изменение.</span><span class="sxs-lookup"><span data-stu-id="1e782-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="1e782-200">Чтобы создать образ в локальной среде и использовать DockerFile, можно использовать команду docker build, как показано на рис. 4-25, так как она сразу помечает образ и создает образы для всех служб в приложении с помощью простой команды.</span><span class="sxs-lookup"><span data-stu-id="1e782-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![Снимок экрана, показывающий выходные данные команды docker-compose build в консоли.](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="1e782-202">**Рис. 4-25**.</span><span class="sxs-lookup"><span data-stu-id="1e782-202">**Figure 4-25**.</span></span> <span data-ttu-id="1e782-203">Выполнение команды docker build</span><span class="sxs-lookup"><span data-stu-id="1e782-203">Running docker build</span></span>

<span data-ttu-id="1e782-204">При необходимости вместо непосредственного выполнения команды `docker build` из папки проекта можно сначала создать развертываемую папку с нужными библиотеками .NET, выполнив команду `dotnet publish`, а затем использовать команду `docker build`.</span><span class="sxs-lookup"><span data-stu-id="1e782-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="1e782-205">В этом примере создается образ Docker с именем `webapi:latest` (`:latest` — это тег, например определенная версия).</span><span class="sxs-lookup"><span data-stu-id="1e782-205">This example creates a Docker image with the name `webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="1e782-206">Этот шаг можно выполнить для каждого пользовательского образа, который требуется создать для составного приложения Docker с несколькими контейнерами.</span><span class="sxs-lookup"><span data-stu-id="1e782-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="1e782-207">Однако в следующем разделе мы увидим, что это проще сделать с помощью `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="1e782-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="1e782-208">Вы можете найти образы, имеющиеся в локальном репозитории (на компьютере разработки), с помощью команды `docker images`, как показано на рисунке 4-26.</span><span class="sxs-lookup"><span data-stu-id="1e782-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![Выходные данные команды docker images в консоли со списком существующих образов.](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="1e782-210">**Рис. 4-26**.</span><span class="sxs-lookup"><span data-stu-id="1e782-210">**Figure 4-26**.</span></span> <span data-ttu-id="1e782-211">Просмотр существующих образов с помощью команды docker images</span><span class="sxs-lookup"><span data-stu-id="1e782-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="1e782-212">Шаг 4. Определение служб в файле docker-compose.yml при сборке составного приложения Docker с несколькими службами</span><span class="sxs-lookup"><span data-stu-id="1e782-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="1e782-213">В файле `docker-compose.yml` можно задать ряд связанных служб для развертывания в качестве составного приложения с помощью команд развертывания, описанных в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="1e782-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="1e782-214">Создайте этот файл в основной или корневой папке решения. Его содержимое должно быть аналогично приведенному в следующем файле `docker-compose.yml`:</span><span class="sxs-lookup"><span data-stu-id="1e782-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="1e782-215">В данном случае в этом файле определены три службы: служба веб-API (ваша пользовательская служба), веб-приложение и служба Redis (популярная служба кэширования).</span><span class="sxs-lookup"><span data-stu-id="1e782-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="1e782-216">Каждая служба развертывается как контейнер, поэтому для каждой из них требуется определенный образ Docker.</span><span class="sxs-lookup"><span data-stu-id="1e782-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="1e782-217">Для этого конкретного приложения:</span><span class="sxs-lookup"><span data-stu-id="1e782-217">For this particular application:</span></span>

- <span data-ttu-id="1e782-218">Служба веб-API строится на основе DockerFile в каталоге `src/WebApi/Dockerfile`.</span><span class="sxs-lookup"><span data-stu-id="1e782-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="1e782-219">Порт узла 51080 перенаправляется на доступный порт 80 в контейнере `webapi`.</span><span class="sxs-lookup"><span data-stu-id="1e782-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="1e782-220">Служба веб-API зависит от службы Redis.</span><span class="sxs-lookup"><span data-stu-id="1e782-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="1e782-221">Веб-приложение обращается к службе веб-API, используя внутренний адрес: `http://webapi`.</span><span class="sxs-lookup"><span data-stu-id="1e782-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="1e782-222">Служба Redis использует [последний общедоступный образ Redis](https://hub.docker.com/_/redis/), извлеченный из реестра Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="1e782-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="1e782-223">[Redis](https://redis.io/) — это популярная система кэширования для серверных приложений.</span><span class="sxs-lookup"><span data-stu-id="1e782-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="1e782-224">Шаг 5. Сборка и запуск приложения Docker</span><span class="sxs-lookup"><span data-stu-id="1e782-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="1e782-225">Если в приложении имеется только один контейнер, его можно запустить путем развертывания на узле Docker (в виртуальной машине или на физическом сервере).</span><span class="sxs-lookup"><span data-stu-id="1e782-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="1e782-226">Однако если приложение состоит из нескольких служб, его также необходимо _скомпоновать_.</span><span class="sxs-lookup"><span data-stu-id="1e782-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="1e782-227">Давайте рассмотрим разные варианты.</span><span class="sxs-lookup"><span data-stu-id="1e782-227">Let's see the different options.</span></span>

<span data-ttu-id="1e782-228">**_Вариант А. Запуск одного контейнера или службы_**</span><span class="sxs-lookup"><span data-stu-id="1e782-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="1e782-229">Образ Docker можно запустить с помощью команды docker run, как показано в этом примере:</span><span class="sxs-lookup"><span data-stu-id="1e782-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 webapp:latest
```

<span data-ttu-id="1e782-230">Для этого конкретного развертывания мы будем перенаправлять запросы, отправленные на порт 50080 узла, на внутренний порт 80.</span><span class="sxs-lookup"><span data-stu-id="1e782-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="1e782-231">**_Вариант Б. Компоновка и запуск многоконтейнерного приложения_**</span><span class="sxs-lookup"><span data-stu-id="1e782-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="1e782-232">В большинстве корпоративных сценариев приложение Docker будет состоять из нескольких служб.</span><span class="sxs-lookup"><span data-stu-id="1e782-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="1e782-233">В таких случаях можно выполнить команду `docker-compose up` (рис. 4-27), которая использует ранее созданный файл docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="1e782-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="1e782-234">В результате ее выполнения выполняется сборка всех пользовательских образов и развертывается скомпонованное приложение со всеми связанными контейнерами.</span><span class="sxs-lookup"><span data-stu-id="1e782-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![Выходные данные команды docker-compose up в консоли.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="1e782-236">**Рис. 4-27**.</span><span class="sxs-lookup"><span data-stu-id="1e782-236">**Figure 4-27**.</span></span> <span data-ttu-id="1e782-237">Результаты выполнения команды docker-compose up</span><span class="sxs-lookup"><span data-stu-id="1e782-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="1e782-238">После выполнения команды `docker-compose up` приложение и связанные с ним контейнеры развертываются в узле Docker, как показано в представлении виртуальной машины на рисунке 4-28.</span><span class="sxs-lookup"><span data-stu-id="1e782-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Виртуальная машина, в которой выполняются многоконтейнерные приложения.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="1e782-240">**Рис. 4-28**.</span><span class="sxs-lookup"><span data-stu-id="1e782-240">**Figure 4-28**.</span></span> <span data-ttu-id="1e782-241">Виртуальная машина с развернутыми контейнерами Docker</span><span class="sxs-lookup"><span data-stu-id="1e782-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="1e782-242">Шаг 6. Тестирование приложения Docker (в локальной виртуальной машине для непрерывного развертывания)</span><span class="sxs-lookup"><span data-stu-id="1e782-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="1e782-243">Этот шаг будет зависеть от того, что делает ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="1e782-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="1e782-244">В случае простого веб-API Hello World на основе .NET, развернутого в виде единственного контейнера или службы, для доступа к службе достаточно указать TCP-порт из файла Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="1e782-244">In a simple .NET Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="1e782-245">В узле Docker откройте браузер и перейдите на этот сайт. Вы должны увидеть работающее приложение или службу, как показано на рисунке 4-29.</span><span class="sxs-lookup"><span data-stu-id="1e782-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Ответ от localhost/API/values в браузере.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="1e782-247">**Рис. 4-29**.</span><span class="sxs-lookup"><span data-stu-id="1e782-247">**Figure 4-29**.</span></span> <span data-ttu-id="1e782-248">Локальное тестирование приложения Docker с помощью браузера</span><span class="sxs-lookup"><span data-stu-id="1e782-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="1e782-249">Обратите внимание на то, что используется порт 50080, однако внутренние запросы перенаправляются на порт 80, поскольку именно так было выполнено развертывание с помощью команды `docker compose`, как это описывалось ранее.</span><span class="sxs-lookup"><span data-stu-id="1e782-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="1e782-250">Это можно проверить с помощью браузера, используя cURL из терминала, как показано на рис. 4-30.</span><span class="sxs-lookup"><span data-stu-id="1e782-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![Результат cURL, полученный из http://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="1e782-252">**Рис. 4-30**.</span><span class="sxs-lookup"><span data-stu-id="1e782-252">**Figure 4-30**.</span></span> <span data-ttu-id="1e782-253">Локальное тестирование приложения Docker с помощью CURL</span><span class="sxs-lookup"><span data-stu-id="1e782-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="1e782-254">**Отладка контейнера, запущенного в Docker**</span><span class="sxs-lookup"><span data-stu-id="1e782-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="1e782-255">Visual Studio Code поддерживает отладку Docker при использовании Node.js и других платформ, таких как контейнеры .NET.</span><span class="sxs-lookup"><span data-stu-id="1e782-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET containers.</span></span>

<span data-ttu-id="1e782-256">Вы также можете отлаживать контейнеры .NET или .NET Framework в Docker с помощью Visual Studio для Windows или Mac, как описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="1e782-256">You also can debug .NET or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="1e782-257">См. сведения об <https://blog.docker.com/2016/07/live-debugging-docker/>отладке контейнеров Docker Node.js<https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span><span class="sxs-lookup"><span data-stu-id="1e782-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="1e782-258">[Назад](docker-apps-development-environment.md)
> [Вперед](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="1e782-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
