---
title: DOCKER-gRPC для разработчиков WCF
description: Создание образов DOCKER для ASP.NET Core приложений gRPC
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970093"
---
# <a name="create-docker-images"></a><span data-ttu-id="156e8-103">Создание образов DOCKER</span><span class="sxs-lookup"><span data-stu-id="156e8-103">Create Docker images</span></span>

<span data-ttu-id="156e8-104">В этом разделе рассматриваются создание образов DOCKER для приложений ASP.NET Core gRPC, готовых к работе в DOCKER, Kubernetes или в других средах контейнеров.</span><span class="sxs-lookup"><span data-stu-id="156e8-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="156e8-105">Пример приложения, используемый с веб-приложением ASP.NET Core MVC и службой gRPC, доступен в репозитории [DotNet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="156e8-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="156e8-106">Базовые образы Майкрософт для приложений ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="156e8-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="156e8-107">Корпорация Майкрософт предоставляет ряд базовых образов для создания и запуска приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="156e8-107">Microsoft provides a range of base images for building and running .NET applications.</span></span> <span data-ttu-id="156e8-108">Чтобы создать образ ASP.NET Core 5,0, используйте два базовых образа:</span><span class="sxs-lookup"><span data-stu-id="156e8-108">To create an ASP.NET Core 5.0 image, you use two base images:</span></span>

- <span data-ttu-id="156e8-109">Образ пакета SDK для сборки и публикации приложения.</span><span class="sxs-lookup"><span data-stu-id="156e8-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="156e8-110">Образ среды выполнения для развертывания.</span><span class="sxs-lookup"><span data-stu-id="156e8-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="156e8-111">Изображение</span><span class="sxs-lookup"><span data-stu-id="156e8-111">Image</span></span> | <span data-ttu-id="156e8-112">Описание</span><span class="sxs-lookup"><span data-stu-id="156e8-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="156e8-113">mcr.microsoft.com/dotnet/sdk</span><span class="sxs-lookup"><span data-stu-id="156e8-113">mcr.microsoft.com/dotnet/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-sdk/) | <span data-ttu-id="156e8-114">Для создания приложений с помощью `docker build` .</span><span class="sxs-lookup"><span data-stu-id="156e8-114">For building applications with `docker build`.</span></span> <span data-ttu-id="156e8-115">Не для использования в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="156e8-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="156e8-116">mcr.microsoft.com/dotnet/aspnet</span><span class="sxs-lookup"><span data-stu-id="156e8-116">mcr.microsoft.com/dotnet/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | <span data-ttu-id="156e8-117">Содержит зависимости среды выполнения и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="156e8-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="156e8-118">Для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="156e8-118">For production.</span></span> |

<span data-ttu-id="156e8-119">Для каждого образа существует четыре варианта, основанные на разных дистрибутивах Linux, различающихся по тегам.</span><span class="sxs-lookup"><span data-stu-id="156e8-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="156e8-120">Теги изображений</span><span class="sxs-lookup"><span data-stu-id="156e8-120">Image tag(s)</span></span> | <span data-ttu-id="156e8-121">Linux</span><span class="sxs-lookup"><span data-stu-id="156e8-121">Linux</span></span> | <span data-ttu-id="156e8-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="156e8-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="156e8-123">5,0-бустер-тонкий, 5,0</span><span class="sxs-lookup"><span data-stu-id="156e8-123">5.0-buster-slim, 5.0</span></span> | <span data-ttu-id="156e8-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="156e8-124">Debian 10</span></span> | <span data-ttu-id="156e8-125">Изображение по умолчанию, если не указан вариант ОС.</span><span class="sxs-lookup"><span data-stu-id="156e8-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="156e8-126">5,0-Alpine</span><span class="sxs-lookup"><span data-stu-id="156e8-126">5.0-alpine</span></span> | <span data-ttu-id="156e8-127">Alpine 3,12</span><span class="sxs-lookup"><span data-stu-id="156e8-127">Alpine 3.12</span></span> | <span data-ttu-id="156e8-128">Базовые образы Alpine намного меньше, чем Debian или Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="156e8-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="156e8-129">5,0 — фокус</span><span class="sxs-lookup"><span data-stu-id="156e8-129">5.0-focal</span></span>| <span data-ttu-id="156e8-130">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="156e8-130">Ubuntu 20.04</span></span> | |

<span data-ttu-id="156e8-131">Базовый образ Alpine составляет около 100 МБ по сравнению с 200 МБ для образов Debian и Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="156e8-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="156e8-132">Некоторые программные пакеты или библиотеки могут быть недоступны в управлении пакетами Alpine.</span><span class="sxs-lookup"><span data-stu-id="156e8-132">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="156e8-133">Если вы не знаете, какой образ следует использовать, то, вероятно, вам нужно выбрать Debian по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="156e8-133">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="156e8-134">Убедитесь, что для сборки и среды выполнения используется один и тот же вариант Linux.</span><span class="sxs-lookup"><span data-stu-id="156e8-134">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="156e8-135">Приложения, созданные и опубликованные на одном варианте, могут не работать на другом.</span><span class="sxs-lookup"><span data-stu-id="156e8-135">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="156e8-136">Создайте образ Docker.</span><span class="sxs-lookup"><span data-stu-id="156e8-136">Create a Docker image</span></span>

