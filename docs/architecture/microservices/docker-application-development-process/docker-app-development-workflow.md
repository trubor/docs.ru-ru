---
title: Рабочий процесс разработки для приложений Docker
description: Сведения о рабочем процессе для разработки приложений Docker. Начнем по шагам, рассмотрим подробности оптимизации файлов Dockerfile и закончим на упрощенном рабочем процессе, доступном при использовании Visual Studio.
ms.date: 01/13/2021
ms.openlocfilehash: fff0a59bb6001eeb50c31c68bfeceeb71c439223
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189552"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="dee32-104">Рабочий процесс разработки для приложений Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="dee32-105">Жизненный цикл разработки приложений начинается на компьютере разработчика, где разработчик локально программирует приложение на предпочитаемом языке и тестирует его.</span><span class="sxs-lookup"><span data-stu-id="dee32-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="dee32-106">Независимо от выбранного языка, инфраструктуры и платформы, в рамках этого рабочего процесса разработчик всегда разрабатывает и тестирует контейнеры Docker, но делает это локально.</span><span class="sxs-lookup"><span data-stu-id="dee32-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="dee32-107">В каждый контейнер (экземпляр образа Docker) входят следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="dee32-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="dee32-108">Выбранная операционная система (например, дистрибутив Linux, Windows Nano Server или Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="dee32-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="dee32-109">Файлы, добавленные во время разработки, например исходный код и двоичные файлы и приложения.</span><span class="sxs-lookup"><span data-stu-id="dee32-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="dee32-110">Сведения о конфигурации, например параметры среды и зависимости.</span><span class="sxs-lookup"><span data-stu-id="dee32-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="dee32-111">Рабочий процесс разработки приложений Docker на основе контейнера</span><span class="sxs-lookup"><span data-stu-id="dee32-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="dee32-112">В этом разделе описывается рабочий процесс *внутреннего цикла* разработки приложений на основе контейнера Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="dee32-113">Рабочий процесс внутреннего цикла означает, что речь идет только о разработке, которая выполняется на компьютере разработчика, не касаясь более широкого рабочего процесса DevOps.</span><span class="sxs-lookup"><span data-stu-id="dee32-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="dee32-114">Начальные этапы настройки среды здесь не рассматриваются, так как они выполняются только один раз.</span><span class="sxs-lookup"><span data-stu-id="dee32-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="dee32-115">Приложение состоит из ваших собственных служб и дополнительных библиотек (зависимостей).</span><span class="sxs-lookup"><span data-stu-id="dee32-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="dee32-116">Ниже приведены основные шаги, которые обычно выполняются при сборке приложения Docker, как показано на рисунке 5-1.</span><span class="sxs-lookup"><span data-stu-id="dee32-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Схема, на которой показаны семь шагов, необходимых для создания контейнерного приложения.":::
<span data-ttu-id="dee32-118">Процесс разработки для приложений на основе Docker: 1) создайте код приложения; 2) напишите файлы Dockerfile; 3) создайте образы, определенные в файлах Dockerfile; 4) (необязательно) создайте службы в файле docker-compose.yml; 5) запустите контейнер или приложение docker-compose; 6) проведите тестирование приложений или микрослужб; 7) отправьте все в репозиторий и повторите.</span><span class="sxs-lookup"><span data-stu-id="dee32-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="dee32-119">**Рис. 5-1**.</span><span class="sxs-lookup"><span data-stu-id="dee32-119">**Figure 5-1.**</span></span> <span data-ttu-id="dee32-120">Пошаговый рабочий процесс разработки приложения на основе контейнера Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="dee32-121">В этом разделе подробно описывается весь процесс, и каждый важный шаг объясняется с акцентом на среду Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee32-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="dee32-122">Если разработка выполняется с помощью редактора и CLI (например, Visual Studio Code и Docker CLI на macOS или Windows), то необходимо знать каждый шаг и обычно более детально, чем при использовании Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee32-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="dee32-123">Дополнительные сведения о работе в среде CLI см. в электронной книге [Жизненный цикл приложений в контейнерах Docker с платформами и средствами Майкрософт](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="dee32-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="dee32-124">При использовании Visual Studio 2019 многие из этих шагов выполняются автоматически, что значительно повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="dee32-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="dee32-125">Это особенно справедливо в тех случаях, когда используется Visual Studio 2019 и планируется создание многоконтейнерных приложений.</span><span class="sxs-lookup"><span data-stu-id="dee32-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="dee32-126">Например, всего лишь одним щелчком мыши Visual Studio добавляет `Dockerfile` и файл `docker-compose.yml` в проекты с конфигурацией для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="dee32-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="dee32-127">При запуске приложения в Visual Studio он создает образ Docker и запускает многоконтейнерное приложение непосредственно в Docker; вы даже можете отлаживать несколько контейнеров одновременно.</span><span class="sxs-lookup"><span data-stu-id="dee32-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="dee32-128">Эти возможности значительно повышают скорость разработки.</span><span class="sxs-lookup"><span data-stu-id="dee32-128">These features will boost your development speed.</span></span>

<span data-ttu-id="dee32-129">Однако то, что Visual Studio автоматизирует эти действия, не означает, что вам не нужно знать, что происходит внутри Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="dee32-130">Таким образом, каждый шаг подробно описывается в следующих рекомендациях.</span><span class="sxs-lookup"><span data-stu-id="dee32-130">Therefore, the following guidance details every step.</span></span>

