---
title: Сборка приложений ASP.NET Core, развернутых как контейнеры Linux в кластерах AKS/Kubernetes
description: Жизненный цикл контейнерного приложения Docker на основе платформы и средств Майкрософт
ms.date: 01/06/2021
ms.openlocfilehash: 7a8f8272ab2faabd0398aeeb2039b6f034b4dedb
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970645"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="71324-103">Сборка приложений ASP.NET Core, развернутых как контейнеры Linux в оркестраторе AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="71324-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="71324-104">Служба Azure Kubernetes (AKS) представляет собой службы оркестрации управляемой среды Kubernetes в Azure, упрощающие развертывание контейнеров и управление ими.</span><span class="sxs-lookup"><span data-stu-id="71324-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="71324-105">Основные функции AKS:</span><span class="sxs-lookup"><span data-stu-id="71324-105">AKS main features are:</span></span>

- <span data-ttu-id="71324-106">Размещенный в Azure уровень управления</span><span class="sxs-lookup"><span data-stu-id="71324-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="71324-107">Автоматические обновления</span><span class="sxs-lookup"><span data-stu-id="71324-107">Automated upgrades</span></span>
- <span data-ttu-id="71324-108">самовосстановление;</span><span class="sxs-lookup"><span data-stu-id="71324-108">Self-healing</span></span>
- <span data-ttu-id="71324-109">Настраиваемое пользователем масштабирование</span><span class="sxs-lookup"><span data-stu-id="71324-109">User-configurable scaling</span></span>
- <span data-ttu-id="71324-110">Упрощение взаимодействия с пользователем для разработчиков и операторов кластера.</span><span class="sxs-lookup"><span data-stu-id="71324-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="71324-111">В приведенных ниже примерах рассматривается создание приложения ASP.NET Core 5.0, которое выполняется в Linux и развертывается в кластере AKS в Azure, при этом его разработка осуществляется в Visual Studio 2019 версии 16.8.</span><span class="sxs-lookup"><span data-stu-id="71324-111">The following examples explore the creation of an ASP.NET Core 5.0 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019 version 16.8.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="71324-112">Создание проекта ASP.NET Core с помощью Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="71324-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="71324-113">ASP.NET Core — это универсальная платформа разработки, которая поддерживается корпорацией Майкрософт и сообществом .NET на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="71324-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="71324-114">Она является кроссплатформенной, поддерживает Windows, Mac OS и Linux и может использоваться на устройствах, в облаке, во внедренных системах и в сценариях Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="71324-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="71324-115">В этом примере используется пара простых проектов, основанных на шаблонах Visual Studio, поэтому не требуется много дополнительных знаний для создания примера.</span><span class="sxs-lookup"><span data-stu-id="71324-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="71324-116">Вам достаточно создать проект с помощью стандартного шаблона, который включает в себя все элементы для запуска небольшого проекта с помощью REST API и веб-приложение с Razor Pages, использующее технологии ASP.NET Core 5.0.</span><span class="sxs-lookup"><span data-stu-id="71324-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 5.0 technology.</span></span>