<span data-ttu-id="156e8-137">Образ DOCKER определяется *Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="156e8-137">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="156e8-138">Этот *Dockerfile* представляет собой текстовый файл, содержащий все команды, необходимые для создания приложения, и установки всех зависимостей, необходимых для сборки или запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="156e8-138">This *Dockerfile* is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="156e8-139">В следующем примере показан самый простой Dockerfile для приложения ASP.NET Core 5,0:</span><span class="sxs-lookup"><span data-stu-id="156e8-139">The following example shows the simplest Dockerfile for an ASP.NET Core 5.0 application:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="156e8-140">Dockerfile состоит из двух частей: первый использует `sdk` базовый образ для сборки и публикации приложения, второй создает образ среды выполнения из `aspnet` базы.</span><span class="sxs-lookup"><span data-stu-id="156e8-140">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="156e8-141">Это связано с тем `sdk` , что изображение составляет около 900 МБ по сравнению с 200 МБ для образа среды выполнения, и большая часть его содержимого не требуется во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="156e8-141">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="156e8-142">Этапы сборки</span><span class="sxs-lookup"><span data-stu-id="156e8-142">The build steps</span></span>

| <span data-ttu-id="156e8-143">Шаг</span><span class="sxs-lookup"><span data-stu-id="156e8-143">Step</span></span> | <span data-ttu-id="156e8-144">Описание</span><span class="sxs-lookup"><span data-stu-id="156e8-144">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="156e8-145">Объявляет базовый образ и присваивает ему `builder` псевдоним.</span><span class="sxs-lookup"><span data-stu-id="156e8-145">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="156e8-146">Создает `/src` каталог и задает его в качестве текущего рабочего каталога.</span><span class="sxs-lookup"><span data-stu-id="156e8-146">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="156e8-147">Копирует все, что находится под текущим каталогом на узле, в текущий каталог на образе.</span><span class="sxs-lookup"><span data-stu-id="156e8-147">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="156e8-148">Восстанавливает все внешние пакеты (ASP.NET Core 3,0 Framework предварительно устанавливается вместе с пакетом SDK).</span><span class="sxs-lookup"><span data-stu-id="156e8-148">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="156e8-149">Создает и публикует сборку выпуска.</span><span class="sxs-lookup"><span data-stu-id="156e8-149">Builds and publishes a Release build.</span></span> <span data-ttu-id="156e8-150">Обратите внимание, что `--runtime` флаг не требуется.</span><span class="sxs-lookup"><span data-stu-id="156e8-150">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="156e8-151">Шаги образа среды выполнения</span><span class="sxs-lookup"><span data-stu-id="156e8-151">The runtime image steps</span></span>

| <span data-ttu-id="156e8-152">Шаг</span><span class="sxs-lookup"><span data-stu-id="156e8-152">Step</span></span> | <span data-ttu-id="156e8-153">Описание</span><span class="sxs-lookup"><span data-stu-id="156e8-153">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="156e8-154">Объявляет новый базовый образ.</span><span class="sxs-lookup"><span data-stu-id="156e8-154">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="156e8-155">Создает `/app` каталог и задает его в качестве текущего рабочего каталога.</span><span class="sxs-lookup"><span data-stu-id="156e8-155">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="156e8-156">Копирует опубликованное приложение из предыдущего образа, используя `builder` псевдоним из первой `FROM` строки.</span><span class="sxs-lookup"><span data-stu-id="156e8-156">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="156e8-157">Задает выполнение команды при запуске контейнера.</span><span class="sxs-lookup"><span data-stu-id="156e8-157">Sets the command to run when the container starts.</span></span> <span data-ttu-id="156e8-158">`dotnet`Команда в образе среды выполнения может запускать только DLL-файлы.</span><span class="sxs-lookup"><span data-stu-id="156e8-158">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="156e8-159">HTTPS в DOCKER</span><span class="sxs-lookup"><span data-stu-id="156e8-159">HTTPS in Docker</span></span>

<span data-ttu-id="156e8-160">Базовые образы Майкрософт для DOCKER задают `ASPNETCORE_URLS` для переменной среды значение `http://+:80` , означающее, что Kestrel выполняется без протокола HTTPS для этого порта.</span><span class="sxs-lookup"><span data-stu-id="156e8-160">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="156e8-161">Если вы используете протокол HTTPS с пользовательским сертификатом (как описано в разделе Локальные [приложения gRPC](self-hosted.md)), следует переопределить эту конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="156e8-161">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this configuration.</span></span> <span data-ttu-id="156e8-162">Задайте переменную среды в части Dockerfile, созданной в образе среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="156e8-162">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="156e8-163">Файл dockerignore</span><span class="sxs-lookup"><span data-stu-id="156e8-163">The .dockerignore file</span></span>

