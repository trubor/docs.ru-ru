---
title: Определение многоконтейнерного приложения с помощью docker-compose.yml
description: Как указать композицию микрослужб для многоконтейнерного приложения с помощью docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: c375d328ab9064315682fab91cb5e49e9a384b56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682670"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="0b733-103">Определение многоконтейнерного приложения с помощью docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="0b733-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="0b733-104">В данном руководстве файл [docker-compose.yml](https://docs.docker.com/compose/compose-file/) был представлен в разделе [Шаг 4. Определение служб в файле docker-compose.yml при сборке многоконтейнерного приложения Docker](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="0b733-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="0b733-105">Тем не менее существуют дополнительные способы использования файлов docker-compose, которые стоит изучить более подробно.</span><span class="sxs-lookup"><span data-stu-id="0b733-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="0b733-106">Например, в файле docker-compose.yml вы можете явно описать, как следует развертывать ваше многоконтейнерное приложение.</span><span class="sxs-lookup"><span data-stu-id="0b733-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="0b733-107">При необходимости также можно описать, как вы планируете собирать свои пользовательские образы Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="0b733-108">(Пользовательские образы Docker можно также собрать с помощью Docker CLI.)</span><span class="sxs-lookup"><span data-stu-id="0b733-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="0b733-109">В сущности, вы определяете каждый из контейнеров, которые планируете развернуть, и конкретные характеристики для каждого развертывания контейнера.</span><span class="sxs-lookup"><span data-stu-id="0b733-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="0b733-110">Создав файл описания многоконтейнерного развертывания, вы можете развернуть все решение в одном действии, управляемом командой CLI [docker-compose up](https://docs.docker.com/compose/overview/), или развернуть решение прозрачно из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b733-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="0b733-111">В противном случае придется использовать Docker CLI, чтобы разворачивать контейнер за контейнером в несколько этапов с помощью команды `docker run` из командной строки.</span><span class="sxs-lookup"><span data-stu-id="0b733-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="0b733-112">Таким образом, для каждой службы, определенной в файле docker-compose.yml, необходимо указать ровно один образ или сборку.</span><span class="sxs-lookup"><span data-stu-id="0b733-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="0b733-113">Остальные ключи являются необязательными и соответствуют своим аналогам в командной строке `docker run`.</span><span class="sxs-lookup"><span data-stu-id="0b733-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="0b733-114">В следующем примере кода YAML представлено определение возможно глобального, но единственного файла docker-compose.yml для примера eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0b733-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="0b733-115">Это ненастоящий файл docker-compose из eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0b733-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="0b733-116">Это упрощенная и объединенная в один файл версия, представляющая не лучший способ работы с файлами docker-compose, как будет показано ниже.</span><span class="sxs-lookup"><span data-stu-id="0b733-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="0b733-117">Корневой ключ в этом файле — services.</span><span class="sxs-lookup"><span data-stu-id="0b733-117">The root key in this file is services.</span></span> <span data-ttu-id="0b733-118">Под этим ключом определяются службы, которые требуется развернуть и запустить при выполнении команды `docker-compose up` или при развертывании из Visual Studio с помощью этого файла docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0b733-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="0b733-119">В данном случае в файле docker-compose.yml определено несколько служб, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="0b733-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="0b733-120">Имя службы</span><span class="sxs-lookup"><span data-stu-id="0b733-120">Service name</span></span> | <span data-ttu-id="0b733-121">Описание</span><span class="sxs-lookup"><span data-stu-id="0b733-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="0b733-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="0b733-122">webmvc</span></span>       | <span data-ttu-id="0b733-123">Контейнер, включающий приложение MVC ASP.NET Core и использующий микрослужбы из C\# на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="0b733-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="0b733-124">catalog-api</span><span class="sxs-lookup"><span data-stu-id="0b733-124">catalog-api</span></span>  | <span data-ttu-id="0b733-125">Контейнер, включающий микрослужбу Catalog веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b733-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="0b733-126">ordering-api</span><span class="sxs-lookup"><span data-stu-id="0b733-126">ordering-api</span></span> | <span data-ttu-id="0b733-127">Контейнер, включающий микрослужбу Ordering веб-API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0b733-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="0b733-128">sqldata</span><span class="sxs-lookup"><span data-stu-id="0b733-128">sqldata</span></span>     | <span data-ttu-id="0b733-129">Контейнер, запускающий SQL Server для Linux, в котором содержатся базы данных микрослужб.</span><span class="sxs-lookup"><span data-stu-id="0b733-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="0b733-130">basket-api</span><span class="sxs-lookup"><span data-stu-id="0b733-130">basket-api</span></span>   | <span data-ttu-id="0b733-131">Контейнер с микрослужбой Basket веб-API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0b733-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="0b733-132">basketdata</span><span class="sxs-lookup"><span data-stu-id="0b733-132">basketdata</span></span>  | <span data-ttu-id="0b733-133">Контейнер, запускающий службу кэша REDIS, с базой данных basket в качестве кэша REDIS.</span><span class="sxs-lookup"><span data-stu-id="0b733-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="0b733-134">Простой контейнер API веб-службы</span><span class="sxs-lookup"><span data-stu-id="0b733-134">A simple Web Service API container</span></span>

<span data-ttu-id="0b733-135">Рассмотрим один контейнер. Контейнер-микрослужба catalog-api имеет простое определение:</span><span class="sxs-lookup"><span data-stu-id="0b733-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="0b733-136">Эта контейнерная служба имеет следующую базовую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="0b733-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="0b733-137">Она основывается на пользовательском образе **eshop/catalog-api**.</span><span class="sxs-lookup"><span data-stu-id="0b733-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="0b733-138">Проще говоря, в файле не задан ключ build:.</span><span class="sxs-lookup"><span data-stu-id="0b733-138">For simplicity's sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="0b733-139">Это означает, что образ должен быть предварительно создан (с помощью команды docker build) или загружен (с помощью команды docker pull) из любого реестра Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="0b733-140">Она определяет переменную среды с именем ConnectionString со строкой подключения, которая должна использоваться Entity Framework для доступа к экземпляру SQL Server, содержащему модель данных каталога.</span><span class="sxs-lookup"><span data-stu-id="0b733-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="0b733-141">В данном случае в одном контейнере SQL Server содержатся несколько баз данных.</span><span class="sxs-lookup"><span data-stu-id="0b733-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="0b733-142">Поэтому на компьютере разработки потребуется меньше памяти для Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="0b733-143">Однако можно было бы также развернуть по одному контейнеру SQL Server для каждой базы данных микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="0b733-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="0b733-144">Имя SQL Server — **sqldata**. Это же имя используется для контейнера, в котором выполняется экземпляр SQL Server для Linux.</span><span class="sxs-lookup"><span data-stu-id="0b733-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="0b733-145">Это удобно: благодаря данной возможности служба разрешения имен (внутренняя для узла Docker) разрешит сетевой адрес, так что вам не нужно знать внутренний IP-адрес для контейнеров при обращении к ним из других контейнеров.</span><span class="sxs-lookup"><span data-stu-id="0b733-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don't need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="0b733-146">Так как строка подключения определяется переменной среды, можно задавать эту переменную посредством другого механизма и в другое время.</span><span class="sxs-lookup"><span data-stu-id="0b733-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="0b733-147">Например, можно задать другую строку подключения при развертывании в рабочей среде на финальных узлах или сделать это из конвейеров CI/CD в Azure DevOps Services или в другой предпочитаемой системе DevOps.</span><span class="sxs-lookup"><span data-stu-id="0b733-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="0b733-148">Она представляет порт 80 для внутреннего доступа к службе **catalog-api** в узле Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="0b733-149">В данном случае этот узел является виртуальной машиной Linux, так как он основан на образе Docker для Linux, но можно настроить контейнер для запуска в образе Windows.</span><span class="sxs-lookup"><span data-stu-id="0b733-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="0b733-150">Она переадресует предоставленный порт 80 в порт 5101 на хост-компьютере Docker (виртуальной машине Linux).</span><span class="sxs-lookup"><span data-stu-id="0b733-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="0b733-151">Она связывает веб-службу со службой **sqldata** (экземпляром SQL Server для базы данных Linux, запущенным в контейнере).</span><span class="sxs-lookup"><span data-stu-id="0b733-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="0b733-152">Если вы указываете эту зависимость, контейнер catalog-api не будет запускаться до запуска контейнера sqldata. Это важно, поскольку для catalog-api требуется уже запущенная база данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0b733-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="0b733-153">Тем не менее во многих случаях недостаточно использовать этот вид зависимости контейнера, так как Docker выполняет проверку только на уровне контейнера.</span><span class="sxs-lookup"><span data-stu-id="0b733-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="0b733-154">Иногда служба (в данном случае SQL Server) может быть еще не готова, поэтому рекомендуется реализовать в клиентских микрослужбах логику повторов с экспоненциальным отходом.</span><span class="sxs-lookup"><span data-stu-id="0b733-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="0b733-155">Таким образом, если контейнер зависимостей будет не готов в течение некоторого времени, приложение по-прежнему будет устойчивым.</span><span class="sxs-lookup"><span data-stu-id="0b733-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="0b733-156">Она настроена для разрешения доступа к внешним серверам: параметр extra\_hosts позволяет получать доступ к внешним серверам или компьютерам за пределами узла Docker (то есть за пределами виртуальной машины Linux по умолчанию, которая является узлом разработки Docker), таким как локальный экземпляр SQL Server на компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="0b733-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="0b733-157">В файле `docker-compose.yml` также есть другие, более сложные параметры, которые мы рассмотрим в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="0b733-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="0b733-158">Использование файлов docker-compose для нескольких сред</span><span class="sxs-lookup"><span data-stu-id="0b733-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="0b733-159">Файлы `docker-compose.*.yml` — это файлы определения. Они могут использоваться несколькими инфраструктурами, которые распознают этот формат.</span><span class="sxs-lookup"><span data-stu-id="0b733-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="0b733-160">Самым простым средством является команда docker-compose.</span><span class="sxs-lookup"><span data-stu-id="0b733-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="0b733-161">Таким образом, используя команду docker-compose, вы можете реализовать следующие основные сценарии.</span><span class="sxs-lookup"><span data-stu-id="0b733-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="0b733-162">Среды разработки</span><span class="sxs-lookup"><span data-stu-id="0b733-162">Development environments</span></span>

<span data-ttu-id="0b733-163">При разработке приложений важно иметь возможность запускать приложение в изолированной среде разработки.</span><span class="sxs-lookup"><span data-stu-id="0b733-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="0b733-164">Вы можете создать такую среду с помощью команды CLI docker-compose или использовать Visual Studio, в котором команда docker-compose применяется внутренним образом.</span><span class="sxs-lookup"><span data-stu-id="0b733-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="0b733-165">Файл docker-compose.yml позволяет настраивать и документировать все зависимости служб вашего приложения (другие службы, кэш, базы данных, очереди и т. п.).</span><span class="sxs-lookup"><span data-stu-id="0b733-165">The docker-compose.yml file allows you to configure and document all your application's service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="0b733-166">С помощью команды CLI docker-compose вы можете создавать и запускать один или несколько контейнеров для каждой зависимости одной командой (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="0b733-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="0b733-167">Файлы docker-compose.yml — это файлы конфигурации, интерпретированные подсистемой Docker, но они также служат в качестве удобных файлов документирования сведений о составе вашего многоконтейнерного приложения.</span><span class="sxs-lookup"><span data-stu-id="0b733-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="0b733-168">Тестовые среды</span><span class="sxs-lookup"><span data-stu-id="0b733-168">Testing environments</span></span>

<span data-ttu-id="0b733-169">Важной частью любого процесса непрерывного развертывания (CD) или непрерывной интеграции (CI) являются модульные тесты и интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="0b733-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="0b733-170">Для этих автоматических тестов требуется изолированная среда, чтобы на них не влияли пользователи или какие-либо изменения данных в приложении.</span><span class="sxs-lookup"><span data-stu-id="0b733-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application's data.</span></span>

<span data-ttu-id="0b733-171">Используя Docker Compose, можно очень просто создавать и уничтожать такую изолированную среду с помощью нескольких команд, выполненных в командной строке, или скриптов, например, с помощью следующих команд:</span><span class="sxs-lookup"><span data-stu-id="0b733-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="0b733-172">Рабочие развертывания</span><span class="sxs-lookup"><span data-stu-id="0b733-172">Production deployments</span></span>

<span data-ttu-id="0b733-173">Команду Compose можно также использовать для развертывания в удаленной подсистеме Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="0b733-174">Типичный случай — развертывание на один экземпляр узла Docker (такой как рабочая виртуальная машина или сервер с установленной [машиной Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="0b733-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="0b733-175">При использовании любых других оркестраторов (Azure Service Fabric, Kubernetes и т. п.) может потребоваться добавить параметры настройки и конфигурации метаданных, аналогичные имеющимся в файле docker-compose.yml, но в формате, необходимом для этого другого оркестратора.</span><span class="sxs-lookup"><span data-stu-id="0b733-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="0b733-176">В любом случае docker-compose является удобным инструментом и форматом метаданных для рабочих процессов развертывания, тестирования и работы, хотя рабочий процесс работы может отличаться в зависимости от используемого оркестратора.</span><span class="sxs-lookup"><span data-stu-id="0b733-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="0b733-177">Использование нескольких файлов docker-compose для обработки разных сред</span><span class="sxs-lookup"><span data-stu-id="0b733-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="0b733-178">Если планируются разные среды, необходимо использовать несколько файлов compose.</span><span class="sxs-lookup"><span data-stu-id="0b733-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="0b733-179">Это позволяет создать несколько вариантов конфигурации в зависимости от среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="0b733-180">Переопределение базового файла docker-compose</span><span class="sxs-lookup"><span data-stu-id="0b733-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="0b733-181">Вы можете использовать единственный файл docker-compose.yml, как показано в упрощенных примерах, приведенных в предыдущих разделах.</span><span class="sxs-lookup"><span data-stu-id="0b733-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="0b733-182">Однако для большинства приложений это не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="0b733-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="0b733-183">По умолчанию Compose читает два файла, docker-compose.yml и дополнительный файл docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="0b733-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="0b733-184">Как показано на рисунке 6-11, если вы работаете в Visual Studio и включаете поддержку Docker, Visual Studio при этом создает дополнительный файл docker-compose.vs.debug.g.yml для отладки приложения, вы можете просмотреть этот файл в папке obj\\Docker\\ в главной папке решения.</span><span class="sxs-lookup"><span data-stu-id="0b733-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Файлы в проекте docker-compose.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="0b733-186">**Рис. 6-11**.</span><span class="sxs-lookup"><span data-stu-id="0b733-186">**Figure 6-11**.</span></span> <span data-ttu-id="0b733-187">Файлы docker-compose в Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="0b733-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="0b733-188">Структура файлов проекта **docker-compose**:</span><span class="sxs-lookup"><span data-stu-id="0b733-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="0b733-189">*.dockerignore* — используется для пропуска файлов.</span><span class="sxs-lookup"><span data-stu-id="0b733-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="0b733-190">*docker-compose.yml* — используется для создания микрослужб.</span><span class="sxs-lookup"><span data-stu-id="0b733-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="0b733-191">*docker-compose.override.yml* — используется для настройки среды микрослужб.</span><span class="sxs-lookup"><span data-stu-id="0b733-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="0b733-192">Файлы docker-compose можно изменить в любом редакторе, например в Visual Studio Code или Sublime, и запустить приложение с помощью команды docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="0b733-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="0b733-193">По определению файл docker-compose.yml содержит базовую конфигурацию и другие статические параметры.</span><span class="sxs-lookup"><span data-stu-id="0b733-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="0b733-194">Это означает, что конфигурация службы не должна изменяться в зависимости от целевой среды развертывания.</span><span class="sxs-lookup"><span data-stu-id="0b733-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="0b733-195">Файл docker-compose.override.yml, как следует из его имени, содержит параметры конфигурации, которые переопределяют базовую конфигурацию, например конфигурацию, зависящую от среды развертывания.</span><span class="sxs-lookup"><span data-stu-id="0b733-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="0b733-196">У вас может быть несколько файлов переопределения с разными именами.</span><span class="sxs-lookup"><span data-stu-id="0b733-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="0b733-197">Файлы переопределения обычно содержат дополнительные сведения, необходимые для приложения, но относящиеся к конкретной среде или развертыванию.</span><span class="sxs-lookup"><span data-stu-id="0b733-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="0b733-198">Планирование нескольких сред</span><span class="sxs-lookup"><span data-stu-id="0b733-198">Targeting multiple environments</span></span>

<span data-ttu-id="0b733-199">Распространенный вариант использования заключается в том, что определяется несколько файлов compose, чтобы можно было планировать несколько сред, таких как рабочая среда, промежуточная среда, среда CI или среда разработки.</span><span class="sxs-lookup"><span data-stu-id="0b733-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="0b733-200">Для поддержки этих разных сред можно разделить конфигурацию Compose на несколько файлов, как показано на рисунке 6-12.</span><span class="sxs-lookup"><span data-stu-id="0b733-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Схема трех файлов docker-compose, которые задаются для переопределения базового файла.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="0b733-202">**Рис. 6-12**.</span><span class="sxs-lookup"><span data-stu-id="0b733-202">**Figure 6-12**.</span></span> <span data-ttu-id="0b733-203">Несколько файлов docker-compose, переопределяющих значения в базовом файле docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="0b733-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="0b733-204">Вы можете использовать комбинацию нескольких файлов docker-compose\*.yml для работы в разных средах.</span><span class="sxs-lookup"><span data-stu-id="0b733-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="0b733-205">Вы начинаете с базового файла docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0b733-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="0b733-206">Этот базовый файл содержит базовые или статические параметры конфигурации, которые не изменяются в зависимости от среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-206">This base file contains the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="0b733-207">Например, приложение eShopOnContainers имеет в качестве базового файла следующий файл docker-compose.yml (упрощен путем уменьшения числа служб).</span><span class="sxs-lookup"><span data-stu-id="0b733-207">For example, the eShopOnContainers app has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="0b733-208">Значения в базовом файле docker-compose.yml не должны изменяться из-за разных целевых сред развертывания.</span><span class="sxs-lookup"><span data-stu-id="0b733-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="0b733-209">Если рассмотреть, например, определение службы webmvc, то можно увидеть, что эта информация большей частью одинакова независимо от планируемой среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="0b733-210">В этом определении содержится следующая информация.</span><span class="sxs-lookup"><span data-stu-id="0b733-210">You have the following information:</span></span>

- <span data-ttu-id="0b733-211">Имя службы: webmvc.</span><span class="sxs-lookup"><span data-stu-id="0b733-211">The service name: webmvc.</span></span>

- <span data-ttu-id="0b733-212">Пользовательский образ контейнера: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="0b733-212">The container's custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="0b733-213">Команда для создания пользовательского образа Docker, указывающая, какой Dockerfile следует использовать.</span><span class="sxs-lookup"><span data-stu-id="0b733-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="0b733-214">Зависимости от других служб, чтобы данный контейнер не запускался до запуска других контейнеров зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0b733-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="0b733-215">У вас могут быть дополнительные параметры конфигурации, но суть в том, что в базовом файле docker-compose.yml вы просто задаете ту информацию, которая является общей для всех сред.</span><span class="sxs-lookup"><span data-stu-id="0b733-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="0b733-216">Затем в файле docker-compose.override.yml или в аналогичных файлах для рабочей или промежуточной среды необходимо указать конфигурацию, характерную для каждой среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="0b733-217">Обычно файл docker-compose.override.yml используется для среды разработки, как в следующем примере из eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0b733-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="0b733-218">В этом примере конфигурация переопределения для среды разработки представляет некоторые порты для узла, задает переменные среды с URL-адресами перенаправления, а также указывает строки подключения для среды разработки.</span><span class="sxs-lookup"><span data-stu-id="0b733-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="0b733-219">Все эти параметры предназначены только для среды разработки.</span><span class="sxs-lookup"><span data-stu-id="0b733-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="0b733-220">При выполнении команды `docker-compose up` (или запуске ее из Visual Studio) эта команда считывает переопределения автоматически, как если бы оба файла были объединены.</span><span class="sxs-lookup"><span data-stu-id="0b733-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="0b733-221">Предположим, что требуется другой файл Compose для рабочей среды, с другими значениями конфигурации, портами или строками подключения.</span><span class="sxs-lookup"><span data-stu-id="0b733-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="0b733-222">Вы можете создать другой файл переопределения, например с именем `docker-compose.prod.yml`, содержащий другие параметры и переменные среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="0b733-223">Этот файл может храниться в другом репозитории Git или управляться и защищаться другой группой.</span><span class="sxs-lookup"><span data-stu-id="0b733-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="0b733-224">Развертывание с помощью конкретного файла переопределения</span><span class="sxs-lookup"><span data-stu-id="0b733-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="0b733-225">Чтобы использовать несколько файлов переопределения или файл переопределения с другим именем, можно указать эти файлы с помощью параметра -f в команде docker-compose.</span><span class="sxs-lookup"><span data-stu-id="0b733-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="0b733-226">Команда compose объединяет файлы в том порядке, в котором они указаны в командной строке.</span><span class="sxs-lookup"><span data-stu-id="0b733-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="0b733-227">В следующем примере показано, как выполняется развертывание с файлами переопределения.</span><span class="sxs-lookup"><span data-stu-id="0b733-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="0b733-228">Использование переменных среды в файлах docker-compose</span><span class="sxs-lookup"><span data-stu-id="0b733-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="0b733-229">Удобно, особенно в рабочих средах, иметь возможность получать сведения о конфигурации из переменных среды, как показано в предыдущих примерах.</span><span class="sxs-lookup"><span data-stu-id="0b733-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="0b733-230">Вы можете сослаться на переменную среды в файлах docker-compose делаются с помощью синтаксиса ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="0b733-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="0b733-231">Следующая строка из файла docker-compose.prod.yml показывает, как ссылаться на значение переменной среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="0b733-232">Переменные среды создаются и инициализируются разными способами в зависимости от среды узла (Linux, Windows, кластер Cloud и т. п.).</span><span class="sxs-lookup"><span data-stu-id="0b733-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="0b733-233">Однако рекомендуется использовать ENV-файл.</span><span class="sxs-lookup"><span data-stu-id="0b733-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="0b733-234">Файлы docker-compose поддерживает объявление переменных среды по умолчанию в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="0b733-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="0b733-235">Эти значения для переменных среды являются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b733-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="0b733-236">Однако они могут быть переопределены значениями, которые, возможно, заданы в каждой из сред (ОС узла или переменные среды из кластера).</span><span class="sxs-lookup"><span data-stu-id="0b733-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="0b733-237">Этот ENV-файл следует поместить в ту папку, из которой выполняется команда docker-compose.</span><span class="sxs-lookup"><span data-stu-id="0b733-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="0b733-238">В следующем примере показан ENV-файл, аналогичный [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env)-файлу для приложения eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0b733-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="0b733-239">Для команды docker-compose необходимо, чтобы каждая строка в ENV-файле была в формате \<variable\>=\<value\>.</span><span class="sxs-lookup"><span data-stu-id="0b733-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="0b733-240">Значения, установленные в среде выполнения, всегда переопределяют значения, определенные в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="0b733-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="0b733-241">Аналогичным образом значения, переданные с помощью аргументов командной строки, тоже переопределяют значения по умолчанию, заданные в ENV-файле.</span><span class="sxs-lookup"><span data-stu-id="0b733-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="0b733-242">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="0b733-242">Additional resources</span></span>

- <span data-ttu-id="0b733-243">**Общие сведения о Docker Compose** </span><span class="sxs-lookup"><span data-stu-id="0b733-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="0b733-244">**Несколько файлов Compose** </span><span class="sxs-lookup"><span data-stu-id="0b733-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="0b733-245">Создание оптимизированных образов Docker ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b733-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="0b733-246">Если вы изучаете Docker и .NET Core по источникам в Интернете, вы обнаружите файлы Dockerfile, демонстрирующие простоту создания образа Docker путем копирования источника в контейнер.</span><span class="sxs-lookup"><span data-stu-id="0b733-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="0b733-247">Эти примеры показывают, что, используя простую конфигурацию, можно получить образ Docker со средой, упакованной с приложением.</span><span class="sxs-lookup"><span data-stu-id="0b733-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="0b733-248">В следующем примере показан такой простой Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0b733-248">The following example shows a simple Dockerfile in this vein.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="0b733-249">Такой Dockerfile будет работать.</span><span class="sxs-lookup"><span data-stu-id="0b733-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="0b733-250">Тем не менее вы можете существенно оптимизировать ваши образы, особенно образы рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="0b733-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="0b733-251">В модели контейнера и микрослужб вы постоянно запускаете контейнеры.</span><span class="sxs-lookup"><span data-stu-id="0b733-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="0b733-252">Обычно контейнеры используются таким образом, чтобы не перезапускать спящий контейнер, так как контейнер является одноразовым.</span><span class="sxs-lookup"><span data-stu-id="0b733-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="0b733-253">Оркестраторы (такие как Kubernetes и Azure Service Fabric) просто создают экземпляры образов.</span><span class="sxs-lookup"><span data-stu-id="0b733-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="0b733-254">Это означает, что вам нужно будет выполнить оптимизацию путем предварительной компиляции приложения во время его сборки, чтобы ускорить процесс создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="0b733-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="0b733-255">Когда контейнер запускается, он должен быть готов к выполнению.</span><span class="sxs-lookup"><span data-stu-id="0b733-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="0b733-256">Не следует выполнять восстановление и компиляцию во время выполнения с помощью команд `dotnet restore` и `dotnet build` CLI, как показано в записях блога о .NET Core и Docker.</span><span class="sxs-lookup"><span data-stu-id="0b733-256">Don't restore and compile at run time using the `dotnet restore` and `dotnet build` CLI commands as you may see in blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="0b733-257">Команда .NET выполняет важнейшую работу, чтобы сделать .NET Core и ASP.NET Core платформой, оптимизированной для работы с контейнерами.</span><span class="sxs-lookup"><span data-stu-id="0b733-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="0b733-258">.NET Core является не только облегченной платформой с небольшим объемом памяти; команда разработчиков сконцентрировалась на оптимизированных образах Docker для трех основных сценариев и опубликовала их в реестре центра Docker по адресу *dotnet/core*, начиная с версии 2.1:</span><span class="sxs-lookup"><span data-stu-id="0b733-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="0b733-259">**Разработка**: приоритетной является возможность быстрой интеграции и отладки изменений, а размер вторичен.</span><span class="sxs-lookup"><span data-stu-id="0b733-259">**Development**: The priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="0b733-260">**Сборка**: приоритетным направлением является компиляция приложения, и образ включает двоичные файлы и другие зависимости для их оптимизации.</span><span class="sxs-lookup"><span data-stu-id="0b733-260">**Build**: The priority is compiling the application, and the image includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="0b733-261">**Рабочая среда**: основное внимание уделяется быстрому развертыванию и запуску контейнеров, поэтому эти образы ограничены двоичными файлами и содержимым, необходимыми для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="0b733-261">**Production**: The focus is fast deploying and starting of containers, so these images are limited to the binaries and content needed to run the application.</span></span>

<span data-ttu-id="0b733-262">Команда разработчиков .NET предоставляет в [dotnet/core](https://hub.docker.com/_/microsoft-dotnet/) (в Docker Hub) четыре основных варианта:</span><span class="sxs-lookup"><span data-stu-id="0b733-262">The .NET team provides four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet/) (at Docker Hub):</span></span>

1. <span data-ttu-id="0b733-263">**sdk**: для сценариев разработки и сборки;</span><span class="sxs-lookup"><span data-stu-id="0b733-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="0b733-264">**aspnet**: для производственных сценариев ASP.NET;</span><span class="sxs-lookup"><span data-stu-id="0b733-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="0b733-265">**runtime**: для производственных сценариев .NET;</span><span class="sxs-lookup"><span data-stu-id="0b733-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="0b733-266">**runtime-deps**: для сценария рабочей среды у [автономных приложений](../../../core/deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="0b733-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained)</span></span>

<span data-ttu-id="0b733-267">Чтобы ускорить запуск, образы среды выполнения также автоматически настраивают aspnetcore\_urls на порт 80 и использование Ngen для создания собственного кэша образов для сборок.</span><span class="sxs-lookup"><span data-stu-id="0b733-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="0b733-268">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="0b733-268">Additional resources</span></span>

- <span data-ttu-id="0b733-269">**Создание оптимизированных образов Docker в ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="0b733-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="0b733-270">**Создание образов Docker для приложений .NET Core**</span><span class="sxs-lookup"><span data-stu-id="0b733-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="0b733-271">[Назад](data-driven-crud-microservice.md)
> [Вперед](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="0b733-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