![Добавьте окно нового проекта в Visual Studio, выбрав "Веб-приложение ASP.NET Core".](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="71324-118">**Рис. 4-35**.</span><span class="sxs-lookup"><span data-stu-id="71324-118">**Figure 4-35**.</span></span> <span data-ttu-id="71324-119">Создание веб-приложения ASP.NET Core в Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="71324-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="71324-120">Чтобы создать пример проекта в Visual Studio, выберите **Файл** > **Создать** > **Проект**, укажите тип проекта **Интернет** и затем выберите шаблон **Веб-приложение ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="71324-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="71324-121">При необходимости можно также выполнить поиск шаблона.</span><span class="sxs-lookup"><span data-stu-id="71324-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="71324-122">Затем введите имя и расположение приложения, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="71324-122">Then enter the application name and location as shown in the next image.</span></span>

![Введите имя и расположение проекта.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="71324-124">**Рис. 4-36**.</span><span class="sxs-lookup"><span data-stu-id="71324-124">**Figure 4-36**.</span></span> <span data-ttu-id="71324-125">Введите имя и расположение проекта в Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="71324-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="71324-126">Убедитесь, что выбрана платформа ASP.NET Core 5.0.</span><span class="sxs-lookup"><span data-stu-id="71324-126">Verify that you've selected ASP.NET Core 5.0 as the framework.</span></span> <span data-ttu-id="71324-127">Платформа .NET 5.0 включена в последнюю версию продукта Visual Studio 2019 и автоматически устанавливается и настраивается при его установке.</span><span class="sxs-lookup"><span data-stu-id="71324-127">.NET 5.0 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![Диалоговое окно Visual Studio для выбора типа веб-приложения ASP.NET Core с выбранным параметром API.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="71324-129">**Рис. 4-37**.</span><span class="sxs-lookup"><span data-stu-id="71324-129">**Figure 4-37**.</span></span> <span data-ttu-id="71324-130">Выбор ASP.NET CORE 5.0 и типа проекта "Веб-API"</span><span class="sxs-lookup"><span data-stu-id="71324-130">Selecting ASP.NET CORE 5.0 and Web API project type</span></span>

<span data-ttu-id="71324-131">Обратите внимание, что поддержка Docker в настоящее время не включена. Отобразить ее можно после создания проекта.</span><span class="sxs-lookup"><span data-stu-id="71324-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="71324-132">При наличии любой предыдущей версии .NET Core можно скачать и установить версию 3.1 по адресу <https://dotnet.microsoft.com/download>.</span><span class="sxs-lookup"><span data-stu-id="71324-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="71324-133">Чтобы показать, что вы можете реализовать поддержку Docker в проекте в любое время, добавьте поддержку Docker сейчас.</span><span class="sxs-lookup"><span data-stu-id="71324-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="71324-134">Щелкните узел проекта правой кнопкой мыши в обозревателе решений и выберите в контекстном меню пункт **Добавить** > **Поддержка Docker**.</span><span class="sxs-lookup"><span data-stu-id="71324-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Пункт контекстного меню, позволяющий добавить поддержку Docker в существующий проект: Щелкните проект правой кнопкой мыши и выберите "Добавить" > "Поддержка Docker".](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="71324-136">**Рис. 4-38**.</span><span class="sxs-lookup"><span data-stu-id="71324-136">**Figure 4-38**.</span></span> <span data-ttu-id="71324-137">Добавление поддержки Docker в существующий проект</span><span class="sxs-lookup"><span data-stu-id="71324-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="71324-138">Чтобы завершить добавление поддержки Docker, можно выбрать платформу Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="71324-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="71324-139">В данном случае это **Linux**.</span><span class="sxs-lookup"><span data-stu-id="71324-139">In this case, select **Linux**.</span></span>

![Параметр диалогового окна для выбора целевой операционной системы для Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="71324-141">**Рис. 4-39**.</span><span class="sxs-lookup"><span data-stu-id="71324-141">**Figure 4-39**.</span></span> <span data-ttu-id="71324-142">Выбор контейнеров Linux.</span><span class="sxs-lookup"><span data-stu-id="71324-142">Selecting Linux containers.</span></span>

<span data-ttu-id="71324-143">Выполнив эти простые шаги, вы запустите свое приложение ASP.NET Core 5.0 в контейнере Linux.</span><span class="sxs-lookup"><span data-stu-id="71324-143">With these simple steps, you have your ASP.NET Core 5.0 application running on a Linux container.</span></span>

<span data-ttu-id="71324-144">Аналогичным образом можно добавить очень простой проект **WebApp** (рис. 4-40) для использования конечной точки веб-API, хотя здесь это не рассматривается.</span><span class="sxs-lookup"><span data-stu-id="71324-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="71324-145">После этого вы добавите поддержку оркестратора для проекта **WebApi**, как показано далее на рисунке 4-40.</span><span class="sxs-lookup"><span data-stu-id="71324-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![Добавление поддержки оркестратора в проект WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="71324-147">**Рис. 4-40**.</span><span class="sxs-lookup"><span data-stu-id="71324-147">**Figure 4-40**.</span></span> <span data-ttu-id="71324-148">Добавление поддержки оркестратора в проект *WebApi*.</span><span class="sxs-lookup"><span data-stu-id="71324-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="71324-149">При выборе параметра `Docker Compose`, который подходит для локальной разработки, Visual Studio добавляет проект docker-compose с файлами docker-compose, как показано на рисунке 4-41.</span><span class="sxs-lookup"><span data-stu-id="71324-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Добавление в решение docker-compose](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="71324-151">**Рис. 4-41**.</span><span class="sxs-lookup"><span data-stu-id="71324-151">**Figure 4-41**.</span></span> <span data-ttu-id="71324-152">Добавление поддержки оркестратора в проект *WebApi*.</span><span class="sxs-lookup"><span data-stu-id="71324-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="71324-153">Эти исходные файлы похожи на следующие:</span><span class="sxs-lookup"><span data-stu-id="71324-153">The initial files added are similar to these ones:</span></span>

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

<span data-ttu-id="71324-154">Чтобы приложение выполнялось с Docker Compose, необходимо внести несколько изменений в `docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="71324-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

<span data-ttu-id="71324-155">Теперь приложение можно запустить с помощью клавиши **F5** или кнопки **Воспроизвести** либо сочетания клавиш **CTRL + F5**, выбрав проект docker-compose, как показано на рисунке 4-42.</span><span class="sxs-lookup"><span data-stu-id="71324-155">Now you can run your application with the **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Выполнение проекта docker-compose с помощью Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="71324-157">**Рис. 4-42**.</span><span class="sxs-lookup"><span data-stu-id="71324-157">**Figure 4-42**.</span></span> <span data-ttu-id="71324-158">Добавление поддержки оркестратора в проект *WebApi*.</span><span class="sxs-lookup"><span data-stu-id="71324-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="71324-159">При выполнении приложения docker-compose, как описано ниже, вы получаете следующее:</span><span class="sxs-lookup"><span data-stu-id="71324-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="71324-160">Созданные образы и контейнеры создаются в соответствии с файлом docker-compose.</span><span class="sxs-lookup"><span data-stu-id="71324-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="71324-161">В браузере открывается адрес, настроенный в диалоговом окне "Свойства" для проекта `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="71324-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="71324-162">Открывается окно **Контейнер** (в Visual Studio 2019 версии 16.4 и более поздней).</span><span class="sxs-lookup"><span data-stu-id="71324-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="71324-163">Предоставляется поддержка отладчика для всех проектов в решении, как показано на следующих изображениях.</span><span class="sxs-lookup"><span data-stu-id="71324-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="71324-164">Браузер открыт:</span><span class="sxs-lookup"><span data-stu-id="71324-164">Browser opened:</span></span>

![Представление браузера с выполняющимся веб-приложением](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="71324-166">**Рис. 4-43**.</span><span class="sxs-lookup"><span data-stu-id="71324-166">**Figure 4-43**.</span></span> <span data-ttu-id="71324-167">Окно браузера с приложением, выполняющимся в нескольких контейнерах.</span><span class="sxs-lookup"><span data-stu-id="71324-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="71324-168">Окно "Контейнеры"</span><span class="sxs-lookup"><span data-stu-id="71324-168">Containers window:</span></span>

![Окно "Контейнеры" в Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="71324-170">**Рис. 4-44**.</span><span class="sxs-lookup"><span data-stu-id="71324-170">**Figure 4-44**.</span></span> <span data-ttu-id="71324-171">Окно "Контейнеры" в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="71324-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="71324-172">Окно **Контейнеры** позволяет просматривать запущенные контейнеры, доступные образы, переменные среды, журналы и сопоставления портов, проверять файловую систему, подключать отладчик или открывать окно терминала в среде контейнера.</span><span class="sxs-lookup"><span data-stu-id="71324-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="71324-173">Как видно, интеграция между Visual Studio 2019 и Docker полностью ориентирована на обеспечение продуктивной работы разработчика.</span><span class="sxs-lookup"><span data-stu-id="71324-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="71324-174">Конечно, можно также вывести список образов с помощью команды `docker images`.</span><span class="sxs-lookup"><span data-stu-id="71324-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="71324-175">Вы должны увидеть образы `webapi` и `webapp` с тегами `dev`, созданные при автоматическом развертывании вашего проекта с помощью Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="71324-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![Выходные данные команды docker images в консоли представляют собой список, содержащий следующее: репозиторий, тег, идентификатор образа, дата создания и размер.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="71324-177">**Рис. 4-45**.</span><span class="sxs-lookup"><span data-stu-id="71324-177">**Figure 4-45**.</span></span> <span data-ttu-id="71324-178">Представление образов Docker</span><span class="sxs-lookup"><span data-stu-id="71324-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="71324-179">Регистрация решения в Реестре контейнеров Azure (ACR)</span><span class="sxs-lookup"><span data-stu-id="71324-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="71324-180">Вы можете отправить образы в [Реестр контейнеров Azure (ACR)](https://azure.microsoft.com/services/container-registry/), но можно также использовать Docker Hub или любой другой реестр, чтобы оттуда образы можно было развернуть в кластере AKS.</span><span class="sxs-lookup"><span data-stu-id="71324-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="71324-181">Создание экземпляра ACR</span><span class="sxs-lookup"><span data-stu-id="71324-181">Create an ACR instance</span></span>

<span data-ttu-id="71324-182">Выполните следующую команду из **az cli**:</span><span class="sxs-lookup"><span data-stu-id="71324-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="71324-183">Имя реестра контейнеров (например, `exploredocker`) должно быть уникальным в пределах Azure и содержать от 5 до 50 буквенно-цифровых знаков.</span><span class="sxs-lookup"><span data-stu-id="71324-183">The container registry name (e.g `exploredocker`) must be unique within Azure, and contain 5-50 alphanumeric characters.</span></span> <span data-ttu-id="71324-184">Дополнительные сведения см. в разделе [Создание реестра контейнеров](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry).</span><span class="sxs-lookup"><span data-stu-id="71324-184">For more details, refer [Create a container registry](/azure/container-registry/container-registry-get-started-azure-cli#create-a-container-registry)</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="71324-185">Создание образа в режиме выпуска</span><span class="sxs-lookup"><span data-stu-id="71324-185">Create the image in Release mode</span></span>

<span data-ttu-id="71324-186">Теперь мы создадим образ в режиме **Выпуск** (готовом к выпуску), заменив значение на **Выпуск**, как показано на рис. 4-46, и запустив приложение, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="71324-186">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Параметр панели инструментов в Visual Studio для сборки в режиме выпуска.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="71324-188">**Рис. 4-46**.</span><span class="sxs-lookup"><span data-stu-id="71324-188">**Figure 4-46**.</span></span> <span data-ttu-id="71324-189">Выбор режима выпуска</span><span class="sxs-lookup"><span data-stu-id="71324-189">Selecting Release Mode</span></span>

<span data-ttu-id="71324-190">При выполнении команды `docker images` вы увидите создание обоих образов — одного для режима `debug` (**dev**) и другого для режима `release` (**latest**).</span><span class="sxs-lookup"><span data-stu-id="71324-190">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="71324-191">Создание тега образа</span><span class="sxs-lookup"><span data-stu-id="71324-191">Create a new Tag for the Image</span></span>

<span data-ttu-id="71324-192">Каждый образ контейнера должен быть помечен именем `loginServer` реестра.</span><span class="sxs-lookup"><span data-stu-id="71324-192">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="71324-193">Данный тег используется для маршрутизации при отправке образов контейнеров в реестр образов.</span><span class="sxs-lookup"><span data-stu-id="71324-193">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="71324-194">Вы можете просмотреть имя `loginServer` на портале Azure, используя сведения из Реестра контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="71324-194">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Представление имени Реестра контейнеров Azure в правом верхнем углу браузера.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="71324-196">**Рис. 4-47**.</span><span class="sxs-lookup"><span data-stu-id="71324-196">**Figure 4-47**.</span></span> <span data-ttu-id="71324-197">Представление имени реестра</span><span class="sxs-lookup"><span data-stu-id="71324-197">View of the name of the Registry</span></span>

<span data-ttu-id="71324-198">Кроме того, можно выполнить следующую команду:</span><span class="sxs-lookup"><span data-stu-id="71324-198">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Выходные данные консоли для указанной выше команды.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="71324-200">**Рис. 4-48**.</span><span class="sxs-lookup"><span data-stu-id="71324-200">**Figure 4-48**.</span></span> <span data-ttu-id="71324-201">Получение имени реестра с помощью **az cli**</span><span class="sxs-lookup"><span data-stu-id="71324-201">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="71324-202">В обоих случаях вы получите нужное имя.</span><span class="sxs-lookup"><span data-stu-id="71324-202">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="71324-203">В нашем примере это `exploredocker.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="71324-203">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="71324-204">Теперь вы можете пометить образ, используя самый последний образ (образ выпуска), с помощью команды:</span><span class="sxs-lookup"><span data-stu-id="71324-204">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="71324-205">После выполнения команды `docker tag` выведите список образов с помощью команды `docker images`, при этом вы должны увидеть образ с новым тегом.</span><span class="sxs-lookup"><span data-stu-id="71324-205">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Выходные данные команды docker images в консоли.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="71324-207">**Рис. 4-49**.</span><span class="sxs-lookup"><span data-stu-id="71324-207">**Figure 4-49**.</span></span> <span data-ttu-id="71324-208">Представление помеченных образов</span><span class="sxs-lookup"><span data-stu-id="71324-208">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="71324-209">Отправка образа в Azure ACR</span><span class="sxs-lookup"><span data-stu-id="71324-209">Push the image into the Azure ACR</span></span>

<span data-ttu-id="71324-210">Войдите в Реестр контейнеров Azure:</span><span class="sxs-lookup"><span data-stu-id="71324-210">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="71324-211">Отправьте образ в Реестр контейнеров Azure с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="71324-211">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="71324-212">Этой команде требуется некоторое время на отправку образа, при этом она предоставляет вам сведения о выполняемой операции.</span><span class="sxs-lookup"><span data-stu-id="71324-212">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="71324-213">На следующем рисунке видно, что выходные данные одного изображения готовы, а другие еще выполняются.</span><span class="sxs-lookup"><span data-stu-id="71324-213">In the following image, you can see the output from one image completed and another in progress.</span></span>

![Выходные данные команды docker push в консоли.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="71324-215">**Рис. 4-50**.</span><span class="sxs-lookup"><span data-stu-id="71324-215">**Figure 4-50**.</span></span> <span data-ttu-id="71324-216">Выходные данные консоли для команды push.</span><span class="sxs-lookup"><span data-stu-id="71324-216">Console output from the push command.</span></span>

<span data-ttu-id="71324-217">Чтобы развернуть многоконтейнерное приложение в кластере AKS, потребуется несколько файлов манифеста, `.yaml` файлы, которые имеют большую часть свойств, взятых из файлов `docker-compose.yml` и `docker-compose.override.yml`.</span><span class="sxs-lookup"><span data-stu-id="71324-217">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> <span data-ttu-id="71324-218">Предыдущие файлы `.yml` включают только порты `HTTP` с помощью параметра `ASPNETCORE_URLS`, чтобы избежать проблем с отсутствующим сертификатом в примере приложения.</span><span class="sxs-lookup"><span data-stu-id="71324-218">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="71324-219">Сведения о том, как создать кластер AKS для этого примера, см. в разделе [**Развертывание в службе Azure Kubernetes (AKS)**](deploy-azure-kubernetes-service.md) этого руководства.</span><span class="sxs-lookup"><span data-stu-id="71324-219">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="71324-220">Теперь почти все готово для развертывания с помощью **kubectl**, но сначала нужно получить учетные данные из кластера AKS с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="71324-220">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Выходные данные указанной выше команды в консоли: Объединено "explore-docker-aks" в качестве текущего контекста в C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="71324-222">**Рис. 4-51**.</span><span class="sxs-lookup"><span data-stu-id="71324-222">**Figure 4-51**.</span></span> <span data-ttu-id="71324-223">Получение учетных данных из AKS в среду kubectl.</span><span class="sxs-lookup"><span data-stu-id="71324-223">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="71324-224">Также необходимо разрешить кластеру AKS получать образы из ACR с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="71324-224">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="71324-225">Выполнение предыдущей команды может занять несколько минут.</span><span class="sxs-lookup"><span data-stu-id="71324-225">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="71324-226">Затем используйте команду `kubectl apply` для запуска развертываний, а затем — `kubectl get all` для получения списка объектов кластера.</span><span class="sxs-lookup"><span data-stu-id="71324-226">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Выходные данные консоли для указанной выше команды: развертывания применены.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="71324-229">**Рис. 4-52**.</span><span class="sxs-lookup"><span data-stu-id="71324-229">**Figure 4-52**.</span></span> <span data-ttu-id="71324-230">Развертывание в Kubernetes</span><span class="sxs-lookup"><span data-stu-id="71324-230">Deployment to Kubernetes</span></span>

<span data-ttu-id="71324-231">Подождите некоторое время, пока подсистема балансировки нагрузки не получит внешний IP-адрес, проверив `kubectl get services`, после чего приложение должно быть доступно по этому адресу, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="71324-231">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![Представление приложения, развернутого в AKS, в браузере](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="71324-233">**Рис. 4-53**.</span><span class="sxs-lookup"><span data-stu-id="71324-233">**Figure 4-53**.</span></span> <span data-ttu-id="71324-234">Развертывание в Kubernetes</span><span class="sxs-lookup"><span data-stu-id="71324-234">Deployment to Kubernetes</span></span>

<span data-ttu-id="71324-235">После завершения развертывания можно получить доступ к [веб-интерфейсу Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) с помощью локального прокси-сервера, используя туннель SSH.</span><span class="sxs-lookup"><span data-stu-id="71324-235">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="71324-236">Сначала необходимо создать ClusterRoleBinding с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="71324-236">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="71324-237">Чтобы запустить прокси-сервер, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="71324-237">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="71324-238">Окно браузера должно открыться в `http://127.0.0.1:8001` с представлением, аналогичным следующему:</span><span class="sxs-lookup"><span data-stu-id="71324-238">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Представление панели мониторинга Kubernetes в браузере, показывающее развертывания, объекты pod, наборы реплик и службы.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="71324-240">**Рис. 4-54**.</span><span class="sxs-lookup"><span data-stu-id="71324-240">**Figure 4-54**.</span></span> <span data-ttu-id="71324-241">Просмотр сведений о кластере Kubernetes</span><span class="sxs-lookup"><span data-stu-id="71324-241">View Kubernetes cluster information</span></span>

<span data-ttu-id="71324-242">Теперь у вас есть приложение ASP.NET Core, которое выполняется в контейнерах Linux и развернуто в кластере AKS в Azure.</span><span class="sxs-lookup"><span data-stu-id="71324-242">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="71324-243">Дополнительные сведения о развертывании с использованием Kubernetes см. в статье <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="71324-243">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="71324-244">[Назад](set-up-windows-containers-with-powershell.md)
> [Вперед](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="71324-244">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