<span data-ttu-id="156e8-164">Во многом подобно `.gitignore` файлам, которые исключают определенные файлы и каталоги из системы управления версиями, `.dockerignore` файл можно использовать для исключения копирования файлов и каталогов в образ во время сборки.</span><span class="sxs-lookup"><span data-stu-id="156e8-164">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="156e8-165">Этот файл не только экономит время, но также может избежать некоторых ошибок, возникающих при `obj` копировании каталога с компьютера в образ.</span><span class="sxs-lookup"><span data-stu-id="156e8-165">This file not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="156e8-166">Как минимум, необходимо добавить в файл записи для `bin` и `obj` `.dockerignore` .</span><span class="sxs-lookup"><span data-stu-id="156e8-166">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="156e8-167">Создание образа</span><span class="sxs-lookup"><span data-stu-id="156e8-167">Build the image</span></span>

<span data-ttu-id="156e8-168">Для `StockKube.sln` решения, содержащего два разных приложения `StockData` и `StockWeb` , проще всего разместить Dockerfile для каждого из них в базовом каталоге.</span><span class="sxs-lookup"><span data-stu-id="156e8-168">For a `StockKube.sln` solution containing two different applications `StockData` and `StockWeb`, it's simplest to put the Dockerfile for each one of them in the base directory.</span></span> <span data-ttu-id="156e8-169">В этом случае для создания образа используйте следующую `docker build` команду из того же каталога, в котором `.sln` находится файл.</span><span class="sxs-lookup"><span data-stu-id="156e8-169">In that case, to build the image, use the following `docker build` command from the same directory where `.sln` file resides.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

<span data-ttu-id="156e8-170">Флаг с непонятным именем `--tag` (который можно сократить до `-t` ) задает полное имя изображения, включая фактический тег, если он указан.</span><span class="sxs-lookup"><span data-stu-id="156e8-170">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="156e8-171">В `.` конце указывается контекст, в котором будет выполняться сборка; текущий рабочий каталог для `COPY` команд в Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="156e8-171">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="156e8-172">Если в одном решении имеется несколько приложений, Dockerfile можно разместить для каждого приложения в отдельной папке рядом с `.csproj` файлом.</span><span class="sxs-lookup"><span data-stu-id="156e8-172">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="156e8-173">Необходимо по-прежнему выполнить `docker build` команду из базового каталога, чтобы убедиться, что решение и все проекты скопированы в образ.</span><span class="sxs-lookup"><span data-stu-id="156e8-173">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="156e8-174">Можно указать Dockerfile под текущим каталогом с помощью `--file` `-f` флага (или).</span><span class="sxs-lookup"><span data-stu-id="156e8-174">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="156e8-175">Запуск образа в контейнере на компьютере</span><span class="sxs-lookup"><span data-stu-id="156e8-175">Run the image in a container on your machine</span></span>

<span data-ttu-id="156e8-176">Чтобы запустить образ в локальном экземпляре DOCKER, используйте `docker run` команду.</span><span class="sxs-lookup"><span data-stu-id="156e8-176">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

<span data-ttu-id="156e8-177">`-ti`Флаг подключает текущий терминал к терминалу контейнера и выполняется в интерактивном режиме.</span><span class="sxs-lookup"><span data-stu-id="156e8-177">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="156e8-178">`-p 5000:80`Порт 80 в контейнере публикуется (Links) для порта 5000 на сетевом интерфейсе localhost.</span><span class="sxs-lookup"><span data-stu-id="156e8-178">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="156e8-179">Отправка образа в реестр</span><span class="sxs-lookup"><span data-stu-id="156e8-179">Push the image to a registry</span></span>

<span data-ttu-id="156e8-180">Убедившись, что образ работает, отправьте его в реестр DOCKER, чтобы сделать доступным в других системах.</span><span class="sxs-lookup"><span data-stu-id="156e8-180">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="156e8-181">Внутренним сетям потребуется подготавливать реестр DOCKER.</span><span class="sxs-lookup"><span data-stu-id="156e8-181">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="156e8-182">Это действие может выполняться так же просто, как и [собственный `registry` образ DOCKER](https://docs.docker.com/registry/deploying/) (реестр DOCKER выполняется в контейнере DOCKER), но доступны различные более комплексные решения.</span><span class="sxs-lookup"><span data-stu-id="156e8-182">This activity can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="156e8-183">Для внешнего общего доступа и использования в облаке доступны различные управляемые реестры, такие как [Реестр контейнеров Azure](/azure/container-registry/) или [DOCKER Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="156e8-183">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="156e8-184">Чтобы отправить в центр DOCKER, перед именем образа необходимо указать имя пользователя или организации.</span><span class="sxs-lookup"><span data-stu-id="156e8-184">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

<span data-ttu-id="156e8-185">Чтобы отправить в частный реестр, добавьте перед именем образа имя узла реестра и имя Организации.</span><span class="sxs-lookup"><span data-stu-id="156e8-185">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

<span data-ttu-id="156e8-186">После того как образ находится в реестре, его можно развернуть на отдельных узлах DOCKER или в подсистеме оркестрации контейнеров, например Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="156e8-186">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="156e8-187">[Назад](self-hosted.md)
>[Вперед](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="156e8-187">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