![Изображение для шага 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="dee32-132">Шаг 1.</span><span class="sxs-lookup"><span data-stu-id="dee32-132">Step 1.</span></span> <span data-ttu-id="dee32-133">Начало программирования и создание первого приложения или базовой службы</span><span class="sxs-lookup"><span data-stu-id="dee32-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="dee32-134">Разработка приложения Docker аналогична разработке приложения без Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="dee32-135">Разница заключается в том, что при разработке для Docker развертывание и тестирование приложения или служб, работающих в контейнерах Docker, выполняется в локальной среде (в ВМ Linux или напрямую в Windows, если используются контейнеры Windows).</span><span class="sxs-lookup"><span data-stu-id="dee32-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="dee32-136">Настройка локальной среды с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="dee32-137">Перед началом работы убедитесь, что [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) для Windows установлен, как описано в следующих инструкциях:</span><span class="sxs-lookup"><span data-stu-id="dee32-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="dee32-138">Начало работы с Docker CE для Windows</span><span class="sxs-lookup"><span data-stu-id="dee32-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="dee32-139">Кроме того, вам нужна Visual Studio 2019 (версия 16.4 или более поздняя) с установленной рабочей нагрузкой **Кроссплатформенная разработка .NET Core**, как показано на рис. 5.2.</span><span class="sxs-lookup"><span data-stu-id="dee32-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Снимок экрана: выбор рабочей нагрузки "Кроссплатформенная разработка .NET Core".](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="dee32-141">**Рис. 5-2**.</span><span class="sxs-lookup"><span data-stu-id="dee32-141">**Figure 5-2**.</span></span> <span data-ttu-id="dee32-142">Выбор рабочей нагрузки **Кроссплатформенная разработка .NET Core** при установке Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="dee32-143">Можно приступать к программированию приложения в обычной среде .NET (как правило, в .NET Core и более поздних версий, если вы планируете использовать контейнеры) даже до включения Docker в вашем приложении и развертывания и тестирования в Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-143">You can start coding your application in plain .NET (usually in .NET Core or later if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="dee32-144">Тем не менее рекомендуется начать работу в Docker как можно быстрее, поскольку это будет реальная среда, и любые проблемы можно будет обнаружить гораздо раньше.</span><span class="sxs-lookup"><span data-stu-id="dee32-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="dee32-145">Это также рекомендуется потому, что Visual Studio настолько упрощает работу с Docker, что практически все действия очевидны; лучший пример — отладка многоконтейнерного приложения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee32-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-146">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-146">Additional resources</span></span>

- <span data-ttu-id="dee32-147">**Начало работы с Docker CE для Windows** </span><span class="sxs-lookup"><span data-stu-id="dee32-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="dee32-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="dee32-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Изображение для шага 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="dee32-150">Шаг 2.</span><span class="sxs-lookup"><span data-stu-id="dee32-150">Step 2.</span></span> <span data-ttu-id="dee32-151">Создание файла Dockerfile, связанного с существующим базовым образом .NET</span><span class="sxs-lookup"><span data-stu-id="dee32-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="dee32-152">Dockerfile необходим для каждого пользовательского образа, который вы хотите создать; кроме того, Dockerfile потребуется для каждого контейнера, который будет развертываться автоматически из Visual Studio или вручную с помощью Docker CLI (с помощью команд docker run и docker-compose).</span><span class="sxs-lookup"><span data-stu-id="dee32-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="dee32-153">Если в приложении имеется единственный экземпляр пользовательской службы, необходим один Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dee32-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="dee32-154">Если в приложении имеется несколько служб (как в архитектуре на основе микрослужб), потребуется по одному Dockerfile для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="dee32-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="dee32-155">Dockerfile размещается в корневой папке приложения или службы.</span><span class="sxs-lookup"><span data-stu-id="dee32-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="dee32-156">Он содержит команды, которые указывают Docker, как настраивать и запускать приложение или службу в контейнере.</span><span class="sxs-lookup"><span data-stu-id="dee32-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="dee32-157">Можно вручную создать Dockerfile в коде и добавить его в проект вместе с зависимостями .NET.</span><span class="sxs-lookup"><span data-stu-id="dee32-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="dee32-158">В Visual Studio со средствами для Docker эта задача выполняется лишь несколькими щелчками мыши.</span><span class="sxs-lookup"><span data-stu-id="dee32-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="dee32-159">При создании нового проекта в Visual Studio 2019 можно выбрать параметр **Enable Docker Support** (Включить поддержку Docker), как показано на рисунке 5-3.</span><span class="sxs-lookup"><span data-stu-id="dee32-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Снимок экрана: флажок Enable Docker Support (Включить поддержку Docker).](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="dee32-161">**Рис. 5-3**.</span><span class="sxs-lookup"><span data-stu-id="dee32-161">**Figure 5-3**.</span></span> <span data-ttu-id="dee32-162">Включение поддержки Docker при создании нового проекта ASP.NET Core в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="dee32-163">Поддержку Docker в существующий проект веб-приложения ASP.NET Core можно также включить, щелкнув правой кнопкой мыши проект в **обозревателе решений** и выбрав **Добавить** > **Поддержка Docker**, как показано на рисунке 5-4.</span><span class="sxs-lookup"><span data-stu-id="dee32-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Снимок экрана: пункт "Поддержка Docker" в меню "Добавить".](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="dee32-165">**Рис. 5-4**.</span><span class="sxs-lookup"><span data-stu-id="dee32-165">**Figure 5-4**.</span></span> <span data-ttu-id="dee32-166">Включение поддержки Docker в существующем проекте Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="dee32-167">Это действие добавляет *Dockerfile* в проект с необходимой конфигурацией и доступно только для проектов ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dee32-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="dee32-168">Аналогичным образом, Visual Studio также позволяет добавить файл `docker-compose.yml` для всего решения при помощи параметра **Добавить > Поддержка оркестратора контейнеров**. На шаге 4 мы рассмотрим этот параметр более подробно.</span><span class="sxs-lookup"><span data-stu-id="dee32-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="dee32-169">Использование существующего официального образа .NET Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="dee32-170">Обычно вы создаете пользовательский образ для своего контейнера на основе базового образа, который можно получить из официального репозитория, например через реестр [Центра Docker](https://hub.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="dee32-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="dee32-171">Именно это происходит на внутреннем уровне при включении поддержки Docker в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee32-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="dee32-172">Ваш Dockerfile будет использовать существующий образ `dotnet/core/aspnet`.</span><span class="sxs-lookup"><span data-stu-id="dee32-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="dee32-173">Ранее было показано, какие образы и репозитории Docker можно использовать в зависимости от выбранной платформы и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="dee32-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="dee32-174">Например, если вы выбрали ASP.NET Core (Windows или Linux), следует использовать образ `mcr.microsoft.com/dotnet/aspnet:5.0`.</span><span class="sxs-lookup"><span data-stu-id="dee32-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/aspnet:5.0`.</span></span> <span data-ttu-id="dee32-175">Таким образом, достаточно просто указать, какой базовый образ Docker будет использоваться для контейнера.</span><span class="sxs-lookup"><span data-stu-id="dee32-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="dee32-176">Для этого добавьте `FROM mcr.microsoft.com/dotnet/aspnet:5.0` в свой Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dee32-176">You do that by adding `FROM mcr.microsoft.com/dotnet/aspnet:5.0` to your Dockerfile.</span></span> <span data-ttu-id="dee32-177">Visual Studio выполнит это автоматически, но в случае обновления версии вы обновляете это значение.</span><span class="sxs-lookup"><span data-stu-id="dee32-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="dee32-178">Использование официального репозитория образов .NET из Центра Docker с номером версии гарантирует, что на всех компьютерах (включая компьютеры для разработки, тестирования и работы) будут доступны одни и те же функции языка.</span><span class="sxs-lookup"><span data-stu-id="dee32-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="dee32-179">Ниже приведен пример Dockerfile для контейнера ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dee32-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="dee32-180">В этом случае образ основан на версии 5.0 официального образа Docker ASP.NET Core (несколько архитектур, для Linux и Windows).</span><span class="sxs-lookup"><span data-stu-id="dee32-180">In this case, the image is based on version 5.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="dee32-181">Это параметр `FROM mcr.microsoft.com/dotnet/aspnet:5.0`.</span><span class="sxs-lookup"><span data-stu-id="dee32-181">This is the setting `FROM mcr.microsoft.com/dotnet/aspnet:5.0`.</span></span> <span data-ttu-id="dee32-182">(Дополнительные сведения об этом базовом образе см. на странице [Образ ASP.NET Core Docker](https://hub.docker.com/_/microsoft-dotnet-aspnet/).) Кроме того, в Dockerfile необходимо указать Docker прослушивать порт TCP, который будет использоваться во время выполнения (в данном случае это порт 80, как задано в параметре EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="dee32-182">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-aspnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="dee32-183">В Dockerfile можно задать дополнительные параметры конфигурации, в зависимости от используемого языка и платформы.</span><span class="sxs-lookup"><span data-stu-id="dee32-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="dee32-184">Например, параметр ENTRYPOINT со значением `["dotnet", "MySingleContainerWebApp.dll"]` указывает Docker запускать приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="dee32-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET application.</span></span> <span data-ttu-id="dee32-185">Если для создания и запуска приложения .NET используется пакет SDK и .NET CLI (dotnet CLI), этот параметр будет другим.</span><span class="sxs-lookup"><span data-stu-id="dee32-185">If you're using the SDK and the .NET CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="dee32-186">Параметр ENTRYPOINT, который находится в нижней строке, и другие параметры будут отличаться в зависимости от языка и платформы, выбранных для приложения.</span><span class="sxs-lookup"><span data-stu-id="dee32-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-187">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-187">Additional resources</span></span>

- <span data-ttu-id="dee32-188">**Создание образов Docker для приложений .NET 5** </span><span class="sxs-lookup"><span data-stu-id="dee32-188">**Building Docker Images for .NET 5 Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="dee32-189">**Создание собственного образа**.</span><span class="sxs-lookup"><span data-stu-id="dee32-189">**Build your own image**.</span></span> <span data-ttu-id="dee32-190">В официальной документации Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="dee32-191">**Следите за образами контейнеров .NET** </span><span class="sxs-lookup"><span data-stu-id="dee32-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="dee32-192">**Совместное использование .NET и Docker — новости с DockerCon 2018** </span><span class="sxs-lookup"><span data-stu-id="dee32-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="dee32-193">Использование мультиархитектурных репозиториев</span><span class="sxs-lookup"><span data-stu-id="dee32-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="dee32-194">Один репозиторий может содержать варианты платформ, например образ Linux и образ Windows.</span><span class="sxs-lookup"><span data-stu-id="dee32-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="dee32-195">Эта функция позволяет поставщикам, таким как Майкрософт, которые создают базовые образы, создать один репозиторий для охвата нескольких платформ (т. е. Windows и Linux).</span><span class="sxs-lookup"><span data-stu-id="dee32-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="dee32-196">Например, репозиторий [dotnet/core](https://hub.docker.com/_/microsoft-dotnet/) в реестре Центра Docker обеспечивает поддержку Linux и Windows Nano Server при использовании одного и того же имени репозитория.</span><span class="sxs-lookup"><span data-stu-id="dee32-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="dee32-197">Можно указать тег, явно задающий платформу, как в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="dee32-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim` \
  <span data-ttu-id="dee32-198">Цели: среда выполнения .NET 5, только на Linux</span><span class="sxs-lookup"><span data-stu-id="dee32-198">Targets: .NET 5 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1909` \
  <span data-ttu-id="dee32-199">Цели: среда выполнения .NET 5, только на Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="dee32-199">Targets: .NET 5 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="dee32-200">Появилась возможность указывать одно и то же имя образа, даже с одинаковым тегом, и новые мультиархитектурные образы (например, образ `aspnet`) будут использовать версию Windows или Linux в зависимости от развернутой базовой ОС Docker, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="dee32-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/aspnet:5.0` \
  <span data-ttu-id="dee32-201">Несколько архитектур: среда выполнения .NET 5, поддерживающая Linux и Windows Nano Server, в зависимости от базовой ОС Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-201">Multi-arch: .NET 5 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="dee32-202">Таким образом, при запросе образа с узла Windows будет получен вариант для Windows, а при запросе образа с тем же именем с узла Linux будет получен вариант для Linux.</span><span class="sxs-lookup"><span data-stu-id="dee32-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="dee32-203">Многоэтапная сборка в файле Dockerfile</span><span class="sxs-lookup"><span data-stu-id="dee32-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="dee32-204">Dockerfile похож на пакетный сценарий.</span><span class="sxs-lookup"><span data-stu-id="dee32-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="dee32-205">Он похож на действия в ситуации, если бы вам необходимо было установить что-то на компьютере из командной строки.</span><span class="sxs-lookup"><span data-stu-id="dee32-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="dee32-206">Он начинается с базового образа, который задает начальный контекст; это как начальная файловая система, которая надстраивается над базовой ОС.</span><span class="sxs-lookup"><span data-stu-id="dee32-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="dee32-207">Это не ОС в строгом смысле, но можно представить его как "ОС внутри контейнера".</span><span class="sxs-lookup"><span data-stu-id="dee32-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="dee32-208">Выполнение каждой командной строки создает новый слой в файловой системе с изменениями от предыдущего таким образом, чтобы при их объединении создавалась результирующая файловая система.</span><span class="sxs-lookup"><span data-stu-id="dee32-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="dee32-209">Поскольку каждый новый уровень "накладывается" на предыдущий и итоговый размер образа увеличивается с каждой командой, образы могут становиться очень большими, если они включают, например, пакет SDK для сборки и публикации приложения.</span><span class="sxs-lookup"><span data-stu-id="dee32-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="dee32-210">Здесь в дело вступает многоэтапная сборка (в Docker 17.05 и более поздних версий), творя настоящие чудеса.</span><span class="sxs-lookup"><span data-stu-id="dee32-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="dee32-211">Основная ее идея в том, что можно разделить процесс выполнения Dockerfile на этапы; каждый этап — исходный образ, за которым следуют команды, а последний этап определяет размер окончательного образа.</span><span class="sxs-lookup"><span data-stu-id="dee32-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="dee32-212">Короче говоря, многоэтапная сборка позволяет разделить создание образа на этапы и затем собрать окончательный образ, используя только соответствующие каталоги из промежуточных этапов.</span><span class="sxs-lookup"><span data-stu-id="dee32-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="dee32-213">Общая стратегия использования этой функции такова:</span><span class="sxs-lookup"><span data-stu-id="dee32-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="dee32-214">Использовать базовый образ пакета SDK (его размер не имеет значения), где есть все необходимое для сборки и публикации приложения в папке.</span><span class="sxs-lookup"><span data-stu-id="dee32-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="dee32-215">Затем использовать небольшой базовый образ времени выполнения и скопировать папку публикации из предыдущего этапа для создания небольшого окончательного образа.</span><span class="sxs-lookup"><span data-stu-id="dee32-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="dee32-216">Возможно, лучший способ понять, как работает многоэтапный процесс, — это пройти в файле Dockerfile по каждой строке; давайте начнем с базового файла Dockerfile, созданного с помощью Visual Studio при добавлении поддержки Docker в проект, чтобы позже внести некоторые оптимизации.</span><span class="sxs-lookup"><span data-stu-id="dee32-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="dee32-217">Исходный файл Dockerfile может выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dee32-217">The initial Dockerfile might look something like this:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="dee32-218">И вот подробности, по одной строке:</span><span class="sxs-lookup"><span data-stu-id="dee32-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="dee32-219">**Строка 1.** Начнем этап с небольшого базового образа времени выполнения, назвав его **base**.</span><span class="sxs-lookup"><span data-stu-id="dee32-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="dee32-220">**Строка 2.** Создайте в образе каталог **/app**.</span><span class="sxs-lookup"><span data-stu-id="dee32-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="dee32-221">**Строка 3.** Откройте порт **80**.</span><span class="sxs-lookup"><span data-stu-id="dee32-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="dee32-222">**Строка 5.** Начнем новый этап с крупного образа для сборки и публикации.</span><span class="sxs-lookup"><span data-stu-id="dee32-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="dee32-223">Назовем его **build**.</span><span class="sxs-lookup"><span data-stu-id="dee32-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="dee32-224">**Строка 6.** Создайте в образе каталог **/src**.</span><span class="sxs-lookup"><span data-stu-id="dee32-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="dee32-225">**Строка 7.** Скопируйте указанные файлы проектов **.csproj** до строки 16, чтобы иметь возможность восстановить пакеты позже.</span><span class="sxs-lookup"><span data-stu-id="dee32-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="dee32-226">**Строка 17.** Восстановите пакеты для проекта **Catalog.API** и связанных проектов.</span><span class="sxs-lookup"><span data-stu-id="dee32-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="dee32-227">**Строка 18.** Скопируйте **все дерево каталогов решения** (за исключением файлов и каталогов, включенных в файл **.dockerignore**) в каталог **/src** в образе.</span><span class="sxs-lookup"><span data-stu-id="dee32-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="dee32-228">**Строка 19.** Укажите в качестве текущей папки проект **Catalog.API**.</span><span class="sxs-lookup"><span data-stu-id="dee32-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="dee32-229">**Строка 20.** Скомпилируйте проект (и другие зависимости проекта) и поместите его в каталог проекта **/app** в образе.</span><span class="sxs-lookup"><span data-stu-id="dee32-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="dee32-230">**Строка 22.** Начните новый этап, продолжая работу со сборкой.</span><span class="sxs-lookup"><span data-stu-id="dee32-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="dee32-231">Назовем его **publish**.</span><span class="sxs-lookup"><span data-stu-id="dee32-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="dee32-232">**Строка 23.** Опубликуйте проект (и его зависимости), поместив его в каталог проекта **/app** в образе.</span><span class="sxs-lookup"><span data-stu-id="dee32-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="dee32-233">**Строка 25.** Начните новый этап, продолжая работу над образом **base**. Назовем его **final**.</span><span class="sxs-lookup"><span data-stu-id="dee32-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="dee32-234">**Строка 26.** Измените текущий каталог на **/app**.</span><span class="sxs-lookup"><span data-stu-id="dee32-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="dee32-235">**Строка 27.** Скопируйте каталог **/app** из этапа **publish** в текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dee32-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="dee32-236">**Строка 28.** Определите команду, которая будет выполняться при запуске контейнера.</span><span class="sxs-lookup"><span data-stu-id="dee32-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="dee32-237">Теперь давайте рассмотрим некоторые оптимизации для повышения производительности всего процесса; в случае eShopOnContainers сборка полного решения в контейнерах Linux занимает около 22 минут или более.</span><span class="sxs-lookup"><span data-stu-id="dee32-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="dee32-238">Вы используете преимущества многоуровневого кэша Docker, которая не представляет особых сложностей: если базовый образ и команды — такие же, как в некоторых ранее выполненных случаях, можно просто использовать полученный слой без необходимости повторного выполнения команд, что экономит время.</span><span class="sxs-lookup"><span data-stu-id="dee32-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="dee32-239">Таким образом, давайте сосредоточимся на этапе **build**; строки 5–6 практически одинаковы, но строки 7–17 отличаются для каждой службы из eShopOnContainers, поэтому они должны выполняться каждый раз, но если изменить строки 7–16 на следующие:</span><span class="sxs-lookup"><span data-stu-id="dee32-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```dockerfile
COPY . .
```

<span data-ttu-id="dee32-240">то они будет практически аналогичны для каждой службы; строка копирует все решение и создаст слой большего размера, но при этом</span><span class="sxs-lookup"><span data-stu-id="dee32-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="dee32-241">процесс копирования будет выполняться только в первый раз (и при перестроении в случае изменения файла); для всех других служб будет использоваться кэш.</span><span class="sxs-lookup"><span data-stu-id="dee32-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="dee32-242">Так как более крупный образ находится на промежуточном этапе, он не влияет на размер окончательного образа.</span><span class="sxs-lookup"><span data-stu-id="dee32-242">Since the larger image occurs in an intermediate stage, it doesn't affect the final image size.</span></span>

<span data-ttu-id="dee32-243">Следующая значительная оптимизация касается команды `restore`, выполняемой в строке 17; она также отличается для каждой службы eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dee32-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="dee32-244">Если вы измените эту строку так:</span><span class="sxs-lookup"><span data-stu-id="dee32-244">If you change that line to just:</span></span>

```dockerfile
RUN dotnet restore
```

<span data-ttu-id="dee32-245">то она позволит восстановить пакеты для всего решения, что позволяет повторять ее только один раз вместо 15.</span><span class="sxs-lookup"><span data-stu-id="dee32-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="dee32-246">Тем не менее `dotnet restore` запускается, только если в папке есть лишь один файл проекта или решения, поэтому решения этой задачи немного сложнее. Если не вдаваться в подробности, все обстоит так:</span><span class="sxs-lookup"><span data-stu-id="dee32-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="dee32-247">Добавьте приведенные ниже строки в **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="dee32-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="dee32-248">`*.sln` для игнорирования всех файлов решения в главном дереве папок</span><span class="sxs-lookup"><span data-stu-id="dee32-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="dee32-249">`!eShopOnContainers-ServicesAndWebApps.sln`, чтобы включить только этот файл решения.</span><span class="sxs-lookup"><span data-stu-id="dee32-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="dee32-250">Включите аргумент `/ignoreprojectextensions:.dcproj` в `dotnet restore`, чтобы он также игнорировал проект docker-compose и восстанавливал только пакеты для решения eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="dee32-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="dee32-251">Для окончательной оптимизации отметим, что строка 20 является избыточной, так как строка 23 также собирает приложение и следует, по сути, сразу после строки 20, поэтому можно убрать еще одну времязатратную команду.</span><span class="sxs-lookup"><span data-stu-id="dee32-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="dee32-252">Полученный файл будет таким:</span><span class="sxs-lookup"><span data-stu-id="dee32-252">The resulting file is then:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/sdk:5.0 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app .
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="dee32-253">Создание базового образа с нуля</span><span class="sxs-lookup"><span data-stu-id="dee32-253">Creating your base image from scratch</span></span>

<span data-ttu-id="dee32-254">Вы можете создать собственный базовый образ Docker с нуля.</span><span class="sxs-lookup"><span data-stu-id="dee32-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="dee32-255">Этот сценарий не рекомендуется для тех, кто только начинает работать с Docker, но если вы хотите задать определенные биты базового образа, это можно сделать.</span><span class="sxs-lookup"><span data-stu-id="dee32-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-256">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-256">Additional resources</span></span>

- <span data-ttu-id="dee32-257">**Мультиархитектурные образы .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="dee32-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="dee32-258">**Создание базового образа**.</span><span class="sxs-lookup"><span data-stu-id="dee32-258">**Create a base image**.</span></span> <span data-ttu-id="dee32-259">Официальная документация Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Изображение для шага 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="dee32-261">Шаг 3.</span><span class="sxs-lookup"><span data-stu-id="dee32-261">Step 3.</span></span> <span data-ttu-id="dee32-262">Создание пользовательских образов Docker и внедрение в них собственных приложений или служб</span><span class="sxs-lookup"><span data-stu-id="dee32-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="dee32-263">Для каждой службы в приложении необходимо создать связанный образ.</span><span class="sxs-lookup"><span data-stu-id="dee32-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="dee32-264">Если приложение состоит из одной службы или веб-приложения, достаточно одного образа.</span><span class="sxs-lookup"><span data-stu-id="dee32-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="dee32-265">Обратите внимание, что образы Docker в Visual Studio создаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="dee32-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="dee32-266">Следующие действия потребуются только в рабочем процессе с использованием редактора/CLI и подробно описываются, чтобы показать, что происходит внутри.</span><span class="sxs-lookup"><span data-stu-id="dee32-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="dee32-267">Разработчик должен выполнять разработку и тестирование локально до тех пор, пока не завершит и отправит компонент или пока не перейдет в систему управления версиями (например, в GitHub).</span><span class="sxs-lookup"><span data-stu-id="dee32-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="dee32-268">Это означает, что необходимо создавать образы Docker и разворачивать контейнеры на локальном узле Docker (на виртуальной машине Windows или Linux), а затем выполнять запуск, тестирование и отладку этих локальных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="dee32-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="dee32-269">Чтобы создать пользовательский образ в локальной среде с помощью Docker CLI и Dockerfile, можно использовать команду docker build, как показано на рисунке 5-5.</span><span class="sxs-lookup"><span data-stu-id="dee32-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Снимок экрана, показывающий выходные данные команды docker build в консоли.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="dee32-271">**Рис. 5-5**.</span><span class="sxs-lookup"><span data-stu-id="dee32-271">**Figure 5-5**.</span></span> <span data-ttu-id="dee32-272">Создание пользовательского образа Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-272">Creating a custom Docker image</span></span>

<span data-ttu-id="dee32-273">При необходимости вместо непосредственного выполнения команды docker build из папки проекта можно сначала создать развертываемую папку с нужными библиотеками .NET и двоичными файлами, выполнив команду `dotnet publish`, а затем использовать команду `docker build`.</span><span class="sxs-lookup"><span data-stu-id="dee32-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="dee32-274">Это создаст образ Docker с именем `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="dee32-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="dee32-275">В данном случае :first — это тег, представляющий конкретную версию.</span><span class="sxs-lookup"><span data-stu-id="dee32-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="dee32-276">Этот шаг можно повторить для каждого пользовательского образа, который вам требуется создать для своего составного приложения Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="dee32-277">Если приложение состоит из нескольких контейнеров (т. е. это многоконтейнерное приложение), можно также использовать команду `docker-compose up --build`, чтобы собрать все связанные образы одной командой с помощью метаданных, представленных в связанном файле docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dee32-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="dee32-278">Вы можете найти существующие в локальном репозитории образы с помощью команды docker images, как показано на рисунке 5-6.</span><span class="sxs-lookup"><span data-stu-id="dee32-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Выходные данные команды docker images в консоли со списком существующих образов.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="dee32-280">**Рис. 5-6**.</span><span class="sxs-lookup"><span data-stu-id="dee32-280">**Figure 5-6.**</span></span> <span data-ttu-id="dee32-281">Просмотр существующих образов с помощью команды docker images</span><span class="sxs-lookup"><span data-stu-id="dee32-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="dee32-282">Создание образов Docker с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="dee32-283">При использовании Visual Studio для создания проекта с поддержкой Docker не требуется создавать образ явно.</span><span class="sxs-lookup"><span data-stu-id="dee32-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="dee32-284">Этот образ создается автоматически, когда вы нажимаете клавиши **F5** или **Ctrl-F5** и запускаете приложение или службу, добавленную в Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="dee32-285">Этот шаг выполняется в Visual Studio автоматически, и вы не увидите, как это происходит, но важно знать, что происходит внутри.</span><span class="sxs-lookup"><span data-stu-id="dee32-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Изображение для необязательного шага 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="dee32-287">Шаг 4.</span><span class="sxs-lookup"><span data-stu-id="dee32-287">Step 4.</span></span> <span data-ttu-id="dee32-288">Определение служб в файле docker-compose.yml при сборке многоконтейнерного приложения Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="dee32-289">В файле [docker-compose.yml](https://docs.docker.com/compose/compose-file/) можно задать ряд связанных служб для развертывания в качестве составного приложения с помощью команд развертывания.</span><span class="sxs-lookup"><span data-stu-id="dee32-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="dee32-290">Он также настраивает отношения зависимости и конфигурацию среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dee32-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="dee32-291">Чтобы использовать файл docker-compose.yml, его необходимо создать в основной или корневой папке решения, и его содержимое должно быть аналогично приведенному в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="dee32-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mcr.microsoft.com/mssql/server:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="dee32-292">Данный файл docker-compose.yml представляет собой упрощенную и объединенную версию.</span><span class="sxs-lookup"><span data-stu-id="dee32-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="dee32-293">Он содержит статические данные конфигурации для каждого контейнера (такие как имя пользовательского образа), которые требуются всегда, а также сведения о конфигурации, которые могут зависеть от среды развертывания, такие как строка подключения.</span><span class="sxs-lookup"><span data-stu-id="dee32-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="dee32-294">В следующих разделах вы узнаете, как можно разбить конфигурацию в файле docker-compose.yml на несколько файлов docker-compose и переопределить значения в зависимости от среды и типа выполнения (отладка или выпуск).</span><span class="sxs-lookup"><span data-stu-id="dee32-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="dee32-295">В примере файла docker-compose.yml определяются четыре службы: служба `webmvc` (веб-приложение), две микрослужбы (`ordering-api` и `basket-api`) и один контейнер источника данных, `sqldata`, на основе SQL Server для Linux, работающего как контейнер.</span><span class="sxs-lookup"><span data-stu-id="dee32-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="dee32-296">Каждая служба развертывается как контейнер, поэтому образ Docker требуется для каждой службы.</span><span class="sxs-lookup"><span data-stu-id="dee32-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="dee32-297">Файл docker-compose.yml задает не только используемые контейнеры, но и их индивидуальные конфигурации.</span><span class="sxs-lookup"><span data-stu-id="dee32-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="dee32-298">Например, в определении контейнера `webmvc` в файле .yml задается следующее.</span><span class="sxs-lookup"><span data-stu-id="dee32-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="dee32-299">Использует предварительно созданный образ `eshop/web:latest`.</span><span class="sxs-lookup"><span data-stu-id="dee32-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="dee32-300">Однако вы также можете настроить сборку этого образа при выполнении команды docker-compose с дополнительной конфигурацией на основе раздела build: в файле docker-compose.</span><span class="sxs-lookup"><span data-stu-id="dee32-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="dee32-301">Инициализируются две переменные среды (CatalogUrl и OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="dee32-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="dee32-302">Предоставленный порт 80 в контейнере переадресуется на внешний порт 80 на хост-компьютере.</span><span class="sxs-lookup"><span data-stu-id="dee32-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="dee32-303">Веб-приложение связывается со службами catalog и ordering с помощью параметра depends_on.</span><span class="sxs-lookup"><span data-stu-id="dee32-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="dee32-304">В результате данная служба будет ожидать запуска этих служб.</span><span class="sxs-lookup"><span data-stu-id="dee32-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="dee32-305">Мы вернемся к файлу docker-compose.yml в следующем разделе, когда будем рассматривать реализацию микрослужб и многоконтейнерных приложений.</span><span class="sxs-lookup"><span data-stu-id="dee32-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="dee32-306">Работа с файлом docker-compose.yml в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="dee32-307">Наряду с возможностью добавления Dockerfile в проект, как уже отмечалось, Visual Studio 2017 версии 15.8 и выше позволяет включить в решении поддержку оркестратора для Docker Compose.</span><span class="sxs-lookup"><span data-stu-id="dee32-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="dee32-308">При добавлении поддержки оркестратора контейнеров, как показано на рисунке 5-7, в первый раз Visual Studio создает файл Dockerfile для проекта и создает новый проект (раздел службы) в решении с несколькими глобальными файлами `docker-compose*.yml`, а затем добавляет проект для таких файлов.</span><span class="sxs-lookup"><span data-stu-id="dee32-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="dee32-309">Затем можно открыть файлы docker-compose.yml и добавить в них дополнительные возможности.</span><span class="sxs-lookup"><span data-stu-id="dee32-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="dee32-310">Вам необходимо будет повторить эту операцию для каждого проекта, который вы хотите включить в файл docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dee32-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="dee32-311">На момент написания этой статьи Visual Studio поддерживает оркестраторы **Docker Compose** и **Kubernetes/Helm**.</span><span class="sxs-lookup"><span data-stu-id="dee32-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Снимок экрана: пункт "Поддержка оркестратора контейнеров" в контекстном меню проекта.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="dee32-313">**Рис. 5-7**.</span><span class="sxs-lookup"><span data-stu-id="dee32-313">**Figure 5-7**.</span></span> <span data-ttu-id="dee32-314">Добавление поддержки Docker в Visual Studio 2019 щелчком правой кнопки мыши на проекте ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dee32-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="dee32-315">После добавления поддержки оркестратора в решение в Visual Studio вы также увидите новый узел в обозревателе решений (в файле проекта `docker-compose.dcproj`), содержащий добавленные файлы docker-compose.yml, как показано на рисунке 5-8.</span><span class="sxs-lookup"><span data-stu-id="dee32-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Снимок экрана: узел docker-compose в обозревателе решений.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="dee32-317">**Рис. 5-8**.</span><span class="sxs-lookup"><span data-stu-id="dee32-317">**Figure 5-8**.</span></span> <span data-ttu-id="dee32-318">Узел дерева **docker-compose**, добавленный в обозреватель решений Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="dee32-319">Можно развернуть многоконтейнерное приложение с единственным файлом docker-compose.yml с помощью команды `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="dee32-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="dee32-320">Однако Visual Studio добавляет группу этих файлов, чтобы вы могли переопределять значения в зависимости от среды (разработки или рабочей) и типа выполнения (выпуска или отладки).</span><span class="sxs-lookup"><span data-stu-id="dee32-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="dee32-321">Эта возможность разъясняется в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="dee32-321">This capability will be explained in later sections.</span></span>

![Изображение для шага 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="dee32-323">Шаг 5.</span><span class="sxs-lookup"><span data-stu-id="dee32-323">Step 5.</span></span> <span data-ttu-id="dee32-324">Сборка и запуск приложения Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-324">Build and run your Docker application</span></span>

<span data-ttu-id="dee32-325">Если в приложении имеется только один контейнер, его можно запустить путем развертывания на узле Docker (на виртуальной машине или физическом сервере).</span><span class="sxs-lookup"><span data-stu-id="dee32-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="dee32-326">Но если приложение содержит несколько служб, его можно развернуть как составное приложение с помощью одной команды CLI (`docker-compose up)`) или в Visual Studio, в котором внутри будет выполняться эта же команда.</span><span class="sxs-lookup"><span data-stu-id="dee32-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="dee32-327">Давайте рассмотрим разные варианты.</span><span class="sxs-lookup"><span data-stu-id="dee32-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="dee32-328">Вариант А. Запуск приложения в одном контейнере</span><span class="sxs-lookup"><span data-stu-id="dee32-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="dee32-329">Использование Docker CLI</span><span class="sxs-lookup"><span data-stu-id="dee32-329">Using Docker CLI</span></span>

<span data-ttu-id="dee32-330">Контейнер Docker можно запустить с помощью команды `docker run`, как показано на рисунке 5-9.</span><span class="sxs-lookup"><span data-stu-id="dee32-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="dee32-331">Приведенная выше команда создает новый экземпляр контейнера из указанного образа при каждом запуске.</span><span class="sxs-lookup"><span data-stu-id="dee32-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="dee32-332">Можно использовать параметр `--name` для указания имени контейнера, а затем использовать `docker start {name}` (также поддерживаются идентификатор контейнера и автоматически присваиваемое имя) для запуска существующего экземпляра контейнера.</span><span class="sxs-lookup"><span data-stu-id="dee32-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Снимок экрана: запуск контейнера Docker с помощью команды docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="dee32-334">**Рис. 5-9**.</span><span class="sxs-lookup"><span data-stu-id="dee32-334">**Figure 5-9**.</span></span> <span data-ttu-id="dee32-335">Запуск контейнера Docker с помощью команды docker run</span><span class="sxs-lookup"><span data-stu-id="dee32-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="dee32-336">В этом случае команда привязывает внутренний порт 5000 контейнера к порту 80 хост-компьютера.</span><span class="sxs-lookup"><span data-stu-id="dee32-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="dee32-337">Это означает, что узел выполняет прослушивание порта 80 и переадресацию в порт 5000 в контейнере.</span><span class="sxs-lookup"><span data-stu-id="dee32-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="dee32-338">Показанный хэш — это идентификатор контейнера; ему также присваивается случайное доступное для чтения имя, если параметр `--name` не используется.</span><span class="sxs-lookup"><span data-stu-id="dee32-338">The hash shown is the container ID and it's also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="dee32-339">Использование Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-339">Using Visual Studio</span></span>

<span data-ttu-id="dee32-340">Если вы еще не добавили поддержку оркестратора контейнеров, запустите одноконтейнерное приложение в Visual Studio, нажав клавишу **Ctrl-F5**. Кроме того, клавиша **F5** позволяет отлаживать приложение внутри контейнера.</span><span class="sxs-lookup"><span data-stu-id="dee32-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="dee32-341">Контейнер запускается локально с помощью команды docker run.</span><span class="sxs-lookup"><span data-stu-id="dee32-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="dee32-342">Вариант Б. Запуск многоконтейнерного приложения</span><span class="sxs-lookup"><span data-stu-id="dee32-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="dee32-343">В большинстве корпоративных сценариев приложение Docker будет состоять из нескольких служб; это означает, что необходимо запускать многоконтейнерное приложение, как показано на рисунке 5-10.</span><span class="sxs-lookup"><span data-stu-id="dee32-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Виртуальная машина с несколькими контейнерами Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="dee32-345">**Рис. 5-10**.</span><span class="sxs-lookup"><span data-stu-id="dee32-345">**Figure 5-10**.</span></span> <span data-ttu-id="dee32-346">Виртуальная машина с развернутыми контейнерами Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="dee32-347">Использование Docker CLI</span><span class="sxs-lookup"><span data-stu-id="dee32-347">Using Docker CLI</span></span>

<span data-ttu-id="dee32-348">Для запуска многоконтейнерного приложения с помощью Docker CLI используйте команду `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="dee32-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="dee32-349">Эта команда разворачивает многоконтейнерное приложение с помощью файла **docker-compose.yml**, существующего на уровне решения.</span><span class="sxs-lookup"><span data-stu-id="dee32-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="dee32-350">На рисунке 5-11 показаны результаты выполнения этой команды из главного каталога решения, в котором находится файл docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="dee32-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Вид экрана с результатом выполнения команды docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="dee32-352">**Рис. 5-11**.</span><span class="sxs-lookup"><span data-stu-id="dee32-352">**Figure 5-11**.</span></span> <span data-ttu-id="dee32-353">Пример результата выполнения команды docker-compose up</span><span class="sxs-lookup"><span data-stu-id="dee32-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="dee32-354">После выполнения команды docker-compose up приложение и связанные с ним контейнеры развертываются в узле Docker, как показано на рисунке 5-10.</span><span class="sxs-lookup"><span data-stu-id="dee32-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="dee32-355">Использование Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-355">Using Visual Studio</span></span>

<span data-ttu-id="dee32-356">Запуск многоконтейнерного приложения с помощью Visual Studio 2019 не может быть проще.</span><span class="sxs-lookup"><span data-stu-id="dee32-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="dee32-357">Просто нажмите клавишу **Ctrl-F5** для запуска или **F5** для отладки, как обычно, настроив проект **docker-compose** как запускаемый.</span><span class="sxs-lookup"><span data-stu-id="dee32-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="dee32-358">Visual Studio обрабатывает все необходимые настройки, чтобы можно было создать точки останова обычным образом и без особых усилий отлаживать наконец ставшие независимыми процессы, запущенные на "удаленных серверах" с уже подключенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="dee32-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="dee32-359">Как упоминалось ранее, каждый раз при добавлении поддержки решения Docker в проект в решении этот проект настраивается в глобальном (на уровне решения) файле docker-compose.yml, что позволяет запускать или отлаживать все решение сразу.</span><span class="sxs-lookup"><span data-stu-id="dee32-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="dee32-360">Visual Studio будет запускать по одному контейнеру для каждого проекта с включенной поддержкой решения Docker и выполнять все внутренние шаги автоматически (dotnet publish, docker build и т. д.).</span><span class="sxs-lookup"><span data-stu-id="dee32-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="dee32-361">Если вы хотите оценить масштаб этой утомительной работы, взгляните на файл:</span><span class="sxs-lookup"><span data-stu-id="dee32-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="dee32-362">Здесь важно то, что, как показано на рисунке 5-12, в Visual Studio 2019 имеется дополнительная команда **Docker** для действия клавиши F5.</span><span class="sxs-lookup"><span data-stu-id="dee32-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="dee32-363">Эта возможность позволяет запускать или отлаживать многоконтейнерное приложение путем запуска всех контейнеров, определенных в файлах docker-compose.yml на уровне решения.</span><span class="sxs-lookup"><span data-stu-id="dee32-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="dee32-364">Возможность отладки многоконтейнерных решений означает, что можно установить несколько точек останова, чтобы все они были в разных проектах (контейнерах), и во время отладки из Visual Studio вы будете останавливаться в точках останова, заданных в разных проектах, и работать в разных контейнерах.</span><span class="sxs-lookup"><span data-stu-id="dee32-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Снимок экрана: панель инструментов отладки с запущенным проектом docker-compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="dee32-366">**Рис. 5-12**.</span><span class="sxs-lookup"><span data-stu-id="dee32-366">**Figure 5-12**.</span></span> <span data-ttu-id="dee32-367">Запуск многоконтейнерных приложений в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-368">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-368">Additional resources</span></span>

- <span data-ttu-id="dee32-369">**Развертывание контейнера ASP.NET на удаленном узле Docker** </span><span class="sxs-lookup"><span data-stu-id="dee32-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="dee32-370">Примечание о тестировании и развертывании с использованием оркестраторов</span><span class="sxs-lookup"><span data-stu-id="dee32-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="dee32-371">Команды docker-compose up и docker run (или запуск и отладка контейнеров в Visual Studio) подходят для тестирования контейнеров в вашей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="dee32-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="dee32-372">Но этот подход не следует использовать для развертывания в рабочей среде, где следует выбирать оркестраторы, например [Kubernetes](https://kubernetes.io/) или [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="dee32-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="dee32-373">При работе с Kubernetes необходимо использовать [модули](https://kubernetes.io/docs/concepts/workloads/pods/pod/) для организации контейнеров и [службы](https://kubernetes.io/docs/concepts/services-networking/service/) для их объединения в сеть.</span><span class="sxs-lookup"><span data-stu-id="dee32-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="dee32-374">Можно также использовать [развертывания](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) для упорядочения создания и изменения модулей.</span><span class="sxs-lookup"><span data-stu-id="dee32-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Изображение для шага 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="dee32-376">Шаг 6.</span><span class="sxs-lookup"><span data-stu-id="dee32-376">Step 6.</span></span> <span data-ttu-id="dee32-377">Тестирование приложения Docker с помощью локального узла Docker</span><span class="sxs-lookup"><span data-stu-id="dee32-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="dee32-378">Этот шаг будет зависеть от того, что делает ваше приложение.</span><span class="sxs-lookup"><span data-stu-id="dee32-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="dee32-379">В случае простого веб-приложения .NET Core, развернутого в виде единственного контейнера или службы, можно получить доступ к этой службе, открыв на узле Docker браузер и перейдя в нем на этот сайт, как показано на рисунке 5-13.</span><span class="sxs-lookup"><span data-stu-id="dee32-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="dee32-380">(Если конфигурация в Dockerfile сопоставляет контейнер с портом узла, отличным от 80, укажите этот порт узла в URL-адресе.)</span><span class="sxs-lookup"><span data-stu-id="dee32-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Снимок экрана: ответ с адреса localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="dee32-382">**Рис. 5-13**.</span><span class="sxs-lookup"><span data-stu-id="dee32-382">**Figure 5-13**.</span></span> <span data-ttu-id="dee32-383">Пример локального тестирования приложения Docker с помощью localhost</span><span class="sxs-lookup"><span data-stu-id="dee32-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="dee32-384">Если localhost не указывает на IP-адрес узла Docker (при использовании Docker CE это должно происходить по умолчанию), то для перехода к службе используйте IP-адрес сетевой карты вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="dee32-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="dee32-385">Обратите внимание, что этот URL-адрес в браузере использует порт 80 для рассматриваемого примера конкретного контейнера.</span><span class="sxs-lookup"><span data-stu-id="dee32-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="dee32-386">Однако внутренние запросы перенаправляются на порт 5000, поскольку именно так было выполнено развертывание с помощью команды docker run, как описано в предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="dee32-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="dee32-387">Вы также можете тестировать приложение с помощью команды curl с терминала, как показано на рисунке 5-14.</span><span class="sxs-lookup"><span data-stu-id="dee32-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="dee32-388">В случае установки Docker в Windows по умолчанию всегда будет использоваться IP-адрес узла Docker 10.0.75.1 помимо фактического IP-адреса вашего компьютера.</span><span class="sxs-lookup"><span data-stu-id="dee32-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Выходные данные команды curl, выполненной применительно к http://10.0.75.1/API/values, в консоли.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="dee32-390">**Рис. 5-14**.</span><span class="sxs-lookup"><span data-stu-id="dee32-390">**Figure 5-14**.</span></span> <span data-ttu-id="dee32-391">Пример локального тестирования приложения Docker с помощью curl</span><span class="sxs-lookup"><span data-stu-id="dee32-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="dee32-392">Тестирование и отладка контейнеров в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee32-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="dee32-393">При запуске и отладке контейнеров в Visual Studio 2019 вы можете отлаживать приложения .NET в основном так же, как при запуске без контейнеров.</span><span class="sxs-lookup"><span data-stu-id="dee32-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="dee32-394">Тестирование и отладка без Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="dee32-395">Если при разработке используется редактор или CLI, отлаживать контейнеры будет значительно труднее, и вы, возможно, захотите выполнять отладку путем создания трассировок.</span><span class="sxs-lookup"><span data-stu-id="dee32-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-396">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-396">Additional resources</span></span>

- <span data-ttu-id="dee32-397">**Отладка приложений в локальном контейнере Docker** </span><span class="sxs-lookup"><span data-stu-id="dee32-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="dee32-398">**Стив Ласкер (Steve Lasker). Сборка, отладка, развертывание приложений ASP.NET Core с помощью Docker.**</span><span class="sxs-lookup"><span data-stu-id="dee32-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="dee32-399">Видео.</span><span class="sxs-lookup"><span data-stu-id="dee32-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="dee32-400">Упрощенный рабочий процесс при разработке контейнеров в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="dee32-401">В сущности, при использовании Visual Studio рабочий процесс гораздо проще, чем при использовании редактора или CLI.</span><span class="sxs-lookup"><span data-stu-id="dee32-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="dee32-402">Большинство шагов, необходимых для Docker и связанных с Dockerfile и docker-compose.yml, выполняются скрыто от пользователя или значительно упрощаются благодаря Visual Studio, как показано на рисунке 5-15.</span><span class="sxs-lookup"><span data-stu-id="dee32-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Схема, на которой показаны пять упрощенных шагов по созданию приложения.":::
<span data-ttu-id="dee32-404">Процесс разработки для приложений на основе Docker: 1) создайте код приложения; 2) напишите файлы Dockerfile; 3) создайте образы, определенные в файлах Dockerfile; 4) (необязательно) создайте службы в файле docker-compose.yml; 5) запустите контейнер или приложение docker-compose; 6) проведите тестирование приложений или микрослужб; 7) отправьте все в репозиторий и повторите.</span><span class="sxs-lookup"><span data-stu-id="dee32-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="dee32-405">**Рис. 5-15**.</span><span class="sxs-lookup"><span data-stu-id="dee32-405">**Figure 5-15**.</span></span> <span data-ttu-id="dee32-406">Упрощенный рабочий процесс при разработке в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dee32-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="dee32-407">Кроме того, вам достаточно будет выполнить шаг 2 (добавление поддержки Docker в проекты) только один раз.</span><span class="sxs-lookup"><span data-stu-id="dee32-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="dee32-408">Таким образом, рабочий процесс аналогичен другим обычным задачам разработки, когда для разработки используется .NET.</span><span class="sxs-lookup"><span data-stu-id="dee32-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="dee32-409">Вам нужно знать, что происходит на самом деле (процесс создания образа, какие базовые образы используются, развертывание контейнеров и т. п.), и в некоторых случаях также может потребоваться изменить файл Dockerfile или docker-compose.yml, чтобы настроить функциональность.</span><span class="sxs-lookup"><span data-stu-id="dee32-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="dee32-410">Но благодаря Visual Studio большую часть работы можно выполнить гораздо проще, что существенно повышает эффективность работы.</span><span class="sxs-lookup"><span data-stu-id="dee32-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dee32-411">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-411">Additional resources</span></span>

- <span data-ttu-id="dee32-412">**Стив Ласкер (Steve Lasker). Разработка для Docker на .NET в Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="dee32-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="dee32-413">Использование команд PowerShell в DockerFile для настройки контейнеров Windows</span><span class="sxs-lookup"><span data-stu-id="dee32-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="dee32-414">[Контейнеры Windows](/virtualization/windowscontainers/about/index) позволяют преобразовывать существующие приложения Windows в образы Docker и развертывать их с помощью тех же средств, что и остальную часть экосистемы Docker.</span><span class="sxs-lookup"><span data-stu-id="dee32-414">[Windows Containers](/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="dee32-415">Чтобы использовать контейнеры Windows, выполните команды PowerShell в Dockerfile, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="dee32-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="dee32-416">В этом случае мы используем базовый образ Windows Server Core (параметр FROM) и устанавливаем службы IIS с помощью команды PowerShell (параметр RUN).</span><span class="sxs-lookup"><span data-stu-id="dee32-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="dee32-417">Аналогичным образом можно также использовать команды PowerShell для настройки дополнительных компонентов, таких как ASP.NET 4.x, .NET Framework 4.6 и другого программного обеспечения Windows.</span><span class="sxs-lookup"><span data-stu-id="dee32-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET Framework 4.6, or any other Windows software.</span></span> <span data-ttu-id="dee32-418">Например, следующая команда в Dockerfile настраивает ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="dee32-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="dee32-419">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dee32-419">Additional resources</span></span>

- <span data-ttu-id="dee32-420">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="dee32-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="dee32-421">Примеры команд PowerShell, которые можно выполнять в файлах Dockerfile для включения компонентов Windows.</span><span class="sxs-lookup"><span data-stu-id="dee32-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="dee32-422">[Назад](index.md)
>[Вперед](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="dee32-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
